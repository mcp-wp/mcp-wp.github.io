# Reference

## `Server` class

The `Server` class is a core component of the MCP for WordPress implementation and is a small wrapper around the [MCP PHP SDK](https://github.com/logiscape/mcp-sdk-php).

This class provides:

- Tool registration (`register_tool()`)
- Resource registration (`register_resource()`)
- JSON-RPC request handling (`handle_message()`)

### Examples

Register a Tool

```PHP
$server->register_tool(
	[
		'name'        => 'calculate_total',
		'description' => 'Calculate the total amount'
		'callable'    => function( $params ) {
			return $params['price'] * $params['quantity'];
		},
		'inputSchema' => [
			'properties' => [
				'price'    => [ 'type' => 'integer' ],
				'quantity' => [ 'type' => 'integer' ]
			],
		],
	]
);
```


## `RouteInformation` class

The `RouteInformation` class encapsulates metadata about a WordPress REST API route. It provides methods to determine route characteristics, REST method type, and controller details.

This class is used to:

- Identify REST route types (`singular`/`list`, `GET`/`POST`/`DELETE`, etc.).
- Validate and process REST controller callbacks.
- Generate sanitized route names for MCP registration.

### Methods

| Name                                                     | Return Type | Description                                                 |
|----------------------------------------------------------|-------------|-------------------------------------------------------------|
| `RouteInformation::__construct($route, $method, $title)` | `void`      | Initializes the class with a REST route, method, and title. |
| `RouteInformation::get_name()`                           | `string`    | Get a tool name for the route.                              |
| `RouteInformation::get_description()`                    | `string`    | Get a human-friendly description.                           |

## `RestApi` class

The `RestApi` class is responsible for mapping WordPress REST API endpoints into MCP tools. It does this by:

- Extracting route details from the REST API.
- Generating input schemas from REST arguments.
- Creating AI tools dynamically based on route metadata.

This enables seamless AI-driven interactions with the WordPress REST API.

### Methods

| Name                                                               | Return Type | Description                                           |
|--------------------------------------------------------------------|-------------|-------------------------------------------------------|
| `RestApi::args_to_schema( $args )`                                 | `array`     | Converts REST API arguments into a structured schema. |
| `RestApi::sanitize_type( $type )`                                  | `string`    | Maps input types to standard schema types.            |
| `RestApi::get_tools()`                                             | `array`     | Registers REST API endpoints as AI tools in MCP.      |
| `RestApi::rest_callable( $inputs, $route, $method_name, $server )` | `array`     | Executes a REST API call dynamically.                 |

## `MediaManager` class

The `MediaManager` class provides a static method to upload a media file to the WordPress Media Library. It:

- Copies a file into the WordPress uploads directory.
- Registers the file as a WordPress media attachment.
- Generates and updates attachment metadata.

This class is useful for automated media uploads within WP-CLI or AI-powered workflows.

### Methods

| Name                                                   | Return Type | Description                                                      |
|--------------------------------------------------------|-------------|------------------------------------------------------------------|
| `MediaManager::upload_to_media_library( $media_path )` | `int`       | Uploads a media file to WordPress and returns its attachment ID. |

## `ImageTools` class

The `ImageTools` class provides AI-powered image generation functionality within WP-CLI.
It:

- Integrates AI-based image generation tools.
- Registers the tool in the system for easy access.
- Uses a client to fetch AI-generated images.

This class is used to dynamically generate images based on user prompts.

### Methods

| Name                                  | Return Type | Description                                  |
|---------------------------------------|-------------|----------------------------------------------|
| `ImageTools::__construct( $client )`  | `void`      | Initializes ImageTools with an AI client.    |
| `ImageTools::get_tools()`             | `array`     | Returns a list of available AI tools.        |
| `ImageTools::image_generation_tool()` | `Tool`      | Creates an AI-powered image generation tool. |
