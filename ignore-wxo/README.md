# Lab 3: Building AI Agents with IBM Bob and watsonx Orchestrate

## Overview

In this lab, you'll use IBM Bob to build and deploy MCP tools, import them into watsonx Orchestrate, and create an AI agent that can use those tools.

You will build a factorial agent that can:
- Calculate the exact value of a factorial
- Calculate the number of digits in a large factorial
- Use MCP tools inside watsonx Orchestrate
- Run with the `groq/openai/gpt-oss-120b` model

<img width="1793" height="1145" alt="image" src="https://github.com/user-attachments/assets/4b96ca7c-8e8a-43f4-84a3-43bdbaaf90d3" />


## What You'll Build

A complete AI agent workflow with:
- **MCP Server**: Built with FastMCP
- **Tools**: `factorial_value` and `factorial_digits`
- **MCP Client**: Used to validate the tools end to end
- **watsonx Orchestrate Integration**: MCP tools imported into watsonx Orchestrate
- **AI Agent**: A `factorial_agent` using the MCP tools

## Learning Objectives

By the end of this lab, you will:
- ✅ Use IBM Bob as an AI development partner
- ✅ Build an MCP server with FastMCP
- ✅ Create and test MCP tools
- ✅ Validate tools using an MCP client
- ✅ Import MCP tools into watsonx Orchestrate
- ✅ Create an agent YAML file
- ✅ Deploy and verify an agent in watsonx Orchestrate

## Prerequisites

Before starting, ensure you have:
- [ ] IBM Bob installed and running
- [ ] Python 3.8+ installed
- [ ] A Python virtual environment available
- [ ] watsonx Orchestrate ADK installed and configured
- [ ] Access to a watsonx Orchestrate environment
- [ ] Basic understanding of MCP tools and agents

If you haven't completed setup, see [prerequisites.md](../prerequisites.md).

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

## Step 1: Set Up the Python Project (5 minutes)

In this step, you will prepare the workspace for your project and ask IBM Bob to set up the Python environment.

Bob will:
- Create and configure the Python virtual environment
- Prepare the project structure
- Create the initial README file
- Get the environment ready for MCP development

### 1.1: Create and Open the Project Folder

Create a new folder on your machine called:

```text
mcp-wxo
```

Open this folder in IBM Bob.

<img width="2960" height="2155" alt="image" src="https://github.com/user-attachments/assets/f4e869ab-ab12-4748-b52d-64cb8f379c77" />

### 1.2: Ask Bob to Create and Activate a Python Virtual Environment

**Prompt for Bob:**

```bash
Create a Python virtual environment for this project and activate it.
```
<img width="2318" height="2128" alt="image" src="https://github.com/user-attachments/assets/924e68bf-355b-42ef-931e-223a7c70ef89" />


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

## Step 2: Build the MCP Server with Two Tools (10 minutes)

In this step, you will ask Bob to create an MCP server using FastMCP.

The MCP server will include two mathematical tools:

1. `factorial_value`  
   Calculates and returns the exact value of `n!`.

2. `factorial_digits`  
   Returns only the number of decimal digits in `n!`, which is useful when the factorial is too large to display in full.

### 2.1: Ask Bob to Create the MCP Server

**Prompt for Bob:**

```bash
Create MCP Server using FastMCP with two mathematical tools. The first tool “factorial_value” calculates and returns the exact value of n! (the factorial of a given non-negative integer). The second tool “factorial_digits” returns only the number of decimal digits in n!, which is useful when the factorial is too large to display in full. You can have both tools share a common helper function to compute the factorial and avoid duplication of code.
```

<img width="1783" height="1028" alt="image" src="https://github.com/user-attachments/assets/6d390af5-0eba-4a77-8d1f-54ecd765a7b6" />

Bob will create a plan and ask for approval.

Click **Approve**.

### 2.2: Install FastMCP

Bob should identify that FastMCP is required and ask for permission to install it.

Click **Run** when Bob asks to install dependencies.

### 2.3: Review the MCP Server Code

Bob should create MCP server code with:
- A shared helper function to calculate factorials
- A `factorial_value` tool
- A `factorial_digits` tool
- Basic validation for non-negative integers

Expected tool behavior:

```python
factorial_value(5)
# Returns: 120

factorial_digits(120)
# Returns the number of digits in 120!
```

### 2.4: Ask Bob to Create Tests

Bob should also create unit tests for the MCP tools.

If needed, use this prompt:

```bash
Create unit tests for both MCP tools and verify that they work correctly, including error handling for invalid inputs.
```

### 2.5: Let Bob Fix Issues Automatically

Bob may find errors while running the tests.

Allow Bob to:
- Debug the implementation
- Fix the code
- Re-run the tests
- Confirm that all tests pass

### 2.6: Generate Documentation

Ask Bob to document the project.

**Prompt for Bob:**

```bash
Generate clear documentation for this MCP server, including setup instructions, tool descriptions, and example usage.
```

**✅ Checkpoint**: MCP server, tools, tests, and documentation are created successfully.

---

## Step 3: Start the MCP Server and Validate with an MCP Client (10 minutes)

In this step, you will ask Bob to start the MCP server locally and create an MCP client to test the tools end to end.

### 3.1: Ask Bob to Start the MCP Server

**Prompt for Bob:**

```bash
Please start the MCP Server, and test the 2 MCP tools with MCP client.
```
<img width="1774" height="1058" alt="image" src="https://github.com/user-attachments/assets/1e55ad57-1366-450e-b566-2dd98e8637ab" />


Bob will create a plan for:
- Starting the MCP server
- Creating an MCP client
- Connecting the client to the server
- Testing both tools

Click **Approve**.

### 3.2: Review the MCP Client

Bob should create MCP client code that:
- Connects to the local MCP server
- Calls `factorial_value`
- Calls `factorial_digits`
- Tests valid and invalid inputs
- Confirms error handling works correctly

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
