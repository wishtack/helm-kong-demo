# Description
This repo contains a helm chart that deploys kong while also setting up splunk connect to collect data from kubernetes. This should be use for demonstration, training and experimentation only.
⚠️ **Don't use this in production.** ️️️⚠️

# Getting started

## 0. Start minikube

```
minikube start --cpus 4 --memory 8192
```

## 1. Setup helm & tiller if not ready yet
```
helm init --history-max 200
```

## 2. Install chart
```
git clone https://github.com/wishtack/helm-kong-demo
helm install helm-kong-demo/kong-demo --name kong-demo
```

## 3. Enable port forwarding
* 8443: https kong gateway
* 8444: https kong admin api
```
kubectl port-forward service/kong-demo-kong-admin 8444
kubectl port-forward service/kong-demo-kong-proxy 8443:443
```
