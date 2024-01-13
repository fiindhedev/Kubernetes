# deploy whoami 
whoami-deployment.yaml:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: whoami-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: whoami
  template:
    metadata:
      labels:
        app: whoami
    spec:
      containers:
      - name: whoami
        image: containous/whoami
        ports:
        - containerPort: 80
```
Apply the file
```console
kubectl apply -f whoami-deployment.yaml
```
Get the deployment
```console
kubectl get deployment
```
Get the Pods
```console
kubectl get pods
```
