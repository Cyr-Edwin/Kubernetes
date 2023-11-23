## Setting Up RBAC(Role Based Access Control) for a Service Account

* Create a **namespace** with the name apps

> kubectl create namespace apps

* Verify that the namespace has been created

> kubectl get namespace apps

* Create the **ServiceAccount** named api-access in a new **namespace** called apps

> kubectl create sa api-access -n apps


## Creating a ClusterRole and ClusterRoleBinding

*  Create a **ClusterRole** with the name api-clusterrole

> kubectl create clusterrole api-clusterrole --verb=watch,list,get --resource=pods

* Verify that the ClusterRole has been created

> kubectl get clusterrole api-clusterrole

* Create a **ClusterRoleBinding** with the name api-clusterrolebinding.Map the the ServiceAccount from the previous step to te API resource **Pods** with the operations **watch**,**list**,**get**

> kubectl create clusterrolebinding appi-clusterrolebinding --serviceaccount=apps:api-access --clusterrole=api-clusterrole

* Verify that the ClusterRoleBiding has been created

> kubectl get clusterrolebinding api-clusterrolebinding


## Using the ServiceAccount in a Pod

* Create a **Pod** named operator with the image nginx:1.21.1 in the name space apps. Expose the container port 80. Assign the ServiceAccount api-access to the pod

> kubectl run operator --image:nginx:1.21.1 --restard=Never --port:80 --serviceaccount=api-access -n apps


* Create another **Pod** named disposable with the image nginx:1.21.1 in the namespace rm. Do not assign the ServiceAccount to the Pod

> kubectl create namespace rm

> kubectl run disposable --image=nginx:1.21.1 --restard=Never -n rm

* Verify that both Pods have been created

> kubectl get pod operator -n apps

> kubectl get pod disposable -n rm