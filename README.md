# Bob Workshop Portugal: Hands-On Labs

This repository is structured as a guided workshop path across watsonx Orchestrate, Bob, and then both together.

## Workshop Flow

1. Start with [AskHR in `watsonx-orchestrate-labs`](watsonx-orchestrate-labs/ask-hr/README.md) to explore an HR agent experience built in watsonx Orchestrate.
2. Move into [Bob Labs](bob-labs) to build a full-stack todo application and try Python-to-JavaScript code translation with Bob. 
3. Finish with [Bob with watsonx Orchestrate](bob-with-watsonx-orchestrate-labs/lab-wxo-bob/README.md) to combine both platforms in a final agent-and-tool workflow.


<img width="1983" height="793" alt="image" src="https://github.com/user-attachments/assets/a3ec6b18-1fc1-45e1-af30-ccf72ff3dd2e" />


## What You Will Practice

- Building and testing an HR agent in watsonx Orchestrate
- Using Bob's Plan, Code, and Ask modes across different tasks
- Working with GitHub MCP and documentation MCP servers
- Building a Flask + JavaScript + SQLite application
- Translating code between Python and JavaScript with Bob
- Generating and importing watsonx Orchestrate agents and tools

## Repository Structure

```text
.
├── watsonx-orchestrate-labs/
│   └── ask-hr/
├── bob-labs/
│   ├── lab0-prerequisites/
│   ├── lab1/
│   └── lab2/
├── bob-with-watsonx-orchestrate-labs/
│   └── lab-wxo-bob/
└── environment-setup/
```


## Lab Sequence

### 1. AskHR with watsonx Orchestrate

Start the workshop in [`watsonx-orchestrate-labs/ask-hr`](watsonx-orchestrate-labs/ask-hr/README.md).

This exercise focuses on a watsonx Orchestrate HR use case. You will review the business scenario, understand the architecture, and follow the hands-on guide to work with an agent that handles profile data, benefits knowledge, and time-off flows.

### 2. Bob Labs: Build a Todo Application and try Python-to-JavaScript code translation

Before starting the Bob labs, review [`bob-labs/lab0-prerequisites`](bob-labs/lab0-prerequisites/README.md).

Then, explore and follow the hands-on labs available in this folder:

Lab 1: This lab uses Bob to plan and implement a full-stack todo application. It covers project planning, backend creation with Flask, frontend implementation in JavaScript, and GitHub integration through MCP.

Lab 2: This lab uses Bob to analyze an existing Python script, plan a translation strategy, and implement an equivalent JavaScript version while preserving behavior and applying language-specific patterns.

### 3. Final Lab: Bob with watsonx Orchestrate

Finish with [`bob-with-watsonx-orchestrate-labs/lab-wxo-bob`](bob-with-watsonx-orchestrate-labs/lab-wxo-bob/README.md).

This lab brings the two tracks together. You will use Bob plus the watsonx Orchestrate documentation MCP server to generate a Python tool and an agent, then import and validate both assets inside watsonx Orchestrate.
