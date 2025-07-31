# Kubernetes Architecture:

<img width="1024" height="648" alt="image" src="https://github.com/user-attachments/assets/8c47615e-aa5c-433f-8d42-172af25e47cb" />
<img width="1402" height="882" alt="image" src="https://github.com/user-attachments/assets/8cc15e1a-ed37-4b0d-90cd-ed5cfb14cea5" />

Cluster consists of  Master node and the worker node 

Worker nodes are actually running the application workloads 
  Pod is the smallest unit responsible to run the application container 
  Kubelet an agent runs on all the worker nodes and also responsible to create pods
  Container runtime interface  - Docker 
  Kube-proxy for networking and for exposing our application 
 
Master node is responsible for handling workloads inside the cluster 
  Kube-api-serverwhich is the entry point and the authentication system for every request that you make. It also exposes a kubernetes     API for the end user to start using it
  Scheduler  is used to assign ports to the nodes  
  Controller Manager that makes sure everything is working as you want or as you have desired in manifest files 
  Etcd stores all the cluster information is stored inside  

## Installation of Command Line Tools 

### Install aws CLI in host ec2 server. 

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install zip
unzip awscliv2.zip
sudo ./aws/install
aws --version       ->     aws-cli/2.27.55 Python/3.13.4 Linux/6.8.0-1029-aws exe/x86_64.ubuntu.24

### Install kubectl utility - command line tool  for interacting with kubernetes cluster 

curl -LO https://s3.us-west-2.amazonaws.com/amazon-eks/1.33.0/2025-05-01/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client         ->    Client Version: v1.33.0-eks-802817d ; Kustomize Version: v5.6.0

### Install eksctl utility - of eks - open source command line tool to manage k8s cluster with respect to aws.

curl -LO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz"
tar -xzf eksctl_Linux_amd64.tar.gz 
sudo mv eksctl /usr/local/bin/
eksctl version   ->   0.211.0


## Creation of Cluster in EKS via eksctl

" eksctl create cluster \
--name cluster-name \
--region ap-south-1 \
--nodegroup-name Node-grp-name \
--node-type t3.medium \
--nodes 2 \
--managed "

## To update kubeconfig 

aws eks update-kubeconfig --region us-west-2 --name my-eks-cluster

## To view Nodes created 

kubectl gets nodes

# To view Pods running 

kubectl get pods

## To view logs of a pod 

kubectl logs <podname>

## To delete a Kubernetes cluster 

eksctl delete cluster --name <cluster-name> --region ap-south-1


# Minikube setup 

## Installation of minikube  & docker 

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube version       ->     minikube version: v1.36.0
sudo apt install docker.io
docker -v      ->      Docker version 27.5.1, build 27.5.1-0ubuntu3~24.04.2

## To start a Minikube 

minikube start --driver=docker 

## To check minikube status

minikube status

## To Launch minikube dashboard.

minikube dashboard 

## To Stop minikube cluster

minikube stop 

## To delete minikube cluster

minikube delete

## To show available add-ons 

minikube addons list

## To view minikube services running 

minikube service <svc-name>


# Main Kubernetes Objects 

## Pod - po
## ReplicaSets - rs
## deployments - deploy
## service - svc
## Namespace - ns
## 

## To view all k8s object infomation

kubectl api-resources

## To create a object by command 

Kubectl create object name --image=imagename

## To apply an object using manifest.yaml file

kubectl apply -f <obj-manifest>.yaml 

## To delete an object using manifest.yaml file

kubectl delete <obj-manifest>.yaml

## To view objects created &  running 

kubectl get pods
kubectl get deploy
kubectl get rs
kubectl get svc 
kubectl get namespace



































