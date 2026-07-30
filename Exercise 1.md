# Exercise 1: Embedding Creation

#### Estimated Duration: 120 Minutes

## 📘 Scenario

At Contoso Ltd., employees struggle to quickly find relevant information from a large collection of multilingual documents distributed across the organization. To address this challenge, the engineering team plans to build an AI-powered document processing pipeline using Azure services. The solution will automatically extract content from documents, translate text when required, and generate vector embeddings to support intelligent semantic search and accurate question-answering experiences.

## 📋 Overview

In this exercise, you will gain hands-on experience in setting up a comprehensive Azure-based environment for embedding creation and document processing. The exercise is structured into two main parts:

- **Configuring Azure Resources:** You will deploy and configure essential Azure services, including Microsoft Foundry, Azure AI Search (Foundry IQ), Azure AI Document Intelligence, and Azure AI Translator. These resources are required to generate and manage document embeddings and build an intelligent search solution.

- **Deploying Azure Functions:** You will deploy Azure Functions to automate document processing. These functions will extract text from documents, translate content when required, generate embeddings, and process user queries.

## 🎯 Objectives

In this exercise, you will complete the following tasks:

- Task 1: Create a Microsoft Foundry Resource and Deploy Models
  - Task 1.1: Create a Microsoft Foundry Resource
  - Task 1.2: Deploy Models in Microsoft Foundry portal
- Task 2: Create Azure AI Search Resources
  - Task 2.1: Create an AI Search (Foundry IQ) Service
  - Task 2.2: Create Document Intelligence Resource
  - Task 2.3: Create Translator Resource
- Task 3: Deploy Azure Function with Embeddings  

### Task 1: Create a Microsoft Foundry Resource and Deploy Models

In this task, you will begin by deploying a Microsoft Foundry resource through the Azure portal. This involves creating a Foundry resource, configuring it with the appropriate settings, and deploying models such as **gpt-5.4** and **text-embedding-ada-002** using the Microsoft Foundry portal.

Microsoft Foundry provides a unified experience for discovering, deploying, and managing foundation models for building AI-powered applications. Follow these steps to deploy a model using the Microsoft Foundry portal:

### Task 1.1: Create a Microsoft Foundry Resource

1. In the search box of the Azure portal, type **Microsoft Foundry (1)** and select **Microsoft Foundry (2)** from the search results.

   ![](media/foundrynew.png)

1. On the **Microsoft Foundry** page, under Use with Foundry click **+ Create**.

    ![](media/foundry1.png)

1. On the **Basics** tab, configure the following settings:

    - **Subscription:** Default - Pre-assigned subscription **(1)**

    - **Resource Group:** Openai-embedded-<inject key="Deployment ID" enableCopy="false"></inject> **(2)**

    - **Name:** foundry-<inject key="Deployment ID" enableCopy="false"></inject> **(3)**

    - **Region:** <inject key="Region" enableCopy="false" /> **(4)**

    - **Default project name:** proj-default **(5)**

        ![](media/foundry2.png)

1. Click **Review + create**. Review the configuration and click **Create**.
    
    ![](media/foundry3.png)

1. Once the deployment is complete, click on **Go to resource**

    ![](media/foundry4.png)

### Task 1.2: Deploy Models in Microsoft Foundry portal

In this task, you will deploy the AI models required for the lab using Microsoft Foundry. The **gpt-5.4** model will generate grounded responses, while the **text-embedding-ada-002** model will generate vector embeddings for semantic search.

1. In the **Microsoft Foundry** resource click on **Go to Foundry portal**.

    ![](media/foundry5-new.png)

1. Copy the **API key** from the proj-default.

    ![](media/foundry6.png)

    > **Note:** Copy the **API key** and save it in Notepad. You will use it later in the lab.

1. From the navigation pane, select **Build**.

    ![](media/foundry7.png)

1. Click **Deploy(1)** and select **Deploy base model (2)** In Deployments.

    ![](media/foundry8.png)

5. On the **Select a model** page, search for **gpt-5.4 (1)**, select **gpt-5.4 (2)**, and click **Deploy (3)** go to **Custom settings (4)**.

    ![](media/foundry9.png)

    ![](media/foundry10.png)

6. Configure the deployment using the following settings:

    - **Deployment name:** gpt-5.4 **(1)**
    
    - **Deployment type:** Global Standard **(2)**
    
    - **Tokens per Minute Rate Limit:** **40K (3)**
    
    - Click **Deploy (4)**

        ![](media/foundry11.png)

        > **Note:** Copy the deployment name **gpt-5.4** and save it in Notepad. You will use it later in the lab.

7. Click **Deploy(1)** again and select **Deploy base model(2)** In Deployments.

    ![](media/foundry12.png)

8. On the **Select a model** page, search for **text-embedding-ada-002 (1)**, select **text-embedding-ada-002 (2)**, and click **Deploy (3)** go to **Custom settings (4)**.

    ![](media/foundry13.png)

    ![](media/foundry14.png)

9. Configure the deployment using the following settings:

    - **Deployment name:** text-embedding-ada-002 **(1)**
    
    - **Deployment type:** Global Standard **(2)**
    
    - **Tokens per Minute Rate Limit:** **40K (3)**
    
    - Click **Deploy (4)**

        ![](media/foundry15.png)

        > **Note:** Copy the deployment name **text-embedding-ada-002** and save it in Notepad. You will use it later in the lab.

## Task 2: Create Azure AI Search Resources

In this task, you will create the required Azure resources for AI Search, Document Intelligence, and Translator services. This involves setting up each service with the correct configurations, including subscription, resource group, and pricing tier, to support the document processing pipeline.

### Task 2.1: Create AI Search Service

1. Navigate back to the Azure portal, type **AI Search (1)** in the search box, and select **AI Search (Foundry IQ) (2)** from the results.

    ![](./media/E1T2S1-2804.png)

1. On the **Microsoft Foundry | AI Search** blade, click on **+ Create**.

    ![](./media/l1-12-5.png)

1. On the **Basics** tab of **Create a search service** resource page, enter the following details:
   
    - Subscription: Default - **Pre-assigned subscription (1)**
    
    - Resource Group: **Select Openai-embedded-<inject key="Deployment ID" enableCopy="false"></inject> (2)**

    - Service name: **aisearch-<inject key="Deployment ID" enableCopy="false"></inject> (3)**
    
    - Location: Select **<inject key="Region" enableCopy="false" /> (4)**
    
    - Pricing tier: **Standard (5)**

      >**Note:** If you are unable to Select **Standard** pricing tier in **East US**, please select **East US 2** or **Central US** and deploy.

    - Click on **Review + create (6)**

      ![](./media/am6.png)

1. Review the configuration, and click on **Create**.

     ![](./media/lab1-12-8.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
<validation step="c27751de-8370-4a29-92b9-c79ee1e1e436" />

### Task 2.2: Create Document Intelligence Resource

1. On the Azure portal, type **Document intelligence (1)** in the search box and select **Document intelligence (2)** from the results.

    ![](./media/E1T2.2S1-2804.png)

1. On the **Microsoft Foundry | Document intelligence (1)** blade, click on **+ Create (2)**.

    ![](./media/l12-12-02.png)

1. On the **Basics** tab of **Create Document Intelligence** resource page, enter the following details:
   
    - Subscription: Default - **Pre-assigned subscription (1)**
    
    - Resource group: Select **Openai-embedded-<inject key="Deployment ID" enableCopy="false"></inject> (2)**
    
    - Region: Select **<inject key="Region" enableCopy="false" /> (3)**
    
    - Name: **Document-intelligence-<inject key="Deployment ID" enableCopy="false"></inject> (4)**
    
    - Pricing tier: **Standard S0 (1 Call per minute for training API) (5)**

      ![](./media/am8.png)
        
1. Click on **Review + create**, review the configuration, and click on **Create**.

    ![](./media/am26.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
<validation step="a4912828-00ad-4dde-83a3-75feb53266d3" />

### Task 2.3: Create Translator Resource

1. On the Azure portal, type **Translators (1)** in the search box and select **Translators (2)** from the results.

    ![](./media/E1T2.3S1-2804.png)

1. On the **Microsoft Foundry | Translator (1)** blade, click on **+ Create (2)**.

    ![](./media/l1-12-6.png)

1. On the **Basics** tab of **Create Translator** resource page, enter the following details:
   
    - Subscription: **Default - Pre-assigned subscription (1)**
    
    - Resource group: **Openai-embedded-<inject key="Deployment ID" enableCopy="false"></inject> (2)**
    
    - Region: Select **<inject key="Region" enableCopy="false" /> (3)**
    
    - Name: **Translator-<inject key="Deployment ID" enableCopy="false"></inject> (4)**
    
    - Pricing tier: **Standard S1 (Pay as you go) (5)**

    - Click on **Review + create (6)**

      ![](./media/am10.png)
    
1. Review the configuration and click on **Create**.

    ![](./media/am27.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
<validation step="f7eb2333-4b72-4cdb-809d-fd4c522ff2aa" />

## Task 3: Deploy Azure Function with Embeddings

In this task, you will deploy Azure Functions that automate the document processing workflow.

1. From the LabVM, open **File Explorer** by selecting its icon on the Windows Taskbar.

    ![](./media/12.png)

1. Navigate to `C:\LabFiles` **(1)** and double-click on the `deploy-01.json` **(2)** file to open it. 

1. Click on **Try an app on this PC** and select **Notepad (3)** and click **OK (4)**. Copy the template in Notepad for future deployment.

    ![](./media/am12.png)

    >Note: The `deploy-01.json` file is an Azure Resource Manager (ARM) template that automates the deployment of the infrastructure required for this lab. It defines resources such as the Storage Account, Azure Function App, Azure AI Search, Azure AI Document Intelligence, Translator, and Microsoft Foundry integration, along with their configurations and application settings. During the lab, you will update a few parameters in this template before deploying the complete solution.

1. Navigate back to the Azure Portal, type **Deploy a custom template (1)** in the search box, and select **Deploy a custom template (2)** from the results.

    ![](./media/E1T3S4-2804.png)

1. On the **Custom deployment** page, click on **Build your own template in the editor**.

    ![](./media/am14.png)

1. Paste the template you copied in step 2 into the ARM template editor, locate the **AIFoundryModel** parameter and verify the **defaultValue** **(line no: 104 )** is set to `gpt-5.4` **(1)**. Also verify that **AIFoundryDeploymentType** **(line no: 111)** is set to `Chat` **(2)**.

     ![](./media/new01.png)

1. Scroll down to the embeddings section and ensure **AIFoundryEmbeddingsModel** have the **defaultValue** **(line no: 118)** set to `text-embedding-ada-002`.

     ![](./media/new02.png)

1. Click on **Save**.

    ![](./media/new03.png)

1. On the **Basics** tab of **Custom deployment** page, enter the required details given below:

    |Variables	|Values|
    |---|---|
    |**Subscription** | Default - Pre-assigned subscription |
    |**Resource group** | Openai-embedded-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**Region** | <inject key="Region" enableCopy="false" /> |
    |**Azure AI Search** | aisearch-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**Azure AI Search Sku**| standard |
    |**Hosting Plan Name** | hostingplan-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**Hosting Plan Sku** | B3 |
    |**Storage Account Name** | storage<inject key="Deployment ID" enableCopy="false"></inject> |
    |**Function Name** | Functionapp-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**Application Insights Name** | Application-insights-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**Document Intelligence** |Document-intelligence-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**Translator Name** | Translator-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**AI Foundry Name** | foundry-<inject key="Deployment ID" enableCopy="false"></inject> |
    |**AI Foundry Key** | Paste the key that you copied in Task 1.2, Point 2 |
    |**AI Foundry Project Name** | proj-default |

      ![](./media/new04.png)

1. Leave the other value as default and click on **Review + create**, review the configuration, and click on **Create**.

    ![](./media/23052025(3).png)

1. Once the deployment is complete, click on **Go to resource group**.

    >**Note:** The deployment may take around 15-20 minutes to complete, as it is deploying multiple resources and Azure Functions.

    ![](./media/lab1-12-11.png)

1. On the **Overview** page of **Openai-embedded-<inject key="Deployment ID" enableCopy="false"></inject>** resource group, click on **Functionapp-<inject key="Deployment ID" enableCopy="false"></inject>** function app resource.

    ![](./media/rgfunction.png)

1. On the Overview page of **Functionapp-<inject key="Deployment ID" enableCopy="false"></inject>** page, review the three functions that are present under the **Functions** tab.

    ![](./media/24-07-2024(39).png)

1. The Azure Functions are triggered at different stages. Please find it in detail:

    - **BatchStartProcessing:** When a document is uploaded to Azure Storage, it automatically triggers this Azure Function. This function acts as the initial step in the document processing pipeline. Here's how it works:

        - A blob trigger is set up on the Azure Function.
        - As soon as a new file is added to the specified Azure Storage container, the function is activated.
        - This function then initiates the document extraction process using Document Intelligence.

    - **BatchPushResults:** Once the paragraphs are extracted from the document, this Azure Function is triggered. This function handles two tasks:

        - If required, it translates the extracted text using Azure Translator.
        - It then converts the processed text into embeddings using the Microsoft Foundry Service.
        - This function could be triggered by a queue message or by the completion of the first function.

    - **ApiQnA:** When a user submits a search query, this Azure Function is triggered. This function performs several crucial steps:

        - It processes the user's query, potentially cleaning or formatting it.
        - It performs a vector search using the query against the stored embeddings.
        - It then uses Microsoft Foundry to generate a comprehensive answer based on the search results.
        - Finally, it returns this answer to the user.

1. In the left-hand menu, select **Environment variables (1)** under the **Settings** section and click on **Advanced edit (2)** at the top of the page to view or modify the environment variables.

    ![](./media/am15.png)

1. Copy all the values displayed in the environment variables section and paste them into Notepad for the next exercise.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
<validation step="da23d4f2-068b-4149-8071-9870b25d261d" />

## 🧾 Summary

In this exercise, you have accomplished the following:

- Provisioned a Microsoft Foundry resource.
- Deployed models using the Microsoft Foundry portal.
- Deployed a Document Intelligence resource.
- Deployed a Translator resource.
- Deployed a Custom template
- Integrated Microsoft Foundry models into your application.

### Click on **Next >>** to proceed to the next exercise.

![](./media/page_02.png)
