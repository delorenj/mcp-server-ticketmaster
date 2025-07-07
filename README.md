[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/delorenj-mcp-server-ticketmaster-badge.png)](https://mseep.ai/app/delorenj-mcp-server-ticketmaster)

# MCP Server for Ticketmaster
[![smithery badge](https://smithery.ai/badge/mcp-server-ticketmaster)](https://smithery.ai/server/mcp-server-ticketmaster)

A Model Context Protocol server that provides tools for discovering events, venues, and attractions through the Ticketmaster Discovery API.

<a href="https://glama.ai/mcp/servers/u91gv8f3on"><img width="380" height="200" src="https://glama.ai/mcp/servers/u91gv8f3on/badge" alt="Server for Ticketmaster Events MCP server" /></a>

## Features

- Search for events, venues, and attractions with flexible filtering:
  - Keyword search
  - Date range for events
  - Location (city, state, country)
  - Venue-specific searches
  - Attraction-specific searches
  - Event classifications/categories
- Output formats:
  - Structured JSON data for programmatic use
  - Human-readable text for direct consumption
- Comprehensive data including:
  - Names and IDs
  - Dates and times (for events)
  - Price ranges (for events)
  - URLs
  - Images
  - Locations and addresses (for venues)
  - Classifications (for attractions)

## Installation

### Installing via Smithery

To install mcp-server-ticketmaster for Claude Desktop automatically via [Smithery](https://smithery.ai/server/mcp-server-ticketmaster):

```bash
npx -y @smithery/cli install mcp-server-ticketmaster --client claude
```

### Manual Installation
```bash
npx -y install @delorenj/mcp-server-ticketmaster
```

## Configuration

The server requires a Ticketmaster API key. You can get one by:
1. Going to https://developer.ticketmaster.com/
2. Creating an account or signing in
3. Going to "My Apps" in your account
4. Creating a new app to get your API key

Set your API key in your MCP settings file:

```json
{
  "mcpServers": {
    "ticketmaster": {
      "command": "npx",
      "args": ["-y", "@delorenj/mcp-server-ticketmaster"],
      "env": {
        "TICKETMASTER_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Usage

The server provides a tool called `search_ticketmaster` that accepts:

### Required Parameters
- `type`: Type of search ('event', 'venue', or 'attraction')

### Optional Parameters
- `keyword`: Search term
- `startDate`: Start date in YYYY-MM-DD format (for events)
- `endDate`: End date in YYYY-MM-DD format (for events)
- `city`: City name
- `stateCode`: State code (e.g., 'NY')
- `countryCode`: Country code (e.g., 'US')
- `venueId`: Specific venue ID
- `attractionId`: Specific attraction ID
- `classificationName`: Event category (e.g., 'Sports', 'Music')
- `format`: Output format ('json' or 'text', defaults to 'json')

### Examples

#### Structured JSON Output (Default)
```
<use_mcp_tool>
<server_name>ticketmaster</server_name>
<tool_name>search_ticketmaster</tool_name>
<arguments>
{
  "type": "event",
  "keyword": "concert",
  "startDate": "2025-02-01",
  "endDate": "2025-02-28",
  "city": "New York",
  "stateCode": "NY"
}
</arguments>
</use_mcp_tool>
```

#### Human-Readable Text Output
```
<use_mcp_tool>
<server_name>ticketmaster</server_name>
<tool_name>search_ticketmaster</tool_name>
<arguments>
{
  "type": "event",
  "keyword": "concert",
  "startDate": "2025-02-01",
  "endDate": "2025-02-28",
  "city": "New York",
  "stateCode": "NY",
  "format": "text"
}
</arguments>
</use_mcp_tool>
```

## Development

1. Clone the repository
2. Copy the example environment file:
   ```bash
   cp .env.example .env
   ```
3. Add your Ticketmaster API key to `.env`
4. Install dependencies:
   ```bash
   npm install
   ```
5. Build the project:
   ```bash
   npm run build
   ```
6. Test with the inspector:
   ```bash
   npm run inspector
   ```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## License

MIT License - see [LICENSE](LICENSE) file for details
