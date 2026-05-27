# Lab 2: Understanding, Documenting and Modifying an Existing Application with Bob

## Overview

In this lab, you'll learn how to use Bob to understand, document, and modify an existing application. Instead of building an application from scratch, you will work on a prebuilt application and use Bob to explore the codebase, identify relevant files, and implement a new feature.

This reflects a very common real-world scenario, where developers often work on existing projects rather than starting from zero.

The application used in this lab corresponds to the application developed in Lab 1.

> ⚠️ Participants who completed Lab 1 can use their own application files instead of the provided ZIP file.  
> However, some visual or structural differences may exist compared to the reference screenshots used in this guide.

## Before Starting

Download the application ZIP file [here](application.zip). Place it somewhere easily accessible on your computer, such as:
- Desktop
- Documents folder
- Downloads folder

You will extract and open this project in IBM Bob during the first step of the lab.

## What You'll Learn

By the end of this lab, you will:
- ✅ Use Bob to understand an unfamiliar codebase
- ✅ Learn how Bob analyzes project structure and dependencies
- ✅ Identify which files need to be modified for a feature request
- ✅ Compare Ask Mode vs Code Mode behaviors
- ✅ Understand approval workflows and auto-approvals
- ✅ Modify an existing full-stack application


# Understanding Ask Mode vs Code Mode

This lab demonstrated an important distinction between Bob modes:

| Ask Mode | Code Mode |
|---|---|
| Understands and explains code | Modifies and generates code |
| Helps with architecture analysis | Implements features |
| Suggests implementation strategies | Executes changes |
| Ideal for learning and planning | Ideal for development |

Understanding when to use each mode is one of the key productivity gains when working with Bob.

## Lab Structure

- [Set up the project](#step-1-set-up-the-project)
- [Understanding the existing application](#step-2-understanding-the-existing-application)
- [Identifying required file changes](#step-3-identifying-required-file-changes)
- [Implementing a new feature](#step-4-implementing-a-new-feature)
- [Testing the updated application](#step-5-testing-the-updated-application)

---

# Step 1: Set up the project

## 1.1: Extract and open the project

Extract the provided ZIP file and open the project folder in IBM Bob.

```text
lab2-existing-app
```
<img width="3418" height="1984" alt="image" src="https://github.com/user-attachments/assets/4f3e7f4f-3c48-4403-831e-48a855736e6a" />

**✅ Checkpoint**: The project is now open in your workspace.


---

# Step 2: Understanding the existing application

## 2.1: Analyze and document the project structure

Before modifying an application, developers first need to understand:
- What the application does
- How the frontend and backend communicate
- Which files are responsible for specific features
- How the project is structured

This is where Bob becomes especially useful.

Switch to **** and ask Bob:

```text
Please analyze this application and explain:
1. The overall project structure
2. Which files belong to the frontend and backend
3. How the frontend communicates with the backend
4. Diagram
```

<img width="3391" height="1988" alt="image" src="https://github.com/user-attachments/assets/4cfffb99-b681-4095-8852-938b4290a2d4" />

Bob will analyze the existing codebase and help you quickly understand how the application works.

This is particularly valuable when working with:
- Large projects
- Legacy applications
- Applications created by other developers
- Unfamiliar frameworks or architectures

**✅ Checkpoint**: You now understand the structure and responsibilities of the main application files.

---

# Step 3: Identifying required file changes

## 3.1: Ask Bob which files need to change

One of Bob’s strengths is helping developers identify where changes should happen before writing code.

Still in **Ask Mode**, ask Bob:

```text
If I want to add a button that deletes all completed tasks, which files would I need to modify?
```

<img width="3402" height="1971" alt="image" src="https://github.com/user-attachments/assets/763b2e0e-cd4e-41a0-8fcd-482b7d244565" />

Bob will explain what files require changes to implement this feature. Notice that no code is being written yet — Bob is just helping you understand the implementation strategy first.

This separation between planning and implementation is extremely important in real-world development workflows.

**✅ Checkpoint**: You understand which files are involved in the feature implementation.

---

# Step 4: Implementing a new feature

## 4.1: Switch to Code Mode

Now that we understand the project structure and implementation strategy, switch to **Code Mode**.

<img width="3400" height="1974" alt="image" src="https://github.com/user-attachments/assets/56230a9a-b3c7-4577-b8f8-9725ab066908" />

Unlike Ask Mode, Code Mode can:
- Modify files
- Create new code
- Refactor existing logic
- Execute commands
- Implement features directly in the project

---

## 4.2: Ask Bob to implement the feature

Ask Bob:

```text
Implement a new button that deletes all completed tasks.
Modify all necessary frontend and backend files.
```

<img width="3403" height="1976" alt="image" src="https://github.com/user-attachments/assets/9d037f17-c0ea-408a-9299-daeacefa230f" />

Bob will typically:
1. Analyze the existing codebase
2. Create a task plan
3. Identify the necessary files
4. Propose code modifications

This step demonstrates how Bob approaches multi-file changes in a structured way.

---

## 4.3: Reviewing Bob’s proposed changes

Before modifying files, Bob may ask for approval depending on your settings.

You will likely see:
- Proposed file changes
- Generated task lists
- Code diffs
- Approval buttons

This approval flow is important because it keeps developers in control of the generated code.

---

## 4.4: Apply the generated changes

Approve the generated changes and let Bob update the application files.

Once completed, Bob should modify:
- The frontend interface
- The frontend JavaScript logic
- The backend API endpoint
- Any necessary styling

**✅ Checkpoint**: Bob successfully updated the application files.

---

# Step 5: Testing the updated application

## 5.1: Run the application

Ask Bob to run the application again:

```bash
Run the backend application.
```

Then open the frontend.

You should now see the new feature integrated into the application.

---

## 5.2: Test the new feature

Example test:
1. Create several tasks
2. Mark some tasks as completed
3. Click the new "Delete Completed" button
4. ✅ Completed tasks should be removed

<img width="3782" height="2053" alt="image" src="https://github.com/user-attachments/assets/8fca3fae-fc5a-4077-949e-4c9ca5b0af3c" />

If the application does not work correctly, ask Bob to:
- Analyze the issue
- Identify the root cause
- Suggest a fix
- Apply the correction

This mirrors how developers commonly use AI assistants during real debugging workflows.

---

# Step 2: Configure the Documentation Writer Mode

In this step, you will add the Documentation Writer mode to Bob.

This mode is available in the Bob marketplace and was developed by IBM for documentation writting tasks.


## 2.1: Open the Mode marketplace in Bob

Go to **Settings** and open the **Mode** tab.

<img width="3393" height="1980" alt="image" src="https://github.com/user-attachments/assets/1ad9f355-7f25-437d-9180-6e4e90cccdad" />

## 2.2: Search for the Documentation Writer mode

Search for:

```text
Documentation Writer
```

## 2.3: Install the mode

Click **Install**.

<img width="3346" height="1855" alt="image" src="https://github.com/user-attachments/assets/a7a6bfa4-d526-4221-b56a-80552e54003d" />

When prompted for the installation scope, you have 2 options:
- Select **Global** if you regularly work with documentation. The mode will be configured across all workspaces and you can reuse it in the future.
- Select **Project** if you only plan to use it for this lab. The mode will be available only for this project.


## 2.4: Verify the mode is now available

Click on the modes tab.

<img width="3397" height="1976" alt="image" src="https://github.com/user-attachments/assets/0892c88d-c979-4e8a-a078-63e13b55f1ff" />

Check that the Documentation Writer mode is now available.

<img width="3429" height="1975" alt="image" src="https://github.com/user-attachments/assets/9d9fb209-58eb-4364-8301-53a15df1ef7c" />

**✅ Checkpoint:** The Documentation Writer mode is installed and available.


# Congratulations 🎉 You’ve completed Lab 2!

You’ve successfully learned how to:
- ✅ Understand an existing application using Bob
- ✅ Analyze project structure and dependencies
- ✅ Identify files involved in a feature implementation
- ✅ Use Ask Mode for architecture understanding
- ✅ Use Code Mode for feature implementation
- ✅ Review and approve generated code changes

This workflow closely reflects how AI-assisted software development is increasingly used in real enterprise environments.
