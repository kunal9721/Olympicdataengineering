# Olympic Data End-to-End Project

This project aims to ingest, process, and analyze Olympic data from the 2021 Olympics in Tokyo using Azure services and Databricks. The data includes information about athletes, coaches, medals, gender distribution, and teams.

## Table of Contents

Data Source

Azure Setup

Storage Account

Data Factory

Data Ingestion

Data Transformation

Databricks Workspace

Mounting Data

Analytics

Synapse Analytics Workspace

# Data Source

The data is sourced from Kaggle: 2021 Olympics in Tokyo.


# Azure Setup
## Storage Account
Create a storage account on Azure to store the Olympic data.

## Data Factory
Set up an Azure Data Factory to orchestrate the data ingestion pipeline.

## Data Ingestion

Ingest the Olympic data from Kaggle.

Utilize Data Factory to copy data from the source to Azure Blob Storage.

Retrieve raw data file links from GitHub.

# Data Transformation

## Databricks Workspace

Create a Databricks workspace and cluster for data transformation tasks.

## Mounting Data
Mount the Azure Blob Storage to Databricks using an app registration with necessary permissions.

python
configs = {
  "fs.azure.account.auth.type": "OAuth",
  "fs.azure.account.oauth.provider.type": "org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider",
  "fs.azure.account.oauth2.client.id": "<clientid>",
  "fs.azure.account.oauth2.client.secret": "<client secret>",
  "fs.azure.account.oauth2.client.endpoint": "https://login.microsoftonline.com/<tenant_id>/oauth2/token"
}

Mounting point
dbutils.fs.mount(
  source="abfss://<container name>@<storage account>.dfs.core.windows.net",
  mount_point="/mnt/<foldername>",
  extra_configs=configs
)
Transformation Tasks
Perform necessary transformations using Spark in Databricks.

# Analytics
## Synapse Analytics Workspace
Set up a Synapse Analytics workspace with the storage account.

Create a database and tables from data stored in Azure Data Lake.
Conduct analytics using SQL queries.
