# Commands

This package implements the following commands:

### wp ai

AI prompt.

~~~
wp ai <prompt> [--skip-wordpress]
~~~

**OPTIONS**

```
<prompt>
    AI prompt.

[--skip-wordpress]
    Run command without loading WordPress. (Not implemented yet)
```

**EXAMPLES**

```
# Get data from WordPress
$ wp ai "What are the titles of my last three posts?"
- Hello world
- My awesome post
- Another post

# Interact with multiple MCP servers.
$ wp ai "Take file foo.txt and create a new blog post from it"
Success: Blog post created.
```


### wp mcp server list

Lists available MCP servers.

~~~
wp mcp server list [--format=<format>]
~~~

**OPTIONS**

```
[--format=<format>]
    Render output in a particular format.
    ---
    default: table
    options:
      - table
      - csv
      - json
      - count
    ---
```

**EXAMPLES**

```
# Greet the world.
$ wp mcp server list
Success: Hello World!

# Greet the world.
$ wp ai "create 10 test posts about swiss recipes and include generated featured images"
Success: Hello World!
```


### wp mcp server add

Add a new MCP server to the list

~~~
wp mcp server add <name> <server>
~~~

**OPTIONS**

```
<name>
    Name for referencing the server later

<server>
    Server command or URL.
```

**EXAMPLES**

```
# Add server from URL.
$ wp mcp server add "server-github" "https://github.com/mcp"
Success: Server added.

# Add server with command to execute
$ wp mcp server add "server-filesystem" "npx -y @modelcontextprotocol/server-filesystem /my/allowed/folder/"
Success: Server added.
```

### wp mcp server remove

Remove a new MCP server from the list

~~~
wp mcp server remove <name>
~~~

**OPTIONS**

```
<name>
    Name of the server to remove
```

**EXAMPLES**

```
# Remove server.
$ wp mcp server remove "server-filesystem"
Success: Server removed.
```
