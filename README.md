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

The Zepto MCP uses OAuth authentication to securely connect to your Zepto account. After adding the server using any of the methods below, you'll be prompted to authenticate with your Indian mobile number on first use.

### Method 1: JSON-based Configuration

For MCP clients that support manual configuration (Claude Desktop, Cline, etc.), add the following to your MCP settings file:

```json
{
  "mcpServers": {
    "zepto": {
      "type": "http",
      "url": "https://mcp.zepto.co.in/mcp"
    }
  }
}
```

**Configuration file locations:**
- **macOS**: `~/claude.json`

After saving the configuration, restart your MCP client.

### Method 2: Claude Code CLI

If you're using Claude Code, you can add the Zepto MCP with a single command:

```bash
claude mcp add --transport http --scope user zepto https://mcp.zepto.co.in/mcp
```

Follow the prompts to complete the setup. The server will be automatically configured and ready to use.

### Method 3: ChatGPT Desktop (Developer Mode)

To use the Zepto MCP with ChatGPT Desktop:

1. Enable Developer Mode in ChatGPT settings
2. Navigate to the MCP settings section
3. Add a new MCP server with the following details:
   - **Name**: Zepto
   - **URL**: `https://mcp.zepto.co.in/mcp`
4. Save the configuration
5. When you first use Zepto tools, you'll be prompted to authenticate with OAuth

### Authentication

On first use, the MCP will initiate an OAuth flow to authenticate with your Zepto account:
1. You'll receive a prompt to authenticate
2. Enter your Indian mobile number
3. Complete the OTP verification
4. Your session will be securely stored for future use

Once configured, the MCP will automatically load the Zepto tools and make them available for conversational use.

## Issues

If you encounter any problems, have feature requests, or want to report bugs, please raise an issue in this repository’s GitHub Issues section.
