Scenario: Deploy a Stateful Database

In this example, you'll deploy a stateful database, specifically an instance of MongoDB, using Kubernetes. MongoDB is a NoSQL database commonly used in containerized environments.

Components:

    StatefulSet: A Kubernetes StatefulSet resource is used to manage the stateful application (MongoDB). StatefulSets provide guarantees about the ordering and uniqueness of Pods. Each MongoDB instance will have a unique network identity and persistent storage.

    Service: A Kubernetes Service resource is used to expose the MongoDB instances within the cluster for communication between applications and the database.

Steps:

Step 1: Create a Docker Image

Create a Docker image for MongoDB or use an existing official MongoDB image from a container registry.

Step 2: Define Kubernetes StatefulSet

Create a Kubernetes StatefulSet YAML (mongodb-statefulset.yaml) to define the StatefulSet:

yaml

apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: mongodb
spec:
  serviceName: "mongodb-service"
  replicas: 3
  selector:
    matchLabels:
      app: mongodb
  template:
    metadata:
      labels:
        app: mongodb
    spec:
      containers:
      - name: mongodb-container
        image: mongo:latest
        ports:
        - containerPort: 27017
        volumeMounts:
        - name: mongo-storage
          mountPath: /data/db
  volumeClaimTemplates:
  - metadata:
      name: mongo-storage
    spec:
      accessModes: [ "ReadWriteOnce" ]
      storageClassName: "standard"
      resources:
        requests:
          storage: 1Gi

This YAML creates a StatefulSet for MongoDB with three replicas, each having its own persistent storage.

Step 3: Apply the StatefulSet

Apply the StatefulSet to your Kubernetes cluster:

bash

kubectl apply -f mongodb-statefulset.yaml

Step 4: Define a Kubernetes Service

Create a Kubernetes Service YAML (mongodb-service.yaml) to expose MongoDB instances within the cluster:

yaml

apiVersion: v1
kind: Service
metadata:
  name: mongodb-service
spec:
  selector:
    app: mongodb
  ports:
    - protocol: "TCP"
      port: 27017
      targetPort: 27017

This YAML creates a Service to expose the MongoDB instances.

Step 5: Apply the Service

Apply the Service to your Kubernetes cluster:

bash

kubectl apply -f mongodb-service.yaml

Step 6: Access MongoDB

You can access MongoDB within the cluster by connecting to the mongodb-service Service. You can use a MongoDB client or another application to interact with the database.

This example demonstrates how to deploy a stateful application, MongoDB, using Kubernetes. Kubernetes StatefulSets are designed for managing stateful applications and ensure that each instance has its own identity and storage, making them suitable for databases and other stateful workloads.
To access MongoDB deployed within your Kubernetes cluster, you can use a MongoDB client or another application. Here are the general steps to access MongoDB:

    Connect to a Pod: You can access MongoDB by connecting to one of the MongoDB pods running in your StatefulSet. However, you typically don't connect directly to individual pods in a production environment, as Kubernetes Services are used for this purpose.

    Use the Kubernetes Service: To access MongoDB, you should use the Kubernetes Service (mongodb-service) you defined in the previous steps. The Service provides a stable network endpoint that forwards traffic to the MongoDB pods.

Here's how you can access MongoDB using a common MongoDB client like mongo:

Prerequisites:

    Ensure you have the mongo client installed on your local machine.

Steps:

    Get the MongoDB Service IP and Port:

    You can get the IP address and port of the MongoDB Service by running:

    bash

kubectl get svc mongodb-service

Note the CLUSTER-IP and PORT values.

Connect to MongoDB:

Use the mongo client to connect to MongoDB. Replace <CLUSTER-IP> and <PORT> with the values from the previous step:

bash

mongo --host <CLUSTER-IP> --port <PORT>

For example:

bash

    mongo --host 10.100.200.3 --port 27017

    You are now connected to your MongoDB instance running inside the Kubernetes cluster. You can execute MongoDB commands and queries as needed.

Here are some common MongoDB commands you can run once connected:

    Show available databases: show dbs
    Switch to a specific database: use mydb
    List collections in the current database: show collections
    Insert a document into a collection: db.mycollection.insert({ key: 'value' })
    Query documents in a collection: db.mycollection.find()

Remember to replace mydb and mycollection with the actual database and collection names you are working with.

This approach allows you to access and interact with MongoDB in your Kubernetes cluster using a MongoDB client from your local machine.
