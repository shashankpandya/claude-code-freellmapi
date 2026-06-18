# LiteLLM Configuration Guide

Complete guide to configuring LiteLLM as the compatibility bridge.

## Configuration File

**File**: `litellm-config.yaml`  
**Location**: Project root

## Minimal Configuration

```yaml
litellm_settings:
  drop_params: true

model_list:
  - model_name: claude-opus-4-8
    litellm_params:
      model: custom_openai/gpt-4o
      api_base: "http://localhost:8082"
      api_key: "YOUR_KEY"

general_settings:
  master_key: "YOUR_MASTER_KEY"
```

## Key Parameters

### litellm_settings

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `drop_params` | boolean | false | **Required**: Drop unsupported Anthropic parameters |
| `fail_on_invalid_key` | boolean | false | Fail if API key is invalid |
| `request_timeout` | integer | 600 | Request timeout (seconds) |

### model_list

| Parameter | Type | Description |
|-----------|------|-------------|
| `model_name` | string | Claude model name (user-facing) |
| `model` | string | Backend model identifier |
| `api_base` | string | FreeLLMAPI base URL |
| `api_key` | string | API key for authentication |

## Environment Variables

```bash
# In config file
LITELLM_MASTER_KEY=${LITELLM_MASTER_KEY}
LITELLM_API_KEY=${LITELLM_API_KEY}

# In shell
export LITELLM_MASTER_KEY=sk-1234567890
export LITELLM_API_KEY=freellmapi-key
```

## Startup

```bash
# Basic startup
litellm --config litellm-config.yaml --port 4000

# With debug
litellm --config litellm-config.yaml --port 4000 --debug
```

## Verification

```bash
curl http://localhost:4000/health
curl http://localhost:4000/models
```

## Troubleshooting

| Error | Solution |
|-------|----------|
| Invalid YAML | Check indentation (2 spaces, not tabs) |
| Model Not Found | Verify model in model_list |
| Connection Refused | Start FreeLLMAPI first |

## Related Documentation

- [FreeLLMAPI Configuration](./freellmapi.md)
- [Environment Variables](./environment.md)
