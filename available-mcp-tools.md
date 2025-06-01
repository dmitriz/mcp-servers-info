# Available MCP Tools & Commands 🛠️

> Documentation of currently installed and accessible MCP tools in this workspace

## 🔧 Currently Available Research Tools

Based on the function analysis and your coding instructions, you have access to these specific MCP tools:

### 🥇 **Perplexity AI Research** (`f51_perplexity_ask`)
**Capabilities:**
- AI-powered research and analysis
- Contextual understanding of complex queries
- Structured response generation
- Real-time information processing

**Usage Example:**
```
Use for: Complex research questions, trend analysis, comparative studies
Quality: ⭐⭐⭐⭐⭐ (Highest rated)
```

### 🔍 **Brave Web Search** (`f51_brave_web_search`)
**Capabilities:**
- Web search for discovering content
- Access to current information
- Diverse source aggregation
- Real-time data retrieval

**Parameters:**
- `query`: Search query (max 400 chars)
- `count`: Number of results (1-20, default 10)
- `offset`: Pagination offset (max 9, default 0)

### 🌐 **Direct URL Fetch** (`f51_fetch`)
**Capabilities:**
- Direct URL content retrieval
- Markdown conversion
- Raw HTML access
- Pagination support

**Parameters:**
- `url`: Target URL
- `max_length`: Content limit (default 5000)
- `raw`: Get actual HTML vs simplified
- `start_index`: Starting position for pagination

### 📊 **Knowledge Graph Management**
**Memory Tools:**
- `bb7_add_memory`: Add episodes to knowledge graph
- `bb7_search_memory_facts`: Search for relevant facts
- `bb7_search_memory_nodes`: Search node summaries
- `bb7_get_episodes`: Retrieve recent episodes
- `bb7_clear_graph`: Clear all graph data

**Entity Management:**
- `f51_create_entities`: Create new entities
- `f51_add_observations`: Add observations to entities
- `f51_delete_entities`: Remove entities
- `f51_read_graph`: Read entire knowledge graph
- `f51_open_nodes`: Open specific nodes
- `f51_search_nodes`: Search for nodes

### 🗃️ **File System Operations**
**Directory Management:**
- `f51_list_directory`: List directory contents
- `f51_directory_tree`: Get recursive tree view
- `f51_search_files`: Search for files by pattern
- `f51_get_file_info`: Get file metadata

**File Operations:**
- `f51_read_file`: Read single file content
- `f51_read_multiple_files`: Read multiple files
- Access to allowed directories only

### 🛠️ **Development Tools**
**Git Operations:**
- `f51_git_status`: Check repository status
- `f51_git_add`: Stage files
- `f51_git_commit`: Record changes
- `f51_git_log`: View commit history
- `f51_git_diff`: Show differences
- `f51_git_create_branch`: Create new branch
- `f51_git_checkout`: Switch branches

### 🧠 **Advanced AI Tools**
**Sequential Thinking:** (`f51_sequentialthinking`)
- Dynamic problem-solving
- Thought process documentation
- Multi-step analysis
- Hypothesis generation and verification

**Library Documentation:** (`f51_get-library-docs`)
- Fetch up-to-date library docs
- Context7-compatible library access
- Topic-focused documentation

## 📍 Local Search Capabilities

### **Brave Local Search** (`f51_brave_local_search`)
**Purpose:** Find local businesses and places
**Best For:** 
- "Near me" queries
- Physical locations
- Business information
- Restaurant/service discovery

**Returns:**
- Business names and addresses
- Ratings and review counts
- Phone numbers and hours
- Detailed location data

## 🔧 VS Code MCP Commands

### **Available Commands in Command Palette:**
```
MCP: List Servers          - View configured servers
MCP: Add Server            - Add new server configuration
MCP: Start Server          - Start a stopped server
MCP: Stop Server           - Stop a running server
MCP: Restart Server        - Restart server
MCP: Show Output           - View server logs
```

### **Settings Configuration:**
```
chat.mcp.enabled           - Enable/disable MCP support
chat.mcp.discovery.enabled - Auto-discover servers
```

### **Agent Mode Access:**
1. Open Chat: `Ctrl+Alt+I` (Windows) / `⌃⌘I` (Mac)
2. Select "Agent mode" from dropdown
3. Click "Tools" button to manage tools
4. Use approval automation options

## 🔐 Security & Approval Controls

### **Approval Levels Available:**
- **Manual** - Confirm each tool execution (default)
- **Session** - Auto-approve for current session
- **Workspace** - Auto-approve for current workspace
- **Global** - Auto-approve for all future invocations

### **Configuration Methods:**
1. **Workspace**: `.vscode/mcp.json`
2. **Global**: `settings.json` under "mcp" section
3. **Environment**: `.env` files for credentials
4. **Instructions**: `.github/copilot-instructions.md`

## 🎯 Research Tool Effectiveness

Based on comparative analysis in this repository:

| Tool | Effectiveness | Best Use Case | Quality Score |
|------|--------------|---------------|---------------|
| **Perplexity** | Highest | Complex analysis, structured research | ⭐⭐⭐⭐⭐ |
| **Brave Search** | High | Current info, broad coverage | ⭐⭐⭐⭐ |
| **Fetch** | Good | Direct content access, specific URLs | ⭐⭐⭐ |

## 📊 Tool Usage Recommendations

### **For MCP Server Research:**
1. **Start with Perplexity** - Get comprehensive analysis
2. **Use Brave Search** - Find current developments
3. **Fetch specific URLs** - Access official documentation
4. **Document findings** - Use knowledge graph tools

### **For Implementation:**
1. **Check available servers** - Use search tools
2. **Verify installation** - Test with VS Code commands
3. **Configure security** - Set appropriate approval levels
4. **Monitor performance** - Use server management tools

## 🚀 Installation Status

**Current Setup:**
- ✅ Perplexity AI research tool
- ✅ Brave Search integration
- ✅ Direct fetch capabilities
- ✅ Knowledge graph management
- ✅ File system operations
- ✅ Git version control
- ✅ Sequential thinking engine

**VS Code MCP Status:**
- Requires VS Code 1.99+ (Preview)
- Enable via `chat.mcp.enabled` setting
- Access through Agent mode
- Full approval control available

---

*This documentation reflects the currently available MCP tools and commands as of June 2025*
