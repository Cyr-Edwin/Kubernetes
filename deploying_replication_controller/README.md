# Deploying Replication Controller

<h1> Key Concepts<h1>

* **Replicat Set**
> Operates based on the principle of replication, serving the essential function of ensuring a specified number of pods are consistently operational

* **Replication Controller (RC)**

> Fundamental component responsible for maintaining a specified number of replicas of a pod

<h1> Implimentation</h1>

1- ssh to the Master node
> YOUR_SSH_NAME
> YOUR_PASSWORD

2- Create Replication Controller Using Yaml
> kubectl run nginx --image=nginx --dry-run=client -o yaml > rc.yaml
> kubctl create -f rc.yaml

3- Verify Replication Controller
> kubectl get pods

4- Describe Replication Controller
> kubectl describe  rc/nginx

5- Delete Replication Controller
> kubectl delete pods -l app=nginx (**RC  will automatically create 2 new pods**)
> kubectl delete rc nginx
