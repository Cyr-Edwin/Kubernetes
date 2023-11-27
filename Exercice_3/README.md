## Aggregating RBAC Rules

* Create a ClusterRole with the name service-view to the API resources services with the operations get and list

> kubectl create clusterrole service-view --verb=get,list --resource=services

* Create the RoleBinding named ellasmith-service-view in the development namespace. Map the user ellasmith to the ClusterRole service-view

> kubectl create rolebinding ellasmith-service-view -n development --user= ellasmith --clusterrole=service-view