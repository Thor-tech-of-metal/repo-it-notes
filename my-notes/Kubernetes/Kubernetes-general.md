
Kubernetes general
==================

In Kubernetes we have AvailabilityZones, Name spaces, Services, Replicas, Deployments and Pods

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

