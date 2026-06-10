## Install Kind Kubernetes

# install KIND

# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.31.0/kind-linux-amd64

chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# install kubectl

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

chmod +x kubectl

mkdir -p ~/.local/bin

mv ./kubectl ~/.local/bin/kubectl

# Test to ensure the version you installed is up-to-date:

kubectl version --client


# to run the kind cluster

kind create cluster
kubectl gets node( status shoud be running)

Command for kubernative

# to see kind cluster
kind get clusters

# delete kind cluster
kind delete cluster --name tws-cluster

# create kind cluster foe multiple node using config file
kind create cluster --name tws-cluster --config=config.yml

# to see nodes
kubectl get nodes

# to see namespace
kubectl get namespace/kubctl get ns

# to create namespcae in command line
kubectl create ns ---(name of namespace)

# to create pod with particular image in command line
kubectl run nginx --image=nginx -n nginx

# to see pods
kubectl get pods -n  nginx

# to delete pods
kubectl delete pod nginx

#delete namespace
kubectl delete ns nginx

# delete pods 
kubectl delete nginx -n nginx

# Enter into running pods
kubectl exec -it nginx-pod -n nginx -- bash

# to see the running pods logs
kubectl describe pod/nginx-pod -n nginx

# to see pods that created by deployment
kubectl get deployment -n nginx

# to increse and decese pods using deployment
kubectl scale deployment/nginx-deployment -n nginx --replicas=5

# update the running pods with particular version
kubectl set image deployment/nginx-deployment -n nginx nginx=nginx:latest

# to delete pods/depoyment
kubectl delete -f deployment.yml



