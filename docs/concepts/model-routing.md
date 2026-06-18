# Model Routing Guide

Understanding how model names are mapped between Claude Code and backend providers.

## Overview

Model routing maps Claude-style model names to actual backend models so Claude Code can work with any OpenAI-compatible API.

## How It Works

Claude Code uses Anthropic model names:
```
claude-opus-4-8
claude-sonnet-4-0
claude-3-5-haiku
```

LiteLLM maps these to OpenAI model names:
```
gpt-4o
gpt-4o-mini
gpt-4o-mini
```

## Standard Model Mappings

### Claude 4 Models

| Claude Model | OpenAI Equivalent | Use Case |
|------------|-------------------|----------|
| `claude-opus-4-8` | `gpt-4o` | Maximum capability |
| `claude-sonnet-4-0` | `gpt-4o-mini` | Balanced |

### Claude 3 Models

| Claude Model | OpenAI Equivalent |
|------------|-------------------|
| `claude-3-opus-20240229` | `gpt-4` |
| `claude-3-sonnet-20240229` | `gpt-4-turbo` |
| `claude-3-5-haiku` | `gpt-4o-mini` |

## Configuration

### Basic Model Mapping

```yaml
model_list:
  - model_name: claude-opus-4-8
    litellm_params:
      model: custom_openai/gpt-4o
      api_base: "http://localhost:8082"
      api_key: "YOUR_KEY"
```

### Local Model Mapping

```yaml
model_list:
  - model_name: claude-opus-4-8
    litellm_params:
      model: custom_openai/neural-chat:7b
      api_base: "http://localhost:8000"  # LM Studio
```

## Best Practices

1. **Consistent Naming**: Use clear, descriptive names
2. **Document Mappings**: Comment your configuration
3. **Test Mappings**: Verify models work as expected

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Model Not Found | Check model_list entries |
| Wrong Model Called | Verify litellm_params.model |
| No Response | Check API key and connectivity |

## Related Documentation

- [Architecture](./architecture.md)
- [LiteLLM Configuration](../configuration/litellm.md)
