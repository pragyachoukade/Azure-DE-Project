# Azure End-to-End Data Engineering Project

##Overview
This project demonstrates the implementation of an end-to-end data engineering pipeline using sales data. The tools utilized include Azure Data Factory, Azure Databricks, Azure SQL Database, and Azure Data Lake. The architecture follows the medallion approach, which organizes data into three distinct layers: Bronze, Silver, and Gold.

##**Project Steps**
####**1.	Resource Group Creation:** Initiated by creating a resource group in the Azure portal.
####**2.	Storage Account Setup:** Established a storage account service with a hierarchical namespace, creating a Data Lake within the resource group.
####**3.	Azure Data Factory Deployment:** Created an Azure Data Factory service within the resource group to facilitate data integration and transformation. 
####**4.	Container Creation:** Set up three containers in the Data Lake:
     o	Bronze
     o	Silver
     o	Gold
####**5.	Azure SQL Database Creation:** Deployed an Azure SQL Database resource within the resource group and created a table to store incoming data.
####**6.	Data Ingestion:** Developed a pipeline in Azure Data Factory to fetch data from GitHub. This involved:
     o	Performing copy activities to transfer data.
     o	Establishing linked services for connectivity.
     o	Creating a parameterized dataset for reusability.
####**7.	Incremental Data Loading:**
     o	Created a stored procedure in SQL Database to manage incremental data loads.
     o	Established a Watermark Table to track the last loaded data.
     o	Implemented a lookup activity in the pipeline to retrieve both the last and current load data, feeding the output into the copy activity.
####**8.	Data Transformation in Databricks:**
     o	Configured a Unity Metastore in Databricks and created an additional container in the Data Lake for the metastore.
     o	Established an access connector to link Databricks with the Data Lake.
     o	Assigned the metastore to the Databricks workspace and created a cluster.
####**9.	External Locations Setup:** Created three external locations (Bronze, Silver, Gold) to facilitate data read/write operations between containers, ensuring storage credentials were established beforehand.
####**10.	Data Transformation Process:**
     o	Developed a notebook in Databricks to perform transformations, reading data from the Bronze container and writing it to the Silver container.
     o	Conducted basic transformations and created a data model, including dimensions and fact tables, in a new notebook referred to as "Gold."
####**11.	Surrogate Key and Slowly Changing Dimensions:**
     o	Implemented a surrogate key column in the dimension table.
     o	Applied Slowly Changing Dimension Type 1 (Upsert) logic to manage data updates and inserts.
     o	Created a Delta table to support these operations.
####**12.	Workflow Creation:** Established a workflow in Databricks to automate the data processing tasks.

##**Conclusion**
This project effectively showcases the integration of various Azure services to build a robust data engineering pipeline, enabling efficient data ingestion, transformation, and storage.

