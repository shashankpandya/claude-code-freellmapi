# Architecture Guide

Detailed explanation of the Claude Code + FreeLLMAPI + LiteLLM architecture.

## Overview

This system uses a layered architecture with three main components that work together.

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                    Claude Code                                   │
│                  (User Application)                              │
│                                                                 │
│  • Sends requests in Anthropic format                          │
│  • Receives responses in Anthropic format                       │
└─────────────────────────────┬───────────────────────────────────┘
                              │ HTTP Requests
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                         LiteLLM                                  │
│                    (Compatibility Bridge)                        │
│                                                                 │
│  • Translates Anthropic → OpenAI format                         │
│  • Maps model names (claude-opus-4-8 → gpt-4o)                │
│  • Filters unsupported parameters                               │
│  • Translates responses back to Anthropic format                │
└─────────────────────────────┬───────────────────────────────────┘
                              │ HTTP Requests (OpenAI format)
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                        FreeLLMAPI                               │
│                      (API Gateway)                               │
│                                                                 │
│  • Provides OpenAI-compatible API                                │
│  • Manages provider pool                                       │
│  • Handles load balancing                                      │
│  • Monitors provider health                                    │
└─────────────────────────────┬───────────────────────────────────┘
                              │
              ┌───────────────┼───────────────┐
              ▼               ▼               ▼
       ┌───────────┐   ┌───────────┐   ┌───────────┐
       │LM Studio  │   │  Ollama   │   │  OpenAI  │
       │  :8000    │   │  :11434   │   │   API    │
       └───────────┘   └───────────┘   └───────────┘
```

## Component Details

### Claude Code

**Role**: User-facing CLI application

**Key Responsibilities**:
- Interact with users via command-line interface
- Send requests in Anthropic API format
- Handle streaming responses

**Environment Variables**:
```bash
ANTHROPIC_BASE_URL=http://127.0.0.1:4000
ANTHROPIC_AUTH_TOKEN=sk-...
CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1
```

### LiteLLM

**Role**: Compatibility bridge/translation layer

**Key Responsibilities**:
- Translate request format (Anthropic ↔ OpenAI)
- Map Claude model names to backend models
- Filter unsupported parameters
- Handle API key routing

**Critical Configuration**:
```yaml
litellm_settings:
  drop_params: true  # CRITICAL: Removes unsupported params
```

### FreeLLMAPI

**Role**: OpenAI-compatible API gateway

**Key Responsibilities**:
- Provide OpenAI-style endpoints
- Manage pool of backend providers
- Load balance across providers
- Health monitoring

**Default Port**: 8082

## Parameter Translation

| Claude Parameter | OpenAI Parameter | Notes |
|----------------|-----------------|-------|
| `max_tokens_to_sample` | `max_tokens` | Renamed |
| `temperature` | `temperature` | Preserved |
| `top_p` | `top_p` | Preserved |
| `top_k` | ❌ | **Dropped** (no OpenAI equivalent) |
| `system_prompt` | `system` | Format change |
| `stop_sequences` | `stop` | Renamed |

## Configuration Requirements

| Component | Must Have |
|-----------|-----------|
| **LiteLLM** | `drop_params: true` |
| **LiteLLM** | Model mappings in `model_list` |
| **FreeLLMAPI** | Provider pool configured |
| **Claude Code** | `ANTHROPIC_BASE_URL` pointing to LiteLLM |

## Related Documentation

- [Model Routing](./model-routing.md)
- [Configuration](../configuration/README.md)
- [Troubleshooting](../troubleshooting/common-issues.md)
