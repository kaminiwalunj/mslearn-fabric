# Get started with Real-Time Analytics and Data Science with Microsoft Fabric

### Overall Estimated Duration: 4 Hours

## Prerequisites

- Basic understanding of cloud computing and data analytics concepts.  
- Familiarity with Microsoft Azure services.  
- A Microsoft Fabric-enabled workspace with necessary permissions.  
- Access to Microsoft Fabric services such as OneLake, Data Engineering, and Data Science experiences.  
- Familiarity with PowerBI reports.

## Architecture

The architecture for this lab is designed to enable a seamless, end-to-end workflow for data processing and machine learning within a Lakehouse environment. The process begins with the creation of a Lakehouse, which acts as the central data storage layer where raw files are uploaded for further analysis. Users then operate within a notebook interface, where data is loaded into DataFrames for exploration and transformation. Leveraging Apache Spark, machine learning models are trained efficiently at scale within this environment. To manage and monitor experiments, MLflow is integrated into the architecture, allowing users to track, compare, and analyze multiple model runs. Once a model is finalized, it is saved for future use, and the notebook is persisted as part of the workflow. Finally, the Spark session is properly terminated to optimize resource usage. This architecture supports a structured, scalable, and reproducible pipeline—from data ingestion to model training and experiment tracking, ensuring clarity and control at every stage of the lab.

## Architecture Diagram

![Architecture Diagram](./Images/archdiagram.png)

## Explanation of Components

The architecture for this lab involves several key components:

- **Workspace**: A centralized environment for managing resources, projects, and collaboration.
- **Lakehouse**: A unified storage solution combining data lakes and warehouses for scalable analytics.
- **Notebook**: An interactive document for writing, executing, and visualizing code, commonly used in data science and engineering.

## Getting Started with the Lab

Welcome to Real-Time Analytics and Data Science with Microsoft Fabric Workshop! We've prepared a seamless environment for you to explore and learn about fabric services. Let's begin by making the most of this experience.

## Accessing Your Lab Environment

Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.
 
![](./Images/8-7-25-g1.png)
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment Details** tab.
 
![Explore Lab Resources](./Images/june-getting-started-3.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the guide in a separate window by selecting the **Split Window** button from the top right corner.
 
![Use the Split Window Feature](./Images/june-getting-started-2.png)
 
## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](./Images/8-7-25-g2.png)
 
## Lab Guide Zoom In/Zoom Out
 
1. To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

  ![OpenAI](./Images/june-getting-started-6upd.png)

## Login to the Azure Portal

1. On your virtual machine, click on the Azure Portal icon as shown below:
 
   ![Launch Azure Portal](./Images/sc900-image.png)
 
1. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](./Images/sc900-image-1.png)
 
1. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![Enter Your Password](./Images/sc900-image-2.png)

1. If you see the 'Action Required' pop-up, click 'Ask Later'.
 
   > **NOTE**: Do not enable MFA, select Ask Later.

1. If you see the pop-up Stay Signed in?, select No.

   > **NOTE**: If prompted with MFA, and the Ask Later option is not available, please follow the steps highlighted under - [Steps to Proceed with MFA Setup if Ask Later Option is Not Visible](#steps-to-proceed-with-mfa-setup-if-ask-later-option-is-not-visible)

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a Welcome to **Microsoft Azure** popup window appears, select **Maybe Later** to skip the tour.

## Steps to Proceed with MFA Setup if Ask Later Option is Not Visible

   > **Note:** Continue with the exercises if MFA is already enabled or the option is unavailable.

1. At the **"More information required"** prompt, select **Next**.

1. On the **"Keep your account secure"** page, select **Next** twice.

1. **Note:** If you don’t have the Microsoft Authenticator app installed on your mobile device:

   - Open **Google Play Store** (Android) or **App Store** (iOS).
   - Search for **Microsoft Authenticator** and tap **Install**.
   - Open the **Microsoft Authenticator** app, select **Add account**, then choose **Work or school account**.

1. A **QR code** will be displayed on your computer screen.

1. In the Authenticator app, select **Scan a QR code** and scan the code displayed on your screen.

1. After scanning, click **Next** to proceed.

1. On your phone, enter the number shown on your computer screen in the Authenticator app and select **Next**.
       
1. If prompted to stay signed in, you can click **No**.

1. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

1. Now, click on the **Next** from the lower right corner to move to the next page.
   
### Support Contact
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.
 
Learner Support Contacts:
 
- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!

Now, click on **Next** from the lower right corner to move on to the next page.

  ![Asklater](./Images/next.png)
 
### Happy learning!
