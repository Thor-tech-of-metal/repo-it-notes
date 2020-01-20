#### North->South traffic 

Classic traffic is already know as north to south (N->S) 

Client --> ( Ingress / gateway)--> Pods 1...N

#### East-->West traffic 

In service meshes the traffic is east to west and it is all defined inside de pod. The pods contains the application and the service meshes.

**For instance:**
Pod1: have 1) App 2) Service Mesh. Everything running in the same pod.
```json
  * App and Service Mesh talk each other as localhost directly. 
  * The network traffic is inside the pod. No certificates etc
  * The service mesh will take care of how the App talk to the rest of the world
``` 

The SM allows to declare in an imperative way the services that are allow to talk with my service and the services that my services is allow to talk to.   
The traffic rules are defined in "side cards".

The service mesh provides:
```js
* Service Auth. By defining side cards rules.
* Experiment: you can define the sides cards to route 70% of the trafic to S1-version1 and 30% to S1-version2 .
* It can collect matrix about the traffics. This matrix can be collected by Azure for instance.

```

The main idea of service mesh is removing unwanted logic (routing/security) from the APP and use k8s predefined solutions SM.  

**SMI:**

Service mesh interface. collections of apis that register they self with Kubernetes.  


**Istio**

Connect, secure, control, and observe services.
Istio is an open source service mesh designed to make it easier to connect, manage and secure traffic between, and obtain telemetry about microservices running in containers. 


**Watch** https://www.youtube.com/watch?v=izVWk7rYqWI
