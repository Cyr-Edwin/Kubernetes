## Creating a Deployment

<h6>Create a new Deployment named nginx with a single replica in the namespace magic. Wait until all replicas transition into the "Running" status. This can take a couple of seconds.</h6>

> kubectl create deployment nginx --image=nginx:1.17.0 -n magic

<h6>Verify that the Deployment has been created</h6>

> kubectl get deployments -n magic

<h6>The Deployment controls a Pod using the image nginx:1.17.0. Set the following resource requirements for the container:

resources.requests.cpu to 250m
resources.requests.memory to 100Mi
resources.limits.cpu to 500m
resources.limits.memory to 500Mi</h6>

> kubectl edit deployment nginx -n magic

## Creating a Horizontal Pod Autoscaler

<h6>Autoscale the Deployment with the help of a Horizontal Pod Autoscaler named nginx-hpa.

The average utilization of CPU should be 65% and the average utilization of memory should be 1Gi. Set the minimum number of replicas to 3 and the maximum number of replicas to 20.</h6>