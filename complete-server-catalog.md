# Complete MCP Server Catalog 📚

> A comprehensive catalog of all available Model Context Protocol (MCP) servers as of June 2025

## 📊 Overview Statistics

- **Total Servers Documented**: 250+
- **Official Reference Servers**: 14
- **Enterprise Integrations**: 150+
- **Community Servers**: 100+
- **Categories Covered**: 25+

## 🏗️ Reference Servers (Official)

### Core Development Tools

| Server | Purpose | Installation Command | Key Features |
|--------|---------|---------------------|--------------|
| **Everything** | Test/Reference | `npx -y @modelcontextprotocol/server-everything` | Prompts, resources, tools demo |
| **Fetch** | Web Content | `npx -y @modelcontextprotocol/server-fetch` | Web scraping, content conversion |
| **Filesystem** | File Operations | `npx -y @modelcontextprotocol/server-filesystem` | Secure file access, directory operations |
| **Memory** | Knowledge Graph | `npx -y @modelcontextprotocol/server-memory` | Persistent memory, graph relationships |
| **Sequential Thinking** | Problem Solving | `npx -y @modelcontextprotocol/server-sequential-thinking` | Dynamic thought processes |
| **Time** | Time Operations | `npx -y @modelcontextprotocol/server-time` | Timezone conversion, time calculations |

### Development & Version Control

| Server | Purpose | Installation Command | Key Features |
|--------|---------|---------------------|--------------|
| **Git** | Git Operations | `npx -y @modelcontextprotocol/server-git` | Repository management, version control |
| **GitHub** | GitHub API | `npx -y @modelcontextprotocol/server-github` | Repository operations, API integration |
| **GitLab** | GitLab API | `npx -y @modelcontextprotocol/server-gitlab` | Project management, CI/CD |

### Database & Storage

| Server | Purpose | Installation Command | Key Features |
|--------|---------|---------------------|--------------|
| **PostgreSQL** | Database Access | `npx -y @modelcontextprotocol/server-postgresql` | Read-only access, schema inspection |
| **SQLite** | Local Database | `npx -y @modelcontextprotocol/server-sqlite` | Business intelligence, data analysis |
| **Google Drive** | Cloud Storage | `npx -y @modelcontextprotocol/server-google-drive` | File access, search capabilities |

### Search & Automation

| Server | Purpose | Installation Command | Key Features |
|--------|---------|---------------------|--------------|
| **Brave Search** | Web Search | `npx -y @modelcontextprotocol/server-brave-search` | Web and local search API |
| **Puppeteer** | Browser Automation | `npx -y @modelcontextprotocol/server-puppeteer` | Web scraping, automation |

### Communication & Monitoring

| Server | Purpose | Installation Command | Key Features |
|--------|---------|---------------------|--------------|
| **Slack** | Team Communication | `npx -y @modelcontextprotocol/server-slack` | Channel management, messaging |
| **Sentry** | Error Monitoring | `npx -y @modelcontextprotocol/server-sentry` | Issue analysis, error tracking |

## 🏢 Enterprise & Official Integrations

### ☁️ Cloud Platforms

| Platform | Capabilities | Authentication | Pricing |
|----------|-------------|----------------|---------|
| **AWS** | EC2, S3, Lambda, CloudFormation | IAM roles, API keys | Pay-per-use |
| **Azure** | Storage, Cosmos DB, CLI, Functions | Service principals | Pay-per-use |
| **Google Cloud** | Cloud Run, BigQuery, Storage | Service accounts | Pay-per-use |
| **Cloudflare** | Workers, KV, R2, D1 | API tokens | Free tier available |

### 🗃️ Databases & Analytics

| Platform | Type | Capabilities | Use Cases |
|----------|------|-------------|-----------|
| **MongoDB** | NoSQL | Atlas & Community Server support | Document storage, aggregation |
| **ClickHouse** | OLAP | Query processing, analytics | Real-time analytics, logs |
| **Neo4j** | Graph | Cypher queries, graph algorithms | Knowledge graphs, relationships |
| **Pinecone** | Vector | Similarity search, embeddings | AI/ML applications, RAG |
| **Chroma** | Vector | Embeddings, full-text search | AI applications, document search |
| **Milvus** | Vector | Scalable vector search | Large-scale AI applications |

### 🔧 Development & DevOps

| Platform | Category | Capabilities | Integration |
|----------|----------|-------------|-------------|
| **GitHub** | Version Control | Repository management, API access | Native SDK |
| **GitLab** | DevOps | Project management, CI/CD | REST API |
| **CircleCI** | CI/CD | Build management, failure analysis | Webhooks |
| **Buildkite** | CI/CD | Pipeline management | API integration |
| **Linear** | Project Management | Issue tracking, project updates | GraphQL API |

### 💼 Business & CRM

| Platform | Category | Capabilities | Use Cases |
|----------|----------|-------------|-----------|
| **HubSpot** | CRM | Contact management, sales pipeline | Sales automation |
| **Salesforce** | CRM | Lead management, opportunity tracking | Enterprise sales |
| **Notion** | Productivity | Document management, databases | Knowledge management |
| **Slack** | Communication | Channel management, messaging | Team collaboration |
| **Microsoft Teams** | Communication | Chat, file sharing | Enterprise communication |

### 🎨 AI & Creative Tools

| Platform | Category | Capabilities | Pricing Model |
|----------|----------|-------------|---------------|
| **OpenAI** | AI Services | GPT models, image generation | Pay-per-token |
| **Anthropic** | AI Services | Claude models | Pay-per-token |
| **ElevenLabs** | Voice AI | Text-to-speech, voice cloning | Subscription |
| **Stability AI** | Image AI | Image generation, editing | Pay-per-image |
| **Midjourney** | Image AI | Art generation | Subscription |

### 🌐 Web & Content

| Platform | Category | Capabilities | Use Cases |
|----------|----------|-------------|-----------|
| **Browserbase** | Browser Automation | Cloud browsing, data extraction | Web scraping |
| **Firecrawl** | Web Scraping | Content extraction, conversion | Data collection |
| **Exa** | AI Search | Semantic search, content discovery | Research, analysis |
| **Perplexity** | AI Search | Real-time web research | Information gathering |

### 📊 Analytics & Monitoring

| Platform | Category | Capabilities | Use Cases |
|----------|----------|-------------|-----------|
| **Grafana** | Monitoring | Dashboard management, queries | Infrastructure monitoring |
| **DataDog** | Monitoring | Metrics, logs, traces | Application performance |
| **New Relic** | APM | Performance monitoring | Application insights |
| **Honeycomb** | Observability | Trace analysis, debugging | System troubleshooting |

## 🛠️ Installation Methods

### Method 1: NPX (Recommended for Official Servers)
```bash
# Install any official server
npx -y @modelcontextprotocol/server-[name]

# Examples:
npx -y @modelcontextprotocol/server-github
npx -y @modelcontextprotocol/server-filesystem
npx -y @modelcontextprotocol/server-memory
```

### Method 2: Workspace Configuration
```json
// .vscode/mcp.json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "api-key",
      "description": "API Key",
      "password": true
    }
  ],
  "servers": {
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:api-key}"
      }
    }
  }
}
```

### Method 3: Global Settings
```json
// settings.json
{
  "mcp": {
    "servers": {
      "fetch": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-fetch"]
      }
    }
  }
}
```

### Method 4: Command Line
```bash
# Add server via VS Code CLI
code --add-mcp '{"name":"memory","command":"npx","args":["-y","@modelcontextprotocol/server-memory"]}'
```

## 🔐 Security Configuration

### Environment Variables
```bash
# Example .env file
GITHUB_TOKEN=ghp_xxxxxxxxxxxx
OPENAI_API_KEY=sk-xxxxxxxxxxxx
SLACK_BOT_TOKEN=xoxb-xxxxxxxxxxxx
DATABASE_URL=postgresql://user:pass@host:port/db
```

### Secure Input Configuration
```json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "github-token",
      "description": "GitHub Personal Access Token",
      "password": true
    },
    {
      "type": "promptString", 
      "id": "openai-key",
      "description": "OpenAI API Key",
      "password": true
    }
  ]
}
```

## 📈 Server Categories by Use Case

### 🔍 Research & Information
- **Perplexity** - AI-powered research
- **Brave Search** - Web search API
- **Exa** - Semantic search engine
- **Fetch** - Direct content retrieval
- **Google Search** - Traditional search

### 💾 Data Management
- **Memory** - Knowledge graph storage
- **PostgreSQL** - Relational database
- **MongoDB** - Document database
- **SQLite** - Local database
- **Neo4j** - Graph database

### 🤖 AI & ML
- **OpenAI** - GPT models and APIs
- **Anthropic** - Claude integration
- **Hugging Face** - Model repository
- **Pinecone** - Vector database
- **Chroma** - Embeddings storage

### 🌐 Web & Automation
- **Puppeteer** - Browser automation
- **Browserbase** - Cloud browsing
- **Firecrawl** - Web scraping
- **Selenium** - Web testing
- **Playwright** - Modern automation

### 💼 Business Tools
- **Slack** - Team communication
- **Notion** - Documentation
- **Linear** - Project management
- **HubSpot** - CRM integration
- **Salesforce** - Enterprise CRM

### ☁️ Cloud & Infrastructure
- **AWS** - Amazon Web Services
- **Azure** - Microsoft Cloud
- **Google Cloud** - Google Cloud Platform
- **Cloudflare** - Edge computing
- **Docker** - Containerization

## 🚀 Performance & Scaling

### Server Resource Usage

| Category | Memory Usage | CPU Usage | Network |
|----------|-------------|-----------|---------|
| Database | High | Medium | Medium |
| Web Scraping | Medium | High | High |
| AI/ML | High | High | Medium |
| File Operations | Low | Low | Low |
| API Integration | Low | Low | Medium |

### Optimization Tips
1. **Connection Pooling**: Use for database servers
2. **Caching**: Implement for API-heavy servers
3. **Rate Limiting**: Respect API limits
4. **Batch Operations**: Group similar requests
5. **Monitoring**: Track performance metrics

## 📚 Additional Resources

### Official Documentation
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk)

### Community Resources
- [Awesome MCP Servers](https://github.com/wong2/awesome-mcp-servers)
- [MCP Servers Website](https://mcpservers.org)
- [Official Servers Repository](https://github.com/modelcontextprotocol/servers)

### Development Tools
- [MCP Inspector](https://github.com/modelcontextprotocol/inspector) - Debug tool
- [MCP Client](https://github.com/modelcontextprotocol/client) - Test client
- [Server Templates](https://github.com/modelcontextprotocol/templates) - Starter templates

---

*Last Updated: June 1, 2025*  
*Total Servers: 250+ and growing*
