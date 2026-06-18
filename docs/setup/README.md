# Setup Guides

Step-by-step instructions for setting up Claude Code with FreeLLMAPI and LiteLLM on your platform.

## Choose Your Platform

| Platform | Guide | Difficulty |
|----------|-------|------------|
| Windows | [Windows Setup](./windows.md) | ⭐ Beginner |
| Linux | [Linux Setup](./linux.md) | ⭐⭐ Intermediate |
| macOS | [macOS Setup](./macos.md) | ⭐⭐ Intermediate |

## Quick Setup (All Platforms)

```powershell
# 1. Clone repository
git clone https://github.com/shashankpandya/claude-code-freellmapi.git
cd claude-code-freellmapi

# 2. Install components (in their own directories)
# FreeLLMAPI: npm install -g freellmapi
# LiteLLM: pip install litellm

# 3. Start services
.\examples\combined-startup.ps1

# 4. Test
.\examples\test-prompts.ps1
```

## Setup Steps Overview

1. **Install Prerequisites** - Python, Node.js, Git
2. **Install Components** - FreeLLMAPI, LiteLLM
3. **Configure** - Create config files
4. **Start Services** - Run startup scripts
5. **Validate** - Test with provided scripts

## Detailed Platform Guides

| Platform | Guide |
|----------|-------|
| Windows | [Windows Setup Guide](./windows.md) |
| Linux | [Linux Setup Guide](./linux.md) |
| macOS | [macOS Setup Guide](./macos.md) |

## Visual Reference

👉 [Setup Showcase](./showcase.md) - See what successful setup looks like

## Next Steps After Setup

1. [Validate Setup](../validation/README.md)
2. [Configure Models](../concepts/model-routing.md)
3. [Troubleshoot Issues](../troubleshooting/README.md)
