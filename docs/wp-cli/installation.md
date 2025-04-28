---
sidebar_position: 1
---

# Installation

Installing this package requires WP-CLI v2.11 or greater. Update to the latest stable release with `wp cli update`.

Tip: for better support of the latest PHP versions, use the v2.12 nightly build with `wp cli update --nightly`.

To install the latest development version of this package, use the following command:

```bash
wp package install mcp-wp/ai-command:dev-main
```

Right now this package requires a local WordPress installation with the [AI Servicdes](https://github.com/felixarntz/ai-services) plugin active. That plugin is where you configure your LLM API key.

```bash
wp plugin install --activate ai-services
```

After that, within the local WordPress installation, you can run the first command:

```bash
wp ai "Greet my friend Pascal" # uses the example "greet-user" tool
```

You can use [dedicated commands](./commands.md) for adding local or remote MCP servers. For example:

```bash
wp mcp server add "mysite" "https://example.com/wp-json/mcp/v1/mcp
```

If you want to use MCP with another WordPress installation, install the [MCP Server WordPress plugin](../mcp-server).
