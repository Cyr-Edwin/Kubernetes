# Write a Yaml file that allowds communication between containers in a Pod

<h6> Definitions</h6>

* Pod

> the smallest unit of execution that have one or more containers and each container runs one or more applications.

* Yaml

> "Yet Another Markup Language", it is a file used to define or create an object in Kubernets( pods, deployment , services).

<h6> Command used</h6>

* Create a pod without running it

> kubectl run pod_name --image=image_name --dry-run=client -o yaml >file_name.yaml

* Run the pod

> kubectl create -f file_name.yaml

* Check the logs of a container in a Pod

> kubectl logs pod_name -c container_name