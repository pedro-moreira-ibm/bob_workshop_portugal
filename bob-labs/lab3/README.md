# Lab 3: Security Analysis & Code Fixes with Bob

## Overview

In this lab, you'll use Bob to analyze an existing application, identify security vulnerabilities and implement fixes. 

You'll learn how Bob recognizes common security issues like SQL injection, XSS and hardcoded secrets and then use Bob's different modes to fix them.

> 🔍 **Bob Findings: Automated Security Analysis in Action**  
> This lab showcases **Bob Findings**, Bob’s automated security and code quality analysis engine.  
>
> Bob Findings provides continuous, proactive analysis with severity ratings, actionable remediation guidance, and practical code examples. It’s like having a security expert reviewing your code in real time, providing clear recommendations and proactive insights to reduce risk, improve code quality, and minimize technical debt.

## What You'll Analyze

You will work with a vulnerable application that contains intentional security flaws, including:

- SQL injection vulnerabilities in database queries
- Cross-Site Scripting (XSS) in frontend code
- Hardcoded secrets and credentials
- Missing input validation
- Insecure error handling

## Lab Structure

- [Code Exploration with Ask Mode](#step-1-code-exploration-with-ask-mode)
- [Bug Identification with Plan Mode](#step-2-bug-identification-with-plan-mode)
- [Security Vulnerability Deep Dive](#step-3-security-vulnerability-deep-dive)
- [Implementing Fixes with Code Mode](#step-4-implementing-fixes-with-code-mode)

---

# Step 1: Code Exploration with Ask Mode

## 1.1: Download the vulnerable app

The [`vulnerable-app/`](vulnerable-app/) directory contains an application with intentional security issues.

Download or open the vulnerable application in your local workspace.

**✅ Checkpoint**: The vulnerable application is available in your workspace.

---

## 1.2: Understand the vulnerable codebase

Before fixing security issues, it is important to understand how the application is structured and where potential vulnerabilities may exist.

You will use Bob to explore both the backend and the frontend code.

---

## 1.3: Switch to Ask Mode

Open Bob and switch to **Ask Mode**.

Ask Mode is useful when you want Bob to explain, analyze, or reason about code without modifying files.

> 💡 **Key Learning**  
> Ask Mode is perfect for understanding unfamiliar code and getting explanations of how things work.

---

## 1.4: Explore the backend

Ask Bob:

```text
Please analyze the code in lab3/vulnerable-app/backend/ and explain:
1. What is the overall structure of the application?
2. How are database queries constructed?
3. How is user input handled?
4. What security measures are in place?
```

Bob should identify:

- A Flask application with REST API endpoints
- Direct string concatenation or formatting in SQL queries
- Hardcoded database credentials
- Missing input validation
- Limited or insecure security controls

**✅ Checkpoint**: You understand the backend structure and where security risks may exist.

---

## 1.5: Explore the frontend

Ask Bob:

```text
Analyze the frontend code in lab3/vulnerable-app/frontend/ and explain:
1. How is user input displayed in the UI?
2. Are there any DOM manipulation methods that could be risky?
3. How is data from the API rendered?
```

Bob should identify:

- Use of `innerHTML` for rendering user content
- No input sanitization
- Direct insertion of user data into the DOM
- Potential XSS risks

**✅ Checkpoint**: You understand how the frontend renders user-generated content.

---

## 1.6: Ask about specific functions

Ask Bob:

```text
Explain the search_todos() function in app.py.
What does it do and are there any security concerns?
```

Bob should explain that the function uses string formatting to build SQL queries, which makes it vulnerable to SQL injection attacks.

**✅ Checkpoint**: You have identified a specific vulnerable backend function.

---

# Step 2: Bug Identification with Plan Mode

Now let's use **Plan Mode** to systematically identify all the issues and create a structured remediation plan.

## 2.1: Switch to Plan Mode

Change from **Ask Mode** to **Plan Mode**.

> 💡 **Key Learning**  
> Plan Mode is useful for analysis, planning, and creating structured approaches to complex problems.  
>
> The generated to-do list serves as your roadmap for the implementation phase.

---

## 2.2: Request a security analysis

> 💡 **Using Bob Findings**  
> Bob Findings can automatically scan your code for security vulnerabilities, code quality issues, and compliance violations.  
>
> The analysis you're about to request demonstrates Bob's security vulnerability detection capabilities, which go beyond basic static analysis by providing context-aware recommendations.

Ask Bob:

```text
Analyze the codebase in lab3/vulnerable-app/ for security vulnerabilities.
Create a comprehensive report including:
1. List of all security issues found
2. Severity rating for each issue (Critical/High/Medium/Low)
3. Potential impact of each vulnerability
4. Recommended fix for each issue
5. Priority order for fixes
```

Bob should provide a structured analysis similar to this:

```text
SECURITY ANALYSIS REPORT
========================

CRITICAL ISSUES:
1. Hardcoded Database Credentials (config.py)
   - Impact: Full database access if code is exposed
   - Fix: Use environment variables
   - Priority: 1

2. SQL Injection (app.py, search_todos function)
   - Impact: Unauthorized data access, data manipulation
   - Fix: Use parameterized queries
   - Priority: 1

HIGH ISSUES:
3. Cross-Site Scripting (app.js, displayTodo function)
   - Impact: Script injection, session hijacking
   - Fix: Use textContent instead of innerHTML
   - Priority: 2

MEDIUM ISSUES:
4. Missing Input Validation
   - Impact: Invalid data in database
   - Fix: Add validation middleware
   - Priority: 3
```

**✅ Checkpoint**: You have a structured overview of the main security vulnerabilities.

---

## 2.3: Create a fix plan

Ask Bob:

```text
Based on the security analysis, create a detailed plan for fixing these issues.
Include:
1. Order of fixes, from most critical first
2. Files that need to be modified
3. Specific code changes required
4. Testing strategy
```

Bob should create a detailed to-do list with the fixes needed.

This demonstrates Bob's ability to break down complex problems into actionable steps.

> ⚠️ **Important**  
> Review the to-do list Bob created, but do not implement the fixes yet.  
>
> First, you will examine each vulnerability type in detail in the next step. This ensures you understand what you are fixing and why.

**✅ Checkpoint**: You have a clear remediation plan before modifying the code.

---

# Step 3: Security Vulnerability Deep Dive

This step provides a detailed explanation of each vulnerability type.

If you are already familiar with these security concepts, you can skip directly to [Step 4: Implementing Fixes with Code Mode](#step-4-implementing-fixes-with-code-mode).

## What you'll learn in this deep dive

- How SQL injection attacks work
- How XSS vulnerabilities can be exploited
- Why hardcoded secrets are dangerous
- Best practices for secure coding

---

## 3.1: SQL injection vulnerability

**Location:**

```text
vulnerable-app/backend/app.py
```

Vulnerable code:

```python
@app.route('/api/todos/search', methods=['GET'])
def search_todos():
    query = request.args.get('q')
    # VULNERABLE: Direct string formatting in SQL
    sql = f"SELECT * FROM todos WHERE title LIKE '%{query}%'"
    results = db.session.execute(sql)
    return jsonify([dict(row) for row in results])
```

### The problem

An attacker could send a malicious query such as:

```text
?q='; DROP TABLE todos; --
```

This could result in a SQL statement like:

```sql
SELECT * FROM todos WHERE title LIKE '%'; DROP TABLE todos; --%'
```

This is dangerous because the attacker-controlled input becomes part of the SQL query.

A successful SQL injection attack can lead to:
- Unauthorized data access
- Data modification
- Data deletion
- Full database compromise

**✅ Key takeaway**: User input should never be inserted directly into SQL queries. Use parameterized queries instead.

---

## 3.2: Cross-Site Scripting vulnerability

**Location:**

```text
vulnerable-app/frontend/app.js
```

Vulnerable code:

```javascript
function displayTodo(todo) {
    const todoElement = document.createElement('div');

    // VULNERABLE: innerHTML with user content
    todoElement.innerHTML = `
        <h3>${todo.title}</h3>
        <p>${todo.description}</p>
    `;

    document.getElementById('todo-list').appendChild(todoElement);
}
```

### The problem

An attacker could create a todo with the following title:

```html
<img src=x onerror="alert('XSS Attack!')">
```

If this content is inserted using `innerHTML`, the browser may execute it as code.

This is dangerous because an attacker may be able to:
- Execute malicious JavaScript
- Steal session data
- Modify the page content
- Redirect users to malicious websites

**✅ Key takeaway**: Avoid using `innerHTML` with user-generated content. Prefer safe DOM manipulation methods such as `textContent`.

---

## 3.3: Hardcoded secrets vulnerability

**Location:**

```text
vulnerable-app/backend/config.py
```

Vulnerable code:

```python
# VULNERABLE: Hardcoded credentials
DATABASE_URL = "postgresql://admin:SuperSecret123@localhost/todos"
API_KEY = "sk_live_abc123xyz789"
SECRET_KEY = "my-secret-key-12345"
```

### The problem

Hardcoded secrets are dangerous because:

- Credentials are visible in source code
- Anyone with code access may gain access to sensitive systems
- Credentials cannot be changed without code changes
- Different environments may accidentally share the same credentials
- Secrets may be exposed if the repository is pushed publicly

**✅ Key takeaway**: Secrets should be stored in environment variables, not directly in source code.

---

# Step 4: Implementing Fixes with Code Mode

Now let's fix the vulnerabilities using Bob's Code Mode.

## 4.1: Switch to Code Mode

Change to **Code Mode**.

Code Mode can:
- Modify files
- Create new code
- Refactor existing logic
- Apply fixes directly to the project

---

## 4.2: Fix the SQL injection vulnerability

Ask Bob:

```text
Fix the SQL injection vulnerability in vulnerable-app/backend/app.py.
Replace the string formatting with parameterized queries using SQLAlchemy.
```

Before:

```text
Location: vulnerable-app/backend/app.py
```

```python
@app.route('/api/todos/search', methods=['GET'])
def search_todos():
    query = request.args.get('q')
    sql = f"SELECT * FROM todos WHERE title LIKE '%{query}%'"
    results = db.session.execute(sql)
    return jsonify([dict(row) for row in results])
```

After:

```text
Location: vulnerable-app/backend/app.py
```

```python
from sqlalchemy import text

@app.route('/api/todos/search', methods=['GET'])
def search_todos():
    query = request.args.get('q', '')

    sql = text("SELECT * FROM todos WHERE title LIKE :query")
    results = db.session.execute(sql, {"query": f"%{query}%"})

    return jsonify([dict(row) for row in results])
```

**✅ Checkpoint**: SQL queries now use parameterized input instead of direct string formatting.

---

## 4.3: Fix the Cross-Site Scripting vulnerability

Ask Bob:

```text
Fix the XSS vulnerability in vulnerable-app/frontend/app.js.
Replace innerHTML usage with safe DOM manipulation using textContent.
Update all functions that display user-generated content.
```

Before:

```text
Location: vulnerable-app/frontend/app.js
```

```javascript
function displayTodo(todo) {
    const todoElement = document.createElement('div');

    todoElement.innerHTML = `
        <h3>${todo.title}</h3>
        <p>${todo.description}</p>
    `;

    document.getElementById('todo-list').appendChild(todoElement);
}
```

After:

```text
Location: vulnerable-app/frontend/app.js
```

```javascript
function displayTodo(todo) {
    const todoElement = document.createElement('div');

    const title = document.createElement('h3');
    title.textContent = todo.title;

    const description = document.createElement('p');
    description.textContent = todo.description;

    todoElement.appendChild(title);
    todoElement.appendChild(description);

    document.getElementById('todo-list').appendChild(todoElement);
}
```

**✅ Checkpoint**: User-generated content is now rendered safely using `textContent`.

---

## 4.4: Fix the hardcoded secrets vulnerability

Ask Bob:

```text
Fix the hardcoded secrets in vulnerable-app/backend/config.py.
1. Move secrets to environment variables
2. Create a .env.example file with placeholder values
3. Add python-dotenv to requirements.txt
4. Update the code to load from environment
```

Before:

```text
Location: vulnerable-app/backend/config.py
```

```python
# VULNERABLE: Hardcoded credentials
DATABASE_URL = "postgresql://admin:SuperSecret123@localhost/todos"
API_KEY = "sk_live_abc123xyz789"
SECRET_KEY = "my-secret-key-12345"
```

After:

```text
Location: vulnerable-app/backend/config.py
```

```python
import os
from dotenv import load_dotenv

load_dotenv()

DATABASE_URL = os.getenv("DATABASE_URL")
API_KEY = os.getenv("API_KEY")
SECRET_KEY = os.getenv("SECRET_KEY")
```

Create a `.env.example` file:

```text
DATABASE_URL=postgresql://username:password@localhost/database_name
API_KEY=your_api_key_here
SECRET_KEY=your_secret_key_here
```

Add `python-dotenv` to `requirements.txt`:

```text
python-dotenv
```

**✅ Checkpoint**: Secrets are now loaded from environment variables instead of being hardcoded.

---

> 🎯 **Bob Findings in Action**  
> In this lab, you experienced Bob's automated security analysis capabilities.  
>
> Bob Findings continuously monitors your code for vulnerabilities and provides actionable remediation guidance. This proactive approach helps you catch security issues before they reach production, reducing risk and technical debt.

---

# Congratulations 🎉 You’ve completed Lab 3!

You’ve successfully learned how to:

- ✅ Use Ask Mode to understand existing code
- ✅ Use Plan Mode to identify bugs and plan fixes
- ✅ Find and fix hardcoded secrets and credentials
- ✅ Implement security fixes
- ✅ Apply secure coding best practices
