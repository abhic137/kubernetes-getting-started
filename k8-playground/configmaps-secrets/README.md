Certainly, let's include ConfigMaps and Secrets in the simplified exercise. Here's a step-by-step guide:

**Step 1: Create a Deployment**

1. Create a file named `webapp-deployment.yaml` with the following content:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
        - name: webapp-container
          image: nginx:latest
          ports:
            - containerPort: 80
          env:
            - name: APP_CONFIG
              valueFrom:
                configMapKeyRef:
                  name: webapp-config
                  key: app.conf
            - name: DB_USERNAME
              valueFrom:
                secretKeyRef:
                  name: db-credentials
                  key: username
            - name: DB_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: db-credentials
                  key: password
```

2. Apply this deployment to your cluster:

```bash
kubectl apply -f webapp-deployment.yaml
```

**Step 2: Create ConfigMaps**

1. Create a file named `webapp-configmap.yaml` with the following content:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: webapp-config
data:
  app.conf: |
    server {
        listen 80;
        server_name localhost;
        location / {
            proxy_pass http://webapp-service;
        }
    }
```

2. Apply the ConfigMap:

```bash
kubectl apply -f webapp-configmap.yaml
```

**Step 3: Create Secrets**

1. Create a file named `webapp-secret.yaml` with the following content:

You can encode data in base64 using the following command:

bash
```
echo -n 'my-username' | base64
echo -n 'my-password' | base64
```
Replace <base64-encoded-username> and <base64-encoded-password> with the respective base64-encoded values.

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: db-credentials
type: Opaque
data:
  username: <base64-encoded-username>
  password: <base64-encoded-password>
```

Replace `<base64-encoded-username>` and `<base64-encoded-password>` with your actual credentials, base64 encoded.

2. Apply the Secrets:

```bash
kubectl apply -f webapp-secret.yaml
```

**Step 4: Port Forwarding**

1. To access your web application with ConfigMaps and Secrets, use port forwarding:

```bash
kubectl port-forward deployment/webapp-deployment 8080:80
```

**Step 5: Access the Web Application**

1. Open a web browser and navigate to `http://localhost:8080`. You should see the Nginx welcome page.

This exercise includes ConfigMaps and Secrets for configuration and sensitive data management, allowing you to access your web application with these settings through port forwarding on your local machine.
