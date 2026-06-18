# macOS Setup Guide

Complete setup guide for macOS systems.

## Overview

**Estimated Time:** 15-20 minutes  
**Difficulty:** ⭐⭐ Intermediate

## Step 1: Install Dependencies

```bash
# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Python and Node.js
brew install python3 node

# Git is usually pre-installed
```

## Step 2: Install Components

```bash
pip3 install litellm
npm install -g freellmapi
```

## Step 3: Clone Repository

```bash
git clone https://github.com/shashankpandya/claude-code-freellmapi.git
cd claude-code-freellmapi
```

## Step 4: Configure

```bash
cp examples/litellm-config.yaml litellm-config.yaml
```

## Step 5: Start Services

```bash
chmod +x examples/*.sh
./examples/combined-startup.sh
```

## Step 6: Verify

```bash
curl http://localhost:8082/health
curl http://localhost:4000/health
```

## Apple Silicon Notes

If using M1/M2/M3, you may need Rosetta 2:
```bash
softwareupdate --install-rosetta
```

## Next Steps

- [Validation Guide](../validation/README.md)
- [Troubleshooting](../troubleshooting/common-issues.md)
