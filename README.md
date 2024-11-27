<!--
To help prepare content for AI Tour, please use this template repository for organizing your sessions and preparing the content for future presentors.
1. Update this readme with the todo's listed below
2. The src folder has been created for all development tasks when creating this session
3. The Lab folder is in-person and async participation with content, please update this folder with instructions for participants to follow along.
4. The Presenter Notes folder is the train the trainer section. Here add any slide decks, demo videos, and other content as needed. This page has a rough layout to provide ideas but can be edited as needed.
5. If you are taking advantage of the static front end site, edit the content in the _config.yml file as needed (specifically the title and description)
 -->
# Developer's Guide to Customizing Microsoft Copilot

![Developer's Guide to Customizing Microsoft Copilot](https://github.com/user-attachments/assets/fcec3359-83e7-4ec7-849d-079cd677fcfa)

This repo is a companion to this session at Microsoft AI Tour, a worldwide tour of events.

## Session Description

This session will introduce the components of the Microsoft Copilot stack and explain the different options of extensibility and integration that you can enable with Microsoft Copilot. The session contains architecture and code deepdives that help showcase the different extensibility pathways.

## Learning Outcomes
You will learn how to integrate your systems, workflows, and applications directly with Microsoft Copilot, maximizing Copilot's potential through different types of copilot extensions. You will learn which type of extensibility and development pathway is the right one for you and see these extensions be built live during the breakout.

## Technology Used

- Declarative agents
- Plugins
- Custom engine agents
- Teams AI library
- Teams Toolkit
- Visual Studio Code
- Microsoft 365 Copilot
- Azure OpenAI
- Azure AI Search

## Additional Resources and Continued Learning

If you are presenting these slides, you can find additional resources, including the slides for the presentation to deliver this session [here](/session-delivery-resources/README.md).

| Resources          | Links                             | Description        |
|:-------------------|:----------------------------------|:-------------------|
| Copilot Developer Camp  | [Link](https://aka.ms/copilotdevcamp) | Learn more about Copilot Extensibility with hands on with Labs and Samples|
| Microsoft 365 Copilot Extensibility Learn Paths | [Link](https://aka.ms/extend-microsoft365-copilot)| Explore Microsoft 365 Copilot Extensibility with Learn paths|


## Content Owners

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->

<table>
<tr>
    <td align="center"><a href="http://learnanalytics.microsoft.com">
        <img src="https://github.com/aycabas.png" width="100px;" alt="Ayca Bas"/><br />
        <sub><b>Ayca Bas
</b></sub></a><br />
            <a href="https://github.com/aycabas" title="talk">📢</a> 
    </td>
    <td align="center"><a href="http://learnanalytics.microsoft.com">
        <img src="https://github.com/garrytrinder.png" width="100px;" alt="Garry Trinder"/><br />
        <sub><b>Garry Trinder
</b></sub></a><br />
            <a href="https://github.com/garrytrinder" title="talk">📢</a> 
    </td>
    <td align="center"><a href="http://learnanalytics.microsoft.com">
        <img src="https://github.com/rabwill.png" width="100px;" alt="Rabia Williams"/><br />
        <sub><b>Rabia Williams
</b></sub></a><br />
            <a href="https://github.com/garrytrinder" title="talk">📢</a> 
    </td>    
    <td align="center"><a href="http://learnanalytics.microsoft.com">
        <img src="https://github.com/barnam-bora.png" width="100px;" alt="Barnam Bora"/><br />
        <sub><b>Barnam Bora
</b></sub></a><br />
            <a href="https://github.com/barnam-bora" title="talk">📢</a> 
    </td>
</tr></table>

<!-- ALL-CONTRIBUTORS-LIST:END -->

## Responsible AI 

Microsoft is committed to helping our customers use our AI products responsibly, sharing our learnings, and building trust-based partnerships through tools like Transparency Notes and Impact Assessments. Many of these resources can be found at [https://aka.ms/RAI](https://aka.ms/RAI).
Microsoft’s approach to responsible AI is grounded in our AI principles of fairness, reliability and safety, privacy and security, inclusiveness, transparency, and accountability.

Large-scale natural language, image, and speech models - like the ones used in this sample - can potentially behave in ways that are unfair, unreliable, or offensive, in turn causing harms. Please consult the [Azure OpenAI service Transparency note](https://learn.microsoft.com/legal/cognitive-services/openai/transparency-note?tabs=text) to be informed about risks and limitations.

The recommended approach to mitigating these risks is to include a safety system in your architecture that can detect and prevent harmful behavior. [Azure AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/overview) provides an independent layer of protection, able to detect harmful user-generated and AI-generated content in applications and services. Azure AI Content Safety includes text and image APIs that allow you to detect material that is harmful. We also have an interactive Content Safety Studio that allows you to view, explore and try out sample code for detecting harmful content across different modalities. The following [quickstart documentation](https://learn.microsoft.com/azure/ai-services/content-safety/quickstart-text?tabs=visual-studio%2Clinux&pivots=programming-language-rest) guides you through making requests to the service.

Another aspect to take into account is the overall application performance. With multi-modal and multi-models applications, we consider performance to mean that the system performs as you and your users expect, including not generating harmful outputs. It's important to assess the performance of your overall application using [generation quality and risk and safety metrics](https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-metrics-built-in).

You can evaluate your AI application in your development environment using the [prompt flow SDK](https://microsoft.github.io/promptflow/index.html). Given either a test dataset or a target, your generative AI application generations are quantitatively measured with built-in evaluators or custom evaluators of your choice. To get started with the prompt flow sdk to evaluate your system, you can follow the [quickstart guide](https://learn.microsoft.com/azure/ai-studio/how-to/develop/flow-evaluate-sdk). Once you execute an evaluation run, you can [visualize the results in Azure AI Studio](https://learn.microsoft.com/azure/ai-studio/how-to/evaluate-flow-results).
