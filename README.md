# Bob Workshop Portugal: Hands-On Labs

This repository is structured as a guided workshop path across watsonx Orchestrate, Bob, and then both together.

## Workshop Flow

1. Start with [watsonx Orchestrate labs](watsonx-orchestrate-labs/) and choose either [AskHR](watsonx-orchestrate-labs/ask-hr/README.md) or [Agentic Workflow](watsonx-orchestrate-labs/agentic-workflow/README.md).
2. Move into [Bob Labs](bob-labs/) to work through the Bob-focused tutorials from prerequisites through Java modernization.
3. Finish with [Bob with watsonx Orchestrate](bob-with-watsonx-orchestrate-labs/README.md) to combine both platforms in a final agent-and-tool workflow.

<img width="1983" height="793" alt="image" src="https://github.com/user-attachments/assets/a3ec6b18-1fc1-45e1-af30-ccf72ff3dd2e" />

## What You Will Practice

- Building and testing agents in watsonx Orchestrate
- Designing an agentic workflow with document extraction and human-in-the-loop steps
- Using Bob's Plan, Code, and Ask modes across different tasks
- Building a Flask + JavaScript + SQLite application
- Reviewing and remediating vulnerable code
- Translating code between Python and JavaScript with Bob
- Modernizing legacy Java code
- Generating and importing watsonx Orchestrate agents and tools

## Repository Structure

```text
.
├── watsonx-orchestrate-labs/
│   ├── agentic-workflow/
│   └── ask-hr/
├── bob-labs/
│   ├── lab0-prerequisites-old/
│   ├── lab1/
│   ├── lab2/
│   ├── lab3/
│   ├── lab4/
│   └── lab5/
├── bob-with-watsonx-orchestrate-labs/
│   └── README.md
└── environment-setup/
```

## Lab Sequence

### 1. watsonx Orchestrate Labs

Start in [`watsonx-orchestrate-labs`](watsonx-orchestrate-labs/).

- [`ask-hr`](watsonx-orchestrate-labs/ask-hr/README.md): Explore an HR agent experience built in watsonx Orchestrate.
- [`agentic-workflow`](watsonx-orchestrate-labs/agentic-workflow/README.md): Build a no-code workflow for a bank-account opening use case with document extraction and branching logic.

### 2. Bob Labs

Each Bob lab now includes its own prerequisites section. The original consolidated setup guide is still available in [`bob-labs/lab0-prerequisites-old`](bob-labs/lab0-prerequisites-old/README.md).

Then, explore the hands-on labs in this order:

1. [`lab1`](bob-labs/lab1/README.md): Build a full-stack todo application with Bob.
2. [`lab2`](bob-labs/lab2/README.md): Understand, extend, and document an existing application with Bob.
3. [`lab3`](bob-labs/lab3/README.md): Analyze a vulnerable codebase and prioritize security fixes with Bob.
4. [`lab4`](bob-labs/lab4/README.md): Translate a Python data-processing script into JavaScript with Bob.
5. [`lab5`](bob-labs/lab5/README.md): Modernize a legacy Java application with Bob.

### 3. Final Lab: Bob with watsonx Orchestrate

Finish with [`bob-with-watsonx-orchestrate-labs`](bob-with-watsonx-orchestrate-labs/README.md).

This lab brings the two tracks together. You will use Bob plus the watsonx Orchestrate documentation MCP server to generate a Python tool and an agent, then import and validate both assets inside watsonx Orchestrate.
