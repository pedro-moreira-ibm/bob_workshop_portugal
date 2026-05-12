# Lab 3: Building AI Agents with IBM Bob and watsonx Orchestrate

## Overview

In this lab, you will use IBM Bob to build an agent and a Python tool, and then import them into watsonx Orchestrate using the official watsonx Orchestrate documentation MCP server as reference.

You will build a simple AI agent capable of:
- Calculating how much time is left until Christmas 2026
- Responding in a Santa Claus style

---

## Learning Objectives

By the end of this lab, you will be able to:

- ✅ Use IBM Bob as an AI development assistant
- ✅ Connect and use an MCP server in Bob
- ✅ Build agents and tools with Bob
- ✅ Import agents and tools into watsonx Orchestrate
- ✅ Import MCP-based tools into watsonx Orchestrate

---

## Prerequisites

Before starting, ensure you have:

- [ ] IBM Bob installed and running
- [ ] Python 3.8+ installed
- [ ] A Python virtual environment available
- [ ] watsonx Orchestrate ADK installed and configured
- [ ] Access to a watsonx Orchestrate environment
- [ ] Basic understanding of MCP tools and AI agents

---

## Lab Structure

```text
Lab 3 Timeline 
├── Step 1: Set Up the Python Project
├── Step 2: Configure the watsonx Orchestrate Documentation MCP
├── Step 3: Use Bob to Create a Tool and an Agent
├── Step 4: Import the Agent and Tool into watsonx Orchestrate
└── Step 5: Access watsonx Orchestrate and Test the Agent
```

---

# Step 1: Set Up the Python Project

In this step, you will prepare the project workspace and configure the Python environment.

Bob will help you:
- Create and configure the Python virtual environment
- Prepare the project structure
- Initialize the project workspace

## 1.1: Create and Open the Project Folder

Create a new folder on your machine called:

```text
wxo-bob
```

Open this folder in IBM Bob.

<img width="3838" height="2220" alt="image" src="https://github.com/user-attachments/assets/85d39175-6237-4b3c-8c78-d39f7d13de37" />


**✅ Checkpoint:** The project folder is open in Bob.

---

# Step 2: Configure the watsonx Orchestrate Documentation MCP

In this step, you will connect the watsonx Orchestrate documentation MCP server to Bob.

This MCP server will allow Bob to use the official watsonx Orchestrate documentation as reference when generating agents and tools, helping ensure the generated assets follow the expected format and are compatible with watsonx Orchestrate.

---

## 2.1: Open the MCP Marketplace in Bob

Go to **Settings** and open the **MCP** tab.

<img width="3818" height="2212" alt="image" src="https://github.com/user-attachments/assets/3437d789-9c72-4061-bd57-ef53c1508c38" />

---

## 2.2: Search for the watsonx Orchestrate MCP

Search for:

```text
orchestrate
```

Open the **watsonx Orchestrate ADK Docs MCP**.

<img width="3837" height="2220" alt="image" src="https://github.com/user-attachments/assets/6e76b258-1089-4917-93a3-2e07de6efa67" />

---

## 2.3: Install the MCP Server

Click **Install**.

<img width="3818" height="1375" alt="image" src="https://github.com/user-attachments/assets/c8f04fe8-0291-4b40-966d-a5298c93239b" />

When prompted for the installation scope:
- Select **Global** if you regularly work with watsonx Orchestrate
- Select **Project** if you only plan to use it for this lab

Using Project scope can help keep Bob's context lighter and more focused.

<img width="3816" height="2213" alt="image" src="https://github.com/user-attachments/assets/0d9cfd72-e80d-4a8c-a293-bd52b1cc87bd" />

---

## 2.4: Verify the MCP Server is Active

Return to the MCP tab and confirm that a green dot appears next to the MCP server, indicating that it is installed and active.

<img width="3424" height="1971" alt="image" src="https://github.com/user-attachments/assets/a9a4fecf-2006-4965-baca-2d32f626b12c" />

**✅ Checkpoint:** The watsonx Orchestrate documentation MCP server is installed and active.

---

# Step 3: Use Bob to Create a Tool and an Agent

In this step, you will use Bob to generate:
- A Python tool
- An AI agent that uses that tool

---

## 3.1: Ask Bob to Create the Tool

**Prompt for Bob:**

```bash
Please create a python tool that calculates how much days we have left until christmas of 2026, following the watsonx Orchestrate ADK documentation MCP server as reference.
```

<img width="3824" height="2220" alt="image" src="https://github.com/user-attachments/assets/86759582-df42-4027-bc52-63e7960a5d1e" />

Bob will use the MCP server to understand the expected watsonx Orchestrate tool format and generate the tool accordingly.

<img width="3833" height="2230" alt="image" src="https://github.com/user-attachments/assets/555054f4-515a-4b33-aa40-07c6f0d2eff6" />

Approve any commands Bob requests to run.

---

## 3.2: Ask Bob to Create the Agent

**Prompt for Bob:**

```bash
Please create an agent that uses the previously created tool whenever the user asks how much time is left until Christmas, answering in a Santa Claus style.

I want groq/openai/gpt-oss-120b to be the agent LLM.

Follow the watsonx Orchestrate ADK documentation MCP server as reference.
```

<img width="3821" height="2217" alt="image" src="https://github.com/user-attachments/assets/b621c6c0-5757-4d67-8018-0ad1910b9b50" />

Bob will once again use the MCP documentation server as reference to generate the agent.

After the generation is complete, inspect the generated agent file and verify:
- The tool is correctly connected to the agent
- The instructions and behavior match the intended use case

<img width="3839" height="2222" alt="image" src="https://github.com/user-attachments/assets/db3d437c-7cca-49cd-b6d3-c19422f7e708" />

**✅ Checkpoint:** The agent and tool were successfully created.

---

# Step 4: Import the Agent and Tool into watsonx Orchestrate

In this step, you will connect your local project to a watsonx Orchestrate environment and import the generated assets.

Before importing anything, you will need:
- An IBM Cloud API key
- Your watsonx Orchestrate instance URL

Bob will then help:
- Configure the watsonx Orchestrate environment
- Authenticate to the environment
- Import the tool and agent
- Resolve any dependency or configuration issues

---

## 4.1: Generate an IBM Cloud API Key

Go to your IBM Cloud account and generate an API key.

<img width="3682" height="1954" alt="image" src="https://github.com/user-attachments/assets/623b0b38-6639-4855-9f55-ca5cadcd1257" />

<img width="3636" height="1921" alt="image" src="https://github.com/user-attachments/assets/6c8c9e34-2913-4422-bc05-c197ea48f11b" />

Store the API key securely because you will use it in the next steps.

---

## 4.2: Retrieve Your watsonx Orchestrate Instance URL

Open your watsonx Orchestrate environment in the browser.

<img width="3654" height="1841" alt="image" src="https://github.com/user-attachments/assets/2d037624-70e7-40ad-a705-de51b8b054c5" />

<img width="3671" height="1850" alt="image" src="https://github.com/user-attachments/assets/2955be47-cc4b-4c45-8561-68988a7d58c3" />

Copy the instance URL.

<img width="3711" height="1838" alt="image" src="https://github.com/user-attachments/assets/7c67b5ba-f3e5-48a5-83b9-2a459a37fa59" />

Example:

```text
https://api.us-south.watson-orchestrate.cloud.ibm.com/instances/xxxxxxxx
```

---

## 4.3: Create and Activate a watsonx Orchestrate Environment

Return to Bob and open a new terminal.

<img width="3839" height="1495" alt="image" src="https://github.com/user-attachments/assets/478f2b0d-3d05-49fe-a184-c3450a20729e" />

**Command for the terminal:**

```bash
orchestrate env add -n wxo-bob -u <INSERT_YOUR_URL> --type ibm_iam --activate
```

When prompted, paste your API key.

It is expected that the key will not appear while typing. This is normal and done for security reasons.

After pressing Enter, you should see a confirmation message indicating that the environment was successfully created and activated.

<img width="3368" height="1975" alt="image" src="https://github.com/user-attachments/assets/820f856f-5c5f-4c93-acef-af0e2ee65c67" />

---

## 4.4: Ask Bob to Import the Agent and Tool

Now that the environment is configured, ask Bob to import the assets into watsonx Orchestrate.

**Prompt for Bob:**

```bash
Import the python tool and agent to my wxo-bob watsonx Orchestrate environment. Follow the watsonx Orchestrate ADK documentation MCP server to find the appropriate import commands.
```

<img width="3839" height="2220" alt="image" src="https://github.com/user-attachments/assets/8e45f0fa-abc4-44ab-9d67-4f6befed053d" />

During the import process, Bob may need to resolve issues such as:
- Tool names containing spaces
- Missing dependencies
- Requirements file updates
- Configuration adjustments

Allow Bob to apply fixes and retry the import if necessary.

<img width="3839" height="2141" alt="image" src="https://github.com/user-attachments/assets/17d854d0-6eec-4e5c-b93e-17eb26d4de6e" />

**✅ Checkpoint:** The agent and tool were successfully imported into watsonx Orchestrate.

---

# Step 5: Access watsonx Orchestrate and Test the Agent

---

## 5.1: Open watsonx Orchestrate

Launch your watsonx Orchestrate environment.

<img width="3710" height="1824" alt="image" src="https://github.com/user-attachments/assets/9151dd76-0570-4388-96ff-616e5bceab0c" />

---

## 5.2: Open the Build Tab

Navigate to the **Build** tab.

<img width="3704" height="1833" alt="image" src="https://github.com/user-attachments/assets/05811452-1acd-4d9b-971b-26ac553d1669" />

Verify that both the agent and tool are available.

<img width="3779" height="2031" alt="image" src="https://github.com/user-attachments/assets/1726e663-be7a-48c3-9c7f-06dd3321a38d" />

---

## 5.3: Open and Test the Agent

Open the agent, inspect its configuration, and test it directly from the UI.

<img width="3839" height="2054" alt="image" src="https://github.com/user-attachments/assets/4fa466e9-e1db-423d-87d6-8e2ec6c2e3bc" />

**✅ Checkpoint:** The agent and tool are successfully working inside watsonx Orchestrate.

---

# Congratulations! 🎉

You have successfully completed Lab 3.

In this lab, you learned how to:
- ✅ Use IBM Bob to build AI agents and tools
- ✅ Configure and use MCP servers in Bob
- ✅ Generate watsonx Orchestrate-compatible assets
- ✅ Import tools and agents into watsonx Orchestrate
- ✅ Validate and test an AI agent in watsonx Orchestrate
