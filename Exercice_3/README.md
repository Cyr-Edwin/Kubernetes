## Aggregating RBAC Rules

* Create a ClusterRole with the name service-view to the API resources services with the operations get and list

> kubectl create clusterrole service-view --verb=get,list --resource=services

* Create the RoleBinding named ellasmith-service-view in the development namespace. Map the user ellasmith to the ClusterRole service-view

> kubectl create rolebinding ellasmith-service-view -n development --user= ellasmith --clusterrole=service-view

* Create a ClusterRole with the name combined. Aggregate cluster roles based on the matching label key-value pair rbac.cka.cncf.com/aggregate: "true". Render the selected rules of the ClusterRole combined. How many rules do you see?

> kubectl create clusterole combined --aggregate-rule="rbac.cka.cncf.com/aggregate=true"

> kubectl describe clusterrole combined

* Create a ClusterRole with the name deployment-modify to the API resources deployments with the operations create, delete, patch, and update. Assign the label key-value pair rbac.cka.cncf.com/aggregate: "true". Render the selected rules of the ClusterRole combined. How many rules do you see?

> kubectl create clusterrole deployment-modify --resource=deployments --verb=create,delete,patch,update --dry-run=client -o yaml > deployment-modify.yaml

> kubectl apply -f deployment-modify.yaml

> kubectl describe clusterrole combined

<h6> Deployements are allowed to be created , updated , deleted and patched</h6>


* Run a command to figure out if the user ellasmith can list Services in the namespace development. Write the output of the command to the file list-services-ellasmith.txt. The output is either "no" or "yes."

> kubectl auth can-i list services --as ellasmith -n development > list-services-ellasmith.txt


* Run a command to figure out if the user ellasmith can watch Deployments in the namespace production. Write the output of the command to the file watch-deployments-ellasmith.txt. The output is either "no" or "yes."

> kubectl auth can-i watch deployments --as ellasmith -n production > watch-deployments-ellasmith.txt