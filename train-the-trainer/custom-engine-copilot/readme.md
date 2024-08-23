# Instructions for Custom engine copilots with​ Teams AI Library and VSCode

This demo showcases how to build a custom engine copilot with Retrieval-Augmented Generation for sophisticated question answering using Teams AI library and Teams Toolkit.

https://github.com/user-attachments/assets/99906ce5-fe2d-485f-aac8-af25600dd607


## Pre-requisites

- [Node.js](https://nodejs.org/), supported versions: 16, 18
- [Teams Toolkit Visual Studio Code Extension](https://aka.ms/teams-toolkit) version 5.0.0 and higher or [Teams Toolkit CLI](https://aka.ms/teamsfx-toolkit-cli)
- Prepare your own [Azure OpenAI](https://aka.ms/oai/access), [Azure AI Search](https://azure.microsoft.com/en-us/products/ai-services/ai-search) and [storage account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create) resources.

## Get started with Azure OpenAI

1. Start your demo in Azure OpenAI resource and navigate to Azure OpenAI Studio.
2. Create a deployment model, From the **Deployments** tab, select **Create a new deployment**. Fill out the following details and select **Create**:
    - **Deployment name:** Recommended to use the same name with the selected deployment model, such as `gpt-35-turbo`.
    - **Select a model:** Select `gpt-35-turbo` or higher model.
    - **Model version:** Auto update to default.
    - **Deployment type:** Provisioned-Managed.
    - **Content Filter:** Default.
3. Once your model is successfully created, you can navigate to **Chat**. In the **Setup** section, select **Add your data** tab and then **Add a data source**.
4. Select **Upload files (preview)**, then fill the details as the following and select **Next**:
    - **Subscription:** Select the subscription you created your Azure resources.
    - **Select Azure Blob storage resource:** Select your storage resource. (You'll see a message *Azure OpenAI needs your permission to access this resource*, select **Turn on CORS**.)
    - **Select Azure AI Search resource:** Select your Azure AI Search resournce.
    - **Enter the index name:** Index name, such as `contoso-index`; make note of this. Then select **Next**.
    - Select **Browse for a file** and select the pdf documents from the [data](./data) folder. Then, select **Upload files** and **Next**.
    - Select Search type as `keyword` and chunk size as `1024(Default)`, then **Next**.
    - Select `API Key` as Azure resource authentication type, then **Next**.
5. Once your data  ingestion is completed, use Chat playground to ask questions about your data such as:
    - "Tell me about my policy"
    - "What about perks"

## Bring your data to Teams

1. Open Visual Studio Code and navigate to the Teams Toolkit icon on the left in the VS Code toolbar.
2. Select **Create a New App** > **Custom Engine Copilot** > **Basic AI Chatbot**.
3. Select **JavaScript** as a programming language choice and **Azure OpenAI** as Large Language model of your choice.
    - Paste the Azure OpenAI key and press enter.
    - Paste the Azure OpenAI endpoint and press enter.
    - Type Azure OpenAI deployment model name and press enter.
4. Select a folder for your project root.
5. Provide a name for your project and press enter.
6. After providing all the details mentioned, your project will be scaffolded successfully in seconds.
7. Navigate to `src/app/app.js` and walk through the code quickly.
8. Open `prompts/chat/skprompt.txt` and paste the following prompt:
    ```
    The following conversation is with an AI assistant who is an expert in answering questions over the given context.
    Response should be in short journalistic style with no more than 80 words.
    ```
9. Open `prompts/chat/config.json` and add the following snippet inside the **completion** brackets:
    ```
    "model":"gpt-35-turbo",
    "data_sources":[
      {
        "type": "azure_search",
        "parameters": {
          "endpoint": "YOUR-AZURE-AI-SEARCH-ENDPOINT",
          "index_name": "YOUR-INDEX-NAME",
          "authentication": {
            "type": "api_key",
            "key": "YOUR-AZURE-AI-SEARCH-KEY"
          }
        }
      }
    ] 
    ```

10. Start debugging your app by selecting **Run and Debug** tab on Visual Studio Code and **Debug in Teams (Edge)** or **Debug in Teams (Chrome)**. Microsoft Teams will pop up on your browser. Once your app details show up on Teams, select **Add** and start chatting with your app. To test your app, ask similar questions about your data such as:
    - "Tell me about my policy"
    - "What about perks"

>Source code for this demo is available in [src/custom-engine/](../../src/custom-engine/) folder.
