# Environment Variables Guide

Complete reference for all environment variables.

## Quick Reference

| Variable | Service | Required | Description |
|----------|---------|----------|-------------|
| `ANTHROPIC_BASE_URL` | Claude Code | ✅ | LiteLLM endpoint |
| `ANTHROPIC_AUTH_TOKEN` | Claude Code | ✅ | Authentication token |
| `CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY` | Claude Code | ✅ | Enable model discovery |
| `LITELLM_MASTER_KEY` | LiteLLM | ✅ | LiteLLM auth key |
| `FCC_PORT` | FreeLLMAPI | No | FreeLLMAPI port (default: 8082) |

## Claude Code Variables

### Required

```bash
# LiteLLM endpoint
ANTHROPIC_BASE_URL=http://127.0.0.1:4000

# Authentication token
ANTHROPIC_AUTH_TOKEN=YOUR_TOKEN

# Enable model discovery
CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1
```

### Setting

**PowerShell**:
```powershell
$env:ANTHROPIC_BASE_URL = "http://127.0.0.1:4000"
$env:ANTHROPIC_AUTH_TOKEN = "YOUR_TOKEN"
$env:CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY = "1"
```

**Linux/macOS**:
```bash
export ANTHROPIC_BASE_URL="http://127.0.0.1:4000"
export ANTHROPIC_AUTH_TOKEN="YOUR_TOKEN"
export CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1
```

## LiteLLM Variables

```bash
LITELLM_MASTER_KEY=YOUR_MASTER_KEY
```

## FreeLLMAPI Variables

```bash
FCC_PORT=8082
FCC_DEBUG=true
```

## .env File

Create a `.env` file:

```bash
# Claude Code
ANTHROPIC_BASE_URL=http://127.0.0.1:4000
ANTHROPIC_AUTH_TOKEN=YOUR_TOKEN
CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1

# LiteLLM
LITELLM_MASTER_KEY=YOUR_MASTER_KEY

# FreeLLMAPI
FCC_PORT=8082

# Providers
OPENAI_API_KEY=sk-...
```

### Loading .env

**Linux/macOS**:
```bash
set -a
source .env
set +a
```

## Security Best Practices

1. **Never commit secrets** - Add `.env` to `.gitignore`
2. **Use placeholders** - Never expose real keys in examples
3. **Rotate keys** - Change API keys periodically

## Related Documentation

- [Configuration README](./README.md)
