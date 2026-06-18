# Linux Setup Guide

Complete setup guide for Linux systems.

## Overview

**Estimated Time:** 15-20 minutes  
**Difficulty:** ⭐⭐ Intermediate

## Step 1: Install Dependencies

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install python3 python3-pip git

# Install Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
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

## Next Steps

- [Validation Guide](../validation/README.md)
- [Troubleshooting](../troubleshooting/common-issues.md)
