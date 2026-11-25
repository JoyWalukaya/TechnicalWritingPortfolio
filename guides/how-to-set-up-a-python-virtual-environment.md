# How to Set Up a Python Virtual Environment

A virtual environment is an isolated workspace for a single Python project. It keeps that project's packages separate from your system Python and from your other projects, so upgrading a library for one project cannot break another. This guide shows you how to create a virtual environment, activate it, install packages and share your setup with others.

## Who this guide is for

Anyone writing Python who wants clean, repeatable project setups. You do not need prior experience with virtual environments.

## Prerequisites

- Python 3.3 or later installed. Check your version by running:

  ```bash
  python --version
  ```

  If that command is not found, try `python3 --version`.
- A terminal or command prompt open in your project folder.

> Note: On macOS and Linux the command is often `python3`. On Windows it is usually `python`. Use whichever reports a version above.

## Step 1: Create the virtual environment

From inside your project folder, run:

```bash
python -m venv venv
```

In this command, `-m venv` runs Python's built in venv tool, and the final word is the name of the folder to create. So the last `venv` is the part you can change. This creates a folder that holds a private copy of Python and a place for this project's packages.

To name the folder `.venv` instead, change only the last word:

```bash
python -m venv .venv
```

A leading dot, as in `.venv`, simply hides the folder on macOS and Linux, which some people prefer. Whatever name you choose, use that same name in the activation step below.

## Step 2: Activate the environment

Activating tells your terminal to use the project's Python instead of the system one. The command depends on your operating system. These examples use the folder name `venv`. If you named yours `.venv`, replace `venv` with `.venv` in the command, for example `source .venv/bin/activate`.

**Windows (Command Prompt):**

```bash
venv\Scripts\activate
```

**Windows (PowerShell):**

```bash
venv\Scripts\Activate.ps1
```

**macOS and Linux:**

```bash
source venv/bin/activate
```

When the environment is active, your terminal prompt shows the environment name in brackets, like `(venv)`. That is how you know it worked.

## Step 3: Install packages

With the environment active, install any package using `pip`. For example:

```bash
pip install requests
```

The package is installed only inside this environment, not system wide. Your other projects are untouched.

## Step 4: Save your dependencies

To let someone else recreate your exact setup, save your installed packages to a file:

```bash
pip freeze > requirements.txt
```

This writes every package and its version into `requirements.txt`. Anyone can later install the same set with:

```bash
pip install -r requirements.txt
```

## Step 5: Deactivate when you are done

To leave the environment and return to your system Python, run:

```bash
deactivate
```

Your prompt returns to normal and the environment is no longer active.

## Deleting an environment

A virtual environment is just a folder. To remove it, delete the `venv` folder. On macOS and Linux:

```bash
rm -rf venv
```

On Windows, delete the folder from File Explorer or run:

```bash
rmdir /s venv
```

## Good practice

- Add `venv/` to your project's `.gitignore` file so the environment is not pushed to GitHub. Others recreate it from `requirements.txt` instead.
- Create one virtual environment per project.
- Activate the environment every time you work on the project.

## Summary

| Action | Command |
| --- | --- |
| Create | `python -m venv venv` |
| Activate (macOS or Linux) | `source venv/bin/activate` |
| Activate (Windows) | `venv\Scripts\activate` |
| Install a package | `pip install <name>` |
| Save dependencies | `pip freeze > requirements.txt` |
| Deactivate | `deactivate` |

With a virtual environment in place, your project is isolated, reproducible and easy to share.
