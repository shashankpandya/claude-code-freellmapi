# Setup Showcase

Visual reference for a successful Claude Code + FreeLLMAPI + LiteLLM setup.

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                     CLAUDE CODE                                  │
│                    (Anthropic API)                              │
│                                                                 │
│  Environment Variables:                                        │
│  • ANTHROPIC_BASE_URL=http://127.0.0.1:4000                   │
│  • ANTHROPIC_AUTH_TOKEN=sk-...                                 │
│  • CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1                │
└────────────────────────────┬───────────────────────────────────┘
                             │ HTTP (Anthropic format)
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                     LITELLM (:4000)                              │
│  • Translates Anthropic → OpenAI format                         │
│  • Model mapping (claude-opus-4-8 → gpt-4o)                    │
│  • Drops unsupported parameters (top_k, etc.)                  │
└────────────────────────────┬───────────────────────────────────┘
                             │ HTTP (OpenAI format)
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                   FREELLMAPI (:8082)                              │
│  • OpenAI-compatible API gateway                                 │
│  • Provider pool management                                     │
│  • Load balancing across providers                              │
└────────────────────────────┬───────────────────────────────────┘
                             │
         ┌───────────────────┼───────────────────┐
         ▼                   ▼                   ▼
   ┌───────────┐      ┌───────────┐      ┌───────────┐
   │  LM Studio│      │  Ollama   │      │  OpenAI  │
   │   :8000   │      │  :11434   │      │  API     │
   └───────────┘      └───────────┘      └───────────┘
```

## Service Ports

| Service | Port | Protocol | Purpose |
|---------|------|----------|---------|
| FreeLLMAPI | 8082 | HTTP | OpenAI-compatible API gateway |
| LiteLLM | 4000 | HTTP | Compatibility bridge |
| LM Studio | 8000 | HTTP | Local model inference |
| Ollama | 11434 | HTTP | Local model inference |

## Success Indicators

| Check | Command | Expected Output |
|-------|---------|----------------|
| FreeLLMAPI | `curl http://localhost:8082/health` | `{"status": "ok"}` |
| LiteLLM | `curl http://localhost:4000/health` | `200 OK` |
| Models | `curl http://localhost:4000/models` | List of models |
| Test | `.\examples\test-prompts.ps1` | Responses received |

## Expected File Structure

```
project-root/
├── litellm-config.yaml      # LiteLLM model mappings
├── .fcc_env                  # FreeLLMAPI configuration
├── docs/                     # Documentation
├── examples/                 # Startup scripts
│   ├── start-freellmapi.ps1
│   ├── start-litellm.ps1
│   ├── start-claude.ps1
│   └── test-prompts.ps1
└── ...
```

---

For more details, see:
- [Architecture](../concepts/architecture.md)
- [Configuration](../configuration/README.md)
- [Troubleshooting](../troubleshooting/common-issues.md)
