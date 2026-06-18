# FreeLLMAPI Configuration Guide

Complete guide to configuring FreeLLMAPI as the API gateway.

## Configuration File

**File**: `.fcc_env`  
**Location**: Project root

## Minimal Configuration

```yaml
provider_pool:
  - name: openai
    base_url: "https://api.openai.com/v1"
    api_key: "${OPENAI_API_KEY}"

settings:
  port: 8082
```

## Complete Configuration

```yaml
# Provider Pool
provider_pool:
  - name: openai
    base_url: "https://api.openai.com/v1"
    api_key: "${OPENAI_API_KEY}"
    provider_type: "remote"
    timeout: 120

# Server Settings
settings:
  port: 8082
  debug: true
  log_level: "INFO"
  health_check_interval: 30
  timeout: 60
```

## Provider Configuration

### Provider Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | Yes | Unique identifier |
| `base_url` | string | Yes | Provider API base URL |
| `provider_type` | string | No | "local" or "remote" |
| `api_key` | string | No | API key for remote providers |
| `timeout` | integer | No | Provider-specific timeout |

### Local Providers

**LM Studio**:
```yaml
- name: lm_studio
  base_url: "http://localhost:8000"
  provider_type: "local"
```

**Ollama**:
```yaml
- name: ollama
  base_url: "http://localhost:11434"
  provider_type: "local"
```

### Remote Providers

**OpenAI**:
```yaml
- name: openai
  base_url: "https://api.openai.com/v1"
  api_key: "${OPENAI_API_KEY}"
  provider_type: "remote"
```

## Startup

```bash
# Basic startup
fcc-server --config .fcc_env

# With specific port
fcc-server --port 8082

# With debug
fcc-server --debug
```

## Verification

```bash
curl http://localhost:8082/health
curl http://localhost:8082/providers
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Port in use | Change port or stop conflicting service |
| Provider connection failed | Check provider URL and API keys |
| Configuration error | Check YAML syntax |

## Related Documentation

- [LiteLLM Configuration](./litellm.md)
- [Provider Setup](./providers.md)
