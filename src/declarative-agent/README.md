# Overview of the basic declarative copilot template

## Build a basic declarative copilot

With the declarative copilot, you can build a custom version of Copilot that can be used for specific scenarios, such as for specialized knowledge, implementing specific processes, or simply to save time by reusing a set of AI prompts. 

## Get started

> **Prerequisites**
>
> To run this app template in your local dev machine, you will need:
>
> - [Node.js](https://nodejs.org/), supported versions: 16, 18
> - A [Microsoft 365 account for development](https://docs.microsoft.com/microsoftteams/platform/toolkit/accounts).
> - [Teams Toolkit Visual Studio Code Extension](https://aka.ms/teams-toolkit) (v5.10.0) and higher, or [Teams Toolkit CLI](https://aka.ms/teamsfx-toolkit-cli) beta (3.0.3-beta.2024081502.0) and higher
> - [Microsoft 365 Copilot license](https://learn.microsoft.com/microsoft-365-copilot/extensibility/prerequisites#prerequisites)

### Prepare SharePoint Online

In a web browser:

1. Create a new team site in SharePoint Online with the name `Product marketing`
1. Upload all the documents from the `assets` folder to the Documents library in the site

### Provision your declarative copilot

In Visual Studio Code:

1. First, select the Teams Toolkit icon on the left in the VS Code toolbar.
1. In the file `env/.env.dev`, replace `tenantname` with the name of your Microsoft 365 tenant.
1. In the Account section, sign in with your [Microsoft 365 account](https://docs.microsoft.com/microsoftteams/platform/toolkit/accounts) if you haven't already.
1. Select `Provision` in "Lifecycle" section to provision your declarative copilot.

### Test your declarative copilot

1. Select `Preview in Copilot (Edge)` or `Preview in Copilot (Chrome)` from the launch configuration dropdown.
1. Once the Copilot app is loaded in the browser, click on the "…" menu and select "Copilot chats". You will see your declarative copilot on the right rail. Clicking on it will change the experience to showcase the logo and name of your declarative copilot.
1. Ask a question to your declarative copilot and it should respond based on the instructions provided.

## What's included in the template

| Folder       | Contents                                                                                 |
| ------------ | ---------------------------------------------------------------------------------------- |
| `.vscode`    | VSCode files for debugging                                                               |
| `appPackage` | Templates for the Teams application manifest, the GPT manifest and the API specification |
| `env`        | Environment files                                                                        |

The following files can be customized and demonstrate an example implementation to get you started.

| File                                 | Contents                                                                       |
| ------------------------------------ | ------------------------------------------------------------------------------ |
| `appPackage/declarativeCopilot.json` | Define the behaviour and configurations of the declarative copilot.            |
| `appPackage/manifest.json`           | Teams application manifest that defines metadata for your declarative copilot. |
| `appPackage/instruction.txt`         | Instructions for the declarative agent.                                        |

The following are Teams Toolkit specific project files. You can [visit a complete guide on Github](https://github.com/OfficeDev/TeamsFx/wiki/Teams-Toolkit-Visual-Studio-Code-v5-Guide#overview) to understand how Teams Toolkit works.

| File           | Contents                                                                                                                                  |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `teamsapp.yml` | This is the main Teams Toolkit project file. The project file defines two primary things: Properties and configuration Stage definitions. |

## Addition information and references

- [Extend Microsoft Microsoft 365 Copilot](https://aka.ms/teamsfx-copilot-plugin)