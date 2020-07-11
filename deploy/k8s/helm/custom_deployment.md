## Setup azure cli on windows

## Setup chocolatey on windows

## Setup helm on windows

## Prepare Azure AKS for eshop application deployment
```
az login
az group create --name eshoptest --location westeurope
az acr create --resource-group eshoptest --name eshoptestACR --sku Basic
az acr login --name eshoptestACR
az aks create -g eshoptest -n eshoptestAKS --location westeurope --attach-acr eshoptestACR --generate-ssh-keys

az aks install-cli

az aks get-credentials --resource-group eshoptest --name eshoptestAKS
```

## Install using helm
We needed to update the deployall.ps1 script to match Helm v3:
* remove --name
* add --generate-name

```
.\deploy-all.ps1 -externalDns eshoptestA-eshoptest-6f1acc -aksName eshoptestAKS -aksRg eshoptest -imageTag dev -useMesh $false
```
