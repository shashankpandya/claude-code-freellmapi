# Getting Started

Welcome! This section helps you get up and running quickly with Claude Code using FreeLLMAPI and LiteLLM.

## Quick Navigation

| I'm | Go To |
|-----|-------|
| New to this project | [Quick Start Guide](./quickstart.md) |
| Setting up prerequisites | [Prerequisites](./prerequisites.md) |
| Looking for installation | [Setup Overview](../setup/README.md) |
| Need troubleshooting | [Troubleshooting](../troubleshooting/common-issues.md) |

## What is This Project?

This project enables you to run **Claude Code** (Anthropic's CLI tool) using **FreeLLMAPI** and **LiteLLM** as a compatibility bridge. This allows Claude Code to work with any OpenAI-compatible API, including local models.

### Architecture Overview

```
Claude Code → LiteLLM → FreeLLMAPI → Provider Pool
                ↓            ↓
            (Translation)  (Gateway)
```

**Components:**
- **Claude Code**: User-facing application
- **LiteLLM**: Translates Anthropic ↔ OpenAI formats
- **FreeLLMAPI**: OpenAI-compatible API gateway
- **Provider Pool**: Local (Ollama, LM Studio) or Remote (OpenAI, etc.)

## Next Steps

1. **[Quick Start](./quickstart.md)** - Get running in 5 minutes
2. **[Prerequisites](./prerequisites.md)** - What you need to install
3. **[Setup Guide](../setup/README.md)** - Platform-specific instructions

## Common Use Cases

| Use Case | Guide |
|----------|-------|
| Run Claude Code with local models | [Windows Setup](../setup/windows.md) |
| Use OpenAI API as backend | [LiteLLM Configuration](../configuration/litellm.md) |
| Configure model routing | [Model Routing](../concepts/model-routing.md) |

---

Need help? See [Support](../support/README.md) or [FAQ](../troubleshooting/faq.md).
