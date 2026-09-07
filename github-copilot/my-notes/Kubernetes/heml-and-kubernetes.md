
#### The case


A normal kubernetes *.yml file  has the following sections 

* kind: Deployment 
* kind: Service
* kind: Pod
* And others

For example a  vanilla Kubernetes files
https://github.com/jaegertracing/jaeger-kubernetes/blob/master/production-elasticsearch/elasticsearch.yml

- apiVersion: v1
  kind: Service

#### Helm


* Helm is a package manager for Kubernetes that allows developers and operators to more easily package,
configure, and deploy applications and services onto Kubernetes clusters.


* Helm provides templates *.yaml files for all of the "kind:" sections. for instance we have deployment.yaml and serivice.yaml files.
Helm perform replace values action in all helms files. Values are defined in  values.yaml. Values can be overwritten using another files.

#### Helm chart


A chart is a collection of files that describes a related set of Kubernetes resources.
Helm reserves use of the charts/ and templates/


#### Compile helm  and see all replaced values


`helm template --output-dir test helm --values helm/values.yaml --set az=rameshh
`
#### Values

values.yaml: here are defined all common values. Then this values can be overwritten in another  environment file for instance dev-values.yaml

#### configmap.yaml

* Here we add al files that needs to be added in the volume defined in deployment.yaml volumeMounts: mountPath: /etc/config

In the configmap.yaml there is a "data:" section related to mountPath: /etc/config.
  All files in the data section will end up in  /etc/config

Here we describe which files are added in the pop instance mountPath: /etc/config.

```c
data:
  application.properties: |-
{{ .Files.Get (printf "secrets/config/application-%s.properties" $.Values.app.env) | indent 4 }}
  V0__Initialization.sql: |-
{{ .Files.Get (printf "secrets/config/V0__Initialization.sql") | indent 4 }}


Once  we run the helm to build all files the config files with the concreate env values.
For instance configmap.yaml will looks like this :

data:
  application.properties: |-
    [ blah blah content of the properties files with all values from values.yaml]
    V0__Initialization.sql: |-
      [ SQL SQL SQL ]


```

#### deployment.yaml

Here is where we can define the pod in details such us replicas, volumeMounts and others such is imagePullPolicy: :latest etc
deployment.yaml uses the values which come from values.yaml and [ENVIROMENT]-values.yaml which can overwrite values.yaml


#### serivice.yaml

This file describe the service itself such us serivice name, ports loadBalancerInternal.


#### roles.yaml

Here we defines which actions can be executed  to  the pod from tiller api for instance.

what is the roles.yaml

```c
rules:
- apiGroups: [""] # "" indicates the core API group
  resources: ["pods", "configmaps"]
  verbs: ["get", "list", "watch"]
```


#### Product chart

It is a helm chart that contains all microservices charts and defines how to install the whole applications

#### Domains
  
Domain : dev-deviceservice-LTA.eu-west-1a.nonprod.aurora.tescocloud.com

The domain is defined in service.yaml

```c
  external-dns.alpha.kubernetes.io/hostname: {{ .Values.app.dnsName }}.{{ .Values.az }}.{{ .Values.aurora.domainName }}
```
  where:
  * Values.app.dnsName come from  dev-values.yaml . dnsName: dev-deviceservice-LTA
  * Values.aurora.domainName come from values.yaml. domainName: aurora.tescocloud.com
  * Values.az in defined in the jenkins file "

The following dev-deviceservice-LTA.eu-west-1a.nonprod.aurora.tescocloud.com

  [dns] [context] [aurora domain]


 ```json
  helm --install --set az=eu-west-${availabilityZone}.${prodOrNonProd},app.image.tag=${gitLongCommit}
``` 


#### yaml if then print
  ```json
  {{- if .Values.app.firewall.loadBalancerInternal }}
      service.beta.kubernetes.io/aws-load-balancer-internal: '0.0.0.0/0'
  {{- end }}

```

#### Helm Commands 


*  List all available releases across all namespaces:

```
helm list --all-namespaces
```

List all releases in a specific namespace:

```
helm list --all -q --namespace ccd
``


* Install  pods 

```
helm install [app-name] [chart] --namespace [namespace]
```

* delete pods 

```
helm uninstall -n [namespace] [pod_name_from_get_pods_command]
```

* Upgrade 

```
helm upgrade [release] [chart]
```

* Upgrade to a version
```
helm upgrade [release] [chart] --version [version-number]
```

Roll back a release:
```
helm rollback [release] [revision]
```
