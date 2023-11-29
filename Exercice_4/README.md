## Count the Number of Nodes That Are Ready to Run Normal Workloads
<h6>This question uses the **acgk8s** cluster</h6>

* Switch to the appropriate context:

> kubectl config use-context acgk8s

* Count the number of nodes ready to run a normal workload:

> kubectl get nodes

* Check that the worker nodes can run normal workloads:

> kubectl descrive node acgk8-worker1  

> **check the list of taints. You should see none**

> kubectl describe node acgk8-worker2

> **check the list of taints. You should see none**

* Save this number of nodes to the file /k8s1/count.txt

> echo "2" > /k8s1/count.txt

## Retrieve Error Messages from a Container Log

<h6>In the backend namespace, check the log for the proc container in the data-handler Pod. Save the lines which contain the text ERROR to the file /k82/errors.txt.</h6>

* Obtain error messages from a container's log:

> kubectl logs -n backend data-hanler -c proc

* Return only the error messages:

> kubectl logs -n backend data-handler -c proc | grep ERROR

* Save this output to the file /k8s2/errors.txt:

> kubectl logs -n backend data-handler -c proc | grep ERROR > /k8s2/errors.txt


## Find the Pod with a Label of app=auth in the Web Namespace that is utilizing the most CPU

<h6>Determine which Pod in the web namespace with the label app=auth is using the most CPU. Save the name of this Pod to the file /k8s3/cpu-pod.txt</h6>

> kubectl top -n web --sort-by cpu --selector app=auth > k8s3/cpu-pod.txt