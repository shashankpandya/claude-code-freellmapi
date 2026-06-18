# Configuration Guide

Complete configuration reference for Claude Code with FreeLLMAPI and LiteLLM.

## Configuration Overview

| Component | Config File | Purpose |
|-----------|------------|---------|
| FreeLLMAPI | `.fcc_env` | Provider pool, server settings |
| LiteLLM | `litellm-config.yaml` | Model mappings, translations |
| Claude Code | Environment Variables | API endpoint, auth |

## Quick Links

| Configuration | Guide |
|--------------|-------|
| LiteLLM setup | [LiteLLM Configuration](./litellm.md) |
| FreeLLMAPI setup | [FreeLLMAPI Configuration](./freellmapi.md) |
| Providers | [Provider Setup](./providers.md) |
| Environment | [Environment Variables](./environment.md) |

## Environment Variables Quick Reference

### Claude Code

```bash
# Required
ANTHROPIC_BASE_URL=http://127.0.0.1:4000
ANTHROPIC_AUTH_TOKEN=YOUR_TOKEN
CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1
```

### LiteLLM

```bash
# Required
LITELLM_MASTER_KEY=YOUR_MASTER_KEY
```

## Common Patterns

### Pattern 1: Local Models Only

```yaml
# LiteLLM
model_list:
  - model_name: claude-opus-4-8
    litellm_params:
      model: custom_openai/mistral:latest
      api_base: "http://localhost:8082"
```

### Pattern 2: Remote API

```yaml
# LiteLLM
model_list:
  - model_name: claude-opus-4-8
    litellm_params:
      model: custom_openai/gpt-4o
      api_base: "http://localhost:8082"
```

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Config not loading | Check file paths and YAML syntax |
| Model not found | Verify model_list entries |
| Port conflicts | Change ports in config |

## Related Guides

- [LiteLLM Configuration](./litellm.md)
- [FreeLLMAPI Configuration](./freellmapi.md)
- [Provider Setup](./providers.md)
