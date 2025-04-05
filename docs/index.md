---
sidebar_position: 1
---

# Introduction

This projected originally kicked off during the [CloudFest Hackathon 2025](https://hackathon.cloudfest.com/project/wp-cli-mcp-host/) to implement the [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) in the WordPress ecosystem, specifically integrating it with WP-CLI.

The core innovation is transforming WordPress into an MCP Server and WP-CLI into an MCP Host through a new package, enabling direct AI interactions with WordPress installations during development. This approach provides developers with powerful AI capabilities without requiring a live site or REST API endpoints.

**WordPress MCP Server Layer:**

1. Implementation of MCP Server interfaces in WordPress
2. Resource providers for posts, pages, media, and other WordPress content types
3. Tool definitions for common WordPress actions (content creation, media handling)
4. Context providers for WordPress configuration and site state

**WP-CLI MCP Host Package:**

1. MCP Host implementation within WP-CLI framework
2. New command namespace for AI operations
3. Integration with (local and remote) LLM providers
4. Transport layer for local WordPress communication

You can think of MCP as the "USB port for LLMs", a standard way for LLMs to interact with any third-party system using things like function calling.

While the Hackathon project focused on WP-CLI, the _MCP Server_ is usage-agnostic and can also be exposed via HTTP.

The _MCP Host_, gets information (such as list of available tools) from the server and passes it on to the LLM (e.g. Gemini).

## Contributors

Original CloudFest Hackathon Contributors:

- Pascal Birchler - [@swissspidy](https://github.com/swissspidy)
- Jan-Willem Oostendorp - [@janw-me](https://github.com/janw-me)
- Joost de Valk - [@jdevalk](https://github.com/jdevalk)
- Marco Chiesi - [@marcochiesi](https://github.com/marcochiesi)
- Matt Biscay - [@skyminds](https://github.com/skyminds)
- Moritz Bappert - [@moritzbappert](https://github.com/moritzbappert)
- James Hunt - [@thetwopct](https://github.com/thetwopct)
- Tome Pajkovski - [@tomepajk](https://github.com/tomepajk)
- David Mosterd - [@davidmosterd](https://github.com/davidmosterd)
- Milana Cap - [@zzap](https://github.com/zzap)
