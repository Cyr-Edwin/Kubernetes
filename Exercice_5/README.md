## Edit the Web Frontend Deployment to Expose the HTTP Port

<h6> In the web namespace, there is a deployment called web-frontend. Edit this deployment so that the containers within its Pods expose port 80.</h6>

* Switch to the correct context

> kubectl config use-context ackgje9e

> kubectl edit deployment -n web web-deployment


## Create a Service to Expose the Web Frontend Deployment's Pods Externally

<h6>Create a service called web-frontend-svc in the web namespace. This service should make the Pods from the web-frontend deployment in the web namespace reachable from outside the cluster.

External entities should be able to reach the service by contacting any node in the cluster on port 30080.</h6>

> vi web-frontend-svc.yaml

> :wq

> kubectl create -f  web-frontend-svc.yaml

## Scale Up the Web Frontend Deployment

<h6>Scale the web-frontend deployment in the web namespace up to 5 replicas.</h6>

> kubectl scale deployment web-frontend -n web --replicas=5
 
## Create an Ingress That Maps to the New Service

<h6>Create an Ingress called web-frontend-ingress in the web namespace that maps to the web-frontend-svc service in the web namespace. The Ingress should map all requests on the / path.</h6>

> vi web-frontend-ingress.yaml

> :wq

> kubectl create -f web-frontend-ingress.yaml
