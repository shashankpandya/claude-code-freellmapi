# Common Issues

Detailed solutions for frequently encountered problems.

## Service Errors

### FreeLLMAPI Won't Start

| Cause | Solution |
|-------|----------|
| Port already in use | Find and stop other process, or change port |
| Configuration error | Check `.fcc_env` syntax |
| Node.js not installed | Install Node.js |

**Commands**:
```bash
# Windows: Find process on port 8082
netstat -ano | findstr :8082

# Kill process
taskkill /PID <PID> /F
```

### LiteLLM Won't Start

| Cause | Solution |
|-------|----------|
| Python not installed | Install Python 3.8+ |
| Configuration error | Check `litellm-config.yaml` syntax |
| Port 4000 in use | Change port or stop conflicting service |

**Commands**:
```bash
# Check Python version
python --version

# Verify config syntax
python -c "import yaml; yaml.safe_load(open('litellm-config.yaml'))"
```

### Claude Code Can't Connect

1. Verify LiteLLM is running:
   ```bash
   curl http://localhost:4000/health
   ```

2. Check environment variables:
   ```bash
   echo $ANTHROPIC_BASE_URL
   # Should be: http://127.0.0.1:4000
   ```

## Connection Issues

### "Connection Refused" Errors

```
1. Is FreeLLMAPI running?
   → curl http://localhost:8082/health

2. Is LiteLLM running?
   → curl http://localhost:4000/health

3. Are ports correct?
   → ANTHROPIC_BASE_URL should point to LiteLLM (4000)
```

### Port Conflicts

```bash
# Windows
netstat -ano | findstr "8082 4000"

# Linux/macOS
lsof -i :8082
lsof -i :4000
```

### Authentication Errors (401 Unauthorized)

| Cause | Solution |
|-------|----------|
| Wrong token | Verify `ANTHROPIC_AUTH_TOKEN` matches `LITELLM_MASTER_KEY` |
| Token not set | Set the environment variable |

## Installation Issues

### Python Not Found

**Windows**: Download from https://www.python.org/downloads/, check "Add to PATH"

**Linux**:
```bash
sudo apt update && sudo apt install python3 python3-pip
```

**macOS**:
```bash
brew install python3
```

### npm Install Fails

```bash
npm cache clean --force
npm install -g freellmapi
```

### Module Not Found After Install

```bash
pip uninstall litellm
pip install litellm
```

## Model Issues

### Model Not Found

**Error**: `Model 'claude-opus-4-8' not found`

**Solution**:
1. Check model is in `model_list`
2. Verify exact spelling

### Unsupported Parameters

**Error**: `Unsupported parameter: top_k`

**Solution**: Enable `drop_params`:
```yaml
litellm_settings:
  drop_params: true  # CRITICAL
```

## Debug Mode

Enable debug logging:

```bash
# LiteLLM
litellm --config litellm-config.yaml --debug

# FreeLLMAPI
fcc-server --debug
```

## Related Documentation

- [FAQ](./faq.md)
- [Getting Support](../support/README.md)
