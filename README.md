# UAE Company Registry MCP

Connect your AI assistant to [The Company Atlas](https://thecompanyatlas.com) for UAE company registry research through the Model Context Protocol.

This listing is a focused entry point for:

- UAE trade-licence establishments across the emirates
- English and Arabic name search
- Legal type, status, activities, managers and contact fields

The MCP connection is provided by The Company Atlas. This repository does not run a separate server.

## Connect

```
https://thecompanyatlas.com/mcp/uae
```

Add this URL as a custom MCP connector in Claude, Cursor, or any MCP-compatible client. Sign in with Google when prompted.

- Transport: Streamable HTTP
- Auth: Google OAuth (sign in once, stays authorized)
- Docs: [thecompanyatlas.com/mcp/connect](https://thecompanyatlas.com/mcp/connect)

## Tools

### `Uae_search_companies`

Search the UAE business directory by name and/or filters. Filters are combined with AND logic; include at least one. Many establishments have no English name on file, so `q` is matched against both the English and Arabic names.

| Parameter | Type | Description |
|---|---|---|
| `q` | string, optional | Name substring, English or Arabic, 3–80 characters |
| `emirate` | string, optional | e.g. `Dubai`, `Abu Dhabi` |
| `entityType` | string, optional | Legal type substring, e.g. `Limited Liability` |
| `active` | boolean, optional | Filter by active status |
| `registeredFrom` / `registeredTo` | date, optional | Registration date range |
| `page` / `limit` | integer, optional | Pagination, `limit` up to 50 (default 20) |

### `Uae_get_company`

Full profile of one establishment: contacts, activities, managers, expiry.

## Example prompts

- List Dubai limited liability companies registered in 2025 with "logistics" in the name
- Find Abu Dhabi establishments with an Arabic name containing a given word
- Show the managers and activities for a given UAE company

## Data source

UAE trade-licence registers.
