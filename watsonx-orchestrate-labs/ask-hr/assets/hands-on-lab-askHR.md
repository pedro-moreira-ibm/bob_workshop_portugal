
# 🧑‍💼 AskHR: Automate HR tasks with Agentic AI

## Lab Structure

- [Description of the use case](#description-of-the-use-case)
- [Architecture](#architecture)
- [Instructions](#instructions)
  - [Open watsonx Orchestrate](#open-watsonx-orchestrate)
  - [Create the HR Agent](#create-the-hr-agent)
  - [Test HR Agent in Preview](#test-hr-agent-in-preview)
  - [Deploy and make your Agent available](#deploy-and-make-your-agent-available)
- [Conclusion](#conclusion)



## Description of the use case

This use case targets developing and deploying an AskHR agent leveraging IBM watsonx Orchestrate, as depicted in the provided architecture diagram. This agent will empower employees to interact with HR systems and access information efficiently through conversational AI. 

In this lab we will build an HR agent in watsonx Orchestrate, leveraging tools and external knowledge to connect to a simulated Human Capital Management System. This agent retrieves relevant information from documents to answer user queries and  allows users to view and manage their profiles.

## Architecture

<img width="1668" height="1062" alt="image" src="https://github.com/user-attachments/assets/1b91c902-241c-4afe-a99f-c531b7578765" />

## Instructions

### Open watsonx Orchestrate

- Log in to [IBM Cloud](cloud.ibm.com).
  
  <img width="3694" height="1974" alt="image" src="https://github.com/user-attachments/assets/2c61dc7d-f71e-41c2-ba8f-6124c9ee94a9" />

- Navigate to top left hamburger menu, then to Resource List. Open the AI/Machine Learning section. You should see a **watsonx Orchestrate** service, click to open.

  <img width="1000" alt="image" src="../../../environment-setup/assets/cloud-resource-list.png">

- Click "Launch watsonx Orchestrate" button.

   <img width="1000" alt="image" src="../../../environment-setup/assets/cloud-wxo.png">

- Welcome to watsonx Orchestrate. Open the hamburger menu, click on the down arrow next to **Build**.  Then click on **Agent Builder**:

   <img width="1000" alt="image" src="hands-on-lab-assets/step_1_v2.png">

### Create the HR Agent
1. Click on **Create agent +**:

   <img width="1000" alt="image" src="hands-on-lab-assets/step_2_v2.png">

1. Select **Create from scratch**, give your agent a name, e.g. `HR Agent`, and fill in the **Description** as shown below: 

   ```
   You are an agent who handles employee HR queries.  You provide short and crisp responses, keeping the output to 200 words or less.  You can help users check their profile data, retrieve latest time off balance, update title or address, and request time off. You can also answer general questions about company benefits.
   ```  
   Click on **Create**:

   <img width="1000" alt="image" src="hands-on-lab-assets/step_3_v2.png">
<!--   
1. Click on the down arrow against **Model**. Select Model "llama-3-405b-instruct"

   <img width="1000" alt="image" src="hands-on-lab-assets/step_4_v2.png">
-->   

The natural language description of an agent is important as it is leveraged by the agentic solution to route user messages to the right agent skilled in addressing the request. For more details, please review the [Understanding the description attribute for AI Agent](https://www.ibm.com/docs/en/watsonx/watson-orchestrate/base?topic=agents-recommendations-agent-descriptions) documentation.

**watsonx Orchestrate** supports creating an agent from scratch or from a template which involves browsing a catalog of existing agents and using attributes of another agent as a template for the new agent. For this lab, you will be creating agents from scratch.

> **Note:** To discover all the pre-built agents and tools in **watsonx Orchestrate**, please consult the [catalog of pre-built agents and tools](https://www.ibm.com/docs/en/watsonx/watson-orchestrate/base?topic=discovering-catalog) documentation.

Next, you will go through the process of configuring your agent. The Product Agent page is split in two halves:
- The right half is a preview chat interface that allows you to test the behavior of your agent.
- The left half of the page consits of five key sections that you can use to configure your agent.

<div align="center">
  <img width="3010" height="1728" alt="image" src="https://github.com/user-attachments/assets/51bffc70-ca49-4243-846e-ec7334fc8d86" />
</div>

1. Select **Default** in **Agent style** section.

   <img width="1000" alt="image" src="hands-on-lab-assets/step_5_v3.png">

      > **Note:** For more details, Please consult the [Choosing a reasoning style for your agent](https://www.ibm.com/docs/en/watsonx/watson-orchestrate/base?topic=agents-choosing-style-agent) documentation to understand the difference and how it affects the agent's behavior.
  
1. Scroll down the screen to the **Knowledge** section.
   Click on **Choose knowledge**.
   
   <img width="1000" alt="image" src="hands-on-lab-assets/step_6_v3.png">

      - **Knowledge**: The Knowledge section is where you can add knowledge to the agent. Adding knowledge to agents plays a crucial role in enhancing their conversational capabilities by providing them with the necessary information to generate accurate and contextually relevant responses for specific use cases. You can directly upload files to the agent or connect to a Milvus or Elasticsearch instance as a content repository. Through this Knowledge interface, you can enable your AI agents to implement the Retrieval Augmented Generation (RAG) pattern which is a very popular AI pattern for grounding responses to a trusted source of data such as enterprise knowledge base.

      > **Note:** For more details, please consult the [Adding knowledge to agents](https://www.ibm.com/docs/en/watsonx/watson-orchestrate/current?topic=agents-adding-knowledge) documentation.
  
1. Select **Upload files**.
   Click on **Next**.
   
   <img width="1000" alt="image" src="hands-on-lab-assets/step_7_v3.png">
     
1. Download the [Employee Benefits.pdf](Employee-Benefits.pdf) onto your system, then upload the file here. You can download the pdf by clicking on [Employee Benefits.pdf](Employee-Benefits.pdf) and then click on download icon in opened page as shown in image below.
      <img width="1000" alt="image" src="hands-on-lab-assets/step_7.1_v3.png">

      
   Once you upload the file, Click on **Next**.

   <img width="1000" alt="image" src="hands-on-lab-assets/step_8_v3.png">

1. Add the **Name** "Employee Benefits" to the file. Also, copy the following description into the **Description** section and then click on **Save**:

   ```
   This knowledge base addresses the company's employee benefits, including parental leaves, pet policy, flexible work arrangements, and student loan repayment.
   ```
   
   <div align="center">
     <img width="1024" height="474" alt="image" src="https://github.com/user-attachments/assets/ad58437b-d055-416a-83a2-4c84517550f7" />
   </div>

1. Scroll down to the **Toolset** section. Click on **Add tool +**:

   <img width="1000" alt="image" src="hands-on-lab-assets/step_9_v3.png">

    - **Toolset**: While Knowledge is how you empower agents with a trusted knowledge base, then Toolset is how you enable agents to act by providing them with Tools and Agents. Agents can accomplish tasks by using Tools or can delegate tasks to other Agents which are deeply skilled in such tasks.

    - For Tools, you can use the [**watsonx Orchestrate Agentic Development Kit (ADK)**](https://developer.watson-orchestrate.ibm.com/) to develop and upload Python and OpenAPI tools to a specific **watsonx Orchestrate** instance which you can then add to the agents.

    - Additionally, **watsonx Orchestrate** also supports the addition of [Model Context Protocol (MCP)](https://developer.watson-orchestrate.ibm.com/mcp_server/wxOmcp_overview) tools. MCP is a standard for connecting AI Agents to systems where data lives including content repositories, business tools and development environments. MCP is becoming increasingly popular as the standard for enabling agents with tools.

      > **Note:** For more details, please consult the [Adding tools to an agent](https://www.ibm.com/docs/en/watsonx/watson-orchestrate/base?topic=building-tools) and [Adding agents for orchestration](https://www.ibm.com/docs/en/watsonx/watson-orchestrate/current?topic=agents-adding-orchestration) sections of the documentation.

1. Select **Add from OpenAPI file**:
   
   <div align="center">
     <img width="1467" height="999" alt="image" src="https://github.com/user-attachments/assets/3044aae4-0d1c-4de5-8b1c-08c9bb68b487" />
   </div>

1. Select **Import from file**:

   <img width="1000" alt="image" src="hands-on-lab-assets/step_11_v3.png">

1. Drag and drop or click to upload the [hr.yaml](hr.yaml) file, then click on **Next**:

   <img width="1000" alt="image" src="hands-on-lab-assets/step_12_v3.png">    

1. Select all the operations and click on **Done**:

   <img width="1000" alt="image" src="hands-on-lab-assets/step_13_v3.png">


1. Scroll down to the **Behavior** section. Insert the instructions below into the **Instructions** field:

   ```
   Use your knowledge base to answer general questions about employee benefits. 

   Use the tools to get or update user specific information.

   When user asks to show profile data or check time off balance or update title/address or request time off for the very first time,  first ask the user for their name,  then invoke the tool and then use the same name in the whole session without asking for the name again.

   When the user requests time off, convert the dates to YYYY-MM-DD format, e.g. 5/22/2025 should be converted to 2025-05-22 before passing the date to the post_request_time_off tool.
   ```

      - **Behavior**: The Behavior section of the agent configuration is where you provide instructions to the agent to define how it responds to user requests and situations. You can configure rules that dictate when and how the agent should take action. These rules help the agent behave in a predictable and consistent manner, delivering a seamless user experience. **Note:** For more details, please consult the [Adding instructions to agents](https://www.ibm.com/docs/en/watsonx/watson-orchestrate/current?topic=agents-adding-instructions) documentation.



### Test HR Agent in Preview
Test your agent in the preview chat on the right side by asking the following questions and validating the responses.  They should look similar to what is shown in the screenshots below:

```
Does my company have any pet policy? 
```
<img width="1000" alt="image" src="hands-on-lab-assets/hr_step13.png">

Ask the agent for your profile data. 

```
Show me my profile data.
```

When asked for your name, check the photo below to identify the name assigned to your team (e.g. Team 1 should use Daniel Anderson). This fictional but dynamic database was prepopulated before the workshop. 


<img width="2906" height="1445" alt="image" src="https://github.com/user-attachments/assets/760e31ae-4b4c-4d62-a50e-f6f141b10bee" />

For this tutorial, we used “Victoria Baker” as the employee example.

<img width="855" height="460" alt="image" src="https://github.com/user-attachments/assets/6e97534a-ecec-428e-a6c6-ccc350c701c5" />

After that, ask the agent to update your job title.

```
I'd like to update my title to Sr AI Engineer.
```
<img width="830" height="318" alt="image" src="https://github.com/user-attachments/assets/9a14815b-64ad-45dd-abd6-140fbb2cbd17" />

Now, update your address.
```
Update my address to 222 Main St, San Francisco, CA 94105
```

<img width="2475" height="1390" alt="image" src="https://github.com/user-attachments/assets/ed14f872-e12c-474e-9571-0a90c5b1ee50" />

Check again your profile data to see all the changes you made.
```
Show my profile data.
```

<div align="center">
  <img width="1524" height="724" alt="image" src="https://github.com/user-attachments/assets/8705a4dc-a798-490d-a402-191b9964aaa6" />
</div>



Now, request time off and after define a start and end date.

```
Request time off
```
```
Start date is 2025-12-01 and end date is 2025-12-06
```

When the agent answers, click on "Show Reasoning" and confirm that the agent is chosing the right tool to solve the task.

<div align="center">
<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/fe958154-251d-46b3-9857-088ccfc82fa7" />
</div>

   • **Reasoning**: AI agent reasoning is the process by which an artificial intelligence system makes decisions to achieve a specific goal. An AI agent typically follows a cycle: it understands the environment, processes that information to understand the current situation, decides what action to take, acts on that decision and then updates its knowledge based on what happened.

   AI agents don’t always act alone. They can also interact with other agents and tools to solve more complex tasks. For instance, an AI agent might call on a weather service (a tool) to check the forecast, or coordinate with another AI agent that handles scheduling.

   In these examples, reasoning includes deciding which tools or agents to use, when, and how to communicate with them.  


Now, let's make a completely different question and again analyze the reasoning of the agent.

```
Does my company organize team building activities
```
<div align="center">
<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/9a3ab2f0-0dd6-40d7-8003-475d90668924" />
</div>

The agent recognized that to solve this task, it would not require one of the tools we previously tested. Instead, it found the answer on the "Employee-Benefits.pdf".

Feel free to scroll up in the chat and/or repeat any prompts we already tested, and explore the reasoning behind the agent's answers.

### Deploy and make your Agent available


After completing your tests and once you’re ready to make the agent available to employees, click on "Deploy".

<div align="center">
  <img width="1905" height="956" alt="image" src="https://github.com/user-attachments/assets/4bb19e44-79ca-4b19-a6f6-ebaaeab9e207" />
</div>


# Congratulations 🎉 You’ve reached the end of the workshop! 


This lab provided a hands-on, structured approach to building and testing AI agents in the human resources domain, using a realistic enterprise dataset.

Participants from this workshop walk away with:
- Practical experience using IBM solutions: **watsonx Orchestrate**
- Practical knowledge of **RAG pipelines**
- Experience **creating and deploying AI agents** to automate human resources workflows
