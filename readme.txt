Comprehensive Azure Data Engineering Showcase
This comprehensive project showcases a seamless Azure data engineering solution, commencing from a local SQL database and culminating in Power BI reporting, all orchestrated through automation.

Business Objective
This endeavor serves as an immersive learning opportunity for mastering common data engineering practices, with a primary focus on ETL pipeline techniques. The acquired skills are particularly beneficial for small to medium-sized businesses seeking to transition their local data to the cloud.

Current Environment
Leveraged the AdventureWorks dataset from Microsoft.
Established an on-premises Microsoft SQL server on a personal computer.
Imported the dataset using Microsoft SQL Server Management Studio.
Configured a new user profile, "surendra5882."
Safeguarded the "surendra5882" profile's password credentials as a Secret in Azure Key Vault.

PHASE-1: Data Ingestion
-Data ingestion from the on-premises SQL Server to Azure SQL is seamlessly achieved through Azure Data Factory. The process involves:
-Installation of Self-Hosted Integration Runtime.
-Establishing a secure connection between Azure Data Factory and the local SQL Server.
-Implementation of a copy pipeline to transfer all tables from the local SQL server to the Azure Data Lake's "bronze" folder.
-Azure DataFactory
PHASE-2: Data Transformation
-Post-ingestion, data undergoes transformation following the medallion data lake architecture (bronze, silver, gold). Azure Databricks, utilizing PySpark, is employed for these transformations. Data initially stored in parquet format in the "bronze" folder is converted to the delta format as it progresses to "silver" and "gold." This transformation is executed through Databricks notebooks:
-Mount the storage.
-Transform data from "bronze" to "silver" layer.
-Further transform data from "silver" to "gold" layer.
-Databricks Notebooks
-Azure Data Factory is updated to execute the "bronze" to "silver" and "silver" to "gold" notebooks automatically with each pipeline run.
-Completed Pipeline
PHASE-3: Data Loading
Data from the "gold" folder seamlessly loads into the Business Intelligence reporting application, Power BI, utilizing Azure Synapse. The steps involve:
-Creating a link from Azure Storage (Gold Folder) to Azure Synapse.
-Crafting stored procedures to extract table information as a SQL view.
-Storing views within a server-less SQL Database in Synapse.
-Data Loading

PHASE-4: Data Reporting
-Power BI directly connects to the cloud pipeline using DirectQuery for dynamic database updates. A Power BI report is meticulously developed to visualize AdventureWorks dataset data, encompassing sales, product information, and customer gender.

PHASE-5: Final Pipeline Test
-To validate the end-to-end pipeline, two new customers are introduced to the local SQL database server. Upon success, the pipeline updates, and the Power BI report dynamically reflects the new data. The total number of customers should increase from 847 to 849.

Conclusion and Considerations
-This project showcases the prowess of creating an end-to-end ETL cloud solution using Azure. Some noteworthy considerations include:

The dataset's modest size (7mb total, 800 rows) was intentional to mitigate compute and storage costs.
Multiple applications were utilized for a seemingly simple task.
Given the dataset's simplicity, the project could have been managed entirely through Azure Data Factory, with data cleaning performed downstream in Power BI.
The inclusion of Azure Synapse and Databricks was for the purpose of self-learning and emulating real-world business pipelines.
