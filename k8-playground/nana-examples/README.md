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

*namespaces in k8's provide isolation. 
*we can use it in blue/green deployment
*sharing services between diffrent environments
*2 teams can work on the project without disrupting each others work flow
*we can limit the CPU,RAM, Storage as per the name space requirement
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

normally it takes default namespace.after creating a name space we can apply the config map with the namespace.
to get services which use this namespace
```
kubectl get all -n my-namespace
```
applying a configmap with perticular namespace
```
kubectl apply -f mysql-configmap.yaml --namespace=my-namespace
```
```OR```
we can directly mention the namespace: <namespacename> in the config map config file under the metadata tag.
A tool can be used which directly uses a perticular namespace if we want to deploy a service. it is ```kubens```
```
kubens
```
changes the active namespace to this
```
kubens <namespace>
```
## Ingress concepts
install ingress in minikube
it starts the k8's Nginx implementation of Ingress controller
```
minikube addons enable ingress
```
to view the ingress controller
```
kubectl get pod -n kube-system
```
create ingress rules
to create a ingress rule so that the kubernetes-dashboard will be accesseble from the outside browser
```
kubectl get ns
```
to get all the info about that namespace
```
kubectl get all -n kubernetes-dashboard

```
```
coreslice@coreslice:~/k8-playground/nana-examples$ kubectl get all -n kubernetes-dashboard
NAME                                             READY   STATUS    RESTARTS     AGE
pod/dashboard-metrics-scraper-5dd9cbfd69-qw54f   1/1     Running   2 (6d ago)   15d
pod/kubernetes-dashboard-5c5cfc8747-t4p67        1/1     Running   4 (6d ago)   15d

NAME                                TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
service/dashboard-metrics-scraper   ClusterIP   10.110.128.193   <none>        8000/TCP   15d
service/kubernetes-dashboard        ClusterIP   10.105.64.206    <none>        80/TCP     15d

NAME                                        READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/dashboard-metrics-scraper   1/1     1            1           15d
deployment.apps/kubernetes-dashboard        1/1     1            1           15d

NAME                                                   DESIRED   CURRENT   READY   AGE
replicaset.apps/dashboard-metrics-scraper-5dd9cbfd69   1         1         1       15d
replicaset.apps/kubernetes-dashboard-5c5cfc8747        1         1         1       15d

```

create a ingress file.
apply the file
```
kubectl apply -f dashboard-ingress.yaml
```

