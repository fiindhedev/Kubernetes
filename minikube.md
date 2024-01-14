# Minikube on DigitalOcean

### Preferred system requirements
You can run the system with less than that but you may face problems
```
2 GB RAM or more
2 CPU / vCPU or more
20 GB free hard disk space or more
Docker
```

### Install docker from official repository
```console
curl -sSL get.docker.com | sh
```
check if it is installed
```console
docker --version
```

### Install Kubectl
https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

```console
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```
```console
mv kubectl /bin/kubectl
```
```console
chmod a+x /bin/kubectl
```

### Install Minikube

```console
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
```console
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
```console
sudo chmod +x /usr/local/bin/minikube
```

### Minikube commands
You start your cluster here, for any issues go to [Troubleshooting](#troubleshooting)
```console
minikube start --driver=docker --force
```
Other commands if needed, no need to use them you can start using `kubectl`
```console
minikube addons list
minikube addons enable ingress
minikube dashboard
minikube stop
```
# Troubleshooting
find the error you got and see the steps
- `The "docker" driver should not be used with root privileges.`

Try running the command with `sudo` and make sure you added `--force`

- `Requested cpu count 1 is less than the minimum allowed of 2`

Try running the command like ths
```console
minikube start --driver=docker --extra-config=kubeadm.ignore-preflight-errors=NumCPU --force --cpus 1
```

- `Exiting due to GUEST_MISSING_CONNTRACK: Sorry, Kubernetes 1.28.3 requires crictl to be installed in root's path`

follow these steps
```console
wget https://github.com/kubernetes-sigs/cri-tools/releases/download/VERSION/crictl-VERSION-linux-amd64.tar.gz
```
```console
tar zxvf crictl-v1.28.0-linux-amd64.tar.gz
```
```console
sudo mv crictl /usr/local/bin
```
check if it is installed
```console
sudo crictl --version
```
### Start Minikube with higher resources
```console
minikube config set cpus 2
minikube config set memory 8192
minikube start
```

### Test the setup
```console
kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080
kubectl expose pod hello-minikube --type=NodePort
```
