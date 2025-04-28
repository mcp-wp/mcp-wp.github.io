---
sidebar_position: 1
---

# Installation

You can install the MCP Server plugin to turn any WordPress site into a fully functioning MCP server.

[![Download latest nightly build](https://img.shields.io/badge/Download%20latest%20nightly-24282D?style=for-the-badge&logo=Files&logoColor=ffffff)](https://mcp-wp.github.io/mcp-server/mcp.zip)

This WordPress plugin aims to implement the new [Streamable HTTP transport](https://modelcontextprotocol.io/specification/2025-03-26/basic/transports#streamable-http), as described in the latest MCP specification. It is supposed to work with any MCP client that supports this transport, but it has been tested mostly with the [WP-CLI AI command](https://github.com/mcp-wp/ai-command).

Under the hood it uses the [`logiscape/mcp-sdk-php`](https://github.com/logiscape/mcp-sdk-php) package to set up a fully functioning MCP server. Then, this functionality is exposed through a new `wp-json/mcp/v1/mcp` REST API route in WordPress.

## Usage

Install the latest version of the plugin, either via the link above or the following WP-CLI command:

```bash
wp plugin install --activate https://github.com/mcp-wp/mcp-server/archive/refs/heads/main.zip
```

Then, go to Users -> Profile in your WordPress admin and create a new application password.

After that, you can add the MCP server to your WP-CLI config like so:

```bash
wp mcp server add "mysite" "https://johndie:yourapplicationpassword@example.com/wp-json/mcp/v1/mcp"
```

To verify that it works as expected, you can run something like this:

```bash
wp ai --skip-builtin-servers "List my most recent posts"
```

`--skip-builtin-servers` ignores the MCP server of your local installation so that only the remote one is connected to.

Example using cURL:

```bash
curl -i -X POST -H "Content-Type: application/json" http://johndoe@yourapplicationpassword:example.com/wp-json/mcp/v1/mcp -d '{"jsonrpc":"2.0", "method":"initialize", "id": "0"}'
```

## Testing

You can also test this plugin's functionality with the [MCP Inspector](https://github.com/modelcontextprotocol/inspector), which is a developer tool for testing and debugging MCP servers.

For this purpose, the plugin also supports authentication via the `Authorization` header, so you can pass the application password like so:

```http
Authorization: Bearer johndoe:yourapplicationpassword
```

Example using cURL:

```bash
curl -i -X POST -H "Content-Type: application/json" -H "Authorization: Bearer johndoe:yourapplicationpassword" http://example.com/wp-json/mcp/v1/mcp -d '{"jsonrpc":"2.0", "method":"initialize", "id": "0"}'
```
