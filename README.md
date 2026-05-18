# Bob Workshop Portugal: Hands-On Labs

This repository is structured as a guided workshop path across watsonx Orchestrate, Bob, and then both together.

## Workshop Flow

1. Start with [AskHR in `watsonx-orchestrate-labs`](watsonx-orchestrate-labs/ask-hr/README.md) to explore an HR agent experience built in watsonx Orchestrate.
2. Move into [Bob Lab 1 in `bob-labs`](bob-labs/lab1/README.md) to build a full-stack todo application with Bob.
3. Continue with [Bob Lab 2 in `bob-labs`](bob-labs/lab2/README.md) to use Bob for Python-to-JavaScript code translation.
4. Finish with [Bob with watsonx Orchestrate](bob-with-watsonx-orchestrate-labs/lab-wxo-bob/README.md) to combine both platforms in a final agent-and-tool workflow.

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

## Before You Start

If you are starting the Bob track, review [bob-labs/lab0-prerequisites/README.md](bob-labs/lab0-prerequisites/README.md). For shared environment guidance, see [environment-setup/README.md](environment-setup/README.md).

## Lab Sequence

### 1. AskHR with watsonx Orchestrate

Start the workshop in [`watsonx-orchestrate-labs/ask-hr`](watsonx-orchestrate-labs/ask-hr/README.md).

This exercise focuses on a watsonx Orchestrate HR use case. You will review the business scenario, understand the architecture, and follow the hands-on guide to work with an agent that handles profile data, benefits knowledge, and time-off flows.

### 2. Bob Lab 1: Build a Todo Application

Continue with [`bob-labs/lab1`](bob-labs/lab1/README.md).

Before starting the Bob labs, review [`bob-labs/lab0-prerequisites`](bob-labs/lab0-prerequisites/README.md).

This lab uses Bob to plan and implement a full-stack todo application. It covers project planning, backend creation with Flask, frontend implementation in JavaScript, and GitHub integration through MCP.

### 3. Bob Lab 2: Translate Python to JavaScript

Continue with [`bob-labs/lab2`](bob-labs/lab2/README.md).

This lab uses Bob to analyze an existing Python script, plan a translation strategy, and implement an equivalent JavaScript version while preserving behavior and applying language-specific patterns.

### 4. Final Lab: Bob with watsonx Orchestrate

Finish with [`bob-with-watsonx-orchestrate-labs/lab-wxo-bob`](bob-with-watsonx-orchestrate-labs/lab-wxo-bob/README.md).

This lab brings the two tracks together. You will use Bob plus the watsonx Orchestrate documentation MCP server to generate a Python tool and an agent, then import and validate both assets inside watsonx Orchestrate.
