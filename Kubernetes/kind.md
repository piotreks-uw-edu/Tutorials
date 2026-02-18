## kind install on WSL
### check basics exist
docker --version
kubectl version --client

### install kind
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-linux-amd64
chmod +x kind
sudo mv kind /usr/local/bin/

### create a cluster
kind create cluster

### check cluster exists
kubectl get nodes

### load docker image to cluster
kind load docker-image my-app:latest
