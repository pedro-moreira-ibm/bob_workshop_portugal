# Lab 0: Prerequisites

This page covers the practical requisites for the Bob labs in this repository.

## What You Need

### Required for the Bob Labs

- IBM Bob access
- Python 3.8+
- Node.js 14+
- A terminal
- A local workspace where Bob can create files and run commands


## Instructions to follow before the workshop

Use the command block that matches the machine you will use during the workshop.

### Ubuntu / Debian

```bash
sudo apt-get update
sudo apt-get install -y python3 python3-pip python3-venv nodejs npm git
python3 -m pip install --upgrade pip
```

If you are using another Linux distribution, install the equivalent packages for Python 3, `pip`, `venv`, Node.js, `npm`, and Git using your distribution's package manager.

### macOS

For most attendees, the easiest macOS setup is:

1. Install Python from [python.org]([https://www.python.org/downloads/](https://www.python.org/downloads/release/python-31210/))
2. Install Node.js LTS from [nodejs.org](https://nodejs.org/)
3. Open a new terminal and run:

```bash
python3 -m pip install --upgrade pip
```

If you already use Homebrew, you can also follow the command below:

```bash
brew install python@3.11 node git
python3 -m pip install --upgrade pip
```

### Windows

For most attendees, the easiest Windows setup is:

1. Install Python from [python.org]([https://www.python.org/downloads/](https://www.python.org/downloads/release/python-31210/))
2. Install Node.js LTS from [nodejs.org](https://nodejs.org/)
3. Open a new terminal and run:

```powershell
python -m pip install --upgrade pip
```

## Verify everything was installed before starting Lab 1

Run this command:

```bash
python3 --version
python3 -m pip --version
node --version
npm --version
```

If your machine uses `python` instead of `python3`, use:

```bash
python --version
python -m pip --version
```

Run also this:
```
node --version
npm --version
```

You should be able to see the installed versions.
