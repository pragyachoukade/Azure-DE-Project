# Azure End-to-End Data Engineering Pipeline

This project demonstrates the implementation of an end-to-end data engineering pipeline using sales data. The tools utilized include Azure Data Factory, Azure Databricks, Azure SQL Database, and Azure Data Lake. The architecture follows the medallion approach, which organizes data into three distinct layers: Bronze, Silver, and Gold.
![azure-data-factory-baseline](https://github.com/user-attachments/assets/d4991fb0-07c6-4934-9d55-a06c7ae7d592)


## Project Steps

1. **Resource Group Creation**: Initiated by creating a resource group in the Azure portal.

2. **Storage Account Setup**: Established a storage account service with a hierarchical namespace, creating a Data Lake within the resource group.

3. **Azure Data Factory Deployment**: Created an Azure Data Factory service within the resource group to facilitate data integration and transformation.

![Screenshot (279)](https://github.com/user-attachments/assets/61b9fb36-0599-4181-b2d4-082de0c9bd83)


4. **Container Creation**: Set up three containers in the Data Lake:
   - Bronze
   - Silver
   - Gold

![Screenshot (282)](https://github.com/user-attachments/assets/0a4cd170-c231-4425-8270-b8cacbf1b03d)


5. **Azure SQL Database Creation**: Deployed an Azure SQL Database resource within the resource group and created a table to store incoming data.

6. **Data Ingestion**: Developed a pipeline in Azure Data Factory to fetch data from GitHub. This involved:
   - Performing copy activities to transfer data.
   - Establishing linked services for connectivity.
   - Creating a parameterized dataset for reusability.

7. **Incremental Data Loading**:
   - Created a stored procedure in SQL Database to manage incremental data loads.
   - Established a Watermark Table to track the last loaded data.
   - Implemented a lookup activity in the pipeline to retrieve both the last and current load data, feeding the output into the copy activity.

![Screenshot (283)](https://github.com/user-attachments/assets/014bbf8c-0ec7-4523-aea3-c0929c769c39)

![Screenshot (280)](https://github.com/user-attachments/assets/3e3004af-0567-4723-aefd-ca8af4477071)


8. **Data Transformation in Databricks**:
   - Configured a Unity Metastore in Databricks and created an additional container in the Data Lake for the metastore.
   - Established an access connector to link Databricks with the Data Lake.
   - Assigned the metastore to the Databricks workspace and created a cluster.

9. **External Locations Setup**: Created three external locations (Bronze, Silver, Gold) to facilitate data read/write operations between containers, ensuring storage credentials were established beforehand.

10. **Data Transformation Process**:
    - Developed a notebook in Databricks to perform transformations, reading data from the Bronze container and writing it to the Silver container.
    - Conducted basic transformations and created a data model, including dimensions and fact tables, in a new notebook referred to as "Gold."

11. **Surrogate Key and Slowly Changing Dimensions**:
    - Implemented a surrogate key column in the dimension table.
    - Applied Slowly Changing Dimension Type 1 (Upsert) logic to manage data updates and inserts.
    - Created a Delta table to support these operations.

12. **Workflow Creation**: Established a workflow in Databricks to automate the data processing tasks.
![Screenshot (281)](https://github.com/user-attachments/assets/baf80d34-ddb2-4451-a542-d30d1e5f8806)


## Conclusion

This project effectively showcases the integration of various Azure services to build a robust data engineering pipeline, enabling efficient data ingestion, transformation, and storage.
