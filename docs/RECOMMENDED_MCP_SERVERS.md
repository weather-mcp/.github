# Recommended MCP Servers for Weather MCP Development

This guide provides recommendations for Model Context Protocol (MCP) servers that enhance development workflows for the Weather MCP project.

## Overview

MCP servers extend AI assistants with additional capabilities like accessing documentation, managing repositories, querying databases, and more. This document recommends servers specifically useful for working on:

- **weather-mcp/weather-mcp** - Node.js/TypeScript MCP server
- **weather-mcp/analytics-server** - Fastify, PostgreSQL/TimescaleDB, Redis
- **weather-mcp/website** - Next.js 14, React, Tailwind CSS

---

## 🎯 Tier 1: Essential Servers

These servers provide foundational capabilities for Weather MCP development.

### 1. Context7 - Up-to-Date Documentation ⭐⭐⭐

**What it does:** Provides version-specific, up-to-date documentation and code examples directly from the source for any framework or library.

**Why useful for Weather MCP:**
- Access latest Next.js 14, React, TypeScript documentation
- Get current PostgreSQL/TimescaleDB documentation
- Reference MCP protocol specifications
- Access NOAA API and Open-Meteo API documentation
- Eliminates outdated or generic information

**Installation:**
```bash
npx -y @upstash/context7-mcp --api-key YOUR_API_KEY
```

**Configuration:**
- API key is optional but provides higher rate limits
- Get API key at: https://context7.com/dashboard
- Supports both HTTP and stdio transports

**Use cases:**
- "What's new in Next.js 14 App Router?"
- "Show me PostgreSQL TimescaleDB hypertable examples"
- "How do I implement MCP tool handlers?"

---

### 2. GitHub Official MCP Server ⭐⭐⭐

**What it does:** Complete GitHub repository management including issues, PRs, code reviews, project boards, and workflows.

**Why useful for Weather MCP:**
- Manage all three repositories (weather-mcp, analytics-server, website)
- Create and review pull requests
- Triage bugs and manage issues
- Access GitHub Actions and code security tools
- Read-only mode available for safety

**Installation:**
```bash
npx @modelcontextprotocol/server-github
```

**Configuration:**
- Local: Use Docker with personal access tokens
- Remote: OAuth via https://api.githubcopilot.com/mcp/
- Supports toolsets: repos, issues, pull_requests, actions, code_security
- Read-only mode available with specific configuration

**Key features:**
- Consolidated tools (pull_request_read combines multiple PR tools)
- Server instructions for workflow guidance
- GitHub Projects support

**Use cases:**
- "Create an issue for the analytics server planning"
- "Show me open PRs across all repos"
- "List recent commits in weather-mcp repository"

---

### 3. Filesystem MCP Server ⭐⭐⭐

**What it does:** Secure file operations with configurable access controls, including read, write, search, and directory management.

**Why useful for Weather MCP:**
- Manage files across all three projects
- Search for files and content recursively
- Read/write configuration files
- Secure access control to specific directories

**Installation:**
```bash
# Specify allowed directories
npx @modelcontextprotocol/server-filesystem /home/dgahagan/work/personal/weather-mcp
```

**Features:**
- `read_file`, `read_multiple_files`
- `list_directory`, `search_files`
- `get_file_info`, `write_file`, `edit_file`
- `create_directory`
- Content search with depth and result limits
- Case-insensitive pattern matching

**Use cases:**
- "Find all TypeScript files with 'axios' imports"
- "Read package.json from all three repos"
- "List all markdown files in docs/"

---

### 4. PostgreSQL MCP Server ⭐⭐

**What it does:** Interact with PostgreSQL databases for schema exploration, queries, and analysis.

**Why useful for Weather MCP:**
- Direct database interaction for analytics-server
- Schema exploration and relationship discovery
- Query performance analysis
- Index recommendations

**Two Options:**

#### Option A: Postgres MCP Pro (Recommended for Development)
```bash
npx @crystaldba/postgres-mcp
```

**Features:**
- Query performance analysis
- Index recommendations
- Schema exploration
- Supports development through production

#### Option B: Official PostgreSQL Server (Read-Only)
```bash
npx @modelcontextprotocol/server-postgres
```

**Features:**
- Safer for production environments
- Schema exploration
- Read-only query execution

**Recommendation:** Use Postgres MCP Pro for development, official read-only server for production queries.

**Use cases:**
- "Show me the schema for the analytics database"
- "Analyze query performance for event insertion"
- "Suggest indexes for the time-series tables"

---

## 🔧 Tier 2: Highly Recommended

These servers significantly enhance productivity for specific tasks.

### 5. MCP Omnisearch - Web Search ⭐⭐

**What it does:** Unified access to multiple search engines (Tavily, Brave, Kagi) and AI tools (Perplexity, Exa, Jina AI).

**Why useful for Weather MCP:**
- Research weather API documentation
- Find solutions to technical problems
- Access up-to-date information beyond AI knowledge cutoff
- Privacy-focused search options (Brave)
- Academic research capabilities (Exa)

**Installation:**
```bash
npx @spences10/mcp-omnisearch
```

**Search engines included:**
- **Tavily:** Optimized for factual information with citations
- **Brave:** Privacy-focused with advanced operators (site:, filetype:, etc.)
- **Exa:** Real-time web search and academic papers
- **Perplexity:** AI-powered search
- **Jina AI:** Content processing and summarization

**Use cases:**
- "Search for NOAA API rate limiting best practices"
- "Find recent TimescaleDB performance optimization articles"
- "Research Next.js 14 server components patterns"

---

### 6. Git MCP Server ⭐⭐

**What it does:** Read, search, and manipulate Git repositories programmatically.

**Why useful for Weather MCP:**
- Work with multiple Git repos simultaneously
- Search commit history across projects
- Analyze repository changes
- Automate Git operations

**Installation:**
```bash
npx @modelcontextprotocol/server-git
```

**Features:**
- Repository reading and searching
- Commit history analysis
- Branch management
- Secure, controlled Git operations

**Use cases:**
- "Show me commits related to cache implementation"
- "Compare branches across the three repos"
- "List all contributors to the MCP server"

---

### 7. Memory MCP Server - Knowledge Graph ⭐⭐

**What it does:** Knowledge graph-based persistent memory system using local SQLite storage.

**Why useful for Weather MCP:**
- Remember project-specific context across sessions
- Track relationships between different parts of your stack
- Maintain development notes and decisions
- Store useful code patterns and solutions
- Vector-based semantic search

**Installation:**
```bash
npx @modelcontextprotocol/server-memory
```

**Alternatives:**
- `@spences10/mcp-memory-sqlite`
- `mcp-knowledge-graph` (with fuzzy search)

**Features:**
- Local SQLite storage (completely private)
- Entity and relationship tracking
- Observations and notes
- Vector search for semantic queries
- Persistent across conversations

**Use cases:**
- "Remember that we use Fastify for the analytics server"
- "Store the decision to use TimescaleDB for time-series data"
- "What design patterns have we used in this project?"

---

### 8. Package Version MCP Server ⭐

**What it does:** Provides latest stable package versions from npm, PyPI, Maven, and other registries.

**Why useful for Weather MCP:**
- Ensure you're using current package versions
- Check for updates across Node.js projects
- Get package information and dependencies
- Maintain up-to-date dependencies

**Installation:**
```bash
npx mcp-package-version
```

**Alternative:**
```bash
npx @mateusribeirocampos/npm-mcp-server
```

**Features:**
- Multi-registry support (npm, PyPI, Maven)
- Latest version checking
- Dependency information
- Package metadata

**Use cases:**
- "What's the latest version of @modelcontextprotocol/sdk?"
- "Check if Next.js has any updates"
- "Show me the latest stable TypeScript version"

---

## 🛠️ Tier 3: Useful for Specific Tasks

### 9. Fetch MCP Server

**What it does:** Web content retrieval and conversion optimized for LLM processing.

**Why useful for Weather MCP:**
- Fetch and convert API documentation
- Retrieve web content for analysis
- Convert HTML to markdown
- Optimize content for AI consumption

**Installation:**
```bash
npx @modelcontextprotocol/server-fetch
```

**Use cases:**
- "Fetch the NOAA API documentation page"
- "Convert Open-Meteo API docs to markdown"

---

### 10. Next.js DevTools MCP Server

**What it does:** Direct access to Next.js dev server's runtime errors, routes, logs, and application state.

**Why useful for Weather MCP website:**
- Real-time debugging information
- Route inspection
- Error tracking
- Application state monitoring

**Installation:**
```bash
npx next-devtools-mcp
```

**Note:** Requires Next.js 16+. Website is currently on Next.js 14, so this will be useful after upgrading.

---

### 11. Sequential Thinking MCP Server

**What it does:** Enables dynamic, reflective problem-solving through structured thought processes.

**Why useful for Weather MCP:**
- Break down complex architectural decisions
- Work through multi-step implementations
- Revise and refine approaches dynamically
- Generate and verify solution hypotheses

**Installation:**
```bash
npx @modelcontextprotocol/server-sequential-thinking
```

**Use cases:**
- "Plan the analytics server database schema"
- "Design the website dashboard architecture"

---

### 12. Time MCP Server

**What it does:** Time and timezone conversion capabilities.

**Why useful for Weather MCP:**
- Handle timezone conversions for weather data
- Work with UTC timestamps
- Convert between time formats

**Installation:**
```bash
npx @modelcontextprotocol/server-time
```

**Use cases:**
- "Convert UTC timestamp to PST"
- "What timezone is this weather data in?"

---

## 🚀 Recommended Installation Order

1. **Context7** - Start here for immediate documentation access
2. **GitHub** - Repository management across all 3 repos
3. **Filesystem** - File operations across projects
4. **PostgreSQL** - When you start working on analytics-server
5. **Memory** - Persist project knowledge across sessions
6. **Omnisearch** - Research and problem solving
7. **Git** - Advanced Git operations
8. **Others** - Add as needed for specific tasks

---

## ⚙️ Configuration Tips

### Security Best Practices

- **Use read-only modes initially** for GitHub and PostgreSQL servers
- **Configure Filesystem server** with specific allowed directories only
- **Store API keys** in environment variables, not in configuration files
- **Use GitHub OAuth** for remote access (more secure than Personal Access Tokens)

### Directory Configuration

For the Filesystem server, specify your workspace directory:
```bash
npx @modelcontextprotocol/server-filesystem /home/dgahagan/work/personal/weather-mcp
```

This allows access to all four repos (weather-mcp, analytics-server, website, .github).

### Database Configuration

For PostgreSQL, use connection strings with minimal privileges:
```bash
# Development
postgresql://user:password@localhost:5432/analytics_dev

# Production (read-only recommended)
postgresql://readonly_user:password@localhost:5432/analytics_prod
```

---

## 📚 Official Resources

- **MCP Registry:** https://registry.modelcontextprotocol.io
- **MCP Documentation:** https://modelcontextprotocol.io
- **Official Servers Repository:** https://github.com/modelcontextprotocol/servers
- **GitHub MCP Registry Blog:** https://github.blog/ai-and-ml/generative-ai/how-to-find-install-and-manage-mcp-servers-with-the-github-mcp-registry/
- **Context7 Documentation:** https://context7.com

---

## 🔄 Installation Methods

Most MCP servers can be installed using one of these methods:

### npx (Node.js)
```bash
npx @scope/package-name
```

### Docker
```bash
docker run -i mcp/server-name
```

### Claude Code CLI
```bash
claude mcp add server-name -- npx -y @scope/package-name
```

---

## 💡 Usage Examples

### Context7
```
"Show me the latest Next.js 14 data fetching patterns"
"What's the current TypeScript configuration best practices?"
"How do I implement TimescaleDB continuous aggregates?"
```

### GitHub
```
"List all open issues in weather-mcp repository"
"Create a PR for the analytics server schema changes"
"Show me recent commits across all repos"
```

### Filesystem
```
"Find all files containing 'cache' in the MCP server"
"Read the package.json from all three projects"
"Search for TypeScript errors in the codebase"
```

### PostgreSQL
```
"Show me the analytics database schema"
"Analyze the performance of the event insertion query"
"Suggest indexes for the time-series queries"
```

---

## 🔍 Finding More Servers

New MCP servers are being released regularly. To discover more:

1. **Browse the Official Registry:** https://registry.modelcontextprotocol.io
2. **Search GitHub:** Look for repositories tagged with "mcp-server"
3. **Check npm:** Search for packages with "mcp" in the name
4. **Follow MCP Community:** GitHub discussions and Discord channels

---

## 📝 Contributing to This Guide

This document should be updated as:
- New useful MCP servers are discovered
- Project requirements change
- Better configurations are found
- Team feedback is received

To suggest updates, open an issue or PR in the `.github` repository.

---

## License

This documentation is part of the Weather MCP project and is licensed under the [MIT License](../LICENSE).

---

**Last Updated:** 2025-11-11
**Maintainer:** Weather MCP Organization
**Repository:** https://github.com/weather-mcp/.github
