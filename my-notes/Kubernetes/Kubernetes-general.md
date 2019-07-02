
Kubernetes general
==================

In Kubernetes we have AvailabilityZones, Name spaces, Services, Replicas, Deployments and Pods.

1) A service can be defined as a logical set of pods. It can be defined as an abstraction on the top of the pod which provides all network definitions.  For instance load balancer, IP  and port mappings. 

2) Pod is a collection of docker containers and its storage inside a node of a Kubernetes cluster. There are two types of Pods. Single container pod and Multi container pod

3) Replica Set ensures how many replica of pod should be running. 

4) Deployments are upgraded and higher version of replication controller. Deployments strategy:  Updating, Deleting and Rollback.

5) A node is a working machine in Kubernetes cluster which is also known as a minion. They are working units which can be physical, VM, or a cloud instance.

6) Kubernetes cluster is a set of Kubernetes nodes.

7) Namespace provides an additional qualification to a resource name. 

8) Labels are key-value pairs which are attached to pods, replication controller and services.

A normal kubernetes *.yml file  has the following sections 

* kind: Deployment 
* kind: Service
* kind: Pod
* And others

For example a  vanilla Kubernetes files check the following [file](https://github.com/jaegertracing/jaeger-kubernetes/blob/master/production-elasticsearch/elasticsearch.yml "file")


AvailabilityZones
==================
AvailabilityZone are servers around the world. Each AvailabilityZone have pods running. A pod can have many replicas. 
For example if we have the AvailabilityZones named eu-west-1a-prod, eu-west-1b-prod and eu-west-1c-prod

```cpp
eu-west-1a-prod -->  have --> pods
eu-west-1b-prod -->  have --> pods
eu-west-1c-prod -->  have --> pods

```

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


Name spaces and AvailabilityZones
===================================
In this example --context is the Availability zone  and -n is the name space

```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev describe pods device-service-58c65d99f8-7gjm5

```
Liveness and readiness
========================
* Readiness: making sure that the application is up and running after warming up start up .
* Liveness:  Imagine that the application has a deadlock. , Kubernetes detects that the app is no longer serving requests and restarts the offending pod.

* In the yaml pod we have kind: Pod where readinessProbe and  livenessProbe are defined.

```
kind: Pod
metadata:
  spec:
  containers:
  - name: goproxy
    image: k8s.gcr.io/goproxy:0.1
    ports:
    - containerPort: 8080
    readinessProbe:
      tcpSocket:
        port: 8080
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds: 2
      failureThreshold: 1
      successThreshold: 1
    livenessProbe:
      tcpSocket:
        port: 8080
      initialDelaySeconds: 15
      periodSeconds: 20
      timeoutSeconds: 2
      failureThreshold: 1
      successThreshold: 1
```



General
========
* Kubernetes always check the pod health 
* Kubernates will automatically resurrect killed Pods 
* Kuberntes keeps restarting pods.
* Controllers take care of Pod scaling and healing
