
Commands
========

All commands follow this order 

```cpp
kubectl --context [CONTEXT/ AvailabilityZones] -n [NAME_SPACE] get deployments
```

Get pods command
================

*) get all pods deployments instaces.
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get pods
```
*) get all pods more information for a namespace.
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get pods -o wide
```

*) List all pods in the namespace, including uninitialized ones
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get pods --include-uninitialized
```

*) decrive a pod
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev describe pod feedback-94fd8d555-5bbch

```
*) Describe pod commands
```cpp
 kubectl --context eu-west-1a-nonprod -n payplus-dev describe pods device-service-58c65d99f8-7gjm5
```

*) delete a pop

```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev delete pod device-service-58c65d99f8-7gjm5
```
*) Bash inside a pod  

```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev exec -it mysql-69cbd8d889-gwqzk bash
```
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev exec -it device-service-6c56ddf486-4qdzl sh
```
*) Edit pod  configmap configuatation
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev edit configmap device-service
```

*) get pod secret
```cpp
kubectl --context eu-west-1c-prod -n payplus get secret pods
```

Get services command
====================

*) get all services running.
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get services
```
*) describe a particular service
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev describe service feedback
```

watch events
=============
*) get all pods more information for a namespace.
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get events --watch
```

*) Delete a particular service
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev  delete service feedback
```

Deploy a yaml file in kubernetes
===============
*) Deploy a yaml file with diferent kinds (Service,Deploy,Pods etc)
```cpp
kubectl --context eu-west-1c-prod -n payplus apply -f mysql.yaml
```
*) Undeploy a yaml file with diferent kinds (Service,Deploy,Pods etc)
```cpp
kubectl --context eu-west-1c-prod -n payplus delete  -f mysql.yaml
```


Export  configuations in to a yamls
==========
*) Export   deploy configuations ina  yaml
```cpp
kubectl get deploy [DEPLOY_NAME]   -o yaml > one-eyed-minion-funca.yaml

```
*) Export   service  configuations in a yaml
```cpp
kubectl get service [SERVICE_NAME]   -o yaml > one-eyed-minion-funca-service.yaml
```
*) get a pod yaml
 ```cpp
kubectl get pod  [POD_NAME]   -o yaml > one-eyed-minion-beast-pod.yaml
```

Logs command
============

*) get all logs  for one pod instance
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev logs device-service-8544d88859-s8n6b
```
*) get all logs for one pod instance with tail.
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev logs device-service-8544d88859-s8n6b -f
```

Ip commands
===========
*) Get ExternalIPs of all nodes
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="ExternalIP")].address}'
```
Connect to mysql machine
=========================

0) kubectl --context eu-west-1a-nonprod -n payplus-dev get pods ----- > and get the mysql popd name.
1) kubectl --context eu-west-1a-nonprod -n payplus-dev exec -it mysql-69cbd8d889-gfbrj bash
2) mysql -h mysql.cx.aurora.tescocloud.com -u payplus-dev -p


Deployments
=======

*) get all deployments
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get deployments
```
*)Delete
```cpp
kubectl --context eu-west-1a-nonprod delete deployment device-service -n payplus-dev
```

*)To describe a deployment:
```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev describe deployment device-service

```

Context and name spaces
=======================

*) Get all context
```cpp
kubectl config get-contexts
```

*) get context and name spaces
```cpp
kubectl --context eu-west-1a-nonprod get namespaces
```


Create a mysql clientId based on a deployed pod
=========================
1)  get the deployed configuation from the other name space and save it in a file  called mysql.yaml

```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev get deploy mysql -o yaml > mysql.yaml

```
2)  Change namespace to payplus  and deploy the generated files form  the other name space  mysql.yaml

```cpp
kubectl --context eu-west-1a-nonprod -n payplus-dev apply -f mysql.yaml
```
3) Check your pods
```cpp
kubectl --context eu-west-1c-prod -n payplus get pod

```
