
#### Resources

https://docs.microsoft.com/en-us/java/azure/spring-framework/deploy-spring-boot-java-app-on-kubernetes?view=azure-java-stable

https://github.com/Microsoft/azure-spring-boot/tree/master/azure-spring-boot-samples

#### Create a Resource


```cpp
az group create --name=SptingBootResourceGroup --location=eastus

```

#### Create  private Azure container registry in the resource group


Azure container registry in the resource group.  Then we can push the sample app as a Docker image to this registry.

```cpp
az acr create --admin-enabled --resource-group SptingBootResourceGroup --location eastus  --name SptingBootRegistry --sku Basic
```

output

```cpp
 {
  "adminUserEnabled": true,
  "creationDate": "2019-01-24T12:31:05.196161+00:00",
  "id": "/subscriptions/b68a27d0-f3a1-4cf8-b27d-ed9da9d1306d/resourceGroups/SptingBootExample/providers/Microsoft.ContainerRegistry/registries/SptingBootExampleRegistry",
  "location": "eastus",
  "loginServer": "sptingbootexampleregistry.azurecr.io",
  "name": "SptingBootExampleRegistry",
  "networkRuleSet": null,
  "provisioningState": "Succeeded",
  "resourceGroup": "SptingBootExample",
  "sku": {
    "name": "Basic",
    "tier": "Basic"
  },
  "status": null,
  "storageAccount": null,
  "tags": {},
  "type": "Microsoft.ContainerRegistry/registries"
}

```

The important things is the image server location  **"loginServer": "sptingbootregistry.azurecr.io"**

#### Get the registry password for your resource-group


```cpp
az acr credential show --name sptingbootregistry --resource-group SptingBootResourceGroup
```
result:
```cpp
{
  "passwords": [
    {
      "name": "password",
      "value": "SkYrQwmd60HDtfwGyLSKHCRB7O0=XkTV"
    },
    {
      "name": "password2",
      "value": "yIiK5saW6yScrtGXgYon/pNXBNbsvT=C"
    }
  ],
  "username": "SptingBootRegistry"
}

```
#### Maven only

Create a settings.xml in your ~/.m2 directory with this values

```cpp
mvn package docker:build

```

#### Run your image to make sure it works

1) Run in docker 
```cpp
docker run -p 8181:8080 sptingbootregistry.azurecr.io/gs-spring-boot-docker

```
2) Delete it if you want
```cpp
docker rm $(docker stop $(docker ps -a -q --filter ancestor=sptingbootregistry.azurecr.io/gs-spring-boot-docker  --format="{{.ID}}"))

```

#### Push in the azure docker repository server

1) Login in to your azure docker images repository
```cpp
docker login -u SptingBootRegistry -p "SkYrQwmd60HDtfwGyLSKHCRB7O0=XkTV" sptingbootregistry.azurecr.io
```

2) Push the image in to your azure docker images repository
```cpp
docker push sptingbootregistry.azurecr.io/gs-spring-boot-docker

```
output --> latest: digest: sha256:27a1a349b56533eb37f0807b9ae4d40cc64dd33f686f8e2f991e29e9dd3ca805 size: 2212


#### Create your Kuberntes cluster

```cpp
az aks create \
--resource-group SptingBootResourceGroup \
--name superCluester \
--node-count 1 \
--enable-addons monitoring \
--service-principal 8b373a77-1aae-49f4-80bc-f77b9b1ad871 \
--client-secret D67OyqNwxQwQZl/WtWy9Zdk0PqvpgES7dnh0kpAy/2A= \
--generate-ssh-keys
```

#### Connect to your ASK superCluster


```cpp
sudo az aks get-credentials --resource-group SptingBootResourceGroup --name superCluester
```

#### Create Kuberntes secret for the registry


```cpp
kubectl create secret docker-registry sptingbootregistry --docker-server=sptingbootregistry.azurecr.io --docker-username=SptingBootRegistry --docker-password=SkYrQwmd60HDtfwGyLSKHCRB7O0=XkTV
```

```cpp
kubectl create secret docker-registry sptingbootregistry --docker-server=sptingbootregistry.azurecr.io --docker-username=SptingBootRegistry --docker-password=SkYrQwmd60HDtfwGyLSKHCRB7O0=XkTV

```
read: https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/


#### Output the secret

```cpp
kubectl get secret sptingbootregistry --output=yaml

```

#### Add the secret to the  app deployment yaml


Add imagePullSecrets: in the one-eyed-minion-beast-pod.yaml

For instance:

```cpp
containers:
  - name: one-eyed-minion
    image: sptingbootexampleregistry.azurecr.io/gs-spring-boot-docker:latest
    imagePullPolicy: IfNotPresent
    ports:
    - containerPort: 8080
    env:
    - name: JAVA_OPTS
      value: -Xmx64m -Xms64m
    - name: SPRING_APPLICATION_NAME
      value: "one-eyed-minion"
imagePullSecrets:
    - name: sptingbootexampleregistry

```
####  Deploy from command line

```cpp
kubectl apply -f one-eyed-minion-beast-service.yaml
kubectl apply -f one-eyed-minion-beast.yaml
kubectl apply -f one-eyed-minion-beast-pod.yaml
```


#### Open your dashboard

```cpp
kubectl create clusterrolebinding kubernetes-dashboard \
    --clusterrole=cluster-admin \
    --serviceaccount=kube-system:kubernetes-dashboard
```

```cpp
sudo az aks browse --resource-group=SptingBootResourceGroup --name=superCluester
```
It will open a browser running in http://127.0.0.1:8001/#!/deploy?namespace=default

app name: spting-boot-example
image: sptingbootexampleregistry.azurecr.io/gs-spring-boot-docker:latest

**Errors with dashboard !!!
read:  ** https://blog.jcorioland.io/archives/2018/08/29/azure-aks-rbac-kubernetes-dashboard.html



#### See your new cluster


1 get your credentials

```cpp
sudo az aks get-credentials --resource-group SptingBootResourceGroup --name superCluester
```

2 get your nodes
```cpp
kubectl get nodes
```

3 get your services

```cpp
kubectl get service
```


####  Delete  from command line

```cpp
kubectl delete -f one-eyed-minion-beast-service.yaml
kubectl delete -f one-eyed-minion-beast.yaml
kubectl delete -f one-eyed-minion-beast-pod.yaml
```
