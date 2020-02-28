# Kubernetes Install and Your First Pods

## Kubernetes Local Install

http://play-with-k8s.com

katacoda.com

### minikube

minikube-installer.exe

minikube start

### microk8s

microk8s.kubectl

microk8s.enable dns

alias kubectl=microk8s.kubectl

## Kubectl run, create and apply

kubectl run

kubectl create

kubectl apply

## Our First Pod With Kubectl run

kubectl version

kubectl run my-nginx --image nginx

kubectl get pods

kubectl get all

kubectl delete deployment my-nginx

kubectl get all

## Scaling ReplicaSets

kubectl run my-apache --image httpd

kubectl get all

kubectl scale deploy/my-apache --replicas2

kubectl scale deployment my-apache --replicas2

kubectl get all

## Inspecting Kubernetes Objects

kubectl get pods

kubectl logs deployment/my-apache

kubectl logs deployment/my-apache --follow --tail 1

kubectl logs -l run=my-apache

kubectl get pods

kubectl describe pod/my-apache-<pod id>

kubectl get pods -w

kubectl delete pod/my-apache-<pod id>

kubectl get pods

kubectl delete deployment my-apache

# Exposing Kubernetes Ports

## Service Types

kubectl expose

## Creating a ClusterIP Service

kubectl get pods -w

kubectl create deployment httpenv --image=bretfisher/httpenv

kubectl scale deployment/httpenv --replicas=5

kubectl expose deployment/httpenv --port 8888

kubectl get service

kubectl run --generator run-pod/v1 tmp-shell --rm -it --image bretfisher/netshoot -- bash

curl httpenv:8888

curl [ip of service]:8888

kubectl get service

## Creating a NodePort and LoadBalancer Service

kubectl get all

kubectl expose deployment/httpenv --port 8888 --name httpenv-np --type NodePort

kubectl get services

curl localhost:32334

kubectl expose deployment/httpenv --port 8888 --name httpenv-lb --type LoadBalancer

kubectl get services

curl localhost:8888

kubectl delete service/httpenv service/httpenv-np

kubectl delete service/httpenv-lb deployment/httpenv

## Kubernetes Services DNS

curl <hostname>

kubectl get namespaces

curl <hostname>.<namespace>.svc.cluster.local


 





