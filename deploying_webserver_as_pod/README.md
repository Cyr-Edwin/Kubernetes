# Deploying webserver as a Pod

<h1> Implimentation</h1>

* ssh to the Master Node with credentials

* Verify  kubectl Version

> kubectl version

* Verify Kubelet Service

> systemctl status kubelet

* Verify Prerequisite Pods

> kubectl get pods --all-namespaces

* Deploy a pod with httpd container image

> kubectl run server --image=httpd

* Verify the pod is running 

> kubectl get pods

* configure web page on top of the container image downloaded from the registry

> kubectl exec server -it --bash

*  navigate to the document root folder of the web server.

> cd /var/local/apache2/htdocs

* Add the contents into the index.html

> echo "<html> Hello from my webser</h1> > index.html

* exit the container

> exit

* Fetch the IP address of the container

> kubectl descrobe pods server | grep IP

* Curl request to see the page

> curl ip_of_the_container