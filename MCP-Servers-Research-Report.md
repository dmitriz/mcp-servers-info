# MCP Servers Research Report

## 📋 Table of Contents
1. [Executive Summary](#-executive-summary)
2. [Quick Guide: Finding Approval Settings](#-quick-guide-finding-approval-settings)
3. [What is MCP?](#what-is-mcp)
4. [Automated Approvals - Detailed Analysis](#-automated-approvals---detailed-analysis)
5. [Configuration and Setup](#-configuration-and-setup)
6. [Security and Trust Considerations](#️-security-and-trust-considerations)
7. [Supported Capabilities](#-supported-capabilities)
8. [Tool Usage Workflow](#️-tool-usage-workflow)
9. [Server Management](#-server-management)
10. [Official MCP Server Repository](#-official-mcp-server-repository)
11. [Additional Resources](#-additional-resources)
12. [Important Notes](#️-important-notes)

## 📝 Executive Summary

This comprehensive report analyzes MCP (Model Context Protocol) servers in VS Code, focusing on **automated approval mechanisms** for tool execution. Key findings:

**🔑 Core Findings:**
- **Default Security**: Manual approval required for all tool executions by default
- **Flexible Automation**: Three-tier approval automation (session, workspace, global)
- **Granular Control**: Users can selectively enable/disable tools and review parameters
- **Enterprise Ready**: Secure credential management and centralized settings support

**⚡ Quick Takeaways:**
- MCP enables AI models to interact with external tools through standardized protocol
- VS Code provides robust approval controls to balance automation with security
- Currently in preview (VS Code 1.99+) with extensive third-party ecosystem
- Supports stdio, SSE, and HTTP transport protocols

## 🎯 Quick Guide: Finding Approval Settings

### Step-by-Step Location Guide

#### 1. **Enable MCP Support**
```
File → Preferences → Settings → Search "chat.mcp.enabled" → Enable
```

#### 2. **Access Approval Controls During Tool Execution**
```
1. Open Chat view: Ctrl+Alt+I (Windows/Linux) or ⌃⌘I (Mac)
2. Select "Agent mode" from dropdown
3. Click "Tools" button to manage tool selection
4. When tool is invoked → "Continue" button dropdown appears
```

#### 3. **Approval Automation Options** (in Continue button dropdown)
- **"Continue for this session"** - Auto-approve until VS Code restart
- **"Continue for this workspace"** - Auto-approve for current project only  
- **"Continue for all future invocations"** - Global auto-approval

#### 4. **Manage Configured Servers**
```
Command Palette (Ctrl+Shift+P) → Type "MCP: List Servers"
```

#### 5. **Advanced Control via Configuration**
- **Workspace**: Create `.vscode/mcp.json` file
- **Global**: Add to `settings.json` under "mcp" section
- **Instructions**: Use `.github/copilot-instructions.md` for fine-tuning

#### 6. **Enterprise/Organizational Settings**
```
Centrally manage via VS Code enterprise documentation
Setting: chat.mcp.enabled (can be controlled organizationally)
```

## Overview

Based on research from VS Code documentation and the official Model Context Protocol specification, this report provides comprehensive information about MCP (Model Context Protocol) servers, with particular focus on automated approvals functionality.

**Source:** https://code.visualstudio.com/docs/copilot/chat/mcp-servers

## What is MCP?

Model Context Protocol (MCP) is an open standard that enables AI models to interact with external tools and services through a unified interface. In VS Code, MCP support enhances GitHub Copilot's agent mode by allowing you to connect any MCP-compatible server to your agentic coding workflow.

### Architecture
- **MCP clients** (like VS Code) connect to MCP servers and request actions on behalf of the AI model
- **MCP servers** provide one or more tools that expose specific functionalities through a well-defined interface
- **Model Context Protocol** defines the message format for communication between clients and servers

## 🔐 AUTOMATED APPROVALS - DETAILED ANALYSIS

### Default Approval Behavior
- **Manual Approval Required**: By default, when a tool is invoked, users need to confirm the action before it runs
- **Security Rationale**: This is a critical security measure because tools might run locally on your machine and might perform actions that modify files or data
- **Parameter Review**: Users can verify and edit tool input parameters before running the tool

### Automated Approval Options
VS Code provides flexible automation options through the "Continue" button dropdown:

1. **Session-Level Automation**
   - Automatically confirm the specific tool for the current session only
   - Resets when VS Code session ends

2. **Workspace-Level Automation**  
   - Automatically confirm the tool for the current workspace
   - Persists across sessions within that workspace

3. **Global Automation**
   - Automatically confirm for all future invocations
   - Applies across all workspaces and sessions

### Tool Control Mechanisms

#### Direct Tool Management
- **Tools Button**: Select/deselect tools you want to use in agent mode
- **Search Functionality**: Search tools by typing in the search box
- **Manual Reference**: Directly reference tools in prompts using `#` followed by tool name
- **Cross-Mode Support**: Tool referencing works in all chat modes (ask, edit, and agent mode)

#### Advanced Control Options
- **Configuration Files**: Use `.github/copilot-instructions.md` for fine-tuned tool usage control
- **Server Management**: Use `MCP: List Servers` command to view, start, stop, or restart servers
- **Dynamic Tool Lists**: Tool descriptions can be updated dynamically using list changed events

## 🔧 Configuration and Setup

### Workspace Configuration
Create a `.vscode/mcp.json` file in your workspace:

```json
{
  "inputs": [
    {
      "type": "promptString", 
      "id": "perplexity-key",
      "description": "Perplexity API Key",
      "password": true
    }
  ],
  "servers": {
    "Perplexity": {
      "type": "stdio",
      "command": "npx", 
      "args": ["-y", "server-perplexity-ask"],
      "env": {
        "PERPLEXITY_API_KEY": "${input:perplexity-key}"
      }
    }
  }
}
```

### User Settings Configuration
Add to your `settings.json` for global availability:

```json
{
  "mcp": {
    "servers": {
      "my-mcp-server": {
        "type": "stdio",
        "command": "my-command", 
        "args": []
      }
    }
  }
}
```

### Automatic Discovery
- Enable with `chat.mcp.discovery.enabled` setting
- Automatically detects MCP servers from other tools like Claude Desktop

## 🛡️ Security and Trust Considerations

### Key Security Principles
1. **User Consent and Control**
   - Users must explicitly consent to and understand all data access and operations
   - Users retain control over what data is shared and what actions are taken
   - Clear UIs should be provided for reviewing and authorizing activities

2. **Data Privacy** 
   - Explicit user consent required before exposing user data to servers
   - No transmission of resource data elsewhere without user consent
   - User data protected with appropriate access controls

3. **Tool Safety**
   - Tools represent arbitrary code execution and must be treated with caution
   - Explicit user consent required before invoking any tool
   - Users should understand what each tool does before authorization

### Implementation Guidelines
- **Trusted Sources Only**: Only add servers from trusted sources
- **Review Before Starting**: Review publisher and server configuration before starting
- **Secure Credentials**: Use input variables or environment files to avoid hardcoding sensitive information
- **Server Naming**: Follow camelCase naming conventions (e.g., "uiTesting")

## 📋 Supported Capabilities

### Transport Protocols
- **stdio** (standard input/output) 
- **sse** (server-sent events)
- **http** (streamable HTTP)

### MCP Features
- **Tools**: Functions for the AI model to execute
- **Resources**: Context and data for user or AI model use  
- **Prompts**: Templated messages and workflows for users
- **Sampling**: Server-initiated agentic behaviors and recursive LLM interactions

### VS Code Integration
- **Workspace Folders**: VS Code provides servers with current workspace folders using roots
- **Dynamic Updates**: List and descriptions of tools can be updated dynamically
- **Error Handling**: Error indicators and logs available for troubleshooting

## 🛠️ Tool Usage Workflow

1. **Enable MCP Support**
   - Set `chat.mcp.enabled` setting to true
   - Available starting from VS Code 1.99 (currently in preview)

2. **Configure Servers**
   - Add server configuration to `.vscode/mcp.json` or user settings
   - Use `MCP: Add Server` command from Command Palette

3. **Access Agent Mode**
   - Open Chat view (⌃⌘I on Windows/Linux: Ctrl+Alt+I)
   - Select Agent mode from dropdown

4. **Manage Tools**
   - Select Tools button to view available tools
   - Toggle tools on/off as needed
   - Search tools using search box

5. **Execute Tools**
   - Enter prompts - tools automatically invoked as needed
   - Confirm/approve tool execution (with automation options)
   - Review and edit tool parameters before execution

## 🔍 Server Management

### Commands Available
- **MCP: List Servers** - View configured MCP servers
- **MCP: Add Server** - Add new server configuration  
- **Start/Stop/Restart** - Server lifecycle management
- **Show Output** - View server logs for troubleshooting

### Command-Line Interface
Add servers via CLI:
```bash
code --add-mcp "{\"name\":\"my-server\",\"command\": \"uvx\",\"args\": [\"mcp-server-fetch\"]}"
```

### URL Handler
Install servers via URL:
```javascript
const link = `vscode:mcp/install?${encodeURIComponent(JSON.stringify(obj))}`;
```

## 🌟 Official MCP Server Repository

The official repository (https://github.com/modelcontextprotocol/servers) contains:

### Reference Servers
- **Everything** - Reference/test server with prompts, resources, and tools
- **Fetch** - Web content fetching and conversion  
- **Filesystem** - Secure file operations with configurable access controls
- **Memory** - Knowledge graph-based persistent memory system
- **Sequential Thinking** - Dynamic problem-solving through thought sequences
- **Time** - Time and timezone conversion capabilities

### Third-Party Integrations
Extensive ecosystem including official integrations from companies like:
- AWS, Azure, Google Cloud
- GitHub, GitLab  
- Browserbase, Puppeteer
- Database systems (PostgreSQL, SQLite, Redis)
- And many more...

## 📚 Additional Resources

- **Model Context Protocol Documentation**: https://spec.modelcontextprotocol.io/
- **Official Server Repository**: https://github.com/modelcontextprotocol/servers
- **SDKs Available**: TypeScript, Python, Java, Kotlin, C#, Swift
- **VS Code Agent Mode Guide**: Use agent mode in Visual Studio Code

## ⚠️ Important Notes

- MCP support in VS Code is currently in **preview** status
- Only servers providing **tools** are currently supported (not prompts or resources)
- Docker containers should **not** use detached mode (-d option)
- Environment variables and .env files supported for secure credential management
- Server logs available for troubleshooting via "Show Output" option

---

*Report generated from VS Code MCP documentation and official MCP specification as of June 2025*
