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
```

<img width="3821" height="2217" alt="image" src="https://github.com/user-attachments/assets/b621c6c0-5757-4d67-8018-0ad1910b9b50" />


### 3.3: Run the End-to-End Tests

Bob should run the MCP client and confirm that both tools work through the MCP protocol.

Expected tests:

```python
factorial_value(5)
# Expected result: 120

factorial_digits(120)
# Expected result: number of digits in 120!
```

**✅ Checkpoint**: MCP client successfully validates both tools through the MCP server.

---

## Step 4: Add the MCP Tools to watsonx Orchestrate (10 minutes)

In this step, you will connect your local project to a watsonx Orchestrate environment and import the MCP tools.

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

Store the API key somewhere safe because you will use it in the next step.

### 4.2: Retrieve Your watsonx Orchestrate Instance URL

Open your watsonx Orchestrate environment in the browser.

Copy the URL of your instance.

Example:

```text
https://api.us-south.watson-orchestrate.cloud.ibm.com/instances/xxxxxxxx
```

### 4.3: Ask Bob to Configure the watsonx Orchestrate Environment

For simplicity in this workshop, you can provide the instance URL and API key directly in the prompt.

**⚠️ Note:** This is acceptable for a workshop environment, but in production environments credentials should be managed securely and never shared in prompts, screenshots, or logs.

**Prompt for Bob:**

```bash
Create and configure a watsonx Orchestrate environment using this instance URL: <YOUR_INSTANCE_URL>

Use this IBM Cloud API key: <YOUR_API_KEY>
```

Bob will:
- Create the environment
- Configure authentication
- Verify connectivity
- Activate the environment

Click **Approve** whenever Bob asks for confirmation.

### 4.4: Ask Bob to Import the MCP Tools

Once the environment is configured, ask Bob to import the MCP tools.

**Prompt for Bob:**

```bash
Need to add these MCP tools into watsonx Orchestrate, you can use the command line “orchestrate toolkits” to accomplish that.
```

Bob will:
- Inspect the watsonx Orchestrate CLI help
- Identify the correct import command
- Import the MCP tools
- Fix any dependency or naming issues automatically

Click **Approve** when Bob shows the plan.

### 4.5: Fix Import Issues

During the import, Bob may encounter issues such as:
- Tool names containing spaces
- Missing dependencies
- Requirements file needing updates
- Incorrect configuration values

Allow Bob to fix these issues and retry the import.

### 4.6: Verify the Imported Tools

Bob should confirm that the MCP tools were imported successfully.

Expected result:
- `factorial_value` is available in watsonx Orchestrate
- `factorial_digits` is available in watsonx Orchestrate

**✅ Checkpoint**: MCP tools are imported and ready to use in watsonx Orchestrate.

---

## Step 5: Create a watsonx Orchestrate Agent That Uses the MCP Tools (5 minutes)

In this step, you will ask Bob to create an agent YAML file and import the agent into watsonx Orchestrate.

The agent will use:
- The imported MCP tools
- The `groq/openai/gpt-oss-120b` model

### 5.1: Ask Bob to Create the Agent YAML

**Prompt for Bob:**

```bash
Create Agent YAML file, you can find the yaml specification at below page, use the following llm for the agent “groq/openai/gpt-oss-120b”

https://developer.watson-orchestrate.ibm.com/agents/build_agent

Then import the agent on watsonx Orchestrate using orchestrate command line.
```

Bob will:
- Check the YAML specification
- Create the agent YAML file
- Add the MCP tools to the agent
- Configure the model
- Import the agent using the CLI

Click **Approve** when Bob shows the plan.

### 5.2: Let Bob Fix YAML Errors

If the first import fails, Bob should read the error message and update the YAML file.

Common issues may include:
- Incorrect YAML fields
- Missing required properties
- Incorrect tool references
- Incorrect model format

Allow Bob to fix and re-import the agent.

### 5.3: Verify the Agent Import

Bob should confirm that the agent was imported successfully.

Expected agent name:

```bash
factorial_agent
```

**✅ Checkpoint**: The `factorial_agent` is created in watsonx Orchestrate.

---

## Step 6: Verify the Agent in watsonx Orchestrate (5 minutes)

In this step, you will manually verify that the agent works in watsonx Orchestrate.

### 6.1: Open watsonx Orchestrate

Log in to your watsonx Orchestrate environment.

Go to:

```bash
Manage Agents
```

Search for:

```bash
factorial_agent
```

<img width="1785" height="1009" alt="image" src="https://github.com/user-attachments/assets/2efab59b-ac8c-4fde-ac87-d26981949abd" />


### 6.2: Confirm Agent Configuration

Open the agent and verify:
- The MCP tools are attached
- The agent uses the Groq-hosted model
- The tools are available to the agent

<img width="1784" height="923" alt="image" src="https://github.com/user-attachments/assets/38a99824-e977-4872-b899-c8b011efc391" />


### 6.3: Test the First Tool

Ask the agent:

```bash
What is the factorial value of 5?
```

Expected result:

```bash
120
```

The agent should call the `factorial_value` MCP tool.

### 6.4: Test the Second Tool

Ask the agent:

```bash
How many factorial digits are there on factorial 120?
```

The agent should call the `factorial_digits` MCP tool.

**✅ Checkpoint**: The agent correctly calls both MCP tools from watsonx Orchestrate.

---

## Optional Step 7: Configure Bob with watsonx Orchestrate MCP Servers

This optional step improves Bob’s ability to work with watsonx Orchestrate projects.

You can configure Bob to access MCP servers such as:

### `wxo-docs`

Provides access to public documentation for the watsonx Orchestrate ADK.

### `orchestrate-adk`

Provides access to the watsonx Orchestrate software development kit for creating agents and tools.

This helps Bob:
- Find the right documentation faster
- Understand the watsonx Orchestrate CLI
- Generate better agent and tool configurations
- Reduce manual troubleshooting

---

## Congratulations! 🎉

You've successfully completed Lab 3! You've learned to:

- ✅ Use IBM Bob to build an MCP project
- ✅ Create MCP tools with FastMCP
- ✅ Test MCP tools with unit tests
- ✅ Validate MCP tools using an MCP client
- ✅ Import MCP tools into watsonx Orchestrate
- ✅ Create an agent YAML file
- ✅ Deploy and test an agent in watsonx Orchestrate

## What You've Built

```text
mcp-wxo/
├── README.md
├── requirements.txt
├── server.py
├── client.py
├── tests/
│   └── test_factorial_tools.py
├── agent.yaml
└── docs/
    └── usage.md
```

## Key Takeaways

### IBM Bob as a Development Partner

Bob can:
- Create the project structure
- Write the MCP server
- Generate tests
- Debug issues
- Create documentation
- Import tools and agents
- Verify the final workflow

### MCP Tools

MCP tools allow agents to connect to external capabilities in a structured way.

In this lab, your tools were simple mathematical tools, but the same pattern can be used for:
- Internal APIs
- Databases
- Document search
- Business applications
- Automation workflows

### watsonx Orchestrate Integration

watsonx Orchestrate allows you to:
- Import tools
- Create agents
- Connect agents to models
- Test agent behavior
- Build reusable AI workflows

### Agent YAML Files

Agent YAML files define:
- Agent name
- Agent description
- LLM configuration
- Tool access
- Agent behavior

This makes agents easier to version, review, and deploy.

## Troubleshooting

### MCP Server Issues

**Problem**: FastMCP is not installed

```bash
pip install fastmcp
```

**Problem**: MCP server does not start

Check:
- Virtual environment is activated
- Dependencies are installed
- Server file has no syntax errors
- Correct Python version is being used

### MCP Client Issues

**Problem**: Client cannot connect to server

Check:
- MCP server is running
- Client points to the correct server command or endpoint
- No dependency is missing
- Server logs do not show errors

### watsonx Orchestrate Import Issues

**Problem**: Tool name cannot contain spaces

Use tool names with underscores:

```bash
factorial_value
factorial_digits
```

**Problem**: Missing dependency during import

Update `requirements.txt` and retry the import.

**Problem**: Agent YAML import fails

Check:
- YAML indentation
- Required fields
- Tool names
- Model name
- watsonx Orchestrate agent specification

### Agent Testing Issues

**Problem**: Agent does not call the right tool

Try a more direct prompt:

```bash
Use the factorial_value tool to calculate the factorial value of 5.
```

**Problem**: Agent cannot access tools

Check:
- Tools were imported successfully
- Tools are attached to the agent
- Agent was re-imported after tool changes

## Additional Resources

- https://developer.watson-orchestrate.ibm.com/
- https://developer.watson-orchestrate.ibm.com/agents/build_agent
- https://modelcontextprotocol.io/

## Feedback

How was this lab? We'd love to hear:
- Was the MCP flow clear?
- Did Bob help reduce manual work?
- Were the watsonx Orchestrate steps easy to follow?
- What other tools would you like to connect through MCP?

---

**Last Updated: February 2026**
