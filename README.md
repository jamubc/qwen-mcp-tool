
# Qwen MCP Tool




<div align="center">

[![GitHub Release](https://img.shields.io/github/v/release/jamubc/qwen-mcp-tool?logo=github&label=GitHub)](https://github.com/jamubc/qwen-mcp-tool/releases)
[![npm version](https://img.shields.io/npm/v/qwen-mcp-tool)](https://www.npmjs.com/package/qwen-mcp-tool)
[![npm downloads](https://img.shields.io/npm/dt/qwen-mcp-tool)](https://www.npmjs.com/package/qwen-mcp-tool)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Open Source](https://img.shields.io/badge/Open%20Source-❤️-red.svg)](https://github.com/jamubc/qwen-mcp-tool)


</div>

Note: qwen-cli supports any [![OpenAI endpoint support](https://img.shields.io/badge/-OpenAI-412991?style=flat&logo=openai&logoColor=white)](https://github.com/jamubc/qwen-mcp-tool) type API, thus you can in theory use any [![OpenAI endpoint support](https://img.shields.io/badge/-OpenAI-412991?style=flat&logo=openai&logoColor=white)](https://github.com/jamubc/qwen-mcp-tool) compatible API. I was able to test qwen-cli using gpt-4o-mini without issues, potentially there are problems with persistance and might have to modify install command to handle envs.

This is a simple Model Context Protocol (MCP) server that allows AI assistants to interact with the Qwen CLI. It enables the AI to leverage the power of Qwen's capabilities for analysis using the `@` syntax for direction.

- Ask qwen natural questions, through claude or Brainstorm new ideas in a party of 3!


## TLDR: [![Claude](https://img.shields.io/badge/Claude-D97757?logo=claude&logoColor=fff)](#) + [![Qwen](https://img.shields.io/badge/Qwen-FF6B00?logo=qwen&logoColor=fff)](#)


**Goal**: Use Qwen's powerful analysis capabilities directly in Claude Code to save tokens and analyze large files.

## Prerequisites

Before using this tool, ensure you have:

1. **[Node.js](https://nodejs.org/)** (v16.0.0 or higher)
2. **[Qwen Code CLI](https://github.com/QwenLM/qwen-code)** installed and configured


### One-Line Setup

```bash
claude mcp add qwen-cli -- npx -y qwen-mcp-tool
```

### Verify Installation

Type `/mcp` inside Claude Code to verify the qwen-cli MCP is active.

---

### Alternative: Import from Claude Desktop

If you already have it configured in Claude Desktop:

1. Add to your Claude Desktop config:
```json
"qwen-cli": {
  "command": "npx",
  "args": ["-y", "qwen-mcp-tool"]
}
```

2. Import to Claude Code:
```bash
claude mcp add-from-claude-desktop
```

## Configuration

Register the MCP server with your MCP client:

### For NPX Usage (Recommended)

Add this configuration to your Claude Desktop config file:

```json
{
  "mcpServers": {
    "qwen-cli": {
      "command": "npx",
      "args": ["-y", "qwen-mcp-tool"]
    }
  }
}
```

### For Global Installation

If you installed globally, use this configuration instead:

```json
{
  "mcpServers": {
    "qwen-cli": {
      "command": "qwen-mcp"
    }
  }
}
```

**Configuration File Locations:**

- **Claude Desktop**:
  - **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
  - **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
  - **Linux**: `~/.config/claude/claude_desktop_config.json`

After updating the configuration, restart your terminal session.

## Example Workflow

- **Natural language**: "use qwen to explain index.html", "understand the massive project using qwen", "ask qwen to search for latest news"
- **Claude Code**: Type `/qwen-cli` and commands will populate in Claude Code's interface.

## Usage Examples

### With File References (using @ syntax)

- `ask qwen to analyze @src/main.js and explain what it does`
- `use qwen to summarize @. the current directory`
- `analyze @package.json and tell me about dependencies`

### General Questions (without files)

- `ask qwen to search for the latest tech news`
- `use qwen to explain div centering`
- `ask qwen about best practices for React development related to @file_im_confused_about`

### Using Qwen CLI's Sandbox Mode (-s)

The sandbox mode allows you to safely test code changes, run scripts, or execute potentially risky operations in an isolated environment.

- `use qwen sandbox to create and run a Python script that processes data`
- `ask qwen to safely test @script.py and explain what it does`
- `use qwen sandbox to install numpy and create a data visualization`
- `test this code safely: Create a script that makes HTTP requests to an API`

### Tools (for the AI)

These tools are designed to be used by the AI assistant.

- **`ask-qwen`**: Asks Qwen for its perspective. Can be used for general questions or complex analysis of files.
  - **`prompt`** (required): The analysis request. Use the `@` syntax to include file or directory references (e.g., `@src/main.js explain this code`) or ask general questions (e.g., `Please use a web search to find the latest news stories`).
  - **`model`** (optional): The Qwen model to use. Defaults to `qwen-max`.
  - **`sandbox`** (optional): Set to `true` to run in sandbox mode for safe code execution.
- **`sandbox-test`**: Safely executes code or commands in Qwen's sandbox environment. Always runs in sandbox mode.
  - **`prompt`** (required): Code testing request (e.g., `Create and run a Python script that...` or `@script.py Run this safely`).
  - **`model`** (optional): The Qwen model to use.
- **`Ping`**: A simple test tool that echoes back a message.
- **`Help`**: Shows the Qwen CLI help text.

### Slash Commands (for the User)

You can use these commands directly in Claude Code's interface (compatibility with other clients has not been tested).

- **/analyze**: Analyzes files or directories using Qwen, or asks general questions.
  - **`prompt`** (required): The analysis prompt. Use `@` syntax to include files (e.g., `/analyze prompt:@src/ summarize this directory`) or ask general questions (e.g., `/analyze prompt:Please use a web search to find the latest news stories`).
- **/sandbox**: Safely tests code or scripts in Qwen's sandbox environment.
  - **`prompt`** (required): Code testing request (e.g., `/sandbox prompt:Create and run a Python script that processes CSV data` or `/sandbox prompt:@script.py Test this script safely`).
- **/help**: Displays the Qwen CLI help information.
- **/ping**: Tests the connection to the server.
  - **`message`** (optional): A message to echo back.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

> **Note**: This project is a fork of [github.com/jamubc/gemini-mcp-tool](https://github.com/jamubc/gemini-mcp-tool)

**Disclaimer:** This is an unofficial, third-party tool and is not affiliated with, endorsed, or sponsored by Alibaba Cloud.
