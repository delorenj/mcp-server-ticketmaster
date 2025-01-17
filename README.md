# MCP Server for Ticketmaster Events

A Model Context Protocol server that provides tools for discovering events, venues, and attractions through the Ticketmaster Discovery API.

## Features

- Search for events, venues, and attractions with flexible filtering:
  - Keyword search
  - Date range for events
  - Location (city, state, country)
  - Venue-specific searches
  - Attraction-specific searches
  - Event classifications/categories
- Returns structured JSON data with details including:
  - Names and IDs
  - Dates and times (for events)
  - Price ranges (for events)
  - URLs
  - Images
  - Locations and addresses (for venues)
  - Classifications (for attractions)

## Installation

```bash
npm install mcp-server-ticketmaster
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
      "command": "node",
      "args": ["path/to/mcp-server-ticketmaster/build/index.js"],
      "env": {
        "TICKETMASTER_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Usage

The server provides a tool called `search_ticketmaster` that accepts:
- `type`: Type of search ('event', 'venue', or 'attraction')
- `keyword`: Optional search term
- `startDate`: Optional start date in YYYY-MM-DD format (for events)
- `endDate`: Optional end date in YYYY-MM-DD format (for events)
- `city`: Optional city name
- `stateCode`: Optional state code (e.g., 'NY')
- `countryCode`: Optional country code (e.g., 'US')
- `venueId`: Optional specific venue ID
- `attractionId`: Optional specific attraction ID
- `classificationName`: Optional event category (e.g., 'Sports', 'Music')

Example usage in Claude:
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