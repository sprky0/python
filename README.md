# Python Project Setup Guide (macOS)

This guide is intended for setting up Python projects on macOS, specifically addressing and avoiding the "externally-managed-environment" error.  This error makes me want to punch myself in the face everytime I see it by accident, so here's a guide for me to avoid doing that particular thing.

## "Externally-Managed-Environment" Errors

### Understanding the Error

The "externally-managed-environment" error occurs when you attempt to install Python packages using `pip` directly into your system's Python installation. macOS restricts modifications to this system Python for stability and security.  This certainly makes sense and I'm only /somewhat/ burned up about it.

### The Solution: Virtual Environments

Virtual environments create isolated Python environments, preventing conflicts and ensuring project dependencies are managed correctly.

## Step-by-Step Instructions

1.  **Install Python (Recommended via Homebrew):**

    * If you don't have Homebrew, install it:
        ```bash
        /bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"
        ```
    * Update Homebrew:
        ```bash
        brew update
        ```
    * Install Python 3:
        ```bash
        brew install python
        ```
    * Verify the installed Python version:
        ```bash
        python3 --version
        ```

2.  **Create a Project Directory:**

    * Choose a location for your project and create a new directory:
        ```bash
        mkdir my_python_project
        cd my_python_project
        ```

3.  **Create a Virtual Environment:**

    * Use `venv` to create a virtual environment:
        ```bash
        python3 -m venv venv
        ```
        (You can replace `venv` with a different name if you prefer.)

4.  **Activate the Virtual Environment:**

    * Activate the environment:
        ```bash
        source venv/bin/activate
        ```
    * Your terminal prompt will change to indicate the environment is active (e.g., `(venv) yourusername$`).

5.  **Install Packages:**

    * Install project dependencies using `pip`:
        ```bash
        pip install requests
        ```
        (Replace `requests` with your required packages.)

6.  **Start Coding:**

    * Create your Python files (e.g., `main.py`) and begin coding.

7.  **Deactivate the Virtual Environment:**

    * When finished, deactivate the environment:
        ```bash
        deactivate
        ```
    * Your terminal prompt will return to normal.

## Key Concepts and Best Practices

* **Virtual Environments:** Always use virtual environments for isolated project dependencies.
* **`venv`:** The standard tool for creating virtual environments in Python 3.
* **`pip`:** Use `pip` to install packages within activated virtual environments.
* **.gitignore:** Create a `.gitignore` file to exclude `venv` and other unnecessary files from version control.
* **requirements.txt:** Create a `requirements.txt` file to list project dependencies:
    ```bash
    pip freeze > requirements.txt
    ```
    * To install packages from requirements.txt:
    ```bash
    pip install -r requirements.txt
    ```

## Example Project Workflow

```bash
mkdir my_project
cd my_project
# Get a venv going
python3 -m venv venv
source venv/bin/activate
pip install {yourlibs}
touch main.py
# Now you can write your crap in `main.py`
python main.py
# Stop venv
deactivate

```

