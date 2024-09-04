# Instructions for building declarative copilots with Teams Toolkit for Visual Studio Code

This demo showcases how to build a declarative copilot with Teams Toolkit for Visual Studio Code.

The declarative copilot contains instructions, knowledge and conversation starters and can be used to provide information about products, returns, warranties, repairs and help troubleshoot product issues. The information is sourced from a SharePoint Online site.

## Prerequisites

- [Node.js 18](https://nodejs.org/)
- [Teams Toolkit Visual Studio Code Extension](https://aka.ms/teams-toolkit) pre-release (v5.9.2024081502) and higher, or [Teams Toolkit CLI](https://aka.ms/teamsfx-toolkit-cli) beta (3.0.3-beta.2024081502.0) and higher
- [Copilot for Microsoft 365 license](https://learn.microsoft.com/microsoft-365-copilot/extensibility/prerequisites#prerequisites)
- SharePoint Online site with the name `Product support` that has all the files from [assets](../../src/declarative-copilot/assets/) folder uploaded to the Documents library

## Build a basic declarative copilot

1. Open Visual Studio Code and navigate to the Teams Toolkit icon on the left in the VS Code toolbar.
1. Select **Create a New App**.
1. Select **Copilot Extension**.
1. Select **Declarative Copilot**.
1. Select **No plugin**.
1. Select default folder as the location to create the project.
1. Enter `dc-product-support` as the application name.

After providing all the details mentioned, your project will be scaffolded successfully in seconds and a new window will open with the project structure.

1. Open Teams Toolkit sidebar.
1. Select **Provision** in the lifeycle section.

After the provisioning is completed, you can test your declarative copilot.

1. Press <kbd>F5</kbd> to launch a new browser window.
1. Wait for the browser to navigate to Copilot for Microsoft 365.
1. In Copilot for Microsoft 365 expand the side menu.
1. Select **dc-product-supportlocal**.
1. In the message box, type _What can you do?_ and press <kbd>Enter</kbd>.

Note how the declarative copilot responds with a different message from the default response from Copilot for Microsoft 365.

## Update declarative copilot

In Visual Studio Code:

1. Open **appPackage/declarativeCopilot.json**.
1. Update **id** property with `dc-product-support`.
1. Update **name** property with `Product support`.
1. Update **description** property with:

    ```text
    Contoso Electronics product support copilot is an assistant that provides answers to questions about products that have been designed, built and sold by Contoso Electronics. It can help with a variety of topics, providing information on products, returns, warranties, repairs and help troubleshoot product issues.
    ```

1. Update **instructions** property with:

    ```text
    From now on, you are known as Contoso Electronics Product Support declarative copilot. You are a friendly and approachable assistant, always ready to assist users with their needs. You embody the reliability and consistency of Contoso Electronics, always providing steady and dependable support. Despite being an assistant, you strive to make every interaction feel personal and human-like. You are patient and understanding, making you great at helping users troubleshoot issues. You don't rush users and are always willing to take the time to ensure they fully understand the solution. You are also knowledgeable about all Contoso Electronics products. You can provide advice and guidance on how to use the products, as well as information on repairs, returns, and warranties. Despite your vast knowledge, you communicate in a way that is easy to understand, avoiding technical jargon whenever possible.
    ```

1. Add **conversation_starters** array property with the following code snippet:

    ```json
    "conversation_starters": [
        {
            "title": "Product information",
            "text": "Tell me about the Eagle Air"
        },
        {
            "title": "Returns policy",
            "text": "What is the returns policy?"
        },
        {
            "title": "Product information",
            "text": "Can you provide information on a specific product?"
        },
        {
            "title": "Product troubleshooting",
            "text": "I'm having trouble with a product. Can you help me troubleshoot the issue?"
        },
        {
            "title": "Repair information",
            "text": "Can you provide information on how to get a product repaired?"
        },
        {
            "title": "Contact support",
            "text": "How can I contact support for help?"
        }
    ]
    ```

1. Add **capabilities** array property with the following code snippet:

    ```json
    "capabilities": [
        {
            "name": "OneDriveAndSharePoint",
            "items_by_url": [
                {
                    "url": "https://${{TENANT_NAME}}.sharepoint.com/sites/productsupport"
                }
            ]
        }
    ]
    ```

1. Save the file.
1. Navigate to the Teams Toolkit icon on the left in the VS Code toolbar.
1. Select **Provision** in the lifeycle section.
1. Press <kbd>F5</kbd> to launch a new browser window.
1. Wait for the browser to navigate to Copilot for Microsoft 365.
1. In Copilot for Microsoft 365 expand the side menu.
1. Select **Product support**.
1. Select the conversation starter `Tell me about the Eagle Air`.
1. Send the message.

Note that in the response a document stored in SharePoint Online is cited as the source for information.

> [!NOTE]
> [Source code](../../src/declarative-copilot/) for this demo is available.
