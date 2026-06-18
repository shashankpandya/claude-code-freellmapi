# Concepts

Understanding the core concepts behind Claude Code with FreeLLMAPI and LiteLLM.

## What's in This Section

| Concept | Description | Level |
|---------|-------------|-------|
| [Architecture](./architecture.md) | How all components work together | Beginner |
| [Model Routing](./model-routing.md) | Mapping Claude models to backends | Intermediate |
| [Compatibility Bridge](./compatibility.md) | How LiteLLM translates requests | Advanced |

## Quick Understanding

### 1. Why Do We Need This?

Claude Code expects **Anthropic API format**, but FreeLLMAPI provides **OpenAI API format**. LiteLLM **translates** between them.

### 2. What Does LiteLLM Do?

| Task | Description |
|------|-------------|
| **Format Translation** | Anthropic ↔ OpenAI |
| **Model Mapping** | `claude-opus-4-8` → `gpt-4o` |
| **Parameter Filtering** | Remove unsupported params |

### 3. What Does FreeLLMAPI Do?

| Task | Description |
|------|-------------|
| **Gateway** | Single entry point for multiple providers |
| **Load Balancing** | Distribute requests across providers |
| **Health Monitoring** | Check provider availability |

## Common Patterns

| Pattern | Use Case |
|---------|----------|
| Single Provider | Testing with one backend |
| Multiple Providers (Failover) | Production with backups |
| Local Models | Free usage with Ollama/LM Studio |

## Next Steps

| If You Want To | Go To |
|----------------|-------|
| Understand the full picture | [Architecture](./architecture.md) |
| Set up model mappings | [Model Routing](./model-routing.md) |
| Learn parameter handling | [Compatibility Bridge](./compatibility.md) |
