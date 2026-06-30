# Clerk.io - GTM Web Tag Template

A Google Tag Manager web tag template for [Clerk.io](https://clerk.io), the AI-powered personalisation and product recommendation platform.

## Features

- **Initialise Clerk.js** - Load the Clerk.js library with your public API key
- **Track Product Views** - Send product view events to Clerk.io
- **Track Cart** - Sync the current cart contents with Clerk.io
- **Track Purchases/Sales** - Log completed orders to Clerk.io for training its recommendation engine
- **Track Search** - Send search queries to Clerk.io

## Installation

### From the Community Template Gallery

1. In your GTM workspace, go to **Templates** > **Search Gallery**
2. Search for **Clerk.io**
3. Click **Add to workspace**

### Manual Installation

1. Download `template.tpl` from this repository
2. In GTM, go to **Templates** > **New**
3. Click the overflow menu (three dots) > **Import**
4. Select the downloaded `template.tpl` file

## Setup Guide

### Step 1: Initialise Clerk.js

Create a tag with action type **Initialise**:

| Field | Value |
|---|---|
| Action type | Initialise |
| Public API key | Your Clerk.io public API key (from my.clerk.io > Settings) |
| Language | _(Optional)_ Language code, e.g. `english`, `danish` |
| Collect email | _(Optional)_ Enable automatic email detection |

**Trigger:** All Pages (fires on every page load).

### Step 2: Track Product Views

Create a tag with action type **Track Product View**:

| Field | Value |
|---|---|
| Action type | Track Product View |
| Product ID | A GTM variable returning the current product ID |

**Trigger:** Product detail page view.

### Step 3: Track Cart

Create a tag with action type **Track Cart**:

| Field | Value |
|---|---|
| Action type | Track Cart |
| Cart product IDs | A GTM variable returning an array of product IDs in the cart, e.g. `[123, 456, 789]` |

**Trigger:** Cart update event or cart page view.

### Step 4: Track Purchases

Create a tag with action type **Track Purchase/Sale**:

| Field | Value |
|---|---|
| Action type | Track Purchase/Sale |
| Order ID | The unique order identifier |
| Product IDs | An array of product IDs in the order |
| Customer email | _(Optional)_ The customer email for attribution |

**Trigger:** Order confirmation / thank-you page.

### Step 5: Track Search (optional)

Create a tag with action type **Track Search**:

| Field | Value |
|---|---|
| Action type | Track Search |
| Search query | The search term entered by the visitor |

**Trigger:** Search results page view.

## Field Reference

| Field | Action | Required | Description |
|---|---|---|---|
| Action type | All | Yes | The action the tag performs |
| Public API key | Initialise | Yes | Your Clerk.io public API key |
| Language | Initialise | No | Content language (auto-detected by default) |
| Collect email | Initialise | No | Auto-detect visitor email from input fields |
| Product ID | Product View | Yes | The viewed product's ID |
| Cart product IDs | Cart | Yes | Array of product IDs in the cart |
| Order ID | Sale | Yes | Unique order identifier |
| Product IDs | Sale | Yes | Array of product IDs in the order |
| Customer email | Sale | No | Customer email for attribution |
| Search query | Search | Yes | The visitor's search term |

## Permissions

This template requires the following GTM sandbox permissions:

| Permission | Reason |
|---|---|
| Inject Script | Loads `https://cdn.clerk.io/clerk.js` |
| Access Globals | Reads/writes `Clerk` and `__clerk_q` on the window object |
| Logging | Debug logging to the browser console |

## Resources

- [Clerk.io Documentation](https://docs.clerk.io/)
- [Clerk.js Quick Start](https://docs.clerk.io/docs/clerkjs-quick-start)
- [Clerk.js Shopping Cart Tracking](https://docs.clerk.io/docs/clerkjs-shopping-cart)
- [Clerk.io Sales Tracking API](https://docs.clerk.io/reference/log-sale)

## Author

Created and maintained by [Freek Kampen](https://freekkampen.com) at [New North Digital](https://newnorth.digital?utm_source=github&utm_medium=gtm-template&utm_campaign=clerkio-web-tag)

## License

Apache 2.0 - see [LICENSE](LICENSE).
