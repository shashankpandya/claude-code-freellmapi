# Quick Start Guide

Get Claude Code running with FreeLLMAPI and LiteLLM in under 5 minutes.

## Prerequisites Check

Before starting, ensure you have:

- ✅ Python 3.8 or higher
- ✅ Node.js 16 or higher
- ✅ Git

Not sure if you have these? [Check prerequisites](./prerequisites.md)

## Step 1: Clone the Repository

```powershell
git clone https://github.com/shashankpandya/claude-code-freellmapi.git
cd claude-code-freellmapi
```

## Step 2: Start All Services

The fastest way to get started is using the combined startup script:

```powershell
.\examples\combined-startup.ps1
```

This will start:
1. FreeLLMAPI (API Gateway)
2. LiteLLM (Compatibility Bridge)
3. Set up Claude Code environment variables

## Step 3: Test Your Setup

Run the test prompts to verify everything works:

```powershell
.\examples\test-prompts.ps1
```

You should see responses from Claude Code for each prompt.

## Expected Output

```
=== Test Prompt 1: Basic Greeting ===
Response: Hello! How can I assist you today?

=== Test Prompt 2: Simple Explanation ===
Response: React hooks are functions that let you use state...

=== Test Prompt 3: Code Generation ===
Response: Here's a Python Fibonacci script:
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

## What's Next?

| Goal | Action |
|------|--------|
| Configure for Windows | [Windows Setup Guide](../setup/windows.md) |
| Configure for Linux | [Linux Setup Guide](../setup/linux.md) |
| Configure for macOS | [macOS Setup Guide](../setup/macos.md) |
| Understand the architecture | [Architecture](../concepts/architecture.md) |
| Customize configuration | [Configuration Guide](../configuration/README.md) |

## Troubleshooting

If something doesn't work:

1. **Services won't start?** Check [Common Issues](../troubleshooting/common-issues.md)
2. **Getting errors?** See [Error Reference](../troubleshooting/error-reference.md)
3. **Need help?** [Get Support](../support/README.md)

## Understanding What Happens

When you run the combined startup script:

| Component | Port | Purpose |
|-----------|------|---------|
| FreeLLMAPI | 8082 | OpenAI-compatible API gateway |
| LiteLLM | 4000 | Translates between formats |
| Claude Code | - | Connects to LiteLLM |

---

**Tip**: For a visual reference of what a successful setup looks like, see the [Setup Showcase](../setup/showcase.md).
