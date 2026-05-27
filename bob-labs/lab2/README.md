# Lab 2: Understanding, Documenting and Modifying an Existing Application with Bob

## Overview

In this lab, you'll learn how to use Bob to understand, document, and modify an existing application. Instead of building an application from scratch, you will work on a prebuilt To Do application and use Bob to explore the codebase, identify relevant files, and implement a new feature.

This reflects a very common real-world scenario, where developers often work on existing projects rather than starting from zero.

The application used in this lab corresponds to the application developed in Lab 1.

> ⚠️ Participants who completed Lab 1 can use their own application files instead of the provided ZIP file.  
> However, some visual or structural differences may exist compared to the reference screenshots used in this guide.

## Before Starting

Download the application ZIP file here. Place it somewhere easily accessible on your computer, such as:
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

[INSERT SCREENSHOT HERE — extracting ZIP file]

[INSERT SCREENSHOT HERE — opening project in Bob]

**✅ Checkpoint**: The project is now open in your workspace.

---

# Step 2: Understanding the existing application

## 2.1: Analyze the project structure

Before modifying an application, developers first need to understand:
- What the application does
- How the frontend and backend communicate
- Which files are responsible for specific features
- How the project is structured

This is where Bob becomes especially useful.

Switch to **Ask Mode** and ask Bob:

```text
Please analyze this application and explain:
1. The overall project structure
2. Which files belong to the frontend and backend
3. How the frontend communicates with the backend
4. Which files would most likely need to be modified if I wanted to add a new feature
```

[INSERT SCREENSHOT HERE — Bob explaining project structure]

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

[INSERT SCREENSHOT HERE — Bob identifying required files]

Bob should explain that this feature would likely require changes in:
- `frontend/index.html`
- `frontend/js/app.js`
- `backend/app.py`
- Possibly `frontend/css/styles.css`

Notice that Bob is not writing code yet — it is helping you understand the implementation strategy first.

This separation between planning and implementation is extremely important in real-world development workflows.

**✅ Checkpoint**: You understand which files are involved in the feature implementation.

---

# Step 4: Implementing a new feature

## 4.1: Switch to Code Mode

Now that we understand the project structure and implementation strategy, switch to **Code Mode**.

[INSERT SCREENSHOT HERE — switching to Code Mode]

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

[INSERT SCREENSHOT HERE — Bob creating task list]

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

[INSERT SCREENSHOT HERE — approval workflow]

This approval flow is important because it keeps developers in control of the generated code.

---

## 4.4: Literate Coding Mode

In some situations, Bob may automatically enter **Literate Coding Mode**.

This mode focuses on:
- Explaining code changes
- Providing implementation reasoning
- Generating more understandable code
- Improving maintainability

[INSERT SCREENSHOT HERE — literate coding mode]

This is particularly useful for:
- Learning
- Team collaboration
- Documentation
- Knowledge transfer

---

## 4.5: Apply the generated changes

Approve the generated changes and let Bob update the application files.

[INSERT SCREENSHOT HERE — applying generated changes]

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

[INSERT SCREENSHOT HERE — running the application]

Then open the frontend like you did in Lab 1.

You should now see the new feature integrated into the application.

---

## 5.2: Test the new feature

Example test:
1. Create several tasks
2. Mark some tasks as completed
3. Click the new "Delete Completed" button
4. ✅ Completed tasks should be removed

[INSERT SCREENSHOT HERE — testing the feature]

If the application does not work correctly, ask Bob to:
- Analyze the issue
- Identify the root cause
- Suggest a fix
- Apply the correction

This mirrors how developers commonly use AI assistants during real debugging workflows.

---

# Step 6: Understanding Ask Mode vs Code Mode

This lab demonstrated an important distinction between Bob modes:

| Ask Mode | Code Mode |
|---|---|
| Understands and explains code | Modifies and generates code |
| Helps with architecture analysis | Implements features |
| Suggests implementation strategies | Executes changes |
| Ideal for learning and planning | Ideal for development |

Understanding when to use each mode is one of the key productivity gains when working with Bob.

---

# Congratulations 🎉 You’ve completed Lab 2!

You’ve successfully learned how to:
- ✅ Understand an existing application using Bob
- ✅ Analyze project structure and dependencies
- ✅ Identify files involved in a feature implementation
- ✅ Use Ask Mode for architecture understanding
- ✅ Use Code Mode for feature implementation
- ✅ Review and approve generated code changes

This workflow closely reflects how AI-assisted software development is increasingly used in real enterprise environments.
