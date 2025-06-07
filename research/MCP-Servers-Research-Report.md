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

## 🚀 MCP Server Installation & Discovery Guide

### Summary of 4sysops Article (Link Access Restricted)
*Note: The original article at https://4sysops.com/archives/install-an-mcp-server-for-github-copilot-in-vs-code/ could not be accessed due to access restrictions.*

### 🔍 MCP Server Discovery in AI Coding Agents

#### **Cline (Claude Dev)**
**Repository:** https://github.com/cline/cline  
**Marketplace:** https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev

**Key MCP Features in Cline:**
- **Custom Tool Creation**: Cline can create and install MCP servers on demand
  - Just ask: "add a tool that fetches Jira tickets"
  - Cline handles everything from server creation to installation
  - Custom tools become part of Cline's permanent toolkit

- **Built-in MCP Integration**: 
  - Supports Model Context Protocol for extending capabilities
  - Can create tailored MCP servers for specific workflows
  - Examples: AWS EC2 management, PagerDuty incident fetching, Jira integration

- **Dynamic Tool Installation**:
  ```
  User Request: "add a tool that manages AWS EC2s"
  Cline Response: Creates custom MCP server → Installs it → Ready to use
  ```

#### **Roo Code (Formerly Roo Cline)**
**Repository:** https://github.com/RooCodeInc/Roo-Code  
**Documentation:** https://docs.roocode.com/  
**Website:** https://roocode.com

**Enhanced MCP Capabilities:**
- **Unlimited Custom Tools**: MCP provides framework to expand functionality
- **External API Integration**: Connect to databases, APIs, and specialized tools
- **Multi-Agent Architecture**: Different modes (Code, Architect, Debug) can leverage MCP tools
- **Custom Mode Support**: Create specialized personas that utilize specific MCP servers

**Roo Code MCP Discovery Process:**
1. **Automatic Detection**: Discovers available MCP servers in workspace
2. **Custom Mode Integration**: Different agent modes can access specific tool sets
3. **API Integration**: Seamless connection to external services via MCP protocol

### 📦 MCP Server Installation Methods

#### **Method 1: VS Code Native (Official)**
```json
// .vscode/mcp.json
{
  "servers": {
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"]
    }
  }
}
```

#### **Method 2: Command Line Installation**
```bash
# Add via CLI
code --add-mcp '{"name":"fetch-server","command":"uvx","args":["mcp-server-fetch"]}'
```

#### **Method 3: URL Handler Installation**
```javascript
// Programmatic installation
const link = `vscode:mcp/install?${encodeURIComponent(JSON.stringify(obj))}`;
```

#### **Method 4: Auto-Discovery (Claude Desktop Integration)**
- Enable `chat.mcp.discovery.enabled` setting
- Automatically detects servers from Claude Desktop configuration
- Reuses existing MCP server configurations

### 🛠️ Popular MCP Servers for Installation

#### **Essential Development Servers**
- **GitHub**: Repository management and API integration
- **Filesystem**: Secure file operations with access controls  
- **Fetch**: Web content retrieval and conversion
- **Memory**: Knowledge graph-based persistent memory
- **Sequential Thinking**: Dynamic problem-solving workflows

#### **Database & Infrastructure**
- **PostgreSQL**: Database querying and schema inspection
- **SQLite**: Local database interactions
- **Redis**: Key-value store operations
- **AWS**: Cloud service management
- **Docker**: Container operations

#### **Productivity Tools**
- **Slack**: Team communication and channel management
- **Jira**: Issue tracking and project management
- **Google Drive**: File access and search
- **Puppeteer**: Browser automation and web scraping

### 🔄 MCP Server Discovery Workflow

#### **In Cline:**
1. **User Request**: "I need to integrate with [service]"
2. **Cline Analysis**: Determines if existing MCP server available
3. **Auto-Installation**: Downloads and configures appropriate server
4. **Custom Creation**: If no server exists, creates custom MCP server
5. **Integration**: Tool becomes available for immediate use

#### **In Roo Code:**
1. **Mode Selection**: Choose appropriate agent mode (Code, Architect, etc.)
2. **Tool Discovery**: System scans for available MCP servers
3. **Context-Aware Loading**: Loads relevant tools based on project type
4. **Custom Integration**: Users can configure specific tools per mode
5. **Persistent Access**: Tools remain available across sessions

### 📚 Additional MCP Resources & Links

#### **Official Documentation**
- **MCP Specification**: https://spec.modelcontextprotocol.io/
- **Official Servers Repository**: https://github.com/modelcontextprotocol/servers
- **Anthropic MCP Announcement**: https://www.anthropic.com/news/model-context-protocol

#### **SDKs and Development**
- **TypeScript SDK**: https://github.com/modelcontextprotocol/typescript-sdk
- **Python SDK**: https://github.com/modelcontextprotocol/python-sdk
- **Java SDK**: https://github.com/modelcontextprotocol/java-sdk
- **C# SDK**: https://github.com/modelcontextprotocol/csharp-sdk

#### **Community Resources**
- **MCP Workshop (2hr Video)**: Available on ModelContextProtocol.io
- **Building MCP with LLMs Tutorial**: Step-by-step development guide
- **MCP Inspector**: Interactive debugging tool for testing servers
- **Community Server Gallery**: Growing ecosystem of third-party servers

#### **AI Agent Integration**
- **Cline Documentation**: Available in VS Code marketplace
- **Roo Code Docs**: https://docs.roocode.com/
- **Discord Communities**: Active support for both Cline and Roo Code
- **GitHub Discussions**: MCP specification and development discussions

### 🎯 Best Practices for MCP Server Discovery

#### **Security Considerations**
- Only install servers from trusted sources
- Review server code before installation when possible
- Use input variables for sensitive credentials
- Enable logging for troubleshooting and audit trails

#### **Performance Optimization**
- Install only necessary servers to reduce overhead
- Use workspace-specific configurations for team projects
- Leverage auto-discovery for consistent development environments
- Monitor server resource usage and performance

#### **Development Workflow**
- Start with official reference servers
- Create custom servers for specific organizational needs
- Document server configurations for team sharing
- Use version control for MCP configuration files

---

*Report generated from VS Code MCP documentation and official MCP specification as of June 2025*
