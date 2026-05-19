# Bob with watsonx Orchestrate

## Overview

This workshop combines Bob and watsonx Orchestrate. You will use IBM Bob to build an agent and a tool, then import both into watsonx Orchestrate using the official watsonx Orchestrate documentation MCP server as reference.

You will build a simple AI agent capable of:
- Calculating how much time is left until Christmas 2026

---

## Learning Objectives

By the end of this lab, you will be able to:

- ✅ Use Bob as an AI development agent
- ✅ Connect to an MCP server
- ✅ Build agents and tools with Bob
- ✅ Import agents and tools into watsonx Orchestrate

---

## Lab Flow

```text
Workshop Flow
├── Step 1: Set Up the Python Project
├── Step 2: Configure the watsonx Orchestrate Documentation MCP
├── Step 3: Use Bob to Create a Tool and an Agent
├── Step 4: Import the Agent and Tool into watsonx Orchestrate
└── Step 5: Access watsonx Orchestrate and Test the Agent
```

---

# Step 1: Set up the python project

In this step, you will prepare the project workspace.

## 1.1: Create and open the project folder

Create a new folder on your computer:

```text
wxo-Bob
```

Open this folder in IBM Bob.

<img width="2532" height="1468" alt="image" src="https://github.com/user-attachments/assets/f9d06884-0c45-4cb0-a6ed-dbf9a682e140" />

**✅ Checkpoint:** The project folder is open in Bob.

---

# Step 2: Configure the watsonx Orchestrate documentation MCP

In this step, you will connect the watsonx Orchestrate documentation MCP server to Bob.

This MCP server will allow Bob to use the official watsonx Orchestrate documentation as reference when generating agents and tools, helping ensure the generated assets follow the expected format and are compatible with watsonx Orchestrate.

---

## 2.1: Open the MCP marketplace in Bob

Go to **Settings** and open the **MCP** tab.

<img width="2515" height="1462" alt="image" src="https://github.com/user-attachments/assets/c2a7456f-439c-44e8-8f4f-b657305796f6" />

---

## 2.2: Search for the watsonx Orchestrate MCP

Search for:

```text
watsonx Orchestrate ADK Docs
```

Open the **watsonx Orchestrate ADK Docs**.

<img width="3391" height="1958" alt="image" src="https://github.com/user-attachments/assets/4d4fd84d-f8bd-44a0-b4bc-351e9a7b6f84" />

---

## 2.3: Install the MCP server

Click **Install**.

<img width="3392" height="1963" alt="image" src="https://github.com/user-attachments/assets/d77b6b12-6570-4863-9148-71f4ad364fe1" />

When prompted for the installation scope, you have 2 options:
- Select **Global** if you regularly work with watsonx Orchestrate. The MCP will be configured across all workspaces and you can reuse it in the future.
- Select **Project** if you only plan to use it for this lab. The MCP will be available only for this project.

NOTE: For more info, check the [documentation](https://bob.ibm.com).

<img width="3399" height="1977" alt="image" src="https://github.com/user-attachments/assets/19a1c3ba-37cd-4824-80c8-d02d520f13b6" />

---

## 2.4: Verify the MCP server is active

Return to the MCP tab and confirm that a green dot appears next to the MCP server, indicating that it is installed and active.

<img width="3398" height="1965" alt="image" src="https://github.com/user-attachments/assets/feda3dff-c83f-4553-935d-42c26c9ed009" />

**✅ Checkpoint:** The watsonx Orchestrate documentation MCP server is installed and active.

---

# Step 3: Use Bob to create a tool and an agent

In this step, you will use Bob to generate:
- A Python tool
- An AI agent that uses that tool

---

## 3.1: Change Bob mode to "Advanced"

First, make sure you’ve selected “Advanced” mode in Bob. This mode is well suited for coding tasks like the ones Bob will be asked to perform in the following steps.

> **🎯Customizable Modes**
> Unlike other AI assistants, Bob allows you to create [custom modes](https://bob.ibm.com/docs/ide/features/modes#customizing-modes) tailored to your team's specific workflows.

<img width="3383" height="1970" alt="image" src="https://github.com/user-attachments/assets/764bf5fd-a458-403a-8a17-07a4a5c39693" />

## 3.2: Ask Bob to create the tool

**Prompt for Bob:**

```bash
Please create a single python tool that calculates how much days we have left until christmas of 2026, following the watsonx Orchestrate ADK documentation MCP server as reference.
```

<img width="3398" height="1977" alt="image" src="https://github.com/user-attachments/assets/3e0819cf-859c-4e99-a60b-e2c0ae25c4c2" />

Bob will use the MCP server to understand the expected watsonx Orchestrate tool format and generate the tool accordingly.

<img width="3836" height="2222" alt="image" src="https://github.com/user-attachments/assets/4ff1a424-b50e-4050-a2a2-a8a12d31f866" />

Approve any commands Bob requests to run.

---

## 3.3: Ask Bob to create the agent

**Prompt for Bob:**

```bash
Please create an agent that uses the previously created tool whenever the user asks how much time is left until Christmas, answering in a Santa Claus style.

I want groq/openai/gpt-oss-120b to be the agent LLM.

Follow the watsonx Orchestrate ADK documentation MCP server as reference.
```

<img width="3417" height="1973" alt="image" src="https://github.com/user-attachments/assets/d77325e0-83a8-4faa-9d40-a76e703ec81f" />

Bob will once again use the MCP documentation server as reference to generate the agent.

After the generation is complete, inspect the generated agent file and verify:
- The tool is correctly connected to the agent
- The instructions and behavior match the intended use case

<img width="3820" height="2225" alt="image" src="https://github.com/user-attachments/assets/85948868-29d7-4744-915d-4b09a5b4d2c9" />

**✅ Checkpoint:** The agent and tool were successfully created.

---

# Step 4: Import the agent and tool into watsonx Orchestrate

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

## 4.1: Generate an IBM Cloud API key

Go to your IBM Cloud account and generate an API key.

<img width="3682" height="1954" alt="image" src="https://github.com/user-attachments/assets/623b0b38-6639-4855-9f55-ca5cadcd1257" />

<img width="3636" height="1921" alt="image" src="https://github.com/user-attachments/assets/6c8c9e34-2913-4422-bc05-c197ea48f11b" />

<img width="3666" height="1942" alt="image" src="https://github.com/user-attachments/assets/36965ebe-7944-4b4e-9268-e075822dcc86" />

**Important:** Copy the API key and paste it somewhere, because you will use it in the next steps.


---

## 4.2: Retrieve your watsonx Orchestrate instance URL

Open your watsonx Orchestrate environment in the browser.

<img width="3654" height="1841" alt="image" src="https://github.com/user-attachments/assets/2d037624-70e7-40ad-a705-de51b8b054c5" />

<img width="3671" height="1850" alt="image" src="https://github.com/user-attachments/assets/2955be47-cc4b-4c45-8561-68988a7d58c3" />

Copy the instance URL.

<img width="3711" height="1838" alt="image" src="https://github.com/user-attachments/assets/7c67b5ba-f3e5-48a5-83b9-2a459a37fa59" />


**Important:** Copy the URL and paste it somewhere, because you will use it in the next steps.


---

## 4.3: Install the watsonx Orchestrate ADK

Before you start working with watsonx Orchestrate, you need to make sure you have installed the ADK (Agent Development Kit), which is a comprehensive set of CLI utilities and Python modules that enables you to create, test, and deploy agents and tools for watsonx Orchestrate.

Luckily, we can also ask Bob to help us with that! Let's start a new task for this.

**Prompt for Bob:**

```bash
Install the watsonx Orchestrate ADK
```

<img width="3413" height="1969" alt="image" src="https://github.com/user-attachments/assets/70d1bf43-5602-4c7e-b9cf-3eb47b186cb8" />

Bob will let you know once the installation was successful.

<img width="3410" height="1980" alt="image" src="https://github.com/user-attachments/assets/87c9b373-7c3d-40a4-838b-db6794d75e46" />


---

## 4.4: Create and activate a watsonx Orchestrate environment

Open a new terminal in Bob.

<img width="3410" height="1979" alt="image" src="https://github.com/user-attachments/assets/3ff13ef4-ba93-443b-a785-d6afdff1c176" />

**Command for the terminal:**

```bash
orchestrate env add -n wxo-Bob -u <INSERT_YOUR_URL> --type ibm_iam --activate
```

When prompted, paste your API key.

It is expected that the key will not appear while typing. This is normal and done for security reasons.

After pressing Enter, you should see a confirmation message indicating that the environment was successfully created and activated.

<img width="3393" height="1961" alt="image" src="https://github.com/user-attachments/assets/872a6df6-5729-4759-84d3-c53918a77aef" />

---

## 4.5: Ask Bob to import the agent and tool

Now that the environment is configured, ask Bob to import the assets into watsonx Orchestrate.

**Prompt for Bob:**

```bash
Import the python tool and agent to my wxo-Bob watsonx Orchestrate environment. Follow the watsonx Orchestrate ADK documentation MCP server to find the appropriate import commands.
```

<img width="3400" height="1969" alt="image" src="https://github.com/user-attachments/assets/516e3db9-92c5-41e3-9abc-a0085c9273c3" />

During the import process, Bob may need to resolve issues such as:
- Tool names containing spaces
- Missing dependencies
- Requirements file updates
- Configuration adjustments

Allow Bob to apply fixes and retry the import if necessary.

**✅ Checkpoint:** The agent and tool were successfully imported into watsonx Orchestrate.

---

# Step 5: Access watsonx Orchestrate and test the agent

---

## 5.1: Open watsonx Orchestrate

Launch your watsonx Orchestrate environment.

<img width="3710" height="1824" alt="image" src="https://github.com/user-attachments/assets/9151dd76-0570-4388-96ff-616e5bceab0c" />

---

## 5.2: Open the 'Build' tab

Navigate to the **Build** tab.

<img width="3704" height="1833" alt="image" src="https://github.com/user-attachments/assets/05811452-1acd-4d9b-971b-26ac553d1669" />

Verify that both the agent and tool are available.

<img width="3570" height="1970" alt="image" src="https://github.com/user-attachments/assets/2e48ef18-b6c9-4a6c-bb4f-a30422918a4d" />

<img width="3573" height="1972" alt="image" src="https://github.com/user-attachments/assets/6a316333-6dd4-4209-96be-5c0eb6124886" />


---

## 5.3: Open and test the agent

Open the agent, inspect its configuration, and test it directly from the UI.

**Prompt for the agent:**

```bash
How many days left until Christmas?
```

<img width="3703" height="1965" alt="image" src="https://github.com/user-attachments/assets/bcf66ecb-108f-4818-b041-41c70f2bf3b4" />

You can also click on "Show Reasoning" in order to verify and better understand how the agent used the tool to reach its answer.

<img width="3684" height="1958" alt="image" src="https://github.com/user-attachments/assets/294f5c4b-2fe2-4728-896d-127cd235a487" />

**✅ Checkpoint:** The agent and tool are successfully working inside watsonx Orchestrate.

---

# Congratulations! 🎉

You have successfully completed the Bob x watsonx Orchestrate Lab.

In this lab, you learned how to:
- ✅ Use IBM Bob to build AI agents and tools
- ✅ Configure and use MCP servers in Bob
- ✅ Generate watsonx Orchestrate-compatible assets
- ✅ Import tools and agents into watsonx Orchestrate
- ✅ Validate and test an AI agent in watsonx Orchestrate
