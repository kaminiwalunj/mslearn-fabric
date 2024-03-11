# Lab 1: Get started with Real-Time Analytics in Microsoft Fabric

## Overview

Microsoft Fabric provides an end-to-end platform for data solutions, including real-time data analytics. Synapse Real-Time Analytics in Fabric uses a KQL Database to provide table storage and Kusto Query Language (KQL) which is a powerful tool for analyzing data. This structure provides an efficient way to find insights and patterns from textual or structured data. Moreover, KQL is optimized for data that includes a time series component, such as real-time data from log files or streaming services. With Real-Time Analytics, you can focus and scale up your analytics solution while democratizing data for the needs for your entire data organization.

### _Architecture Diagram_

![Architecture Diagram](./Images/Synapse-Real-Time-Analytics-in-Fabric.png)

## Get started with Real-Time Analytics in Microsoft Fabric

Microsoft Fabric provides a runtime that you can use to store and query data by using Kusto Query Language (KQL). Kusto is optimized for data that includes a time series component, such 
as real-time data from log files or IoT devices.

In Fabric, you only need a source and a Kusto database to start streaming data in and out of Fabric and writing your queries using KQL. Microsoft Fabric also provides KQL Querysets that 
can be shared within the tenant and Power BI using what's known as quick create.

   ![](./Images/realtime-analtyics1.png)

This lab takes approximately **30** minutes to complete.

> **Note**: You'll need a Microsoft Fabric license to complete this exercise. Complete the previous task to proceed further.

## Task 1 : Create a workspace

Before working with data in Fabric, create a workspace with the Fabric trial enabled.

1. Sign into [Microsoft Fabric](https://app.fabric.microsoft.com) at `https://app.fabric.microsoft.com` and select **Power BI**.

   ![](./Images/power-bi.png)

2. From the PowerBI home page, select **Account Manager** from the top-right corner to start the free **Microsoft Fabric trial**.
    
    ![](./Images/PwrBI_1.png)
  
3. In the Account Manager, select **Start Trial**.

   ![](./Images/PwrBI_2.png)
   
4. If prompted, agree to the terms and then select **Start trial**. 

   ![](./Images/PwrBI_3.png)
   
5. Once your trial capacity is ready, you receive a confirmation message. Select **Got it** to begin working in Fabric.

    ![](./Images/PwrBI_4.png)
   
6. Open your **Account manager** again. Notice that you now have a heading for **Trial status**. Your Account manager keeps track of the number of days remaining in your trial.

    ![](./Images/PwrBI_5.png)

   You now have a **Fabric (Preview) trial** that includes a **Power BI trial** and a **Fabric (Preview) trial capacity**.

7. In the menu bar on the left, select **Workspaces** (the icon looks similar to &#128455;).

   ![](./Images/workspace-1.png)

8. Create a new workspace with a name **dp_fabric-<inject key="Deployment ID" enableCopy="false"/>**, selecting a licensing mode that includes Fabric capacity (*Trial*, *Premium*, or *Fabric*).
   
9. When your new workspace opens, it should be empty, as shown here:

    ![Screenshot of an empty workspace in Power BI.](./Images/new-workspace-2.png)

  
10. At the bottom left of the Power BI portal, select the **Power BI** icon and switch to the **Microsoft Fabric** experience.

## Task 2 : Download file for KQL database

Now that you have a workspace, it's time to switch to the *Synapse Real-Time Analytics* experience in the portal and download the data file you're going to analyze.

1. Download the data file for this exercise from [https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/sales.csv](https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/sales.csv), saving it as **sales.csv** on your local computer (or lab VM if applicable)

   OR If you are using the lab virtual machine (lab VM) provided to you, you can get the file from the **C:\LabFiles** directory.

2. Return to browser window with **Microsoft Fabric** Experience.

## Task 3 : Create a KQL database

Kusto query language (KQL) is used to query static or streaming data in a table that is defined in a KQL database. To analyze the sales data, you must create a table in a KQL database and ingest the data from the file.

1. In the **Microsoft Fabric** experience portal, select the **Synapse Real-Time Analytics** experience image as shown here:

    ![Screenshot of selected Fabric Experience home with RTA selected](./Images/fabric-experience-home.png)

2. On the **Home** page for the **Real-Time Analytics** experience, select **KQL database** and create a new database with a name as **kql-database**.

    ![Screenshot of selected Fabric Experience home with RTA selected](./Images/KQL-database.png)

3. When the new database has been created, select the option to Get Data from **Local File**. Then use the wizard to import the data into a new table by selecting the following options:

    ![Screenshot of selected Fabric Experience home with RTA selected](./Images/select-data.png)
    
    - **Destination**:
        - **Database**: *The database you created is already selected*
        - **Table**: *Create a new table named* **sales**.
    - **Source**:
        - **Source type**: File
        - **Upload files**: *Drag or Browse for the file you downloaded earlier*
    - **Schema**:
        - **Compression type**: Uncompressed
        - **Data format**: CSV
        - **Ignore the first record**: *Selected*
        - **Mapping name**: sales_mapping
    - **Summary**:
        - *Review the preview of the table and close the wizard.*

> **Note**: In this example, you imported a very small amount of static data from a file, which is fine for the purposes of this exercise. In reality, you can use Kusto to analyze much larger volumes of data; including real-time data from a streaming source such as Azure Event Hubs.

## Task 4 : Use KQL to query the sales table

Now that you have a table of data in your database, you can use KQL code to query it.

1. Make sure you have the **sales** table highlighted. From the menu bar, select the **Query table** drop-down, and from there select **Show any 100 records** .

2. A new pane will open with the query and its result. 

3. Modify the query as follows:

    ```kusto
   sales
   | where Item == 'Road-250 Black, 48'
    ```

4. Run the query. Then review the results, which should contain only the rows for sales orders for the *Road-250 Black, 48* product.

5. Modify the query as follows:

    ```kusto
   sales
   | where Item == 'Road-250 Black, 48'
   | where datetime_part('year', OrderDate) > 2020
    ```

6. Run the query and review the results, which should contain only sales orders for *Road-250 Black, 48* made after 2020.

7. Modify the query as follows:

    ```kusto
   sales
   | where OrderDate between (datetime(2020-01-01 00:00:00) .. datetime(2020-12-31 23:59:59))
   | summarize TotalNetRevenue = sum(UnitPrice) by Item
   | sort by Item asc
    ```

8. Run the query and review the results, which should contain the total net revenue for each product between January 1st and December 31st 2020 in ascending order of product name.

9. Select **Save as KQL queryset** and save the query as **Revenue by Product**.

## Task 5 : Create a Power BI report from a KQL Query set

You can use your KQL Queryset as the basis for a Power BI report.

1. In the query workbench editor for your query set, run the query and wait for the results.

2. Select **Build Power BI report** and wait for the report editor to open.

3. In the report editor, in the **Data** pane, expand **Kusto Query Result** and select the **Item** and **TotalRevenue** fields.

4. On the report design canvas, select the table visualization that has been added and then in the **Visualizations** pane, select **Clustered bar chart**.

    ![Screenshot of a report from a KQL query.](./Images/powerbireport.png)

5. In the **Power BI** window, in the **File** menu, select **Save**. Then save the report as **Revenue by Item.pbix** in the workspace where your lakehouse and KQL database are defined using a **Non-Business** sensitivity label.
6. Close the **Power BI** window, and in the bar on the left, select the icon for your workspace.

    Refresh the Workspace page if necessary to view all of the items it contains.

7. In the list of items in your workspace, note that the **Revenue by Item** report is listed.

## Clean up resources

In this exercise, you have created a lakehouse, a KQL database to analyze the data uploaded into the lakehouse. You used KQL to query the data and create a query set, which was then used to create a Power BI report.

If you've finished exploring your KQL database, you can delete the workspace you created for this exercise.

1. In the bar on the left, select the icon for your workspace.
2. In the **...** menu on the toolbar, select **Workspace settings**.
3. In the **Other** section, select **Remove this workspace**.
