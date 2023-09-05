
basic commands:
to start and configure the minikube
```
minikube start
minikube -p minikube docker-env
eval $(minikube -p minikube docker-env)
kubectl apply -f <deployment or service filename>.yaml
```
to get into the minikube docker
```
minikube ssh
```
to get the minikube IP
```
minikube ip
```
to get the pods info
```
kubectl get pods
kubectl get pods -o wide
```
to get deployment info
```
kubectl get deployment
```
to delete deployment
```
kubectl delete deployment <deployment_name>
```
to get the services info
```
kubectl get svc   # kubectl get service
```
to delete service
```
kubectl delete service <service_name>
```
