# Lab 3: Building AI Agents with IBM Bob and watsonx Orchestrate

## Overview

In this lab, you'll use IBM Bob to build an agent and tool and import them into watsonx Orchestrate, using as reference the official documentation via the watsonx Orchestrate MCP.

You will build a simple agent that can:
- Calculate how many time until christmas 2026 we have left
- Answer like santa claus style


## Learning Objectives

By the end of this lab, you will:
- ✅ Use IBM Bob as an AI development partner
- ✅ Connect and leverage an MCP server in BOB
- ✅ Build agents and tools with BOB
- ✅ Import agents and tools to watsonx orchestrate
- ✅ Import MCP tools into watsonx Orchestrate


## Prerequisites

Before starting, ensure you have:
- [ ] IBM Bob installed and running
- [ ] Python 3.8+ installed
- [ ] A Python virtual environment available
- [ ] watsonx Orchestrate ADK installed and configured
- [ ] Access to a watsonx Orchestrate environment
- [ ] Basic understanding of MCP tools and agents



## Lab Structure

```text
Lab 3 Timeline (45 minutes)
├── Step 1: Set Up the Python Project (5 min)
├── Step 2: Build the MCP Server (10 min)
├── Step 3: Validate with MCP Client (10 min)
├── Step 4: Import MCP Tools into watsonx Orchestrate (10 min)
├── Step 5: Create the watsonx Orchestrate Agent (5 min)
└── Step 6: Verify the Agent (5 min)
```

---

## Step 1: Set Up the Python Project

In this step, you will prepare the workspace for your project and ask IBM Bob to set up the Python environment.

Bob will:
- Create and configure the Python virtual environment
- Prepare the project structure
- Create the initial README file
- Get the environment ready for MCP development

### 1.1: Create and Open the Project Folder

Create a new folder on your machine called:

```text
wxo-bob
```

Open this folder in IBM Bob.

<img width="3838" height="2220" alt="image" src="https://github.com/user-attachments/assets/85d39175-6237-4b3c-8c78-d39f7d13de37" />

### 1.2: Ask Bob to Create and Activate a Python Virtual Environment

**Prompt for Bob:**

```bash
Create a Python virtual environment for this project and activate it.
```
<img width="3813" height="2217" alt="image" src="https://github.com/user-attachments/assets/73b60df9-89bb-4b84-b726-c348435c6293" />


Bob will:
- Create the virtual environment
- Activate it
- Confirm the environment is ready

Click **Run** or **Approve** when prompted.

### 1.3: Verify the Environment

Bob should confirm that:
- The virtual environment is active
- Python is available
- The project workspace is ready


**✅ Checkpoint**: Project folder is opened in Bob and the Python virtual environment is active.

---

## Step 2: Set up the watsonx Orchestrate documentation MCP

In this step, you will connect the watsonx Orchestrate documentation MCP to BOB, which will be essential to make sure the tools and agents are created according to the expected format and accepted by orchestrate.

### 2.1: Go to BOB Settings and open the MCP tab

<img width="3818" height="2212" alt="image" src="https://github.com/user-attachments/assets/3437d789-9c72-4061-bd57-ef53c1508c38" />


### 2.2: Search for "orchestrate" in the marketplace and open the watsonx Orchestrate ADK Docs MCP

<img width="3837" height="2220" alt="image" src="https://github.com/user-attachments/assets/6e76b258-1089-4917-93a3-2e07de6efa67" />


### 2.3: Install the Server

Click on "Install"

<img width="3818" height="1375" alt="image" src="https://github.com/user-attachments/assets/c8f04fe8-0291-4b40-966d-a5298c93239b" />

When asked for the Instalattion scope, feel free to select what suits you best. If you use Orchestrate on a regular basis, then select Global, as this is a very useful MCP. However, if you are only trying this for a one-time, it's recommendable to select project scope only, so we don't overload BOB context and affect its future performance.

<img width="3816" height="2213" alt="image" src="https://github.com/user-attachments/assets/0d9cfd72-e80d-4a8c-a293-bd52b1cc87bd" />


### 2.4: Confirm the MCP was sucessfully installed

Navigate to the MCP tab again and confirm you can now see a green dot next to the mcp, which means it was sucessfully installed and is now active.

<img width="3424" height="1971" alt="image" src="https://github.com/user-attachments/assets/a9a4fecf-2006-4965-baca-2d32f626b12c" />


**✅ Checkpoint**: Orchestrate documentation MCP server configured and activated successfully.

---

## Step 3: Use BOB to create a tool and an agent

In this step, you will ask Bob to create a python tool and an agent that uses it in watsonx orchestrate

### 3.1: Ask Bob to create the tool

**Prompt for Bob:**

```bash
Please create a python tool that calculates how much days we have left until christmas of 2026, following the watsonx Orchestrate ADK documentation MCP server as reference.
```
<img width="3824" height="2220" alt="image" src="https://github.com/user-attachments/assets/86759582-df42-4027-bc52-63e7960a5d1e" />


Bob will access the MCP to understand the expected format that orchestrate expects, and then build the tool according.

<img width="3833" height="2230" alt="image" src="https://github.com/user-attachments/assets/555054f4-515a-4b33-aa40-07c6f0d2eff6" />


Whenever necessary, **approve** the commands that BOB wants to run.

### 3.2: Ask BOB to create an agent, that will use the tool

**Prompt for Bob:**

```bash
Please create an agent that uses the previously created tool whenever the user asks how much time is left until Christmas, answering in a Santa Claus style.

I want groq/openai/gpt-oss-120b to be the agent LLM.

Follow the watsonx Orchestrate ADK documentation MCP server as reference.
```

<img width="3821" height="2217" alt="image" src="https://github.com/user-attachments/assets/b621c6c0-5757-4d67-8018-0ad1910b9b50" />

Once again, BOB will use the official documentation to produce what was requested. Once its done, explore the agent file to verify that the agent is instructed to use the tool, as well as other behavior instructions that BOB considered relevant for this case and added.

<img width="3839" height="2222" alt="image" src="https://github.com/user-attachments/assets/db3d437c-7cca-49cd-b6d3-c19422f7e708" />



**✅ Checkpoint**: Agent and tool created

---

## Step 4: Add the agent and Tool to watsonx Orchestrate

In this step, you will connect your local project to a watsonx Orchestrate environment and import the agent and tool.

Before Bob can import the tools, you first need:
- An IBM Cloud API key
- The URL of your watsonx Orchestrate instance

Bob will then:
- Configure a watsonx Orchestrate environment
- Authenticate to the environment
- Import the MCP tools
- Fix any dependency or configuration issues
- Verify that the tools are available in watsonx Orchestrate

### 4.1: Generate an IBM Cloud API Key

Go to your IBM Cloud account and generate an API key.

<img width="3682" height="1954" alt="image" src="https://github.com/user-attachments/assets/623b0b38-6639-4855-9f55-ca5cadcd1257" />

<img width="3636" height="1921" alt="image" src="https://github.com/user-attachments/assets/6c8c9e34-2913-4422-bc05-c197ea48f11b" />

Store the API key somewhere safe because you will use it in the next step.

### 4.2: Retrieve Your watsonx Orchestrate Instance URL

Open your watsonx Orchestrate environment in the browser.

<img width="3654" height="1841" alt="image" src="https://github.com/user-attachments/assets/2d037624-70e7-40ad-a705-de51b8b054c5" />

<img width="3671" height="1850" alt="image" src="https://github.com/user-attachments/assets/2955be47-cc4b-4c45-8561-68988a7d58c3" />

Copy the URL of your instance.

<img width="3711" height="1838" alt="image" src="https://github.com/user-attachments/assets/7c67b5ba-f3e5-48a5-83b9-2a459a37fa59" />

Example:

```text
https://api.us-south.watson-orchestrate.cloud.ibm.com/instances/xxxxxxxx
```

### 4.3: Create and activate a watsonx Orchestrate in your terminal

Before we ask BOB to help us import the agent and tool to orchestrate, we should configure an enviornment in watsonx Orchestrate using the credentials collected previously. 

Return to BOB and click on "new terminal"

<img width="3839" height="1495" alt="image" src="https://github.com/user-attachments/assets/478f2b0d-3d05-49fe-a184-c3450a20729e" />


**Command for the terminal:**

```bash
orchestrate env add -n wxo-bob -u <INSERT_YOUR_URL> --type ibm_iam --activate
```

When prompted, paste the API key. It's excpected it won't show up, even if you copied. This happens for security reasons. Just copy once and press Enter.

You should be able to see the message that the environment has sucessfully created and is now active.

<img width="3368" height="1975" alt="image" src="https://github.com/user-attachments/assets/820f856f-5c5f-4c93-acef-af0e2ee65c67" />

### 4.4: Ask Bob to Import the agent and Tool to watsonx Orchestrate

Now that the environment is configured, ask Bob to import the MCP tools.

**Prompt for Bob:**

```bash
Import the python tool and agent to my wxo-bob watsonx Orchestrate environment. Follow the watsonx Orchestrate ADK documentation MCP server to find the appropriate import commands.
```
<img width="3839" height="2220" alt="image" src="https://github.com/user-attachments/assets/8e45f0fa-abc4-44ab-9d67-4f6befed053d" />

During the import, Bob may encounter issues such as:
- Tool names containing spaces
- Missing dependencies
- Requirements file needing updates
- Incorrect configuration values

Allow Bob to fix these issues and retry the import. It will notify you once everything was imported sucessfully.


<img width="3839" height="2141" alt="image" src="https://github.com/user-attachments/assets/17d854d0-6eec-4e5c-b93e-17eb26d4de6e" />


**✅ Checkpoint**: agent and tool are imported and ready to use in watsonx Orchestrate.

---

## Step 5: Access your watsonx Orchestrate UI and try the agent there


### 5.1: Launch watsonx Orchestrate


<img width="3710" height="1824" alt="image" src="https://github.com/user-attachments/assets/9151dd76-0570-4388-96ff-616e5bceab0c" />


### 5.2: Go to the Build Agent tab

Open the Build Tab

<img width="3704" height="1833" alt="image" src="https://github.com/user-attachments/assets/05811452-1acd-4d9b-971b-26ac553d1669" />

Verify that your agent and tool were imported


<img width="3779" height="2031" alt="image" src="https://github.com/user-attachments/assets/1726e663-be7a-48c3-9c7f-06dd3321a38d" />

### 5.3: Open the agent, inspect it and try it!


<img width="3839" height="2054" alt="image" src="https://github.com/user-attachments/assets/4fa466e9-e1db-423d-87d6-8e2ec6c2e3bc" />


**✅ Checkpoint**: everything was imported to watsonx Orchestrate and is sucessfully working.

---

## Congratulations! 🎉

You've successfully completed Lab 3! You've learned to:

- ✅ Use IBM Bob to build tools and agents project
- ✅ Configure and use MCP servers in BOB
- ✅ Import MCP tools into watsonx Orchestrate
- ✅ Test an agent in watsonx Orchestrate


