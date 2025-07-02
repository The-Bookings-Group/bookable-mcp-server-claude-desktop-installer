# Bookable MCP Server - Claude Desktop Installation

A one-click connector to Bookable's remote MCP (Message Control Protocol) server via Server-Sent Events (SSE).

## Features

- Simple, one-click installation
- Seamless connection to Bookable's MCP server
- Lightweight and efficient

## Prerequisites

- Node.js (v14 or higher recommended)
- npm (comes with Node.js)

## Installation

1. Clone this repository:
```bash
  git clone https://github.com/The-Bookings-Group/bookable-mcp-server-claude-desktop-installation
  cd bookable-mcp-server-claude-desktop-installation
```

2. Install dependencies:
```bash
  npm install
```

## Usage

1. Build the package:

   ```bash
   npm run build
   ```
   This will generate a `.dxt` file in the project directory.


2. Install in Claude Desktop:
   - Open Claude Desktop application
   - Go to `Settings` > `Extensions`
   - Click on `Install from file`
   - Select the generated `.dxt` file from this project
   - Restart Claude Desktop if prompted


3. After installation, the Bookable MCP Server connector will be available in your Claude Desktop extensions.

## Configuration

To change the remote MCP server URL:

1. In Claude Desktop, go to `Settings` > `Extensions`
2. Find "One-click connector to Bookable remote MCP via SSE" in the list
3. Click on the extension's settings/gear icon
4. Look for the `Remote URL` configuration option
5. Update the URL to your desired MCP server endpoint (e.g., `https://your-mcp-server.example.com`)
6. Save the settings
7. The extension will automatically reconnect with the new URL

If you need to verify the current configuration or connection status, you can check the extension's logs in the Claude Desktop developer tools.

## Development

### Available Scripts

- `npm run build` - Build the package and generate the .dxt file
- `npm run clean` - Remove build artifacts (*.dxt files)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support, please contact Bookable at hello@bookabletech.com
