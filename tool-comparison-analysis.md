# MCP Research Tools Comparison Analysis

*Generated: June 1, 2025*

## Research Question
**Where does VS Code store MCP server approval decisions like "Always Allow", "Allow in Session", "Allow in Workspace"?**

---

## Tool Comparison Results

### 1. 🤖 Perplexity (`f51_perplexity_ask`)
**Response Quality: ⭐⭐⭐⭐⭐ Excellent**

**Key Findings:**
- **Workspace approvals**: `<workspace>/.vscode/mcp.json`
- **User/Global approvals**: User `settings.json` or `%USERPROFILE%\.mcp.json`
- **Session approvals**: Kept in memory, not persisted
- **No registry storage**: Uses only JSON configuration files

**Strengths:**
✅ Provided specific file paths and table format
✅ Distinguished between different approval scopes
✅ Included citations and sources
✅ Clear explanation of storage mechanisms
✅ Addressed the exact question asked

**Weaknesses:**
❌ Some information may be inferred rather than documented
❌ Mixed VS Code and Visual Studio information

---

### 2. 🔍 Brave Search (`f51_brave_web_search`)
**Response Quality: ⭐⭐⭐ Good**

**Key Findings:**
- Found official VS Code MCP documentation
- Located community discussions and tutorials
- Identified relevant GitHub issues
- Found Medium articles and Reddit discussions

**Strengths:**
✅ Good discovery of relevant sources
✅ Official documentation links
✅ Community discussions for real-world insights
✅ Multiple perspectives and tutorials

**Weaknesses:**
❌ Didn't directly answer the storage location question
❌ Required additional steps to extract information
❌ Mixed quality of sources (some not authoritative)

---

### 3. 📄 Fetch (`f51_fetch`)
**Response Quality: ⭐⭐⭐⭐ Very Good**

**Key Findings from Official VS Code Docs:**
- **Configuration locations**: `.vscode/mcp.json` for workspace, user settings for global
- **Input storage**: VS Code securely stores prompted values
- **Server management**: `MCP: List Servers` command for management
- **Detailed configuration format**: Complete JSON schema provided

**Strengths:**
✅ Official, authoritative documentation
✅ Detailed configuration examples
✅ Up-to-date information (preview status noted)
✅ Technical accuracy guaranteed

**Weaknesses:**
❌ Focused on configuration, not approval storage specifically
❌ Didn't explicitly address "Always Allow" persistence
❌ Required multiple fetches due to content length

---

## Critical Gap Identified

**⚠️ MISSING INFORMATION**: None of the tools provided clear documentation about where VS Code stores the specific approval decisions ("Always Allow", "Allow in Session", "Allow in Workspace") that users make when prompted during MCP tool execution.

The official documentation focuses on:
- Server configuration (`.vscode/mcp.json`, user settings)
- Input parameter storage (securely stored by VS Code)
- Server management commands

But does NOT document:
- Where approval decisions are persisted
- How to view/manage existing approvals
- File locations for authorization state

---

## Tool Effectiveness Assessment

| Tool | Speed | Accuracy | Depth | Directness | Best Use Case |
|------|-------|----------|-------|-------------|---------------|
| **Perplexity** | 🔥 Fast | 🎯 High | 📚 Deep | 🎯 Direct | Complex questions needing synthesis |
| **Brave Search** | 🔥 Fast | ⚖️ Variable | 🌐 Broad | 🔄 Indirect | Discovery and source finding |
| **Fetch** | 🔥 Fast | ✅ Highest | 📖 Focused | 📋 Specific | Official documentation access |

---

## Recommended Research Strategy

**For MCP server questions:**
1. **Start with Fetch** for official VS Code documentation
2. **Use Perplexity** for complex analysis and synthesis
3. **Use Brave Search** for community insights and discovery

**Next Steps Needed:**
- Look for VS Code source code or issue discussions about approval storage
- Test actual approval scenarios to observe file system changes
- Check VS Code extension storage patterns for similar features
