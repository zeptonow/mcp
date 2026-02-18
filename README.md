# Zepto MCP

The Zepto MCP allows MCP-compatible clients (such as Claude Desktop and
Claude Code) to interact directly with Zepto's quick-commerce platform.
It enables grocery search, cart management, order placement, and order
history access through natural language conversations.

This integration is intended for Zepto customers in India with an active
Indian mobile number.

------------------------------------------------------------------------

## Who is it for?

The Zepto MCP is designed for end users who want the convenience of
Zepto's shopping experience inside conversational AI clients. While
early adopters are likely to be developers and power users, this is a
**consumer-facing integration** that works with real Zepto accounts and
real orders.

------------------------------------------------------------------------

## Tools Available

### Search Products

Search Zepto's live product catalog using natural language queries.
Results include real-time product availability, pricing, and relevant
details.

### Cart Management

Manage your Zepto cart conversationally: - Add items to the cart\
- Update quantities
- Remove items

The cart stays in sync with your Zepto account.

### Order Placement

Place Zepto orders directly from the MCP.

**Notes:** - Only **Cash on Delivery (COD)** is supported at this
time. - Orders placed through the MCP are real Zepto orders and follow
the same fulfillment flow as the Zepto app or website.

### Order History

Retrieve your past Zepto orders, including: - Order status (completed,
cancelled, failed, etc.) - Ordered items - Prices and order details

This can be used to review previous purchases or understand order
outcomes.

------------------------------------------------------------------------

## Installation

The Zepto MCP uses OAuth authentication to securely connect to your
Zepto account. Setup differs slightly by client.

------------------------------------------------------------------------

### Method 1: JSON Config (Claude Desktop, Cursor, VSCode etc.)

Claude Desktop provides a **Developer Settings** section that opens the
MCP configuration file directly. Use that interface to add the Zepto
MCP.

For Cursor, find the 'Tools & MCP' section inside Cursor settings, which
will let you edit the config.

A working configuration looks like this:

```json
{ 
    "mcpServers": { 
        "zepto": {
             "command": "npx", 
             "args": [ "mcp-remote", "https://mcp.zepto.co.in/mcp" ] 
        }
    }
}
```

After saving the configuration, restart your client. The Zepto MCP
will then be available for use.

------------------------------------------------------------------------

### Method 2: Claude Code CLI

If you're using Claude Code, you can add the Zepto MCP with a single
command:

```bash
claude mcp add --transport http --scope user zepto https://mcp.zepto.co.in/mcp
```

Follow the prompts to complete setup. Once added, Zepto tools will be
available in your Claude Code sessions.

------------------------------------------------------------------------

### Method 3: ChatGPT

Zepto support for ChatGPT is implemented as an app and is currently **in
beta**, pending approval from OpenAI. It is not yet available for
general use.

Once enabled, the ChatGPT experience will allow users to: - Search for
groceries - Manage their Zepto cart - Place orders - View order history
through a speciaised ChatGPT UI.

**Steps to integrate**
1. Settings > Apps > Advanced settings > Enable Developer Mode
2. Create App "Zepto" with url `https://mcp.zepto.co.in/mcp`
3. Wait for OAuth to pop up and enter credentials
4. Post authentication, Add @zepto in your messages to start using

**Notes**
1. Enable "Local Network Access" to allow loading widgets properly
2. ChatGPT's MCP experience is still maturing, there might be bugs post authentication and while loading tools

------------------------------------------------------------------------

## Authentication

On first use, the MCP initiates an OAuth flow:

1.  You are redirected to a browser page
2.  Enter your Indian mobile number
3.  Verify using an OTP
4.  You are redirected back to the MCP client

After authentication, the MCP can securely access your Zepto account.
Authentication can be cleared directly from the client if needed.

------------------------------------------------------------------------

## Important Notes

-   This integration is **not a sandbox or demo environment**.
-   Any order placed through the Zepto MCP will be processed as a real
    Zepto order.
-   Payments are **Cash on Delivery only** at this time.

------------------------------------------------------------------------

## Privacy

This MCP does not persist or store conversation data.

The MCP only accesses data required to perform the requested actions
(such as searching products, managing carts, placing orders, or
retrieving order history) for the authenticated user.

------------------------------------------------------------------------

## Issues & Feedback

If you encounter issues, want to report bugs, or have feature requests,
please use the GitHub Issues section of this repository.
