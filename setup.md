# Kubernetes
This page has instructions on how to setup kubernetes.
You can execute the commands as instructed.
## Requirments
To get started get these things ready
* Linux server
* SSH connection to your server

That's it, and you can get started
## Setup kubernetes
Get a google cloud key
```console
    curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
```
Add kubernetes repo
```console
    echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
Update `apt` just in case
```console
apt update
```
Download kubernetes ( if you get any errors make sure you did everything right before this command )
```console
apt install -y kubelet=1.20.0-00 kubeadm=1.20.0-00 kubectl=1.20.0-00
```
Download docker ( Just if you didn't before )
```console
curl -sSL get.docker.com | sh
```
