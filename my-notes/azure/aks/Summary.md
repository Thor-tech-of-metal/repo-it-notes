#### Create my Resource group

`az group create --name myResourceGroup --location eastus`



#### Create a create service principals
```json
az ad sp create-for-rbac --skip-assignment
```

response: with appId and password

{
  "appId": "559513bd-0c19-4c1a-87cd-851a26afd5fc",
  "displayName": "azure-cli-2018-09-25-21-10-19",
  "name": "http://azure-cli-2018-09-25-21-10-19",
  "password": "e763725a-5eee-40e8-a466-dc88d980f415",
  "tenant": "72f988bf-86f1-41af-91ab-2d7cd011db48"
}


#### Create AKS cluster

A cluster  where all containers are going to be created

```json
az aks create \
    --resource-group myResourceGroup \
    --name myAKSCluster \
    --node-count 1 \
    --enable-addons monitoring \
    --service-principal <appId> \
    --client-secret <password> \
    --generate-ssh-keys
```

####  Create your ASK cluster.

```
az login
```

1) Azure CLI
`az aks install-cli `

2) get your credentials
`sudo az aks get-credentials --resource-group myResourceGroup --name myAKSCluster`

3) get your pod kubectl
`kubectl get nodes`



#### Create  private Azure container registry in the resource group

Azure container registry in the resource group.  Then we can push the sample app as a Docker image to this registry.

```cpp
az acr create --admin-enabled --resource-group SptingBootResourceGroup --location eastus  --name SptingBootRegistry --sku Basic
```
