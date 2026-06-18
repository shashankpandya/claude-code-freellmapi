# Validation Guide

Verify that your setup is working correctly.

## Quick Validation

### 1. Check Service Health

```bash
# FreeLLMAPI
curl http://localhost:8082/health

# LiteLLM
curl http://localhost:4000/health
```

Expected: `{"status": "ok"}`

### 2. Check Models

```bash
curl http://localhost:4000/models
```

Should return a list of available models.

### 3. Run Test Prompts

```bash
.\examples\test-prompts.ps1
```

## Validation Checklist

- [ ] FreeLLMAPI running on port 8082
- [ ] LiteLLM running on port 4000
- [ ] Health checks pass
- [ ] Models are discoverable
- [ ] Test prompts return responses
- [ ] No errors in console
- [ ] Responses are coherent

## Troubleshooting Failed Validations

| Issue | Cause | Solution |
|-------|-------|----------|
| Health check fails | Service not running | Start the service |
| No models listed | Config error | Check model_list |
| Test times out | Network/provider issue | Check connectivity |

## Related Documentation

- [Troubleshooting](../troubleshooting/README.md)
- [Configuration](../configuration/README.md)
