databricks-cli
==============
  
az container exec --resource-group rg-name --name container-instance-name --exec-command "databricks fs --help"

You can set up a self-hosted agent in Azure Pipelines to run inside a Windows Server Core (for Windows hosts), or Ubuntu container (for Linux hosts) with Docker.
This is useful when you want to run agents with outer orchestration, such as Azure Container Instances.
