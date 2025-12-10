# Zepto MCP 

The Zepto MCP allows Claude and other MCP clients to interact directly with Zepto’s quick-commerce platform. It brings grocery search, cart management, and ordering into a natural conversational workflow for users within India who have an active Indian mobile number.

## Who is it for?

This connector is intended for Zepto customers located in India who want the convenience of Zepto’s shopping experience inside any Claude client that supports the Model Context Protocol.

## Tools Available

- **Search Products**  
  Allows Claude to query Zepto’s catalog for real-time product listings based on user requests.

- **Cart Management**  
  Supports adding, updating, and removing items from the user’s Zepto cart.

- **Order Placement**  
  Enables placing orders and retrieving order details through conversational prompts.

## Installation

To add the Zepto MCP to a MCP client that supports Streamable HTTP MCP servers, register the following endpoint:
`mcp.zepto.com/mcp`

```json
{
  "mcpServers": {
    "zepto": {
      "type": "http",
      "url": "https://mcp.zepto.com/mcp",
    }
  }
}
```
Once configured, the MCP will automatically load the Zepto tools and make them available for conversational use.

## Issues

If you encounter any problems, have feature requests, or want to report bugs, please raise an issue in this repository’s GitHub Issues section.
