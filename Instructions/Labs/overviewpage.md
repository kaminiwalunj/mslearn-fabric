# Create and ingest data with a Microsoft Fabric Lakehouse

## Overview 
The purpose of this lab is to provide hands-on experience in creating and managing a scalable and flexible data store using Microsoft Fabric's Lakehouse. Participants will learn to integrate the capabilities of both data lakes and data warehouses for efficient big data processing and analysis.

The utilized technical specifications are as follows:

  1. Power BI: For data visualization and reporting.
  2. Power Query: For creating visual data transformation queries.
  3. OneLake: Scalable storage layer based on Azure Data Lake Store Gen2.
  4. Apache Spark: Compute engine for big data processing.
  5. SQL: Query engine for relational data analysis.
  6. Delta Lake: Open source storage layer that brings ACID transactions to Apache Spark and big data workloads.


## Objective

By the end of this lab, you will enhance your data management and analysis skills by leveraging Microsoft Fabric's. You will:


**Create a Microsoft Fabric Workspace:** etup: Learn how to initiate a new workspace within Microsoft Fabric. This involves signing into the Fabric platform, navigating to the workspace creation interface, and configuring it with the appropriate Fabric capacity. Trial Activation: Activate a Fabric trial to access all necessary features and tools required for the lab exercises. This includes enabling any additional capacity or features provided during the trial period.

**Set Up a Lakehouse:** Creation: Create a new Lakehouse within the Fabric workspace. This involves defining its name, setting up its configuration, and integrating it with the OneLake scalable storage layer.
Configuration: Configure the Lakehouse to leverage the benefits of both data lakes and data warehouses. This setup allows you to manage and query data efficiently using the unified platform.

**Ingest Data**: Upload: Import data files into the Lakehouse. This includes uploading files from your local computer or a virtual machine to the Lakehouse’s storage. Data Management: Organize the uploaded data within the Lakehouse. This may involve creating subfolders for better data organization and verifying that files are correctly uploaded and accessible.

**Convert Files to Tables**: Transformation: Convert the uploaded data files into structured tables within the Lakehouse. This process involves defining table schemas and loading data from files into these tables to make it queryable. Management: Manage and refresh the newly created tables to ensure they reflect the latest data and are properly structured for querying.

Run SQL Queries : Query Execution  Utilize the SQL endpoint provided by Microsoft Fabric to write and execute SQL queries against the Lakehouse tables. This allows you to perform complex data analysis and retrieve insights from the stored data.
Results Analysis: Review the results of your SQL queries to interpret data and generate meaningful insights. This includes analyzing query outputs and understanding the data trends.
Create Visual Queries:

**Power Query**: Use Power Query to visually create and transform data queries. This involves applying various transformations to prepare data for analysis.
Visualization: Develop visual queries to represent data in an easily understandable format, facilitating better data interpretation and decision-making.
Build Reports:

Report Creation: Develop interactive reports using Power BI based on the data in the Lakehouse. This includes designing report layouts, selecting appropriate visualizations, and configuring report elements to display data effectively.
Saving and Sharing: Save your completed reports within the Fabric workspace and share them with stakeholders. This step includes ensuring that reports are accessible and properly formatted for collaborative analysis and decision-making.
