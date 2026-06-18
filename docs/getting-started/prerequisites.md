# Prerequisites

Before setting up Claude Code with FreeLLMAPI and LiteLLM, ensure you have the required software installed.

## Required Software

### Python 3.8+

**Windows:**
```powershell
# Download from https://www.python.org/downloads/
python --version
```

**Linux:**
```bash
sudo apt update && sudo apt install python3 python3-pip
python3 --version
```

**macOS:**
```bash
brew install python3
python3 --version
```

### Node.js 16+

Download from https://nodejs.org/ (LTS version recommended)

### Git

**Windows:** `winget install Git.Git` or download from https://git-scm.com/

**Linux:** `sudo apt install git`

**macOS:** Usually pre-installed, or `brew install git`

## Verify Installation

```powershell
python --version    # Expected: Python 3.8+
node --version     # Expected: v16+
npm --version      # Expected: 8+
git --version      # Expected: git version 2.x
```

## Port Requirements

| Port | Service | Purpose |
|------|---------|---------|
| 8082 | FreeLLMAPI | OpenAI-compatible API |
| 4000 | LiteLLM | Compatibility bridge |
| 1234 | LM Studio | Local model (optional) |
| 11434 | Ollama | Local model (optional) |

## Next Steps

1. [Quick Start](./quickstart.md) - Get running quickly
2. [Windows Setup](../setup/windows.md) - Detailed Windows guide
3. [Linux Setup](../setup/linux.md) - Detailed Linux guide
