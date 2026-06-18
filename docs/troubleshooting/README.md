# Troubleshooting Guide

Solutions to common issues with Claude Code, FreeLLMAPI, and LiteLLM.

## Quick Navigation

| Issue Type | Guide |
|-----------|-------|
| Installation problems | [Common Issues](./common-issues.md) |
| Error messages | [Common Issues](./common-issues.md) |
| FAQ | [FAQ](./faq.md) |

## Troubleshooting Flowchart

```
Having issues?
    │
    ├── Services won't start?
    │       └──→ Check [Service Errors](./common-issues.md#service-errors)
    │
    ├── Can't connect?
    │       └──→ Check [Connection Issues](./common-issues.md#connection-issues)
    │
    └── Something else?
            └──→ Check [FAQ](./faq.md) or [Get Support](../support/README.md)
```

## Diagnostic Commands

### Check All Services

```bash
# Check FreeLLMAPI
curl http://localhost:8082/health

# Check LiteLLM
curl http://localhost:4000/health

# Check models
curl http://localhost:4000/models
```

### Check Ports

```bash
# Windows
netstat -ano | findstr "8082 4000"

# Linux/macOS
lsof -i :8082
lsof -i :4000
```

## Getting Help

If you can't resolve the issue:

1. Check the [FAQ](./faq.md)
2. Search [GitHub Issues](https://github.com/shashankpandya/claude-code-freellmapi/issues)
3. Open a new issue with details

See [Getting Support](../support/README.md) for more options.
