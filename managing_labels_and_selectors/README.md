# Managing Labels and Selectors

<h5> Key terms</h5>

1 - **Labels** 

key-value pairs attached to various K8s objects, including pods, services, nodes, and more. They add supplementary metadata to these objects.

 2 - **Selectors** 

Mechanisms used to filter and select resources based on their associated labels.

<h6> Implimentation<h6>

1 -  Log into the Master Node

 > ssh Name_Of_Your_Master_Node  and Your_Password



2 - Create the Kubernete Pod Production Environment 

 > kubectl run prod_env --image=nginx:latest --dry-run=client -o yaml > prod_env.yaml 

 > kubectl create -f prod_env.yaml

 * List created Pods with labels

 > kubectl get pods --show-labels



3 - Create the Kubernete Pod  Development Environment

 > kubectl run dev_env --image=nginx --dry-run=client -o yaml > dev_env.yaml

 > kubectl create -f dev_env.yaml



4 - List Pods using Labels Selectors

 > kubectl get pods -l environment=production
 


5 - Delete Pods using Labels Selectors

  > kubectl delete pods --selector=environment=development

