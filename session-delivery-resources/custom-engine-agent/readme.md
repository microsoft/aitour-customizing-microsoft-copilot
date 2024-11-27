# Instructions for Custom engine copilots with​ Teams AI Library and VSCode

This demo showcases how to build a custom engine copilot with Retrieval-Augmented Generation for sophisticated question answering using Teams AI library and Teams Toolkit.

Video instructions are available [here](https://aka.ms/AArxxcf).

## Pre-requisites

- [Node.js](https://nodejs.org/), supported versions: 16, 18
- [Teams Toolkit for Visual Studio Code](https://aka.ms/teams-toolkit) version 5.10.1
- Prepare your own [Azure OpenAI](https://aka.ms/oai/access), [Azure AI Search](https://azure.microsoft.com/en-us/products/ai-services/ai-search) and [storage account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create) resources.
- A Microsoft 365 Account with a permission to **Upload custom apps** to Teams.

## Get started with Azure OpenAI

1. Start your demo in Azure OpenAI resource and navigate to Azure AI Foundry.
2. Create a deployment model, From the **Deployments** tab, select **Create a new deployment**. Fill out the following details and select **Create**:
    - **Deployment name:** Recommended to use the same name with the selected deployment model, such as `gpt-4`.
    - **Select a model:** Select `gpt-4` or higher model.
    - **Model version:** Auto update to default.
    - **Deployment type:** Standard.
    - **Content Filter:** Default.
3. Create an embeddings deployment model, select **Create a new deployment**. Fill out the following details and select Create:
    - **Select a model:** `text-embedding-ada-002`.
    - **Model version:** Default.
    - **Deployment type:** Standard.
    - **Deployment name:** Choose a memorable name, such as text-embeddings
    - **Content Filter:** Default.
4. Once your models are successfully created, you can navigate to **Chat**. In the **Setup** section, select **Add your data** tab and then **Add a data source**.
5. Select **Upload files (preview)**, then fill the details as the following and select **Next**:
    - **Subscription:** Select the subscription you created your Azure resources.
    - **Select Azure Blob storage resource:** Select your storage resource. (You'll see a message *Azure OpenAI needs your permission to access this resource*, select **Turn on CORS**.)
    - **Select Azure AI Search resource:** Select your Azure AI Search resournce.
    - **Enter the index name:** Index name, such as `resumes`; make note of this. 
    - Check the box for *Add vector search to this search resource* and select your embedding model. Then select **Next**.
    - Select **Browse for a file** and select the pdf documents from the [data](./data) folder. Then, select **Upload files** and **Next**.
    - Select Search type as `vector` and chunk size as `1024(Default)`, then **Next**.
    - Select `API Key` as Azure resource authentication type, then **Next**.
5. Once your data  ingestion is completed, use Chat playground to ask questions about your data such as:
    - "Suggest me .NET developers who can speak Spanish"
    - "Suggest me python developers in London Area"

## Bring your data to Teams

1. Clone this github repo, navigate to [custom-engine-agent](../../src/custom-engine-agent/) folder and open it in Visual Studio Code.
2. In the project folder, select `env` folder and rename:
    - **.env.local.sample** file to **.env.local**
    - **.env.local.user.sample** file to **env.local.user**
3. Open `env.local.user` file and fill the values as shown below and save the file:

```json
SECRET_BOT_PASSWORD= <LEAVE BLANK>
SECRET_AZURE_OPENAI_API_KEY='<YOUR-AZURE-OPENAI-RESOURCE-KEY>'
AZURE_OPENAI_ENDPOINT='<YOUR-AZURE-OPENAI-RESOURCE-ENDPOINT>'
AZURE_OPENAI_DEPLOYMENT_NAME='<YOUR-AZURE-OPENAI-RESOURCE-MODEL-NAME>'
AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME='<YOUR-AZURE-OPENAI-RESOURCE-EMBEDDINGS-MODEL-NAME>'
SECRET_AZURE_SEARCH_KEY='<YOUR-AZURE-AI-SEARCH-KEY>'
AZURE_SEARCH_ENDPOINT='<YOUR-AZURE-AI-SEARCH-ENDPOINT>'
INDEX_NAME='<INDEX-NAME>'
TEAMS_APP_UPDATE_TIME= <LEAVE BLANK>
SECRET_AAD_APP_CLIENT_SECRET= <LEAVE BLANK>
HR_EMAIL= <YOUR-DEMO-TENANT-ACCOUNT-EMAIL>
```

Select Teams Toolkit on Visual Studio Code navigation bar, login with Microsoft 365 Account.

>Make sure that sideloading is enabled for your account. If Sideloading is not enabled yet:
>
>1️⃣ Navigate to https://admin.microsoft.com/, which is the Microsoft 365 Admin Center.
>
>2️⃣ In the left panel of the admin center, select Show all to open up the entire navigation. When the panel opens, select Teams to >open the Microsoft Teams admin center.
>
>3️⃣ In the left of the Microsoft Teams admin center, open the Teams apps accordion. Select Setup Policies, you will see a list of >App setup policies. Then, select the Global (Org-wide default) policy.
>
>4️⃣ Ensure the first switch, Upload custom apps is turned On.

Let's test the demo on Teams. Start debugging your app by selecting **Run and Debug** tab on Visual Studio Code and Debug in Teams (Edge) or Debug in Teams (Chrome). Microsoft Teams will pop up on your browser. Once your app details show up on Teams, select Add and start chatting with your app.

>Tip: Testing this exercise locally
>
>Make sure to test and debug this exercise on Teams locally, as some of the Teams AI library capabilities you've implemented in >your app so far won't smoothly work in the Teams App Test Tool.

Ensure your questions are related to your dataset. Go through pdf documents in the resumes folder to understand more about your data. Challenge your custom engine agent by combining requirements and asking complex questions! Some suggestions would be:

Can you suggest a candidate who is suitable for spanish speaking role that requires at least 2 years of .NET experience?
Who are the other good candidates?
Who would be suitable for a position that requires 5+ python development experience?
Can you suggest any candidates for a senior developer position with 7+ year experience that requires Japanese speaking?