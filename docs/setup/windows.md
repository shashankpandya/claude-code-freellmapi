# Windows Setup Guide

Complete setup guide for Windows using PowerShell.

## Overview

**Estimated Time:** 15-20 minutes  
**Difficulty:** ⭐ Beginner

## Step 1: Install Dependencies

### 1. Install Python
1. Download from https://www.python.org/downloads/
2. Run installer, check "Add Python to PATH"
3. Verify: `python --version`

### 2. Install Node.js
1. Download from https://nodejs.org/ (LTS)
2. Verify: `node --version`

### 3. Install Git
```powershell
winget install Git.Git
```

## Step 2: Install Components

```powershell
# LiteLLM
pip install litellm

# FreeLLMAPI
npm install -g freellmapi
```

## Step 3: Clone Repository

```powershell
git clone https://github.com/shashankpandya/claude-code-freellmapi.git
cd claude-code-freellmapi
```

## Step 4: Configure

```powershell
# Copy config files
Copy-Item "examples\litellm-config.yaml" "litellm-config.yaml"
```

## Step 5: Start Services

```powershell
.\examples\combined-startup.ps1
```

## Step 6: Verify

```powershell
Invoke-WebRequest http://localhost:8082/health
Invoke-WebRequest http://localhost:4000/health
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Port in use | `netstat -ano \| findstr :8082` |
| Execution policy | `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` |

## Next Steps

- [Validation Guide](../validation/README.md)
- [Troubleshooting](../troubleshooting/common-issues.md)
