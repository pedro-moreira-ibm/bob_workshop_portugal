# Lab 0: Bob Labs Prerequisites

This page covers the practical setup for the Bob labs in this repository.

## What You Need

### Required for the Bob Labs

- **IBM Bob access**
- **Python 3.8+**
- **Node.js 14+**
- **A terminal**
- **A local workspace where Bob can create files and run commands**

### Recommended for Beginners

If you are not used to development tools yet, use the official installers for Windows or macOS instead of a package manager. That is the simplest path for first-time attendees.

- Python: [https://www.python.org/downloads/](https://www.python.org/downloads/)
- Node.js LTS: [https://nodejs.org/](https://nodejs.org/)
- Git: [https://git-scm.com/downloads](https://git-scm.com/downloads)

For Windows, when installing Python, make sure you enable **Add Python to PATH** before clicking **Install Now**.

You do not need Visual Studio Code for these labs. You will work in Bob.

### Needed Only for Specific Steps

- **Git**
  Required for `bob-labs/lab1` if you want to complete the local git and GitHub integration steps.

- **GitHub account**
  Needed for `bob-labs/lab1` if you want to create and push to a GitHub repository.

- **GitHub MCP configured in Bob**
  Needed for `bob-labs/lab1` if your workshop setup includes the GitHub MCP workflow.

## Commands To Run Before The Workshop

Use the command block that matches the machine you will use during the workshop.

### Ubuntu / Debian / TechZone VM

```bash
sudo apt-get update
sudo apt-get install -y python3 python3-pip python3-venv nodejs npm git
python3 -m pip install --upgrade pip
```

### macOS with Homebrew

```bash
brew install python@3.11 node git
python3 -m pip install --upgrade pip
```

### Windows

For most attendees, the easiest Windows setup is:

1. Install Python from [python.org](https://www.python.org/downloads/)
2. Install Node.js LTS from [nodejs.org](https://nodejs.org/)
3. Install Git from [git-scm.com](https://git-scm.com/downloads)
4. Close and reopen your terminal
5. Run:

```powershell
python -m pip install --upgrade pip
```

If you already use `winget`, Chocolatey, or another package manager, that is also fine, but it is not required for this workshop.

## Before The Workshop Starts

Make sure you can do all of the following without errors:

1. Open Bob successfully.
2. Open a terminal on your machine.
3. Open a folder where you can create files.
4. Run the verification commands below.

## Verify Everything Before Lab 1

Run these commands before the workshop starts:

```bash
python3 --version
python3 -m pip --version
node --version
npm --version
git --version
```

If your machine uses `python` instead of `python3`, use:

```bash
python --version
python -m pip --version
```

Optional virtual environment smoke test:

```bash
python3 -m venv bob-lab-venv
```

If `python3` is not available on your machine, run `python -m venv bob-lab-venv` instead.

If that command succeeds, your Python environment is ready for Lab 1. You can delete the `bob-lab-venv` folder afterward.

Optional Bob workspace smoke test:

1. Open Bob in an empty folder.
2. Ask Bob to create a file named `hello.txt`.
3. Confirm the file appears in your workspace.

If that works, the local workspace permissions are ready for the Bob labs.

## Only If You Will Do The GitHub Part Of Lab 1

After Git is installed, set your name and email once:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list
```

If you do not plan to do the GitHub portion of Lab 1, you can skip this.

## Why These Are Needed

### Bob Lab 1

This lab builds a Flask backend and a JavaScript frontend, then optionally goes through git and GitHub integration.

Used in the lab:
- Python virtual environment creation
- Python package installation
- Running a Flask app
- JavaScript/frontend work
- Optional git initialization, commit, and GitHub push flow

### Bob Lab 2

This lab runs a Python source script and a JavaScript translation.

Used in the lab:
- Running Python locally
- Running `npm install`
- Running Node.js locally

### Final Bob with watsonx Orchestrate Lab

This lab uses Bob for local project work before importing assets into watsonx Orchestrate.

Used in the lab:
- Python project setup
- Python virtual environment creation
- Installing the watsonx Orchestrate ADK during the lab
- Installing the watsonx Orchestrate documentation MCP inside Bob during the lab

You do not need to preinstall the watsonx Orchestrate ADK for this workshop. The final lab covers that step.

## Good To Have, But Not Required

- Basic Python familiarity
- Basic JavaScript familiarity
- Basic Git familiarity
- Basic REST/API concepts
- General comfort using a terminal

These help participants move faster, but they are not strict prerequisites.
