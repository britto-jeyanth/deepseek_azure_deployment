# Steps to Deploy Deepseek on Azure ML Studio

## Prepare Azure ML Studio
Create an Azure ML Workspace. Make note of your **Azure Subscription ID**, **Azure ML Workspace**, and **Azure Resourc Group**


Steps to Deploy on Azure ML Studio
---

We will be using Azure CLI
We will be logging into Azure throught CLI and setting up our Azure ML Workspace
```
az login
```
```
az account set --subscription <subscription ID>
az configure --defaults workspace=<Azure Machine Learning workspace name> group=<resource group>
```

Run this command to create an environment in Azure ML Studio. Feel free to replace `` `name` `` in ``environment.yml``.
```
az ml environment create -f environment.yml
```

Run this command to create an endpoint in Azure ML Studio. Replace `` `name` `` in ``endpoint.yml`` to an unique name.
```
az ml online-endpoint create -f endpoint.yml
```

Run this command to create a deployment in Azure ML Studio. Replace `` `endpoint_name` `` in ``deployment.yml`` to the `` `name` `` in ``endpoint.yml``. Replace `` `image` `` with Azure ML's environment's Azure Container Registry.
```
az ml online-deployment create -f deployment.yml --all-traffic
```