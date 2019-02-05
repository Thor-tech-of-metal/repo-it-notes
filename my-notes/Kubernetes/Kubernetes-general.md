
Kubernetes general
==================

In Kubernetes we have AvailabilityZones, Name spaces, Services, Replicas, Deployments and Pods.

1) A service can be defined as a logical set of pods. It can be defined as an abstraction on the top of the pod which provides a single IP address and DNS name by which pods can be accessed.

1) Pod is a collection of docker containers and its storage inside a node of a Kubernetes cluster. There are two types of Pods. Single container pod and Multi container pod

1) Replica Set ensures how many replica of pod should be running. 

1) Deployments are upgraded and higher version of replication controller. Deployments strategy:  Updating, Deleting and Rollback.

1) A node is a working machine in Kubernetes cluster which is also known as a minion. They are working units which can be physical, VM, or a cloud instance.

1) Kubernetes cluster is a set of Kubernetes nodes.

A normal kubernetes *.yml file  has the following sections 

* kind: Deployment 
* kind: Service
* kind: Pod
* And others

For example a  vanilla Kubernetes files check the following [file](https://github.com/jaegertracing/jaeger-kubernetes/blob/master/production-elasticsearch/elasticsearch.yml "file")


AvailabilityZones
==================
For example if we have the AvailabilityZones named eu-west-1a-prod, eu-west-1b-prod and eu-west-1c-prod

```cpp
eu-west-1a-prod -->  have --> pods
eu-west-1b-prod -->  have --> pods
eu-west-1c-prod -->  have --> pods

```
each AvailabilityZone have pods running. A pod can have many replicas.

Name spaces
============
In this example  each name-space have 3  AvailabilityZones. 1a 1b 1c.

**Name spaces: payplus**
                eu-west-1a-prod
                eu-west-1b-prod
                eu-west-1c-prod

**Name spaces: payplus-dev**
                eu-west-1a-nonprod
                eu-west-1b-nonprod
                eu-west-1c-nonprod


General
========
* Kubernetes always check the pod health 
* Kubernates will automatically resurrect killed Pods 
* Kuberntes keeps restarting pods.  
