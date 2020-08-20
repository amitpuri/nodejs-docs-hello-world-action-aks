---
page_type: sample
languages:
- nodejs
- javascript
products:
- azure
- azure-kubernetes-service
description: "This sample demonstrates a tiny Hello World Node.js app to use github action for aks."
---

## Get Azure Credentials

    az ad sp create-for-rbac --sdk-auth
    
    More on https://github.com/marketplace/actions/azure-kubernetes-set-context

## Add or Update Azure Credential in Secrets

    AZURE_CREDENTIALS from last step

## Add or Update Azure Container Registry in Secrets

    CONTAINER_REGISTRY - Name of the Azure Container Registry
    REGISTRY_USERNAME - User
    REGISTRY_PASSWORD - Password
    
## to get user and password

    az acr update -n <Name of the azure container registry> --admin-enabled true
    az acr credential show --name <Name of the azure container registry> --resource-group <Name of resource group>

## Get access credentials for a managed Kubernetes cluster.

    az aks get-credentials --resource-group <Name of resource group> --name <Name of the managed cluster>

## Add or Update Cluster name in Secrets

    CLUSTER_NAME - Name of the managed cluster
    RESOURCE_GROUP - Name of resource group

## from scratch 

    az group create --name <Name of resource group> --location <Location> e.g. eastus

    az acr create --resource-group <Name of resource group> --name <Name of the azure container registry> --sku Basic
    
    az aks create --resource-group <Name of resource group> --name <Name of the managed cluster> --node-count 1 --enable-addons monitoring --generate-ssh-keys


## to check Git action - update to trigger CI action 
    
    az aks show -g <Name of resource group> -n <Name of the managed cluster>  --query id

    az aks get-credentials --resource-group <Name of resource group> --name <Name of the managed cluster>

    kubectl get nodes

    kubectl get service hello-world --watch

## deleting once done

    az group delete --name <Name of resource group> --yes --no-wait

## In case not install or registered

    az aks install-cli

    az provider show -n Microsoft.OperationsManagement -o table
    az provider show -n Microsoft.OperationalInsights -o table

    az provider register --namespace Microsoft.OperationsManagement
    az provider register --namespace Microsoft.OperationalInsights


## Node.js Hello World

This sample demonstrates a tiny Hello World Node.js app to use github action for aks.

## Contributing

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
