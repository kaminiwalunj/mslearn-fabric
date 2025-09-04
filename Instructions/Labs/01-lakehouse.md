# Lab 01: Create and Ingest Data with a Microsoft Fabric Lakehouse

### Estimated Duration: 120 Minutes

## Overview

The foundation of Microsoft Fabric is a Lakehouse, which is built on top of the OneLake scalable storage layer and uses Apache Spark and SQL compute engines for big data processing. A
Lakehouse is a unified platform that combines:

- The flexible and scalable storage of a data lake
- The ability to query and analyze data in a data warehouse

Imagine your company has been using a data warehouse to store structured data from its transactional systems, such as order history, inventory levels, and customer information. You have
also collected unstructured data from social media, website logs, and third-party sources that are difficult to manage and analyze using the existing data warehouse infrastructure. Your
company's new directive is to improve its decision-making capabilities by analyzing data in various formats across multiple sources, so the company chooses Microsoft Fabric.

Here, we explore how a lakehouse in Microsoft Fabric can help address scenarios like this by providing a scalable and flexible data store for files and tables that you can query using
SQL.

### Architecture Diagram

![](./Images/Create-and-ingest-data-with-MS-fabric-lakehouse.png)


## Lab objectives

In this exercise, you will complete the following tasks:

- Task 1: Create a workspace
- Task 2: Create a Lakehouse
- Task 3: Upload a file
- Task 4: Explore shortcuts
- Task 5: Load file data into a table
- Task 6: Use SQL to query tables
- Task 7: Create a visual query
- Task 8: Create a Report


## Get started with Microsoft Fabric with Its Lakehouses

Large-scale data analytics solutions have traditionally been built around a _data warehouse_, in which data is stored in relational tables and queried using SQL. The growth in "big data" (characterized by high _volumes_, _variety_, and _velocity_ of new data assets) together with the availability of low-cost storage and cloud-scale distributed compute technologies has led to an alternative approach to analytical data storage; the _data lake_. In a data lake, data is stored as files without imposing a fixed schema for storage. Increasingly, data engineers and analysts seek to benefit from the best features of both of these approaches by combining them in a _data lakehouse_; in which data is stored in files in a data lake and a relational schema is applied to them as a metadata layer so that they can be queried using traditional SQL semantics.

In Microsoft Fabric, a lakehouse provides highly scalable file storage in a _OneLake_ store (built on Azure Data Lake Store Gen2) with a metastore for relational objects such as tables and views based on the open source _Delta Lake_ table format. Delta Lake enables you to define a schema of tables in your lakehouse that you can query using SQL.


## Task 1: Create a workspace

Before working with data in Fabric, create a workspace with the Fabric trial enabled.

1. Open the Edge browser and sign in to [Microsoft Fabric](https://app.fabric.microsoft.com) at `https://app.fabric.microsoft.com`.

   - On the Microsoft Fabric page, enter your **email:** <inject key="AzureAdUserEmail"></inject> **(1)** and click **Submit** **(2)**.

     ![](./Images/fb_g2_1_0.png)

   - On the **Enter password** screen, enter your **Password:** <inject key="AzureAdUserPassword"></inject> **(1)** and click **Sign in** **(2)**.

     ![](./Images/fb_ex1_0_1.png)
   
      > **Note**: If you receive the **Welcome to the Fabric view** pop-up, click **Cancel** to skip the tour.

      ![](./Images/fb_ex1_1.png)

1. On the Fabric home page, click the **Fabric** icon from the left pane to open the Fabric experience.

   ![](./Images/fb_ex1_4.png)

1. In the Power BI view, select **Power BI** from the dropdown.

   ![](./Images/powerbi-1.png)

1. From the PowerBI home page, select **Account Manager (1)** from the top-right corner to start the **Free trial (2)** of Microsoft Fabric.

   ![Account-manager-start](./Images/freetrial.png)

1. On the **Activate your 60-day free Fabric trial capacity** window, click **Activate** to continue with the default region.

   ![Start-trial](<./Images/fb_ex1_5.png>)

1. Once your trial capacity is ready, you receive a confirmation message. Select **Stay on current page** to begin working in Fabric.

   ![](./Images/staycurrentonstage.png)

1. Click the **Account manager (1)** icon in the top-right corner. Under the **Profile** section, verify that the **Trial Status**  **(2)** shows the number of days remaining.

   ![](./Images/fb_ex1_6.png)

   > **Note:** You now have a **Fabric (Preview) trial** that includes a **Power BI trial** and a **Fabric (Preview) trial capacity**.
   
   > **Note:** Fabric trial gives full access to most features, but excludes **Copilot**, **trusted workspace access**, and **private link**.

1. In the menu bar on the left, select **Workspaces (1)** (the icon looks similar to &#128455;). Select **+ New Workspace (2)**

   ![](./Images/newworkspace.png)

1. Create a new workspace with a **Fabriclab\_<inject key="DeploymentID" enableCopy="false"/> (1)** , select a licensing mode that includes Fabric capacity **Trail**, and click on **Apply (2)**

   ![](<./Images/fb_ex1_7.png>)

   > **Note**: If you receive the **Introducing task flows (preview)** pop-up, click **Got it** to continue.

   ![](<./Images/fb_ex1_8.png>)

1. When your new workspace opens, it should be empty.

   ![Screenshot of an empty workspace in Power BI.](<./Images/fb_ex1_9.png>)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
>
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="f77f6f86-fc3c-4fca-a8d2-234693b73ba8" />

## Task 2: Create a Lakehouse

Now that you have a workspace, it's time to switch to the _Data engineering_ experience in the portal and create a data lakehouse for your data files.

1. Ensure the **Power BI** **(1)** icon is visible in the left pane. If available, click it, then click **New item** **(2)** at the top of the workspace.

   ![](<./Images/fb_g2_1_1.png>)

1. Search for **Lakehouse (1)** and select the option labeled **Lakehouse (2)** from the results.

   ![](<./Images/fb_g2_1_2.png>)

1. On the **New lakehouse** pane, enter **Lakehouse** **(1)** in the **Name** field, then click **Create** **(2)** to proceed.

   ![](<./Images/fb_g2_1_3.png>)

1. View the new lakehouse, and note that the **Lakehouse explorer** pane on the left enables you to browse tables and files in the lakehouse:

   - The **Tables** folder contains tables that you can query using SQL semantics. Tables in a Microsoft Fabric lakehouse are based on the open source _Delta Lake_ file format, commonly used in Apache Spark.
   - The **Files** folder contains data files in the OneLake storage for the lakehouse that aren't associated with managed delta tables. You can also create _shortcuts_ in this folder to reference data that is
     stored externally.
   - Currently, there are no tables or files in the lakehouse.

     ![](./Images/image91-1.png)

## Task 3: Upload a file

Fabric provides multiple ways to load data into the lakehouse, including built-in support for pipelines that copy data from external sources and data flows (Gen 2) that you can define using visual tools based on Power Query. However, one of the simplest ways to ingest small amounts of data is to upload files or folders from your local computer (or lab VM if applicable).

1. Download the **sales.csv** file from [https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/sales.csv](https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/sales.csv), saving it as
   **sales.csv** on your local computer (or lab VM if applicable).

   > **Note**: To download the file, open a new tab in the browser and paste it into the URL.

   > Right-click anywhere on the page containing the data and select **Save as** to save the page as a CSV file.

   - OR If you are using the lab virtual machine (lab VM) provided to you, you can get the file from the **C:\LabFiles\dp-data-main** directory.

1. On the **Lakehouse explorer** pane, click the ellipses **(1)** next to the **Files** folder, then select **New subfolder** **(2)**.

   ![](<./Images/fb_g2_1_4.png>)

1. On the **New subfolder** pane, enter **data** **(1)** in the **Folder name** field, then click **Create** **(2)** to add the subfolder.

   ![](<./Images/fb_g2_1_5.png>)

1. On the **Lakehouse explorer** pane, click the ellipses **(1)** next to the **data** folder, hover over **Upload** **(2)**, then select **Upload files** **(3)**.

   ![](<./Images/fb_g2_1_6.png>)

1. On the **Upload files** dialog, click the folder icon on the right to browse and select the **sales.csv** file from your local or lab machine.

   ![](<./Images/fb_g2_1_7.png>)

1. On the **Upload files** dialog, after selecting the **sales.csv** file, click **Upload** **(1)** to upload the file into the `data` folder.

   ![](<./Images/fb_g2_1_9.png>)

1. Once the upload is complete and the status shows **Completed**, click the **Close** icon at the top right to exit the **Upload files** dialog.

   ![](<./Images/fb_g2_1_10.png>)

1. In the **Lakehouse explorer** pane, expand **Lakehouse** **(1)**, then expand **Files** **(2)** and select the **data** **(3)** folder. Verify that the **sales.csv** **(4)** file has been uploaded successfully.

   ![Screenshot of uploaded sales.csv file in a lakehouse.](./Images/fb_g2_1_11.png)

1. Select the **sales.csv** file to see a preview of its contents.

   ![](<./Images/fb_cor_1_1.png>)

## Task 4: Explore shortcuts

In many scenarios, the data you need to work with in your lakehouse may be stored in some other location. While there are many ways to ingest data into the OneLake storage for your lakehouse, another option is to instead create a _shortcut_. Shortcuts enable you to include externally sourced data in your analytics solution without the overhead and risk of data inconsistency associated with copying it.

1. In the **ellipses (1)** menu for the **Files** folder, select **New shortcut (2)**.

   ![](./Images/newshortcut.png)

1. View the available data source types for shortcuts. Then close the **New shortcut** dialog box without creating a shortcut.

## Task 5: Load file data into a table

The sales data you uploaded is in a file, which data analysts and engineers can work with directly by using Apache Spark code. However, in many scenarios, you may want to load the data from the file into a table so that you can query it using SQL.

1. In the **Lakehouse explorer** pane, expand **Lakehouse** **(1)**, then expand **Files** **(2)** and select the **data** folder **(3)**. Confirm that the **sales.csv** file appears in the folder **(4)**.

   ![](<./Images/fb_g2_1_11.png>)

1. In the **data** folder, click the ellipses next to the **sales.csv** file to open the context menu.

   ![](<./Images/fb_g2_1_12.png>)

1. In the context menu, hover over **Load to Tables** **(1)**, then select **New table** **(2)** to start creating a table from the CSV file.

   ![](./Images/fb_cor_1_2.png)

1. In the **Load file to new table** dialog box, set the table name to **sales (1)** and confirm the load operation by selecting **Load (2)**. Then wait for the table to be created and loaded.

   > **Tip**: If the **sales** table does not automatically appear, in the **ellipses** menu for the **Tables** folder, select **Refresh**.

   ![](./Images/salesorder.png)

1. In the **Lakehouse explorer** pane, expand **Lakehouse** **(1)**, then expand **Tables** and select **sales** **(2)**. Confirm that the data from the **sales.csv** file is now loaded and displayed in table format **(3)**.

   ![Screenshot of a table preview.](./Images/fb_g2_1_13.png)

1. In the **ellipses (1)** menu for the **sales** table, select **View files (2)** to see the underlying files for this table

   ![Screenshot of a table preview.](./Images/tables.png)

1. In the **File view** for the **sales** table, observe that it contains Delta Lake log files and Parquet data files. These represent the physical storage format of the table.

   ![Screenshot of a table preview.](./Images/fb_g2_1_14.png)

   > **Note:** Files for a delta table are stored in _Parquet_ format, and include a subfolder named **\_delta_log** in which details of transactions applied to the table are logged.

## Task 6: Use SQL to query tables

When you create a lakehouse and define tables in it, a SQL endpoint is automatically created through which the tables can be queried using SQL `SELECT` statements.

1. At the top-right of the Lakehouse page, switch from **Lakehouse (1)** to **SQL analytics endpoint (2)**. Then wait a short time until the SQL query endpoint for your lakehouse opens in a visual interface from which you can query
   It's tables, as shown here:

   ![Screenshot of the SQL endpoint page.](./Images/fb_g2_1_15.png)

1. On the **Home** tab, click the dropdown arrow next to **New SQL query** **(1)**, then select **New SQL query** **(2)** to open a new query editor.

   ![Screenshot of the SQL endpoint page.](./Images/fb_g2_1_16.png)

1. In the new query editor, enter the following SQL query to calculate the total revenue by item:

   ```sql
   SELECT Item, SUM(Quantity * UnitPrice) AS Revenue
   FROM sales
   GROUP BY Item
   ORDER BY Revenue DESC;
   ```

1. Use the **&#9655; Run** button to run the query and view the results, which should show the total revenue for each product.

   ![Screenshot of a SQL query with results.](./Images/run.png)

## Task 7: Create a visual query

While many data professionals are familiar with SQL, data analysts with Power BI experience can apply their Power Query skills to create visual queries.

1. On the **Home** tab, click the dropdown arrow next to **New SQL query** **(1)**, then select **New visual query** **(2)** to open the visual query editor.

   ![Screenshot of a Visual query.](./Images/fb_g2_1_17.png)

1. Drag the **sales (1)** table to the new visual query editor pane that opens to create a **Power Query (2)** as shown here:

   ![Screenshot of a Visual query.](./Images/salesquery.png)

1. In the **Visual query 1** pane, click **Manage columns** **(1)** and select **Choose columns** **(2)**.

   ![Screenshot of a Choose columns dialog box.](./Images/choosecolumns.png)

1. In the **Choose columns** dialog, select only **SalesOrderNumber** and **SalesOrderLineNumber** **(1)**, then click **OK** **(2)**.

   ![Screenshot of a Choose columns dialog box.](./Images/fb_g2_1_18.png)

1. On the **Visual query 1** tab, click **Transform** **(1)**, then select **Group by** **(2)** to start grouping the selected columns.

   ![Screenshot of a Choose columns dialog box.](./Images/fb_g2_1_19.png)

1. On the **Group by** dialog, configure the following **Basic** **(1)** settings:

   - **Group by**: SalesOrderNumber **(2)**
   - **New column name**: LineItems **(3)**
   - **Operation**: Count distinct values **(4)**
   - **Column**: SalesOrderLineNumber **(5)**
   - Click **OK** **(6)** to apply the grouping.

   - When you're done, the results pane under the visual query shows the number of line items for each sales order.

      ![](<./Images/fb_g2_1_20.png>)

## Task 8: Create a Report


In this task, we will create a new semantic model and add a table to the dataset, which will define the data model to be used for reporting in Power BI.


1. Under the **Home** tab, Click on  **New semantic model** **(1)** to create the semantic model.

   ![Screenshot of a data model.](./Images/task8-1.jpg)

   > **Note**: In this exercise, the data model consists of a single table. In a real-world scenario, you would likely create multiple tables in your lakehouse, each of which would be included in the model. You could then define relationships between these tables in the model.

1. Enter **Custom semantic model** **(1)** in the name field and select the table **sales** **(2)**, than click on **Confirm** **(3)** to proceed.

   ![](./Images/task8-2.jpg)

1. In the hub menu bar on the left, Click on your workspace **Fabriclab_XXXXX** **(1)**.

   ![](./Images/task8-3.jpg)

1. Select the **Custom semantic model** and click on **Create report** option to begin creating a report using the semantic model.

   ![](./Images/task8-4.jpg)

1. In the **Data** pane, expand the **sales** table **(1)**, then:

   - Select **Item** **(2)** to use it as the category.
   - Select **Quantity** **(3)** to calculate the total quantity for each item.
   - A **Table Visualization** **(4)** is automatically added to the report canvas.

      ![](./Images/task8-5.jpg)

1. In the **Visualizations** pane, follow these steps to convert the table into a clustered bar chart:

   - Click the **Build visual** icon **(1)** to ensure you're in visual editing mode.
   - Select the **Clustered bar chart** visualization type **(2)**.
   - The report canvas updates to display the item-wise total quantity in a bar chart **(3)**.

      ![](./Images/task8-6.jpg)

1. To save the report, click **File** **(1)** in the top menu, then select **Save** **(2)**.

   ![](./Images/fb_g2_1_26.png)

1. On the **Save your report** screen, enter **Item Sales Report** **(1)** as the name, then click **Save** **(2)** to save it to the selected workspace.

   ![](./Images/task8-7.jpg)

1. Then, in the hub menu bar on the left, select your workspace to verify that it contains the following items:

   - Your lakehouse.
   - The SQL analytics endpoint for your lakehouse.
   - A default dataset for the tables in your lakehouse.
   - The **Item Sales Report** report.

      ![](./Images/task8-8.jpg)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
>
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com We are available 24/7 to help you out.

<validation step="8be3d605-b09f-4738-b1e5-c83a1e304b80" />

<validation step="d75ef970-6298-404c-aeeb-8dafe17b3ac2" />

## Summary

In this exercise, you have accomplished the following:

- Created a workspace to organize and manage your resources
- Built a Lakehouse for storing and processing data
- Uploaded a file into the Lakehouse environment
- Explored shortcuts to efficiently manage data access
- Loaded file data into a structured table
- Queried tables using SQL for data exploration
- Designed a visual query for easier insights
- Created a report to visualize and share your findings


## **Congratulations! You have successfully completed this lab. Please click on next**

![](./Images/bar_g_g_2.png)

#### Happy Learning!!
