# Provider Setup Guide

Configure different backend providers for FreeLLMAPI.

## Supported Providers

### Local Providers

| Provider | Default Port | Description |
|----------|-------------|-------------|
| LM Studio | 8000 | Desktop app for local models |
| Ollama | 11434 | Local model runtime |

### Remote Providers

| Provider | API Type | Description |
|----------|----------|-------------|
| OpenAI | OpenAI | GPT models |
| Azure OpenAI | OpenAI | Microsoft's OpenAI |
| NVIDIA NIM | OpenAI | NVIDIA models |

## LM Studio Setup

1. Download and install from https://lmstudio.ai/
2. Download a model
3. Click "Start Server"
4. Note the port (default: 8000)

**Configuration**:
```yaml
provider_pool:
  - name: lm_studio
    base_url: "http://localhost:8000"
    provider_type: "local"
```

## Ollama Setup

1. Install: `brew install ollama` (macOS) or see https://ollama.ai/
2. Pull a model: `ollama pull llama3`
3. Start server: `ollama serve`

**Configuration**:
```yaml
provider_pool:
  - name: ollama
    base_url: "http://localhost:11434"
    provider_type: "local"
```

## OpenAI Setup

1. Get API key from https://platform.openai.com/api-keys
2. Set up billing

**Configuration**:
```yaml
provider_pool:
  - name: openai
    base_url: "https://api.openai.com/v1"
    api_key: "${OPENAI_API_KEY}"
    provider_type: "remote"
```

## Provider Pool Examples

### Example: Hybrid (Local + Remote)

```yaml
provider_pool:
  - name: ollama
    base_url: "http://localhost:11434"
    provider_type: "local"

  - name: openai
    base_url: "https://api.openai.com/v1"
    api_key: "${OPENAI_API_KEY}"
    provider_type: "remote"

settings:
  port: 8082
```

## Health Checks

```bash
# LM Studio
curl http://localhost:8000/v1/models

# Ollama
curl http://localhost:11434/api/tags
```

## Related Documentation

- [FreeLLMAPI Configuration](./freellmapi.md)
- [Model Routing](../concepts/model-routing.md)
