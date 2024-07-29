# Get started with Lakehouse in Microsoft Fabric

## Overview 
This hands-on lab experience in creating and managing a scalable, flexible data store using Microsoft Fabric's Lakehouse. Participants will learn to integrate data lake and data warehouse capabilities for efficient big data processing and analysis. The technical specifications include Power BI for data visualization, Power Query for creating visual data transformation queries, and OneLake for scalable storage based on Azure Data Lake Store Gen2. Additionally, Apache Spark will be used as the compute engine for big data processing, SQL for relational data analysis, and Delta Lake for bringing ACID transactions to Apache Spark and big data workloads.

## Objective

This lab is aimed to give learners hands-on experience in data management and analysis using Microsoft Fabric. learners will enhance their skills in data integration, transformation, storage, and analysis by leveraging Microsoft Fabric's powerful tools and features.

Participants will learn:

1. **Create and Ingest Data with a Microsoft Fabric Lakehouse**:This hands-on exercise aims to set up a Microsoft Fabric workspace, start by creating a new workspace and setting up a Lakehouse for scalable storage. Ingest data into the Lakehouse from various sources, then convert the data files into tables for structured analysis. Use SQL queries to manipulate and analyze the data, and leverage Power Query for advanced data transformation. Finally, create insightful reports using Power BI to visualize and share your findings.Participants will have set up a Microsoft Fabric workspace, ingested and transformed data into structured tables, and used SQL queries and Power Query to analyze and visualize the data. They will gain practical experience in creating comprehensive reports to communicate insights effectively.

2. **Analyze data with Apache Spark**: This hands-on exercise aims to Begin by creating a Lakehouse and uploading your data files. Next, create a notebook and load the data into a Spark DataFrame for exploration and analysis. Use Spark to transform the data, performing tasks such as filtering, aggregations, and joins. Work with tables using SQL queries to organize and analyze the data further. Finally, visualize the data directly within Spark to gain insights and facilitate decision-making.Participants will successfully set up a Lakehouse, upload and load data into Spark DataFrames, and explore and transform the data using Spark. They will also gain experience in working with tables, running SQL queries, and visualizing data to extract valuable insights.


## Prerequisites 

**Necessary Skills and Knowledge:**

- Basic Understanding of Data Warehousing and Data Lakes: Familiarity with the concepts of structured and unstructured data storage.
- SQL Knowledge: Ability to write and understand basic SQL queries.
- Data Analysis: Basic experience with data analysis and reporting.


## Architecture

Microsoft Fabric Lakehouse is a unified data platform that integrates the flexibility and scalability of a data lake with the structured querying capabilities of a data warehouse. Here is a detailed explanation of the key components involved:

- **OneLake Storage Layer** OneLake is the foundation of Microsoft Fabric's Lakehouse, providing a scalable and flexible storage solution built on Azure Data Lake Store Gen2. It supports storing vast amounts of structured and unstructured data efficiently.

- **Apache Spark** is the compute engine used in Microsoft Fabric for big data processing. It provides high-performance in-memory computation capabilities.

- **SQL compute engines** in Microsoft Fabric allow for querying and managing data using SQL semantics. This enables users to run complex queries on large datasets stored in the Lakehouse.

- **Delta Lake** is an open-source storage layer that provides ACID (Atomicity, Consistency, Isolation, Durability) transactions and scalable metadata handling.

- **Power BI** is a business analytics tool integrated with Microsoft Fabric, used for data visualization and reporting.

- **Power Query** is a data connection technology that enables users to discover, connect, and manipulate data across various sources.


## Architecture diagram

![](./Images/Create-and-ingest-data-with-MS-fabric-lakehouse.png)

## Explanation of Components

- **Microsoft Fabric Workspace:** A centralized environment within Microsoft Fabric where users can manage their data projects. This workspace provides access to various tools and services needed to create and analyze data in a unified platform.

- **Lakehouse:** A scalable and flexible data store within Microsoft Fabric that combines the features of a data lake and a data warehouse. It allows for the storage and querying of both structured and unstructured data using SQL and Apache Spark compute engines.

- **OneLake Storage Layer:** The underlying scalable storage layer used by the Lakehouse, built on Azure Data Lake Store Gen2. It provides robust, scalable storage for large volumes of data in various formats.

- **Data Files and Tables:** Ingested data files that are uploaded into the Lakehouse. These files can be transformed into structured tables that allow for efficient querying and analysis. Tables in Microsoft Fabric Lakehouse are based on the open-source Delta Lake file format.

- **SQL Endpoint:** A feature within Microsoft Fabric that enables users to perform SQL queries on the Lakehouse tables. It provides a familiar SQL interface for data analysts and engineers to query and analyze data efficiently.

- **Power Query:** A data connection technology that enables users to discover, connect, combine, and refine data across a wide variety of sources. In the context of Microsoft Fabric, Power Query allows for visual query creation and data transformation.

- **Power BI:** A suite of business analytics tools within Microsoft Fabric that enables users to create interactive reports and dashboards. Power BI is integrated with the Lakehouse to provide a seamless reporting and visualization experience based on the ingested data.

- **Data Transformation:** The process of converting raw data into a structured format that can be used for analysis. This includes operations such as grouping, filtering, and summarizing data to prepare it for querying and reporting.

- **Report Building:** The creation of interactive reports using Power BI, based on the data stored in the Lakehouse. This involves designing report layouts, selecting visualizations, and configuring report elements to effectively display data insights.

## Getting Started with the lab

## Accessing Your Lab Environment

Once you're ready to dive in, your virtual machine and lab guide will be right at your fingertips within your web browser.
 
![](./Images/labguide.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment Details** tab.
 
![Explore Lab Resources](./Images/env.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the top right corner.
 
![Use the Split Window Feature](./Images/spl.png)
 
## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](./Images/res.png)
 

## Support Contact

1. The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

   Learner Support Contacts:

    - Email Support: labs-support@spektrasystems.com
    - Live Chat Support: https://cloudlabs.ai/labs-support


2. Now, click on Next from the lower right corner to move on to the next page.

Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!

#### Happy Learning!!
