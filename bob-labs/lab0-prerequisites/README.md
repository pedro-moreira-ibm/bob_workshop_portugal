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

1. Install Python from [python.org](https://www.python.org/downloads/release/python-31210/)

<img width="3572" height="1904" alt="image" src="https://github.com/user-attachments/assets/2bdc4d7f-dc7a-452f-8fcd-b0f5286d17f4" />

2. Install Node.js LTS from [nodejs.org](https://nodejs.org/en/download)

<img width="3494" height="1942" alt="image" src="https://github.com/user-attachments/assets/667bf7e4-ed01-4e96-b640-5bb3d54c1751" />

3.  Open a new terminal and run:

```bash
python3 -m pip install --upgrade pip
```


### Windows

For most attendees, the easiest Windows setup is:

1. Install Python from [python.org](https://www.python.org/downloads/release/pymanager-262/)

<img width="3566" height="1884" alt="image" src="https://github.com/user-attachments/assets/40998d9c-79ff-4667-9e6c-298e4fa4be1d" />

2. Install Node.js LTS from [nodejs.org](https://nodejs.org/en/download)

<img width="3157" height="1931" alt="image" src="https://github.com/user-attachments/assets/33622ea0-bd89-420d-9026-0f6a2645fd0b" />

**Do not select this box when prompted, it is not necessary for the labs**

<img width="723" height="560" alt="image" src="https://github.com/user-attachments/assets/baee77c6-028c-485d-8226-4ef48acfa0ab" />

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
