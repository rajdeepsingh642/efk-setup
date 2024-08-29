EFK Set up on Kubernetes Cluster
Elasticsearch will be installed first as a Statefulset which will store all the data as indexed Fluend will be installed as daemonset so that logs can be captured from all Nodes Kibana will be installed as deployment so that it can invokes the Elasticsearch Server and run all the dashboards.


1. Create a Namespace
kubectl create namespace efslog

2. Deploy Elasticsearch
cd elasticsearch
kubectl create -f statefulset.yaml
kubectl create -f service.yaml

3. Deploy Fluentd
cd fluentd
kubectl create -f clusterrole.yaml
kubectl create -f serviceaccount.yaml
kubectl create -f clusterrolebinding.yaml
kubectl create -f daemonset.yaml

4. Deploy Kibana
cd kibana
kubectl create -f deployment.yaml
kubectl create -f service.yaml


