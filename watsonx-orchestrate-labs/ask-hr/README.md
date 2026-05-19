# AskHR with watsonx Orchestrate

<img alt="AskHR" src="assets/hr_landscape.jpg">

This is the starting point of the workshop. In this lab, you begin inside watsonx Orchestrate with an HR-focused agent experience before moving into the Bob labs.

## Scenario

TechCorp Inc., a large global IT organization, needs a better way to handle employee HR operations at scale. Profile updates, benefits questions, and time-off requests are spread across multiple systems, which makes the employee experience fragmented and harder to support.

## Objective

The AskHR exercise shows how watsonx Orchestrate can provide a single entry point for common HR tasks by combining reasoning, tools, and grounded knowledge.

In this lab, you will work with an HR agent that can:

- Retrieve profile information
- Answer benefits-related questions using knowledge assets
- Check time-off balances
- Submit time-off requests
- Update personal details through connected tools

## Architecture

The AskHR solution uses watsonx Orchestrate as the coordination layer for the HR experience.

<img width="1494" height="912" alt="image" src="https://github.com/user-attachments/assets/b53c3498-eff3-4945-9cdb-fb74d622b460" />

### Main Components

- **HR Agent and app in watsonx Orchestrate**: The agent handles user interactions and routes requests to the right tools or knowledge sources.
- **Reusable tools**: OpenAPI-based actions support profile retrieval, time-off operations, and employee detail updates.
- **Knowledge grounding**: Company benefits documents are used to answer policy and benefits questions with grounded responses.
- **Underlying HCM systems**: Connected systems provide the employee data that the agent reads or updates.

## Hands-On Guide

The detailed implementation steps for this lab are in this [hands-on lab](assets/hands-on-lab-askHR.md).

