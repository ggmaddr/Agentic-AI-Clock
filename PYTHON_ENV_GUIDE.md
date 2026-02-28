# Python Virtual Environment & .env Guide

## ✅ What I Just Did For You

### Step 1: Checked Your Python Version
```bash
python3 --version
# Output: Python 3.13.7
```

### Step 2: Found Existing Virtual Environment
Your project already had a `.venv` folder at `/Users/gradyta/Documents/GitHub/agents/.venv`

### Step 3: Activated the Virtual Environment
```bash
source .venv/bin/activate
```

### Step 4: Installed Required Packages
```bash
pip install python-dotenv openai pypdf gradio requests
```

**Packages installed:**
- ✅ `python-dotenv` (1.2.1) - Load environment variables from .env file
- ✅ `openai` (2.7.1) - OpenAI API client
- ✅ `pypdf` (6.7.4) - PDF reading library
- ✅ `gradio` (5.49.1) - Web UI framework
- ✅ `requests` (2.32.5) - HTTP library

### Step 5: Verified Your .env File
Your `.env` file exists with:
- `OPENAI_API_KEY` - configured ✅
- `GROQ_API_KEY` - configured ✅

---

## 📚 Complete Guide to Python Virtual Environments

### What is a Virtual Environment?
A virtual environment is an isolated Python environment that keeps your project dependencies separate from system-wide packages. This prevents version conflicts between different projects.

### What is a .env File?
A `.env` file stores environment variables (like API keys, database passwords) that you don't want to commit to version control. The `python-dotenv` package loads these variables into your Python code.

---

## 🔧 Essential Commands

### 1. Creating a New Virtual Environment

```bash
# Navigate to your project folder
cd /Users/gradyta/Documents/GitHub/agents

# Create a new virtual environment named .venv
python3 -m venv .venv
```

### 2. Activating the Virtual Environment

```bash
# On macOS/Linux
source .venv/bin/activate

# You'll see (.venv) appear in your terminal prompt:
# (.venv) user@computer:~/agents$
```

### 3. Deactivating the Virtual Environment

```bash
# Simply type:
deactivate

# The (.venv) prefix will disappear from your prompt
```

### 4. Installing Packages

```bash
# Make sure your virtual environment is activated first!
source .venv/bin/activate

# Install a single package
pip install package-name

# Install multiple packages
pip install package1 package2 package3

# Install from requirements.txt
pip install -r requirements.txt
```

### 5. Viewing Installed Packages

```bash
# List all installed packages
pip list

# Show details about a specific package
pip show package-name

# Save current packages to requirements.txt
pip freeze > requirements.txt
```

### 6. Viewing All Virtual Environments

```bash
# List all virtual environments in current directory
ls -la | grep venv

# Check which Python is being used (should point to .venv)
which python

# Check Python version
python --version
```

### 7. Switching Between Virtual Environments

```bash
# Deactivate current environment
deactivate

# Navigate to different project
cd /path/to/other/project

# Activate that project's environment
source .venv/bin/activate
```

### 8. Deleting a Virtual Environment

```bash
# First, deactivate if active
deactivate

# Then simply delete the folder
rm -rf .venv

# Or if you want to be asked for confirmation
rm -ri .venv
```

---

## 🔐 Working with .env Files

### Creating a .env File

```bash
# Create the file
touch .env

# Edit it with your favorite editor
nano .env
# or
code .env
```

### Example .env File Structure

```env
# API Keys
OPENAI_API_KEY=sk-proj-your-key-here
GROQ_API_KEY=gsk-your-key-here

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# Other settings
DEBUG=True
PORT=8000
```

### Loading .env in Python

```python
from dotenv import load_dotenv
import os

# Load environment variables from .env file
load_dotenv()

# Access the variables
api_key = os.getenv('OPENAI_API_KEY')
debug_mode = os.getenv('DEBUG', 'False')  # Default value if not found

print(f"API Key loaded: {api_key[:10]}...")  # Print first 10 chars only
```

### Important .env Security Tips

1. **Never commit .env to git!** Add it to `.gitignore`:
   ```bash
   echo ".env" >> .gitignore
   ```

2. **Create a .env.example file** for others:
   ```env
   OPENAI_API_KEY=your-key-here
   GROQ_API_KEY=your-key-here
   ```

3. **Keep different .env files** for different environments:
   - `.env.development`
   - `.env.production`
   - `.env.test`

---

## 🎯 Quick Reference Cheat Sheet

| Task | Command |
|------|---------|
| Create venv | `python3 -m venv .venv` |
| Activate venv | `source .venv/bin/activate` |
| Deactivate venv | `deactivate` |
| Install package | `pip install package-name` |
| List packages | `pip list` |
| Save packages | `pip freeze > requirements.txt` |
| Install from file | `pip install -r requirements.txt` |
| Check Python path | `which python` |
| Delete venv | `rm -rf .venv` |
| Load .env | `load_dotenv()` in Python |
| Get env variable | `os.getenv('VAR_NAME')` |

---

## 🚀 Your Current Setup

**Location:** `/Users/gradyta/Documents/GitHub/agents`

**Virtual Environment:** `.venv` (Python 3.12.11)

**Installed Packages:**
- python-dotenv 1.2.1
- openai 2.7.1
- pypdf 6.7.4
- gradio 5.49.1
- requests 2.32.5

**Environment Variables:**
- OPENAI_API_KEY ✅
- GROQ_API_KEY ✅

**To start working:**
```bash
cd /Users/gradyta/Documents/GitHub/agents
source .venv/bin/activate
python app.py
```

---

## 💡 Pro Tips

1. **Always activate your venv** before running Python scripts or installing packages
2. **Use `pip freeze > requirements.txt`** to share your dependencies with others
3. **Keep .env out of version control** but commit .env.example
4. **Name your venv consistently** (`.venv` or `venv`) across projects
5. **Update pip regularly**: `pip install --upgrade pip`
6. **Use virtual environments for every project** - never install packages globally!

---

## 🐛 Troubleshooting

### "pip: command not found"
```bash
# Try using python -m pip instead
python -m pip install package-name
```

### "Permission denied"
```bash
# Don't use sudo! Activate your venv first
source .venv/bin/activate
pip install package-name
```

### "Module not found" when running script
```bash
# Make sure venv is activated
source .venv/bin/activate
# Verify package is installed
pip list | grep package-name
```

### .env variables not loading
```python
# Make sure you call load_dotenv() before accessing variables
from dotenv import load_dotenv
import os

load_dotenv()  # This must come first!
key = os.getenv('OPENAI_API_KEY')
```

---

Happy coding! 🎉
