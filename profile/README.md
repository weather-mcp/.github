# Weather MCP

Open-source weather data ecosystem for Claude Desktop and AI assistants.

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Stars](https://img.shields.io/github/stars/weather-mcp?style=social)](https://github.com/weather-mcp)
[![Discord](https://img.shields.io/badge/Discord-Join-7289DA?logo=discord&logoColor=white)](https://discord.gg/SEBvEa3YXr)

[MCP Server](https://github.com/weather-mcp/weather-mcp) • [Community](https://github.com/weather-mcp/weather-mcp/discussions) • [Discord](https://discord.gg/SEBvEa3YXr)

**Coming Soon:** [Website](https://weather-mcp.dev) • [Dashboard](https://weather-mcp.dev/dashboard) • [Documentation](https://weather-mcp.dev/docs)

</div>

---

## 🌤️ What is Weather MCP?

**Weather MCP** is a comprehensive Model Context Protocol (MCP) ecosystem that brings real-world weather data to AI assistants like Claude Desktop. It consists of three main components working together to provide weather intelligence, analytics insights, and community resources.

### Core Features

✅ **12 Weather Tools** - Forecasts, alerts, historical data, air quality, marine conditions, and more
✅ **Multi-Provider Support** - Automatic fallback between NOAA and Open-Meteo
✅ **Global Coverage** - US-focused with NOAA, worldwide with Open-Meteo
✅ **No API Keys Required** - Free access to all weather data
✅ **Privacy-First Analytics** - Optional, anonymous usage tracking
✅ **Open Source** - MIT licensed, community-driven

---

## 📦 Projects

<table>
  <tr>
    <td width="33%" align="center">
      <h3>🌤️ MCP Server</h3>
      <p><strong>Status:</strong> Production (v1.6.1)</p>
      <p>Core MCP server for weather data access</p>
      <p>
        <a href="https://github.com/weather-mcp/weather-mcp">
          <img src="https://img.shields.io/github/stars/weather-mcp/weather-mcp?style=social" alt="Stars">
        </a>
      </p>
      <p>
        <a href="https://github.com/weather-mcp/weather-mcp">📖 Documentation</a> •
        <a href="https://github.com/weather-mcp/weather-mcp/issues">🐛 Issues</a>
      </p>
    </td>
    <td width="33%" align="center">
      <h3>📊 Analytics Server</h3>
      <p><strong>Status:</strong> Planning</p>
      <p>Privacy-first analytics collection API</p>
      <p>
        <a href="https://github.com/weather-mcp/analytics-server">
          <img src="https://img.shields.io/github/stars/weather-mcp/analytics-server?style=social" alt="Stars">
        </a>
      </p>
      <p>
        <a href="https://github.com/weather-mcp/analytics-server">📖 Documentation</a> •
        <a href="https://github.com/weather-mcp/analytics-server/issues">🐛 Issues</a>
      </p>
    </td>
    <td width="33%" align="center">
      <h3>🌐 Website</h3>
      <p><strong>Status:</strong> Planning</p>
      <p>Public website and analytics dashboard</p>
      <p>
        <a href="https://github.com/weather-mcp/website">
          <img src="https://img.shields.io/github/stars/weather-mcp/website?style=social" alt="Stars">
        </a>
      </p>
      <p>
        <a href="https://github.com/weather-mcp/website">📖 Documentation</a> •
        <a href="https://github.com/weather-mcp/website/issues">🐛 Issues</a>
      </p>
    </td>
  </tr>
</table>

---

## 🚀 Quick Start

### Install MCP Server

```bash
# Install via npm
npm install -g @dangahagan/weather-mcp

# Or clone and build from source
git clone https://github.com/weather-mcp/weather-mcp.git
cd mcp-server
npm install
npm run build
```

### Configure Claude Desktop

Add to your Claude Desktop MCP settings:

```json
{
  "mcpServers": {
    "weather": {
      "command": "npx",
      "args": ["-y", "@dangahagan/weather-mcp"]
    }
  }
}
```

### Start Using Weather Tools

Ask Claude:
- "What's the weather forecast for Seattle this week?"
- "Are there any weather alerts for Miami?"
- "Show me historical weather data for New York in July 2020"

**[📖 Full Installation Guide →](https://github.com/weather-mcp/weather-mcp#installation)**

---

## 🌟 Available Weather Tools

| Tool | Description | Coverage | Data Source |
|------|-------------|----------|-------------|
| `get_forecast` | 7-day weather forecasts | US + Global | NOAA / Open-Meteo |
| `get_current_conditions` | Current weather + fire weather | US Only | NOAA |
| `get_alerts` | Weather warnings and alerts | US Only | NOAA |
| `get_historical_weather` | Historical data (1940-present) | Global | Open-Meteo |
| `get_air_quality` | Air quality index & pollutants | Global | Open-Meteo |
| `get_marine_conditions` | Wave height, swell, currents | Global | Open-Meteo |
| `get_river_conditions` | River levels & flood monitoring | US Only | NOAA / USGS |
| `get_wildfire_info` | Active wildfire tracking | US Only | NIFC |
| `search_location` | Location search / geocoding | Global | Open-Meteo |
| `check_service_status` | API health check | All | All services |

**[📖 Full API Reference →](https://github.com/weather-mcp/weather-mcp/tree/main/docs)**

---

## 🔒 Privacy & Analytics

Weather MCP respects your privacy:

- **No API Keys Required** - All weather APIs are free and public
- **Optional Analytics** - Opt-in only, disabled by default
- **Anonymous Data** - No PII, coordinates, or location names collected
- **Open Source** - All code is auditable
- **Transparent** - Public analytics dashboard showing aggregate usage

**[📖 Privacy Policy →](https://github.com/weather-mcp/weather-mcp/blob/main/docs/ANALYTICS_MCP_PLAN.md)**

---

## 📊 Live Stats 🚧 Coming Soon

<div align="center">

Once the analytics server is deployed, live usage statistics will be available here:

| Metric | Status |
|--------|--------|
| **Total API Calls (24h)** | Coming Soon |
| **Success Rate** | Coming Soon |
| **Active Installations** | Coming Soon |

**[📊 View Full Dashboard →](https://weather-mcp.dev/dashboard)** *(Coming Soon)*

</div>

---

## 🤝 Contributing

We welcome contributions to any Weather MCP project!

### Ways to Contribute

- 🐛 **Report Bugs** - Open an issue in the relevant repository
- 💡 **Suggest Features** - Share your ideas in GitHub Discussions
- 📝 **Improve Documentation** - Help make our docs better
- 🔧 **Submit Pull Requests** - Fix bugs or add features
- ⭐ **Star Our Repos** - Show your support!

### Getting Started

1. **Choose a project** to contribute to:
   - [MCP Server](https://github.com/weather-mcp/weather-mcp) - Node.js/TypeScript
   - [Analytics Server](https://github.com/weather-mcp/analytics-server) - Fastify/PostgreSQL
   - [Website](https://github.com/weather-mcp/website) - Next.js/React

2. **Read the contributing guide** for that project

3. **Fork, code, and submit a PR** following the project's guidelines

**[📖 Contributing Guide →](https://github.com/weather-mcp/weather-mcp/blob/main/CONTRIBUTING.md)**

---

## 🗺️ Roadmap

### Current (v1.6.x)
- ✅ Production-ready MCP server
- ✅ 12 weather tools with comprehensive coverage
- ✅ Multi-provider support with automatic fallback
- ✅ Extensive testing and documentation

### Coming Soon (v1.7+)
- 🚧 Analytics server deployment
- 🚧 Public website and dashboard launch
- 🚧 Optional opt-in analytics for product improvement
- 🚧 Additional weather providers (NWS, etc.)

### Future (v2.0+)
- 📋 Mobile app integration
- 📋 Plugin system for custom data sources
- 📋 Real-time weather alerts via WebSocket
- 📋 Community showcase and examples

**[📖 Full Roadmap →](https://github.com/weather-mcp/weather-mcp/blob/main/ROADMAP.md)**

---

## 🌍 Community

<div align="center">

### Join the Weather MCP Community

[![GitHub Discussions](https://img.shields.io/badge/GitHub-Discussions-181717?logo=github)](https://github.com/weather-mcp/weather-mcp/discussions)
[![Discord](https://img.shields.io/badge/Discord-Join%20Server-7289DA?logo=discord&logoColor=white)](https://discord.gg/SEBvEa3YXr)
[![Twitter](https://img.shields.io/badge/Twitter-Follow-1DA1F2?logo=twitter&logoColor=white)](https://twitter.com/weather_mcp)

</div>

- **[GitHub Discussions](https://github.com/weather-mcp/weather-mcp/discussions)** - Ask questions, share ideas
- **[Discord Server](https://discord.gg/SEBvEa3YXr)** - Real-time chat with the community
- **[Twitter](https://twitter.com/weather_mcp)** - Updates and announcements
- **[Community Showcase](https://weather-mcp.dev/community/showcase)** - See what others are building *(Coming Soon)*

---

## 📚 Resources

### Documentation
- [MCP Server Documentation](https://github.com/weather-mcp/weather-mcp#readme)
- [API Reference](https://github.com/weather-mcp/weather-mcp/tree/main/docs)
- [Installation Guide](https://github.com/weather-mcp/weather-mcp#installation)
- [Configuration Options](https://github.com/weather-mcp/weather-mcp#configuration)

### Developer Resources
- [Model Context Protocol Spec](https://spec.modelcontextprotocol.io/)
- [NOAA API Documentation](https://www.weather.gov/documentation/services-web-api)
- [Open-Meteo API Documentation](https://open-meteo.com/en/docs)

### Project Information
- [Security Policy](https://github.com/weather-mcp/weather-mcp/blob/main/SECURITY.md)
- [License (MIT)](https://github.com/weather-mcp/weather-mcp/blob/main/LICENSE)
- [Code of Conduct](https://github.com/weather-mcp/weather-mcp/blob/main/CODE_OF_CONDUCT.md)

---

## 💖 Sponsors

Weather MCP is free and open source. If you find it useful, consider supporting the project:

<div align="center">

[![Sponsor on GitHub](https://img.shields.io/badge/Sponsor-GitHub-EA4AAA?logo=github-sponsors&logoColor=white)](https://github.com/sponsors/weather-mcp)
[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-FFDD00?logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/weathermcp)

</div>

---

## 📧 Contact

- **General Inquiries**: hello@weather-mcp.dev
- **Security Issues**: security@weather-mcp.dev
- **Twitter**: [@weather_mcp](https://twitter.com/weather_mcp)

---

## 📄 License

All Weather MCP projects are licensed under the [MIT License](https://opensource.org/licenses/MIT).

```
Copyright (c) 2025 Dan Gahagan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

<div align="center">

**Made with ☀️ by [Dan Gahagan](https://github.com/dgahagan) and [contributors](https://github.com/weather-mcp/weather-mcp/graphs/contributors)**

⭐ Star our repos • 🐛 Report bugs • 💡 Suggest features • 🤝 Contribute

[MCP Server](https://github.com/weather-mcp/weather-mcp) • [Discussions](https://github.com/weather-mcp/weather-mcp/discussions) • [Discord](https://discord.gg/SEBvEa3YXr)

**Coming Soon:** [Website](https://weather-mcp.dev) • [Dashboard](https://weather-mcp.dev/dashboard) • [Documentation](https://weather-mcp.dev/docs)

</div>
