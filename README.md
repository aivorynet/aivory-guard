# AIVory Guard

**AI-Powered Compliance Scanning for Your Coding Assistant**

AIVory Guard is an MCP (Model Context Protocol) server that enables AI coding assistants like Claude Code, Cursor, and Windsurf to perform real-time compliance and security scanning during code generation.

## Features

- **Real-time Security Scanning** - Catch vulnerabilities as code is generated
- **15+ Compliance Standards** - OWASP, GDPR, HIPAA, PCI-DSS, SOC2, ISO27001, and more
- **AI-Powered Analysis** - Deep learning models detect complex security issues
- **Fast Integration** - 5-minute setup with any MCP-compatible AI agent
- **Zero False Positives** - AI analysis reduces noise vs. traditional static analysis

## Quick Start

### Prerequisites

- Node.js 18+ installed
- AIVory backend running (see [Backend Setup](#backend-setup))
- API token from AIVory

### Installation

```bash
# Install globally
npm install -g @aivorynet/guard

# Or use npx (no install needed)
npx @aivorynet/guard init
```

### Configuration

```bash
# Run interactive setup wizard
npx @aivorynet/guard init

# Test the connection
npx @aivorynet/guard test
```

### Connect to AI Agent

**Claude Code** (`~/.config/claude/mcp.json`):
```json
{
  "mcpServers": {
    "aivory": {
      "command": "npx",
      "args": ["@aivorynet/guard"],
      "env": {
        "AIVORY_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

**Cursor** (`.cursor/mcp.json`):
```json
{
  "mcpServers": {
    "aivory": {
      "command": "npx",
      "args": ["--yes", "@aivorynet/guard"]
    }
  }
}
```

## Usage

Once configured, your AI coding assistant will automatically scan code for compliance issues:

```
You: "Write a user authentication function in Java"

AI: [Generates code and uses AIVory Guard to scan it]

AI: "I've created the authentication function with BCrypt password hashing
     and rate limiting. The compliance scan found 0 violations - the code
     meets OWASP and GDPR standards!"
```

## Available Tools

AIVory Guard exposes 5 MCP tools to AI agents:

- **`scan_code`** - Scan a single file for compliance violations
- **`batch_scan`** - Scan multiple files efficiently
- **`get_config`** - Get current compliance configuration
- **`get_rules`** - List available compliance rules
- **`health_check`** - Verify backend connectivity

## Backend Setup

AIVory Guard requires the AIVory Python backend to be running:

```bash
cd /path/to/aivory-backend
python main.py
```

The backend runs on `http://localhost:19999` by default.

### Get API Token

1. Open http://localhost:19999/mcp-docs
2. Fill in the "Generate API Token" form
3. Copy the generated token
4. Run `npx @aivorynet/guard init` and paste the token

## Testing

Test your setup:

```bash
npx @aivorynet/guard test
```

Expected output:
```
✅ Configuration loaded
✅ Backend is healthy
✅ Compliance scan completed

✅ All tests passed!
```

## Documentation

- [Developer Guide](https://docs.aivory.net/guard/developer-guide)
- [API Reference](https://docs.aivory.net/guard/api-reference)
- [Troubleshooting](https://docs.aivory.net/guard/troubleshooting)

## Support

- **Issues**: https://github.com/aivorynet/aivory-guard/-/issues
- **Email**: support@aivory.net
- **Website**: https://aivory.net

## Acknowledgments

Built with:
- [Model Context Protocol (MCP)](https://modelcontextprotocol.io)
- [FastAPI](https://fastapi.tiangolo.com)
- [TypeScript](https://www.typescriptlang.org)

---

**Made with ❤️ by [AIVory](https://aivory.net)**
