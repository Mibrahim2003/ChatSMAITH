# Python Version Setup Guide

## Requirements

**OpenAI Agents SDK Requirements:**
- Python 3.9 or newer (3.9, 3.10, 3.11, or 3.12)
- `openai` package version 2.x (not 1.x)

## Recommended Python Versions

- **Best: Python 3.10 or 3.11** - Most stable and widely tested
- **Good: Python 3.9 or 3.12** - Fully supported
- **Warning: Python 3.13+** - Very new, may have compatibility issues

## Setup Instructions

### Option 1: Use Python 3.10 or 3.11 (Recommended)

If you have Python 3.13 installed but want to use a more stable version:

```bash
# Check if you have Python 3.10 or 3.11 installed
python3.10 --version
python3.11 --version

# Create virtual environment with specific Python version
python3.11 -m venv .venv

# Activate virtual environment
source .venv/bin/activate  # Mac/Linux
# OR
.venv\Scripts\activate  # Windows

# Install packages
pip install -r requirements.txt
```

### Option 2: Install Python 3.11

If you don't have Python 3.10 or 3.11:

**Mac (using Homebrew):**
```bash
brew install python@3.11
python3.11 -m venv .venv
source .venv/bin/activate
```

**Windows:**
1. Download Python 3.11 from https://www.python.org/downloads/
2. Install it (check "Add Python to PATH")
3. Create venv: `python -m venv .venv`
4. Activate: `.venv\Scripts\activate`

**Linux:**
```bash
sudo apt update
sudo apt install python3.11 python3.11-venv
python3.11 -m venv .venv
source .venv/bin/activate
```

### Option 3: Use Current Python (3.13) with Warnings

If you want to proceed with Python 3.13:
- The code will warn you but allow it
- If you encounter issues, switch to Python 3.11

## Verify Your Setup

After setting up, run this in Python/Jupyter:

```python
import sys
print(f"Python version: {sys.version}")
# Should show Python 3.9, 3.10, 3.11, or 3.12
```

## Troubleshooting

### Issue: "Python version too old"
- Upgrade to Python 3.9 or newer

### Issue: "Dependency conflicts"
- Use a clean virtual environment
- Install packages in this order:
  1. `pip install openai>=2.0.0`
  2. `pip install git+https://github.com/openai/openai-agents-python.git`
  3. `pip install -r requirements.txt`

### Issue: "Module not found" after installation
- Restart your Jupyter kernel
- Verify you're using the correct Python environment
- Check: `import sys; print(sys.executable)`

