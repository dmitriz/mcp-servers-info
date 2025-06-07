# Research Starter Pack - MCP Servers 🎓

*A curated guide for researchers, academics, and knowledge workers to get started with MCP servers*

## 🚀 Quick Start

### Essential Research Setup

**Step 1: Enable MCP in VS Code**
```
File → Preferences → Settings → Search "chat.mcp.enabled" → Enable
```

**Step 2: Install Research Essentials**
```bash
# Knowledge management
npx -y @modelcontextprotocol/server-memory

# Web research  
npx -y @modelcontextprotocol/server-fetch

# Version control for research
npx -y @modelcontextprotocol/server-github

# Complex reasoning
npx -y @modelcontextprotocol/server-sequential-thinking
```

**Step 3: Basic Configuration**
Create `.vscode/mcp.json` in your research project:
```json
{
  "servers": {
    "memory": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    },
    "fetch": {
      "type": "stdio",
      "command": "npx", 
      "args": ["-y", "@modelcontextprotocol/server-fetch"]
    },
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
      }
    },
    "sequential-thinking": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    }
  }
}
```

## 🎯 Research Use Cases

### 📚 Literature Review Automation

**Configuration:**
```json
{
  "servers": {
    "fetch": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-fetch"] },
    "memory": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-memory"] },
    "sequential-thinking": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"] }
  }
}
```

**Workflow:**
1. **Fetch Papers**: Use fetch server to download academic papers
2. **Store Knowledge**: Use memory server to build research knowledge graph  
3. **Analyze Patterns**: Use sequential thinking for systematic analysis
4. **Generate Insights**: Create literature summaries and research gaps

### 🔬 Data Collection & Analysis

**Configuration:**
```json
{
  "servers": {
    "puppeteer": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-puppeteer"] },
    "postgresql": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-postgresql"] },
    "memory": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-memory"] }
  }
}
```

**Workflow:**
1. **Automate Collection**: Use Puppeteer for web scraping
2. **Store Data**: Use PostgreSQL for structured storage
3. **Build Context**: Use memory server for relationships
4. **Analyze Results**: Generate insights and visualizations

### 📊 Knowledge Management

**Configuration:**
```json
{
  "servers": {
    "memory": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-memory"] },
    "notion": { "type": "stdio", "command": "npx", "args": ["-y", "@notion/mcp-server"] },
    "github": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-github"] }
  }
}
```

**Workflow:**
1. **Central Memory**: Use memory server as knowledge hub
2. **Documentation**: Use Notion for structured notes
3. **Version Control**: Use GitHub for research versioning
4. **Cross-Reference**: Link concepts across platforms

## 🛠️ Advanced Research Configurations

### 🧠 AI-Enhanced Research Pipeline

**Full Stack Configuration:**
```json
{
  "servers": {
    "memory": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    },
    "sequential-thinking": {
      "type": "stdio", 
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    },
    "fetch": {
      "type": "stdio",
      "command": "npx", 
      "args": ["-y", "@modelcontextprotocol/server-fetch"]
    },
    "puppeteer": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-puppeteer"]
    },
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
      }
    },
    "neo4j": {
      "type": "http",
      "url": "http://localhost:7687/mcp",
      "env": {
        "NEO4J_URI": "bolt://localhost:7687",
        "NEO4J_USER": "${NEO4J_USERNAME}", 
        "NEO4J_PASSWORD": "${NEO4J_PASSWORD}"
      }
    }
  }
}
```

**Capabilities:**
- **Complex Reasoning**: Multi-step problem solving
- **Knowledge Graphs**: Relationship mapping and analysis
- **Web Automation**: Systematic data collection
- **Version Control**: Research process tracking
- **Graph Database**: Advanced relationship analysis

### 📈 Business Research Configuration

**Market Research Setup:**
```json
{
  "servers": {
    "fetch": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-fetch"] },
    "brave-search": { "type": "stdio", "command": "npx", "args": ["-y", "@modelcontextprotocol/server-brave-search"] },
    "linear": { "type": "stdio", "command": "npx", "args": ["-y", "@linear/mcp-server"] },
    "hubspot": { "type": "stdio", "command": "npx", "args": ["-y", "@hubspot/mcp-server"] }
  }
}
```

**Use Cases:**
- **Market Analysis**: Automated competitive research
- **Customer Research**: CRM data analysis
- **Trend Monitoring**: Web-based intelligence gathering
- **Project Management**: Research task coordination

## 🔒 Security for Researchers

### Academic Environment Setup

**Secure Configuration:**
```json
{
  "mcp": {
    "servers": {
      "memory": {
        "type": "stdio",
        "command": "npx", 
        "args": ["-y", "@modelcontextprotocol/server-memory"],
        "approval": {
          "read": "session",
          "write": "manual",
          "delete": "manual"
        }
      }
    },
    "security": {
      "auditLog": true,
      "sessionTimeout": "8h",
      "dataRetention": "90d"
    }
  }
}
```

### Research Data Protection

**Best Practices:**
1. **Environment Variables**: Store sensitive credentials securely
   ```bash
   # .env.mcp
   GITHUB_TOKEN=ghp_xxxxxxxxxxxx
   NEO4J_PASSWORD=secure_password
   OPENAI_API_KEY=sk-xxxxxxxxxxxx
   ```

2. **Workspace Isolation**: Separate configurations per project
3. **Approval Controls**: Manual approval for data modification
4. **Audit Logging**: Track all research operations
5. **Data Backup**: Regular knowledge graph exports

## 📚 Research-Specific Server Recommendations

### By Research Domain

**🔬 Scientific Research**
- **Memory Bank**: Knowledge graph for papers and concepts
- **Fetch**: Academic paper collection
- **Sequential Thinking**: Hypothesis generation and testing
- **PostgreSQL**: Experimental data storage
- **GitHub**: Research code and documentation

**📊 Business Research** 
- **HubSpot**: Customer data analysis
- **Linear**: Research project management
- **Brave Search**: Market intelligence
- **Puppeteer**: Competitive analysis automation
- **Notion**: Research documentation

**🎓 Academic Research**
- **Memory Bank**: Literature knowledge graph
- **Fetch**: Paper and resource collection
- **GitHub**: Research collaboration
- **Neo4j**: Citation network analysis
- **Slack**: Research team communication

**💼 Market Research**
- **Brave Search**: Market trend analysis
- **Puppeteer**: Competitor monitoring
- **Linear**: Research task tracking
- **Fetch**: Industry report collection
- **Memory Bank**: Market intelligence storage

### Quality Ratings for Research

**⭐⭐⭐⭐⭐ Essential (Must-Have)**
- Memory Bank MCP - Knowledge management foundation
- Sequential Thinking MCP - Complex reasoning support
- Fetch MCP - Web content acquisition
- GitHub MCP - Version control and collaboration

**⭐⭐⭐⭐ Highly Useful**
- Puppeteer MCP - Web automation and data collection
- Neo4j MCP - Advanced graph analysis
- Notion MCP - Documentation and knowledge organization
- PostgreSQL MCP - Structured data management

**⭐⭐⭐ Specialized Use Cases**
- Brave Search MCP - Web search automation
- Linear MCP - Project management integration
- Slack MCP - Team communication
- Time MCP - Research timeline management

## 🚀 Common Research Workflows

### Workflow: Academic Paper Analysis

**Setup Time**: 10 minutes  
**Servers**: Memory, Fetch, Sequential Thinking

**Process:**
- Configure memory server for knowledge storage
- Use fetch server to collect academic papers
- Apply sequential thinking for systematic analysis
- Build citation networks in memory graph
- Generate research summaries and insights

**Command Sequence:**
```bash
# Install required servers
npx -y @modelcontextprotocol/server-memory
npx -y @modelcontextprotocol/server-fetch  
npx -y @modelcontextprotocol/server-sequential-thinking
```

### Workflow: Market Intelligence Pipeline

**Setup Time**: 15 minutes  
**Servers**: Puppeteer, Memory, Brave Search, Linear

**Process:**
- Set up automated data collection with Puppeteer
- Store findings in memory knowledge graph
- Use Brave Search for supplementary research
- Track research tasks with Linear integration
- Generate competitive analysis reports

### Workflow: Collaborative Research Project

**Setup Time**: 20 minutes  
**Servers**: GitHub, Memory, Notion, Slack

**Process:**
- Set up version control with GitHub integration
- Create shared knowledge base with Memory server
- Document findings with Notion integration
- Coordinate team communication via Slack
- Maintain research reproducibility

## 🔧 Troubleshooting Common Issues

### Installation Problems

**Issue**: NPX installation fails
**Solution**: 
```bash
# Clear npm cache
npm cache clean --force

# Try global installation
npm install -g @modelcontextprotocol/server-memory

# Alternative: Use specific version
npx -y @modelcontextprotocol/server-memory@latest
```

**Issue**: Authentication errors
**Solution**:
```bash
# Check environment variables
echo $GITHUB_TOKEN

# Set in .env file
echo "GITHUB_TOKEN=your_token_here" >> .env.mcp
```

### Performance Optimization

**Issue**: Slow response times
**Solutions:**
1. **Local Database**: Use local PostgreSQL/Neo4j
2. **Caching**: Enable memory server caching
3. **Connection Pooling**: Configure database connections
4. **Resource Limits**: Monitor memory usage

### Configuration Validation

**Test Configuration:**
```bash
# Validate MCP configuration
npx @modelcontextprotocol/validate-config .vscode/mcp.json

# Test server connectivity  
npx @modelcontextprotocol/test-servers
```

## 📞 Getting Help

### Resources
- **Documentation**: [Official MCP Docs](https://modelcontextprotocol.io)
- **Community**: [GitHub Discussions](https://github.com/modelcontextprotocol/servers/discussions)
- **Examples**: [Research Templates](https://github.com/mcp-research-templates)
- **Support**: [VS Code MCP Guide](https://code.visualstudio.com/docs/copilot/chat/mcp-servers)

### Common Questions
- **Q**: Which servers are essential for academic research?
- **A**: Memory, Fetch, Sequential Thinking, and GitHub provide the core foundation

- **Q**: How do I secure sensitive research data?
- **A**: Use environment variables, enable audit logging, and configure manual approvals for write operations

- **Q**: Can I share configurations with my research team?
- **A**: Yes, commit `.vscode/mcp.json` to your repository and use environment variables for credentials

---

*Happy researching! 🎓📚*
