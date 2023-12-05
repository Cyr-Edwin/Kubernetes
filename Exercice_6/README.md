## Creating a Deployment

<h6>Create a new Deployment named nginx with two replicas in the namespace pluto</h6>
<h6>The Deployment controls a Pod using the image nginx:1.17.0</h6>

> kubectl create deployment nginx --image=nginx:1.17.0 -n pluto --replicas=2

<h6>Verify that the Deployment has been created properly</h6>

> kubectl get deployments -n pluto

## Scaling the Deployment

<h6>Scale the Deployment to seven replicas</h6>

> kubectl scale deployment nginx --replicas=7 -n pluto

<h6> Verify all Pods should transition into the "Running" status.</h6>

> kubectl get deployments, pods -n pluto