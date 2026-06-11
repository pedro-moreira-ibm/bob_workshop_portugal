# Building No-Code Agentic Workflows in watsonx Orchestrate

## Lab Overview

In this tutorial, learn how to create agentic workflows on watsonx Orchestrate without needing to write any code. These workflows help AI agents carry out tasks step-by-step using a static, pre-defined, and reusable structure.

Agentic workflows in watsonx Orchestrate are used to quickly build intelligent, reusable automation with minimal effort, while the platform offers a no-code experience ideal for rapid development and advanced decision-making. This flexibility allows developers to start with visual design and scale into more complex scenarios when needed.

This hands-on guide for creating agentic workflows with human-in-the-loop user activities, forms, document extraction, and generative prompts shows how to mix AI with clear rules and human feedback.

Real-world challenges include:

- **Manual Process**: Employees spend hours reviewing documents and entering data, which slows down operations.
- **Errors**: Human mistakes lead to discrepancies, delays, and potential client issues.
- **Scalability**: As the business expands, the volume of documents grows, requiring more manual labor, which is costly and unsustainable.

As a solution, you can leverage watsonx Orchestrate to automate the extraction of key data from documents.

- **Automated Extraction**: watsonx Orchestrate automatically extracts relevant data from documents, eliminating manual entry.
- **Workflow Integration**: The extracted data is seamlessly integrated into automated processes, such as opening a new bank account, speeding up the process.
- **Confidence Review**: If the extraction confidence is low, a human-in-the-loop review step ensures data accuracy without delays.

## Description of the Use Case

In this tutorial, you will build the **Account Opening Agent**, an AI agent that helps users open new bank accounts through a guided, automated process.

At the core of this agent, you will build the **Create New Bank Account Agentic Workflow** tool, entirely with no code on watsonx Orchestrate.

This agentic workflow handles all the steps in creating a new bank account, such as uploading a passport, extracting user details, checking nationality, and routing users accordingly. It also includes human-in-the-loop activities like form submissions and AI-generated confirmation messages.

## Architecture


The user interacts with the watsonx Orchestrate user interface, asking to open a new bank account. This request is sent to the **Account Opening Agent**, which uses an LLM for tasks such as interpreting instructions, reasoning through the problem, planning the next steps, and deciding whether a tool call is necessary.

When the Account Opening Agent determines that the request involves an account opening request, it invokes the **Create New Bank Account** tool, which will be created as an agentic workflow on watsonx Orchestrate.

This agentic workflow tool performs the following:

1. It asks for the image of the passport.
2. It extracts the details of the passport, including name, passport number, and nationality.
   - If the nationality is not Portuguese, then it stops the flow with a message informing the user to go to a bank branch and speak with a human.
   - If the nationality is Portuguese, it sends the user a form to provide additional details like a phone number and an account type.
3. It generates a confirmation message.

## Lab Structure

- [Open watsonx Orchestrate](#open-watsonx-orchestrate)
- [Create the Account Opening Agent](#step-1-create-the-account-opening-agent)
- [Create the Create New Bank Account Agentic Workflow Tool](#step-2-create-the-create-new-bank-account-agentic-workflow-tool)
- [Extract Details from a Document](#step-3-extract-details-from-a-document)
- [Configure the Conditional Logic](#step-4-configure-the-conditional-logic)
- [Create a Form for Human-in-the-Loop](#step-5-create-a-form-for-human-in-the-loop)
- [Create a Generative Prompt](#step-6-create-a-generative-prompt)
- [Test Your Agent](#step-7-test-your-agent)

---

# Open watsonx Orchestrate

## 1. Log in to IBM Cloud

Log in to IBM Cloud.

<!-- Add screenshot here -->

## 2. Open the watsonx Orchestrate service

Navigate to the top-left hamburger menu, then go to **Resource List**.

Open the **AI / Machine Learning** section. You should see a watsonx Orchestrate service. Click on it.

<!-- Add screenshot here -->

## 3. Launch watsonx Orchestrate

Click **Launch watsonx Orchestrate**.

<!-- Add screenshot here -->

**✅ Checkpoint**: watsonx Orchestrate is open and ready to use.

---

# Step 1: Create the Account Opening Agent

In this step, you are going to create a new agent in the watsonx Orchestrate user interface that guides users through the process of opening a bank account.

You do this by defining the agent’s name and description, customizing its welcome and prompt messages, and configuring the agent behavior to call the **Create New Bank Account Agentic Workflow** tool.

## 1.1: Create a new agent

Click **Create new agent** to access the Agent Builder.

<!-- Add screenshot here -->

## 1.2: Add the agent name and description

The agent description outlines the scope of the agent and makes it easy for other agents and users to know when to interact with this agent.

Fill in the name and description of the agent as follows:

```text
Name: Account Opening Agent

Description: You are an Account Opening Agent to help users open new bank accounts quickly and efficiently. Using the Create New Bank Account Agentic Workflow tool, you guide users through each step of the account opening process, starting with passport upload and automated detail extraction, followed by nationality checks using deterministic logic. You handle human-in-the-loop activities like form submissions and confirmation messages and generate personalized responses using AI prompts.
```

<!-- Add screenshot here -->

## 1.3: Create the agent

Click **Create**.

## 1.4: Customize the welcome message

In the **Profile** section, customize the welcome message from the agent on the home screen to:

```text
Hello, welcome to Account Opening Agent.
```

Click the **Reset** icon in the Preview tab.

<!-- Add screenshot here -->

## 1.5: Add a preset prompt

Click **Add Prompt** to add a pre-set message to start the conversation.

Add this message:

```text
Open a new bank account
```

Remove the remaining default messages.

Then, click **Reset**.

<!-- Add screenshot here -->

## 1.6: Configure the agent behavior

Go to the **Behavior** section to define how the agent should react to requests and respond to users.

Instruct the agent to call the Agentic Workflow tool **Create New Bank Account Agentic Workflow**, which you will create in the next step.

Write the following in the Behavior section:

```text
When the user requests to open a new bank account, call the tool "Create New Bank Account Agentic Workflow" and do not generate or display any additional output. The tool is fully responsible for handling the process and presenting the final response to the user. Your role is strictly to delegate the task to the tool. Do not repeat, summarize, or echo the tool’s output, as it already includes the necessary user-facing messages.
```

<!-- Add screenshot here -->

**✅ Checkpoint**: The Account Opening Agent has been created and configured.

---

# Step 2: Create the Create New Bank Account Agentic Workflow Tool

In this step, you are going to define a new agentic workflow tool that will handle the logic and automation for opening a new bank account.

This tool encapsulates the process that the agent will invoke, ensuring a modular and reusable design.

## 2.1: Add a new tool

Go to the **Toolset** section and click **Add tool** to create the agentic workflow tool.

## 2.2: Select Agentic Workflow

Click **Agentic workflow**.

<!-- Add screenshot here -->

## 2.3: Name the agentic workflow

Give it a name and then click **Start building**.

```text
Name: Create New Bank Account Agentic Workflow
```

<!-- Add screenshot here -->

Your view will look like this:

<!-- Add screenshot here -->

**✅ Checkpoint**: The Create New Bank Account Agentic Workflow tool has been created.

<!-- Optional: Add an additional step for document classification if needed. If this is added, update the architecture section accordingly. -->

---

# Step 3: Extract Details from a Document

In this step, you are going to configure a document extraction activity to extract and collect details from passport images to use during the account opening.

This part of the agentic workflow enables the agent to extract structured data like passport number, nationality, and names from documents.

You define the agentic workflow to ask the user to upload a passport, train the document extractor with sample images, define key fields, and enhance accuracy through normalization and examples.

## 3.1: Download the synthetic passport images

Download these synthetic passport images:

- Passport Image 1, name it: `passport-1.jpg`
- Passport Image 2, name it: `passport-2.png`
- Passport Image 3, name it: `passport-3.png`
- Passport Image 4, name it: `passport-4.png`

> **Note**  
> The first two images, `passport-1.jpg` and `passport-2.png`, will be used for training.  
>
> The last two images, `passport-3.png` and `passport-4.png`, will be used for testing.

## 3.2: Add a User activity

Go back to the agentic workflow in watsonx Orchestrate and drag the **User activity** into your workflow where it says **Add your first step**.

This User activity will be used to get input from the user on the passport.

<!-- Add screenshot here -->

## 3.3: Rename the User activity

Click **User Activity 1** and rename it to:

```text
Upload Passport
```

<!-- Add screenshot here -->

## 3.4: Add a message to the User activity

In the User activity, add a message by clicking the **+** icon.

Then click **Present to user** and select **Message**.

<!-- Add screenshot here -->

## 3.5: Add the passport upload message

Click the message box you just created and add this message:

```text
To get started, please upload your passport image.
```

<!-- Add screenshot here -->

## 3.6: Add the file upload interaction

Add the **File upload** interaction to allow the user to upload their passport.

<!-- Add screenshot here -->

## 3.7: Add a Document extractor activity

After the User activity green box, click the **+** icon and add a **Document extractor** activity.

<!-- Add screenshot here -->

## 3.8: Select Structured format

Since you are going to work with an ID, select **Structured format**.

<!-- Add screenshot here -->

## 3.9: Configure the Document Extractor activity

Edit the name to:

```text
Extract Passport Details
```

Choose the following foundational model for your Document Extractor activity:

```text
mistral-smalll-3-1-24b-instruct-2503
```

> **Note**  
> You can choose a different foundational model since watsonx Orchestrate has integration with foundational model hosting platforms, such as IBM watsonx.ai, Groq, and others.  
>
> This is possible due to the use of the AI Gateway.

<!-- Add screenshot here -->

## 3.10: Define the schema

In this step, you will leverage watsonx Orchestrate because it includes several predefined schemas for different types of documents.

This is helpful and can save a lot of time when configuring the fields you need to extract.

Select **Define schema** and then select **Passport**.

<!-- Add screenshot here -->

## 3.11: Upload training passport images

Upload **Passport Image 1** and **Passport Image 2**.

These images will be used to train the document extractor.

## 3.12: Review the automatically added fields

Review all the fields added automatically by watsonx Orchestrate when you selected the predefined schema **Passport**.

Make sure you keep these fields:

- Passport number
- Full Name
- Date of birth
- Gender
- Nationality
- Date of issue
- Date of expiration

<!-- Add screenshot here -->

## 3.13: Customize the nationality field

Notice that the nationality is written in the user’s native language and you want to normalize that to English.

Hover on the **Nationality** field and click the pencil icon to customize it.

<!-- Add screenshot here -->

## 3.14: Add a description and examples

Provide a description and examples to enable the LLM to detect the nationality more accurately.

```text
Description: Detect the nationality. You will find it in a field called Nationality.

Examples:
Input: PORTUGUESA, Output: Portugal
Input: POLSKIE / POLISH, Output: Poland
Input: ESPAÑOLA, Output: Spain
```

<!-- Add screenshot here -->

## 3.15: Apply and review the changes

Click the **Show on document** button to apply the changes and observe that the output is now correct.

<!-- Add screenshot here -->

## 3.16: Review the other fields

Review the other fields to understand if you need to improve their descriptions and examples.

Everything should be okay.

**✅ Checkpoint**: The workflow can now extract structured passport details.

---

# Step 4: Configure the Conditional Logic

In this step, you are going to add a branching condition to handle different nationalities based on the extracted passport data.

The workflow can then route users with supported nationalities through a supported path while gracefully handling unsupported cases.

You’ll insert a Branch, define a condition, and then display a message for other nationalities to redirect them to human support.

## 4.1: Add Branch flow control

Add **Branch** flow control after the Document Extractor activity.

<!-- Add screenshot here -->

## 4.2: Rename the branch and paths

Rename the branch to:

```text
Nationality?
```

Click **Path 1** and rename it to:

```text
Portuguese
```

Click **Path 2** and rename it to:

```text
Other nationalities
```

<!-- Add screenshot here -->

## 4.3: Edit the Portuguese condition

Click **Edit condition** next to the Portuguese nationality path.

## 4.4: Add the nationality condition

Make the condition:

```text
nationality == Portugal
```

<!-- Add screenshot here -->

## 4.5: Add a User activity for unsupported nationalities

In the **Other nationalities** path, drag a **User activity** into the **Add+** section.

<!-- Add screenshot here -->

## 4.6: Rename the User activity

Rename the User activity to:

```text
Unsupported
```

<!-- Add screenshot here -->

## 4.7: Add a message to the User activity

Click the **+** icon on the User activity.

Then click **Present to user** and select **Message**.

<!-- Add screenshot here -->

## 4.8: Add the unsupported nationality message

Add this output message:

```text
We currently support only Portuguese nationality. For other nationalities, please visit the branch.
```

<!-- Add screenshot here -->

Your branch should look like the following:

<!-- Add screenshot here -->

**✅ Checkpoint**: The workflow can now route Portuguese and non-Portuguese users differently.

---

# Step 5: Create a Form for Human-in-the-Loop

In this step, you will collect detailed user input required for the account creation. The user input will be collected using a structured form.

This step represents a human-in-the-loop interaction, where the user actively provides personal and account-related information such as her or his name, nationality, passport number, contact details, and account type.

By including predefined options and a user-friendly layout, the form ensures that all necessary data to open an account is captured, enabling the agent to proceed with the next steps in the workflow based on the user's input.

## 5.1: Add a User activity in the Portuguese nationality branch

In the **Portuguese** nationality branch, drag a **User activity** into the **+** button.

<!-- Add screenshot here -->

## 5.2: Rename the User activity

Click the User activity and rename it to:

```text
Account Creation Request
```

<!-- Add screenshot here -->

## 5.3: Add a form

In the User activity, click the **Add+** button and then click **Add a form**.

<!-- Add screenshot here -->

## 5.4: Configure the form

Change the form name to:

```text
Account Details
```

Add the following fields.

### Present to user

1. Full Name
2. Date of Birth
3. Gender
4. Nationality
5. Passport Number
6. Date of Issue
7. Date of Expiration

### Collect from user

1. Phone Number — Text
2. Annual Income — Number
3. Account Type — Single Choice

<!-- Add screenshot here -->

## 5.5: Map extracted passport variables to the form

For the following fields, click the **x** icon next to `--Select variable--` to map them to the variable values that were extracted from the passport during the Document Extractor step:

- Full Name — `full_name`
- Date of Birth — `date_of_birth`
- Gender — `gender`
- Nationality — `nationality`
- Passport Number — `passport_number`
- Date of Issue — `date_of_issue`
- Date of Expiration — `date_of_expiration`

<!-- Add screenshot here -->

## 5.6: Configure Account Type options

For the **Account Type** field, on the Source variable, click the `</>` icon and add the variable value:

```json
["Current","Saving"]
```

<!-- Add screenshot here -->

## 5.7: Set required fields

For the **Phone Number** and **Annual Income** fields, enable the **Required field** option.

<!-- Add screenshot here -->

## 5.8: Close the form

Close the form.

Your form should have 10 fields.

<!-- Add screenshot here -->

**✅ Checkpoint**: The workflow now includes a human-in-the-loop form for account creation details.

---

# Step 6: Create a Generative Prompt

In this step, you are going to generate a personalized confirmation message using a generative AI model based on the user’s submitted account details.

The confirmation message provides a professional, human-like response that confirms the account request and sets expectations for the next steps that the user must take.

## 6.1: Add a Generative prompt activity

Click the **+** icon after the form activity.

On **Add a flow activity**, select **Generative prompt**.

<!-- Add screenshot here -->

## 6.2: Select the model

In the model drop-down, choose:

```text
GPT-OSS 120B – OpenAI (via Goq)
```

<!-- Add screenshot here -->

## 6.3: Add the System prompt

In the **System prompt**, write the following:

```text
You are an assistant that generates the final confirmation message for account creation. Your task is to take the provided user details and produce a complete, ready-to-send message. Do not provide instructions or code, only return the final text output.
```

<!-- Add screenshot here -->

## 6.4: Add the User prompt

In the **User prompt**, write the following:

```text
Generate a confirmation message using the following details:
Full Name:

The message should:

1. Start with a greeting and thanking the full name of the customer.
2. Confirm that the account request was submitted successfully.
3. Include a random 8-digit reference number.
4. State that one of our agents will call the customer at their phone number for the next steps.
5. End with the company name: AgentXBankingCo.
```

## 6.5: Add input variables

In the User prompt, add this variable:

- `full_name`

<!-- Add screenshot here -->

## 6.6: Review the Generative prompt

Your Generative prompt should look like the following:

<!-- Add screenshot here -->

## 6.7: Add test values

Give each input variable a test value, such as your name.

<!-- Add screenshot here -->

## 6.8: Generate a preview

Click **Generate Preview** to have an idea of the final response your agent will generate and send to the user at the end of the account opening process.

## 6.9: Add the confirmation message activity

Close the window and then click the **+** icon after the Generative prompt.

Add a new **User activity Message**.

<!-- Add screenshot here -->

## 6.10: Rename the confirmation message activity

Rename the User activity to:

```text
Confirmation Message
```

Then click the **x** on the Output message section to map it to your Generative prompt value.

<!-- Add screenshot here -->

## 6.11: Review the full workflow

You have now completed the entire agentic workflow.

It should look like this:

<!-- Add screenshot here -->

## 6.12: Deploy the agent

Click **Done** and deploy your agent.

## 6.13: Prepare to test

You are now ready to test your agent.

**✅ Checkpoint**: The complete Account Opening Agentic Workflow has been created and deployed.

---

# Step 7: Test Your Agent

In this step, you are going to test the full functionality of the Account Opening Agent by simulating a real user interaction through the watsonx Orchestrate chat interface.

During your tests, you need to verify that your agent behaves as expected:

- Handling document uploads
- Conditional logic
- Form pre-filling
- AI-generated responses

---

## 7.1: Test with an unsupported nationality

Click the hamburger menu and then click **Chat**.

In the Agents drop-down, select:

```text
Account Opening Agent
```

<!-- Add screenshot here -->

Click:

```text
Open a new bank account
```

Or write in the chat:

```text
I would like to open a new bank account
```

Upload **Passport Image 3**.

The agent extracts the passport details and, if the confidence is not high enough, asks the user to review the information.

Notice that the agent responds:

```text
We currently support only Portuguese nationality. For other nationalities, please visit the branch.
```

**✅ Checkpoint**: The unsupported nationality path works correctly.

---

## 7.2: Test with a supported nationality

Open a new chat and write:

```text
I would like to open a new bank account
```

Upload **Passport Image 4**.

Once again, the agent extracts the passport details.

Review the extraction from the passport and click **Submit**.

Notice that all the details are prefilled in the form.

Add the following information:

- Phone Number
- Annual Income
- Account Type

Then click **Submit**.

<!-- Add screenshot here -->

The agentic workflow generates a successful output.

<!-- Add screenshot here -->

**✅ Checkpoint**: The supported nationality path works correctly and returns a confirmation message.

---

# Congratulations 🎉 You’ve Reached the End of the Lab!

This lab guided you through building and deploying an agentic workflow using watsonx Orchestrate.

You began by creating the agent and defining its behavior, followed by designing an agentic workflow that handles passport uploads, document extraction, nationality-based branching, form collection, and AI-generated confirmation messages.

You trained the document extractor with synthetic passport images, normalized nationality values, and used conditional logic to support only Portuguese nationals.

The workflow concluded with a personalized confirmation message displayed to the user. Then, you tested the full experience in the watsonx Orchestrate chat interface, validating both supported and unsupported flows.

The value of agentic workflows is their ability to combine structured automation with flexible, human-like interactions. They allow you to orchestrate complex, multi-step processes like onboarding, document verification, and customer engagement with a no-code approach.

By integrating deterministic logic, user input, and generative AI, agentic workflows empower developers to build intelligent, responsive agents that can adapt to real-world scenarios, reduce manual effort, and improve customer experience. This approach accelerates solution delivery while maintaining transparency and control over each step in the process.

As you move forward, you can enhance your agentic workflows in watsonx Orchestrate by incorporating low-code and code features that offer developers greater flexibility and control. These include adding code blocks for custom Python logic, integrating tools, using foreach loops to iterate over lists, and applying data mapping to transform inputs and outputs.

You can also work with flow variables to manage state across the workflow, use tables with single choice for structured user input, and define complex data using the object data type.
