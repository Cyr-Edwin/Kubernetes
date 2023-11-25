## Setting up RBAC (Role Based Access Control) for a User

* List the available contexts

> kubectl config get-contexts

* Verify the current context

> kubectl config current-context

* Write the current context to the file current-context.txt

> kubectl config current-context > current-context.txt

* Check the permissions assigned to the user johndoe for the verbs list, get, watch, and delete in the default namespace

> kubectl auth can-i list pods --as johndoe

> kubectl auth can-i get pods --as johndoe

> kubectl auth can-i watch pods --as johndoe

>kubectl auth can-i delete pods --as johndoe

* Create a Role with the name pod-reader.Map the user johndoe to the API resources pods with the operations watch, list, get

> kubectl create role pod-reader --verb=watch,list,get --resource=pods

* Verity the role has been created

> kubectl get role pop-reader

* Create RoleBinding named  read-pods in the default namespace. 

> kubectl create rolebinding read-pods --user=Johndoe --role=pod-reader

* Verify  the RoleBinding has been created

> kubectl get rolebinding read-pods

* Switch to the context johndoe-context associated with the user johndoe

> kubectl config use-context johndoe-context

* Create a Pod named nginx with the image nginx:1.21.1 in the namespace default. Expose the container port 80. Write the output to the file create-pod.txt

> kubectl run nginx --image=nginx:1.21.1 --port=80 > create-pod.txt

* List the Pods in the default namespace. Write the output to the file list-pods.txt

> kubectl get pods > list-pods.txt