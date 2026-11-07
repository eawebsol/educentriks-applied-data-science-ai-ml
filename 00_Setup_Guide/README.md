# Environment Setup Guide

**Educentriks | Applied Data Science & AI/ML**  
*From Learning to Real-World Application*

This guide explains how to configure your local Python environment for the 23-day Applied Data Science & AI/ML programme.

Follow the instructions in sequence. Complete the verification steps before proceeding to the course notebooks.

---

## 1. Environment Requirements

| Component | Required version / configuration |
|---|---|
| Operating System | Windows 10/11, 64-bit |
| Python | Python 3.13.x, 64-bit |
| Code Editor | Visual Studio Code |
| Python Environment | `.venv` |
| Notebook Environment | Jupyter |
| Version Control | Git |
| Cloud Alternative | Google Colab (optional) |

### Required VS Code extensions

Install these extensions from the VS Code Extensions Marketplace:

1. Python — Microsoft
2. Jupyter — Microsoft

---

## 2. Install Python

Download Python 3.13.x from the official Python website:

https://www.python.org/downloads/

During installation:

1. Select the option to add Python to PATH, if available.
2. Complete the installation.
3. Open PowerShell.
4. Verify the installation:

```powershell
python --version
```

You should see Python 3.13.x.

Check that the Python launcher is available:

```powershell
py --version
py -0p
```

The `py -0p` command displays the installed Python versions and their locations.

**Important:** Use the 64-bit Python installation. Do not install a different Python version simply because a newer version is available.

---

## 3. Install Visual Studio Code

Download Visual Studio Code:

https://code.visualstudio.com/

Install VS Code using the recommended installation options.

Open VS Code and install the following extensions:

- Python (Microsoft)
- Jupyter (Microsoft)

These extensions provide Python execution, notebook support, debugging and interactive development capabilities.

---

## 4. Install Git

Download Git for Windows:

https://git-scm.com/downloads/win

Complete the installation using the recommended settings.

Verify the installation:

```powershell
git --version
```

Git will be used to download the student repository and retrieve course updates.

---

## 5. Download the Student Repository

Open PowerShell and navigate to the folder where you want to keep your course materials.

For example:

```powershell
cd D:\

mkdir Educentriks
cd Educentriks
```

Clone the student repository:

```powershell
git clone https://github.com/eawebsol/educentriks-applied-data-science-ai-ml.git
```

Move into the repository:

```powershell
cd educentriks-applied-data-science-ai-ml
```

Open the repository in VS Code:

```powershell
code .
```

---

## 6. Create the Python Virtual Environment

A virtual environment keeps the course libraries separate from your system-wide Python installation.

We will use `.venv` throughout this programme.

Open the VS Code terminal and confirm that you are in the student repository root.

Create the environment:

```powershell
py -3.13 -m venv .venv
```

Activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

Your terminal prompt should now display `(.venv)`.

### If PowerShell blocks environment activation

You may encounter an execution policy restriction.

For the current terminal session only, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then activate the environment again:

```powershell
.\.venv\Scripts\Activate.ps1
```

This change applies only to the current PowerShell process.

---

## 7. Upgrade pip and Install Course Libraries

With `.venv` activated, upgrade pip:

```powershell
python -m pip install --upgrade pip
```

Install the course dependencies using the requirements file provided in the repository:

```powershell
python -m pip install -r requirements-py313.txt
```

The requirements file defines the package versions selected for the course.

**Important:**

- Do not independently upgrade individual libraries during the programme.
- Do not install packages into your system-wide Python environment.
- Always activate `.venv` before installing or running course dependencies.
- If a particular day's notebook requires an additional package, follow that day's instructions.

Check for dependency conflicts:

```powershell
python -m pip check
```

---

## 8. Register the Jupyter Kernel

Register `.venv` as a Jupyter kernel:

```powershell
python -m ipykernel install --user --name ds-aiml-313 --display-name "Python 3.13 (.venv)"
```

This makes the course environment available when selecting a kernel in Jupyter notebooks.

In VS Code:

1. Open a notebook (`.ipynb` file).
2. Select **Select Kernel** in the top-right corner.
3. Choose **Python 3.13 (.venv)**.
4. Confirm that the selected kernel belongs to the course environment.

---

## 9. Verify Your Environment

Create a new Python file or run the following code in a notebook:

```python
# Verify the Python version and environment
import sys

print("Python version:", sys.version)
print("Python executable:", sys.executable)
print("Virtual environment:", sys.prefix)

# Verify core data science libraries
import numpy as np
import pandas as pd
import matplotlib
import seaborn as sns
import sklearn
import torch
import streamlit as st

print("\nLibrary verification successful")

print("NumPy:", np.__version__)
print("Pandas:", pd.__version__)
print("Matplotlib:", matplotlib.__version__)
print("Seaborn:", sns.__version__)
print("Scikit-learn:", sklearn.__version__)
print("PyTorch:", torch.__version__)
print("Streamlit:", st.__version__)
```

Confirm the following:

- Python reports version 3.13.x.
- The executable path points to your repository's `.venv` directory.
- All required imports execute without errors.
- The selected notebook kernel is Python 3.13 (.venv).

---

## 10. Daily Working Procedure

Follow this routine whenever you work on the course.

### Step 1: Open the project

Open the student repository folder in VS Code.

### Step 2: Activate the environment

```powershell
.\.venv\Scripts\Activate.ps1
```

### Step 3: Select the notebook kernel

Choose **Python 3.13 (.venv)**.

### Step 4: Open the relevant day's folder

Read that day's `README.md` before starting the notebook.

### Step 5: Follow the notebook sequence

Run the cells in order. Modify the exercises and attempt the assigned tasks independently.

### Step 6: Retrieve course updates

When updates are published, use:

```powershell
git pull
```

Do not overwrite your own work without checking for changes first.

---

## 11. Optional: Google Colab

Google Colab is an optional cloud-based notebook environment.

https://colab.research.google.com/

It can be useful when:

- Your computer has limited processing resources.
- A particular deep learning exercise requires additional computing power.
- You want to run notebooks without installing a local Python environment.

However, local VS Code and `.venv` remain the primary course environment.

Some notebooks may require additional setup when executed in Colab. Follow the relevant day's instructions.

---

## 12. Common Issues and Troubleshooting

| Issue | Suggested action |
|---|---|
| `python` is not recognised | Verify Python installation and PATH configuration. |
| `py -3.13` fails | Confirm Python 3.13 is installed and listed by `py -0p`. |
| PowerShell blocks activation | Use the current-session execution policy command in Section 6. |
| Package installation fails | Confirm `.venv` is activated and check your internet connection. |
| Jupyter cannot find the kernel | Register the kernel again using Section 8. |
| Notebook uses the wrong Python | Select Python 3.13 (.venv) from the notebook kernel menu. |
| Import error | Check the required package and install it inside `.venv`. |

If the issue persists, refer to the repository's troubleshooting materials or discuss it with your instructor.

---

## 13. Environment Setup Checklist

Before starting Day 1, confirm:

- [ ] Python 3.13.x (64-bit) installed.
- [ ] Visual Studio Code installed.
- [ ] Python and Jupyter extensions installed.
- [ ] Git installed.
- [ ] Student repository cloned successfully.
- [ ] `.venv` created and activated.
- [ ] Course dependencies installed.
- [ ] Jupyter kernel registered.
- [ ] Environment verification completed successfully.
- [ ] A sample Jupyter notebook runs without errors.

---

**You are now ready to begin the Applied Data Science & AI/ML programme.**

**Educentriks**  
*From Learning to Real-World Application*
