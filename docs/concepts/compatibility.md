# Compatibility Bridge Guide

Understanding how LiteLLM bridges the gap between Claude Code and OpenAI-compatible APIs.

## API Format Differences

### Request Format

**Anthropic (Claude Code)**:
```json
{
  "model": "claude-opus-4-8",
  "messages": [{"role": "user", "content": "Hello"}],
  "max_tokens_to_sample": 1024,
  "temperature": 0.8,
  "top_k": 40
}
```

**OpenAI (FreeLLMAPI)**:
```json
{
  "model": "gpt-4o",
  "messages": [{"role": "user", "content": "Hello"}],
  "max_tokens": 1024,
  "temperature": 0.8
}
```

## The `drop_params: true` Setting

This is the **critical** configuration that makes everything work.

### What It Does

Without `drop_params: true`:
```
Claude Code → LiteLLM → FreeLLMAPI
                         ↓
                    ERROR: Unknown parameter 'top_k'
```

With `drop_params: true`:
```
Claude Code → LiteLLM → FreeLLMAPI
                    ↓
              Parameters cleaned
                    ↓
              Success!
```

### Configuration

```yaml
litellm_settings:
  drop_params: true  # CRITICAL - enables parameter filtering
```

## Parameter Mapping

### Preserved Parameters

| Anthropic | OpenAI | Notes |
|-----------|--------|-------|
| `temperature` | `temperature` | Same meaning |
| `top_p` | `top_p` | Same meaning |
| `max_tokens` | `max_tokens` | Renamed |

### Dropped Parameters

| Parameter | Reason |
|-----------|--------|
| `top_k` | No OpenAI equivalent |
| `anthropic_version` | Anthropic-specific |
| `reasoning_effort` | Anthropic-specific |

## custom_openai Provider

`custom_openai` is a LiteLLM provider that can call **any** OpenAI-compatible API.

```yaml
general_settings:
  custom_openai:
    base_url: "http://localhost:8082"
    api_key: "YOUR_KEY"
```

## Related Documentation

- [Architecture](./architecture.md)
- [LiteLLM Configuration](../configuration/litellm.md)
