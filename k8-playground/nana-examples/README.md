```
kubectl apply -f mongo-secret.yaml
kubectl get secret

```
before creating the secret 
```
echo -n 'username' | base64
```
We always have to run the secret first and then we have to apply the deployment, we have to refer the secret in the deployment after running the secret yaml file.
```
kubectl apply -f mongo-deployment.yaml 
```
```
kubectl get all
```

```
kubectl describe service <Service_name>
```
create mongo express deployment

create configmap for the following to allow the services to communicate.

just like secrets config maps are also ment to be created first.

```
kubectl apply -f mongo-configmap.yaml 
```

```
kubectl apply -f mongo-express.yaml 

```
to get the pods

```
kubectl get pod -o wide
```
to get the logs

```
kubectl logs <pod_name>
```

This will be the output
```
coreslice@coreslice:~/k8-playground/nana-examples$ kubectl logs mongo-express-58b7cb7879-l9zg6
Welcome to mongo-express
------------------------


(node:7) [MONGODB DRIVER] Warning: Current Server Discovery and Monitoring engine is deprecated, and will be removed in a future version. To use the new Server Discover and Monitoring engine, pass option { useUnifiedTopology: true } to the MongoClient constructor.
Mongo Express server listening at http://0.0.0.0:8081
Server is open to allow connections from anyone (0.0.0.0)
basicAuth credentials are "admin:pass", it is recommended you change this in your config.js!

```

```
kubectl get svc
```


```
coreslice@coreslice:~/k8-playground/nana-examples$ kubectl get svc
NAME                    TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
kubernetes              ClusterIP      10.96.0.1        <none>        443/TCP          14d
mongo-express-service   LoadBalancer   10.97.145.99     <pending>     8081:30000/TCP   7s
mongodb-service         ClusterIP      10.111.114.172   <none>        27017/TCP        72m


```
in order to give the external ip for the mongo-express-service
we have to use this minikube command

```
minikube service <name_of _the _service>
```

## namespaces concept
```
kubectl get namespace
```
```
kubectl cluster-info
```

to create a name space
```
kubectl create namespace <NAME_OF THE NAMESPACE>
```
we can also create with name space config file.



