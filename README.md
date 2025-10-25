# CLAUDE_MCP_TEST_REPO

A test repository for understanding and setting up Claude MCP (Model Context Protocol) Servers.

## What is an MCP Server?

**MCP (Model Context Protocol)** is an open protocol that standardizes how applications provide context to Large Language Models (LLMs) like Claude. Think of MCP servers as bridges that connect Claude to various data sources and tools.

### Key Concepts:

- **MCP Servers** are lightweight programs that expose specific capabilities (data, tools, prompts) to Claude
- They run locally on your machine or in your infrastructure
- They provide Claude with access to external resources like databases, APIs, file systems, and more
- The protocol ensures secure, standardized communication between Claude and your tools

### Benefits:

- 🔌 **Plug-and-play** integration with various data sources
- 🔒 **Secure** - servers run locally with controlled access
- 🛠️ **Extensible** - build custom servers for your specific needs
- 🔄 **Standardized** - one protocol for all integrations

## Setup Instructions

### Prerequisites

- Node.js (v16 or higher) or Python (3.10+)
- Claude Desktop App or API access
- Basic knowledge of JSON configuration

### Step 1: Install an MCP Server

You can use existing MCP servers or build your own. Here are some popular options:

**Using npm (for Node.js based servers):**
```bash
npm install -g @modelcontextprotocol/server-filesystem
```

**Using pip (for Python based servers):**
```bash
pip install mcp-server-sqlite
```

### Step 2: Configure Claude Desktop

1. Open your Claude Desktop configuration file:
   - **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

2. Add your MCP server configuration:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/path/to/allowed/directory"
      ]
    }
  }
}
```

### Step 3: Restart Claude Desktop

After saving the configuration, restart Claude Desktop to load the MCP server.

### Step 4: Verify Connection

Open Claude and try asking it to access resources through the MCP server. For example, if you configured the filesystem server:

```
"Can you list the files in my project directory?"
```

## Building a Custom MCP Server

You can create your own MCP server using the official SDKs:

**TypeScript/Node.js:**
```bash
npm install @modelcontextprotocol/sdk
```

**Python:**
```bash
pip install mcp
```

Check the [official MCP documentation](https://modelcontextprotocol.io) for detailed guides on building custom servers.

## Available MCP Servers

- **Filesystem** - Access local files and directories
- **SQLite** - Query SQLite databases
- **PostgreSQL** - Connect to PostgreSQL databases
- **GitHub** - Interact with GitHub repositories
- **Google Drive** - Access Google Drive files
- **Slack** - Send and receive Slack messages
- And many more...

## Troubleshooting

- **Server not connecting**: Check the configuration file path and syntax
- **Permission errors**: Ensure the server has proper access to resources
- **Server crashes**: Check server logs in Claude Desktop's developer console

## Resources

- [MCP Documentation](https://modelcontextprotocol.io)
- [MCP GitHub Repository](https://github.com/modelcontextprotocol)
- [Claude API Documentation](https://docs.anthropic.com)

## Connect

Created by [@_hsh1m_](https://instagram.com/_hsh1m_)

---

**Note**: This is a test repository for learning and experimenting with MCP servers. Feel free to fork and modify!
