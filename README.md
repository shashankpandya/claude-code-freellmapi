# Claude Code with FreeLLMAPI + LiteLLM

Run Claude Code using FreeLLMAPI + LiteLLM as a compatibility bridge. This enables Claude Code to work with any OpenAI-compatible API, including local models.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Issues](https://img.shields.io/github/issues/shashankpandya/claude-code-freellmapi.svg)](https://github.com/shashankpandya/claude-code-freellmapi/issues)

## 🚀 Quick Start

Get running in 5 minutes:

```powershell
# 1. Clone the repository
git clone https://github.com/shashankpandya/claude-code-freellmapi.git
cd claude-code-freellmapi

# 2. Start all services
.\examples\combined-startup.ps1

# 3. Test your setup
.\examples\test-prompts.ps1
```

**That's it!** Claude Code is now running through FreeLLMAPI and LiteLLM.

## 📚 Documentation

| Topic | Guide |
|-------|-------|
| **New to this?** | [Quick Start Guide](docs/getting-started/quickstart.md) |
| **Windows Setup** | [Windows Guide](docs/setup/windows.md) |
| **Linux Setup** | [Linux Guide](docs/setup/linux.md) |
| **macOS Setup** | [macOS Guide](docs/setup/macos.md) |
| **Configuration** | [Config Guide](docs/configuration/README.md) |
| **Troubleshooting** | [Troubleshooting](docs/troubleshooting/README.md) |

### Full Documentation Index

```
docs/
├── getting-started/      # Quick start, prerequisites
├── setup/                # Platform-specific guides
├── concepts/             # Architecture, model routing
├── configuration/        # Detailed configuration
├── troubleshooting/      # Common issues, FAQ
├── validation/           # Testing your setup
└── support/              # Getting help
```

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     CLAUDE CODE                                  │
│                    (Anthropic API)                              │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                         LITELLM                                 │
│              (Compatibility Bridge :4000)                      │
│                                                                 │
│  • Translates Anthropic → OpenAI format                        │
│  • Maps model names (claude-opus-4-8 → gpt-4o)               │
│  • Drops unsupported parameters                                │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                       FREELLMAPI                                │
│                    (API Gateway :8082)                          │
│                                                                 │
│  • OpenAI-compatible API                                        │
│  • Provider pool management                                    │
│  • Load balancing                                              │
└────────────────────────────┬────────────────────────────────────┘
                             │
         ┌───────────────────┼───────────────────┐
         ▼                   ▼                   ▼
   ┌───────────┐      ┌───────────┐      ┌───────────┐
   │ LM Studio │      │  Ollama   │      │  OpenAI   │
   │  :8000    │      │  :11434   │      │   API     │
   │ (Local)   │      │ (Local)   │      │ (Remote)  │
   └───────────┘      └───────────┘      └───────────┘
```

## ❓ Why This Project?

Claude Code expects **Anthropic API format**, but many providers only support **OpenAI format**. This project uses LiteLLM as a translation layer to bridge the gap.

## 🔧 Key Features

- ✅ Run Claude Code with local models (Ollama, LM Studio)
- ✅ Use OpenAI-compatible APIs as backends
- ✅ Model mapping and routing
- ✅ Platform guides for Windows, Linux, macOS
- ✅ Comprehensive troubleshooting

## 📖 Documentation Highlights

| What You Need | Where to Go |
|--------------|-------------|
| Step-by-step Windows setup | [Windows Guide](docs/setup/windows.md) |
| Understand how it works | [Architecture](docs/concepts/architecture.md) |
| Configure model mappings | [Model Routing](docs/concepts/model-routing.md) |
| Fix common errors | [Troubleshooting](docs/troubleshooting/common-issues.md) |
| Set up local models | [Provider Setup](docs/configuration/providers.md) |

## 🆘 Need Help?

1. **Check the docs**: Most questions are answered in [docs/](docs/README.md)
2. **Common issues**: See [Troubleshooting](docs/troubleshooting/common-issues.md)
3. **FAQ**: [Frequently Asked Questions](docs/troubleshooting/faq.md)
4. **GitHub Issues**: [Open an issue](https://github.com/shashankpandya/claude-code-freellmapi/issues)

## 🤝 Community

| Resource | Link |
|----------|------|
| Contributing | [docs/community/CONTRIBUTING.md](docs/community/CONTRIBUTING.md) |
| Code of Conduct | [docs/community/CODE_OF_CONDUCT.md](docs/community/CODE_OF_CONDUCT.md) |
| Credits | [docs/community/CREDITS.md](docs/community/CREDITS.md) |
| Changelog | [docs/community/CHANGELOG.md](docs/community/CHANGELOG.md) |

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.
