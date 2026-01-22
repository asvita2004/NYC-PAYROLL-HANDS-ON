*** Project Introduction ***
The City of New York would like to develop a Data Analytics platform on Azure Synapse Analytics to accomplish two primary objectives:

Analyze how the City's financial resources are allocated and how much of the City's budget is being devoted to overtime.
Make the data available to the interested public to show how the City’s budget is being spent on salary and overtime pay for all municipal employees.
You have been hired as a Data Engineer to create high-quality data pipelines that are dynamic, can be automated, and monitored for efficient operation. The project team also includes the city’s quality assurance experts who will test the pipelines to find any errors and improve overall data quality.

The source data resides in Azure Data Lake and needs to be processed in a NYC data warehouse. The source datasets consist of CSV files with Employee master data and monthly payroll data entered by various City agencies.



<img width="496" height="563" alt="image" src="https://github.com/user-attachments/assets/3060843a-9f98-42d0-92a8-3a5c73a5153d" />

In the following pages, we will go through the project instructions and by the end you will have built a Data Integration Pipelines on the NYC Payroll Data. We will be using Azure Data Factory to create Data views in Azure SQL DB from the source data files in DataLake Gen2. Then we built our dataflows and pipelines to create payroll aggregated data that will be exported to a target directory in DataLake Gen2 storage over which Synapse Analytics external table is built. At a high level your pipeline will look like below


<img width="574" height="191" alt="image" src="https://github.com/user-attachments/assets/08b8de7a-de33-49f8-8386-3902a925ecca" />


## Azure Services Used
- Azure Data Lake Storage Gen2  
- Azure Data Factory  
- Azure SQL Database  
- Azure Synapse Analytics (Serverless SQL Pool)  
- GitHub

---

## Data Sources
**Master Data**
- AgencyMaster.csv  
- EmpMaster.csv  
- TitleMaster.csv  

**Payroll Data**
- nycpayroll_2020.csv  
- nycpayroll_2021.csv  

---

## Linked Services
Two linked services are created in Azure Data Factory:
- Azure Data Lake Gen2 (source and staging)
- Azure SQL Database (destination and aggregation)

---

## Datasets
Datasets are created for:
- CSV files in Data Lake Gen2
- Tables in Azure SQL Database
- Staging folder for Synapse Analytics

---

## Data Flows
- Data flows load master and payroll data from Data Lake to SQL DB.
- An aggregation data flow:
  - Merges 2020 and 2021 payroll data
  - Calculates TotalPaid  
    (RegularGrossPaid + TotalOTPaid + TotalOtherPay)
  - Groups data by Agency and Fiscal Year
  - Writes results to SQL DB and Data Lake staging

---

## Pipeline
- Master data flows run in parallel.
- Payroll data flows run after master data loads.
- Aggregation flow runs last.
- Pipeline is triggered manually.

---


## GitHub Integration
Azure Data Factory is connected to GitHub.  
All pipelines, datasets, dataflows, and linked services are published to the repository.

---

## How to Run
1. Trigger the pipeline in Azure Data Factory.
2. Monitor pipeline execution.
3. Verify results in SQL DB, Data Lake, and Synapse.

---
