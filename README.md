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

**Notes:** - Multiple payment methods are supported (see
[Payment Methods](#payment-methods) below). - Orders placed through the
MCP are real Zepto orders and follow the same fulfillment flow as the
Zepto app or website.

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

### Method 3: ChatGPT (Status)

Zepto support for ChatGPT is implemented as an app and is currently **in
beta**, pending approval from OpenAI. It is not yet available for
general use.

**Note:** The ChatGPT integration is still in early development and may
exhibit unexpected behavior or instability. We are actively working on
improving reliability.

Once enabled, the ChatGPT experience will allow users to: - Search for
groceries - Manage their Zepto cart - Place orders - View order history

All through natural conversational prompts, similar to other supported
MCP clients.

------------------------------------------------------------------------

## Authentication

On first use, the MCP initiates an OAuth flow:

1.  You are redirected to a browser page
2.  Enter your Indian mobile number
3.  Verify using an OTP
4.  You are redirected back to the MCP client

After authentication, the MCP can securely access your Zepto account.
Authentication can be cleared directly from the client if needed.

### Allowed Redirect URIs

The following redirect URIs are whitelisted for MCP authentication:

-   `claude://claude.ai/settings/connectors`
-   `https://claude.ai/api/mcp/auth_callback`
-   `https://insiders.vscode.dev/redirect`
-   `https://oauth.pstmn.io/v1/callback`
-   `https://vscode.dev/redirect`
-   `http://localhost`
-   `http://localhost/callback`
-   `http://127.0.0.1`
-   `http://127.0.0.1/callback`

Contact us if you need additional URIs whitelisted.

------------------------------------------------------------------------

## Payment Methods

The Zepto MCP supports multiple payment options:

-   **Cash on Delivery (COD)** — Pay when your order arrives.
-   **UPI** — Pay via any UPI app (GPay, PhonePe, etc.) through an
    in-conversation payment link.
-   **Cards** — Credit and debit card payments via a secure checkout
    flow.
-   **Zepto Cash (Wallet)** — Use your Zepto wallet balance to pay for
    orders.
-   **UPI Reserve Pay** — Reserve-and-pay flow powered by NPCI and
    Razorpay. The amount is reserved upfront via UPI and charged upon
    order fulfillment.

You can ask the AI to show available payment methods for your order, or
specify your preferred method directly — e.g. *"Place my order using
UPI"* or *"Pay with Zepto Cash"*.

------------------------------------------------------------------------

## Example Workflows

Here are some things you can try once the Zepto MCP is set up. Just type
these as natural language prompts in your AI client.

### 1. Quick Everyday Order

> "Order 1L Amul Toned Milk, a dozen eggs, and a loaf of bread."

A straightforward flow — the AI searches for the items, adds them to
your cart, and places the order. Great for quick everyday purchases.

### 2. Reorder From History

> "What did I order last time? Reorder the same items."

The AI retrieves your most recent order, lists out the items, and adds
them back to your cart so you can place the order again with a single
confirmation.

### 3. Recipe-Based Shopping

> "I want to make paneer butter masala tonight for 4 people. Figure out
> what ingredients I need and order them from Zepto."

The AI generates a recipe ingredient list, searches for each item on
Zepto, picks the right quantities, adds everything to your cart, and
gives you a total — turning a dinner idea into a ready-to-place order.

### 4. Order From a Photo

> _\[Attach a photo of a recipe card, a screenshot of a dish, or a
> fridge with missing items\]_
>
> "Here's a recipe I found — order everything I'd need to make this."

The AI reads the image, identifies the ingredients or items, searches
for them on Zepto, and builds your cart. Works with recipe screenshots,
handwritten lists, or even a photo of a dish you want to recreate.

### 5. Occasion-Based Shopping

> "I'm hosting a Diwali party for 15 people this weekend. I'll need
> sweets, dry fruits, snacks, drinks, and some basic decorations if
> available. Put together a cart for me."

The AI plans a shopping list based on the occasion, searches across
categories, adds appropriate items and quantities, and presents the
full cart for your review — handling the thinking so you don't have to.

------------------------------------------------------------------------

## Important Notes

-   This integration is **not a sandbox or demo environment**.
-   Any order placed through the Zepto MCP will be processed as a real
    Zepto order.
-   Multiple payment methods are supported — see
    [Payment Methods](#payment-methods) for details.

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
