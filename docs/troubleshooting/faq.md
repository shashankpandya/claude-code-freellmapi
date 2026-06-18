# Frequently Asked Questions

Common questions and answers.

## General

### What is this project?

This project enables running Claude Code using FreeLLMAPI and LiteLLM as a compatibility bridge, allowing Claude Code to work with any OpenAI-compatible API.

### Why do I need a compatibility layer?

Claude Code expects Anthropic API format, but many providers only offer OpenAI-compatible APIs. LiteLLM translates between these formats.

### What are the system requirements?

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| OS | Windows 10, macOS 11, Ubuntu 20.04 | Latest |
| RAM | 4 GB | 8 GB+ |
| Python | 3.8+ | 3.11+ |
| Node.js | 16+ | 18+ |

## Installation

### Do I need to install FreeLLMAPI and LiteLLM separately?

Yes:
- FreeLLMAPI: `npm install -g freellmapi`
- LiteLLM: `pip install litellm`

### Can I use Docker?

Yes, Docker images are available for both components.

## Configuration

### What is `drop_params: true`?

Claude Code sends Anthropic-specific parameters that OpenAI APIs don't understand. Setting `drop_params: true` tells LiteLLM to remove these before forwarding requests.

### Can I use different ports?

Yes, configure each service on different ports:
- FreeLLMAPI: 8082 (default)
- LiteLLM: 4000 (default)

## Models

### Which models are supported?

Any OpenAI-compatible model:
- OpenAI: GPT-4, GPT-3.5
- Local: Llama, Mistral (via Ollama/LM Studio)
- Remote: Any OpenAI-compatible API

### Can I use local models for free?

Yes! Local models through Ollama or LM Studio have no API costs.

## Troubleshooting

### Why am I getting "Connection Refused"?

1. Check services are running
2. Verify ports match configuration
3. Check firewall settings

### Why am I getting "Model Not Found"?

1. Verify model is in `model_list`
2. Check exact spelling
3. Restart LiteLLM after config changes

### Why am I getting "Unsupported Parameter"?

Ensure `drop_params: true` is set in `litellm_settings`.

## Security

### Is it safe to expose these services?

For development on localhost, yes. For production, use authentication and firewalls.

### How do I protect API keys?

- Never commit `.env` to version control
- Use environment variables
- Rotate keys periodically
