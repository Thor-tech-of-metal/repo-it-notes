
General
========
* Kubernetes always check the pod health 
* Kubernates will automatically resurrect killed Pods 
* Kuberntes keeps restarting pods.
* Controllers take care of Pod scaling and healing
* You cannot connect to a Pod directly given that it keeps changing its ips address.




**Pod**: It has a docker container which runs the images. The pods can be replicated. they run inside a  (azure node) or (azure availability zone)

**Service**: The services defines de internal load balance or networking to access all internal pods to an (azure node) or (azure availability zone)

**Ingress**: It is exposed to the outside world. It has access to each services that belongs to a azure cluster or availability zone. 
The ingress can dispatch request based on domains.  A micro services that it  is access from a web client es an example of a micro-services that needs ingress.

For instance:

1 The request goes to the ingress 
2 The ingress maps based on the domain to a certain  