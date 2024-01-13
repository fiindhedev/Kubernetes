# Create namespace with kubernetes
Namespace will be kubectl create namespace `prod`
```console
kubectl create namespace prod
```
Then procced with creating the deplyment with the image `strapi/strapi`
```console
kubectl create deployment strapi-deploy --image=strapi/strapi --replicas=2 --namespace=prod
```
Now print all the created deployments and pods
Deployment:
```console
kubectl get deployments -n prod
```
Pods:
```console
kubectl get pods -n prod
```
You can write the commands like this
```console
kubectl get deployments --namespace=prod
kubectl get pods --namespace=prod
```
