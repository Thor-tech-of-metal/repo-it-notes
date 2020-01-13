#### Create AKS cluster

A cluster  where all containers are going to be created
```properties

az aks create \
    --resource-group myResourceGroup \
    --name myAKSCluster \
    --node-count 1 \
    --enable-addons monitoring \
    --service-principal <appId> \
    --client-secret <password> \
    --generate-ssh-keys
```


#### For Example

```properties
az aks create \
--resource-group myResourceGroup \
--name myAKSCluster \
--node-count 1 \
--enable-addons monitoring \
--service-principal 8b373a77-1aae-49f4-80bc-f77b9b1ad871 \
--client-secret D67OyqNwxQwQZl/WtWy9Zdk0PqvpgES7dnh0kpAy/2A= \
--generate-ssh-keys
```

#### Connect to the cluster

1) Azure CLI
`az aks install-cli `

2) get your credentials
`sudo az aks get-credentials --resource-group myResourceGroup --name myAKSCluster`

3) get your pod kubectl
`kubectl get nodes`

#### Deploy a kubernetes yaml

```properties
kubectl apply -f azure-vote.yaml
```

#### Get the external IP
```properties
kubectl get service azure-vote-front --watch
```
