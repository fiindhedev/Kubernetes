# deploy whoami on Kubernetes playground
Start by creating whoami-deployment.yaml file and editing it
```console
touch whoami-deployment.yaml
```
Then
```console
vi whoami-deployment.yaml
```
Now fill the file with this configuration (if you can't write to the file press `i`):
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
After that press ESC and type `:wq` so you can leave the editor

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

Scale the pods
```console
kubectl scale deployment whoami-deployment --replicas=2
```
