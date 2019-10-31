# Description
This repo contains a helm chart that deploys kong while also setting up splunk connect to collect data from kubernetes. This should be use for demonstration, training and experimentation only.
⚠️ **Don't use this in production.** ️️️⚠️

# Getting started

## 1. Setup helm & tiller if not ready yet
```
helm init --history-max 200
```

## 2. Setup HEC on Splunk

## 3. Install chart
```
SPLUNK_HEC_TOKEN=...
SPLUNK_HOST=...
git clone https://github.com/wishtack/helm-kong-demo
helm install helm-kong-demo/kong-demo --name kong-demo \
  --set global.splunk.hec.token=$SPLUNK_HEC_TOKEN \
  --set global.splunk.hec.host=$SPLUNK_HOST \
  --set global.splunk.hec.indexName=kubernetes
```

## 4. Enable port forwarding
* 8443: https kong gateway
* 8444: https kong admin api
```
kubectl port-forward service/kong-demo-kong 8443 8444
```
