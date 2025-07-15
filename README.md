# Bookable MCP Server - Claude Desktop Installer

A Claude Desktop extension that provides a seamless connection to Bookable's remote MCP (Message Control Protocol) server using Streamable HTTP connection.

## Features

- Pre-compiled installer for easy installation
- Seamless connection to Bookable's MCP server
- Lightweight and efficient
- Configurable MCP server settings

## Quick Start

1. Get the installer:
   - Download the latest `.dxt` file from the [Releases](https://github.com/The-Bookings-Group/bookable-mcp-server-claude-desktop-installation/releases) page

2. Install in Claude Desktop:
   - Open Claude Desktop
   - Go to `Settings` > `Extensions` > `Install from file`
   - Select the downloaded `.dxt` file

3. Configure the connection:
   - In `Settings` > `Extensions`, find "One-click connector to Bookable remote MCP"
   - Click settings icon
   - Enter your Bookable credentials:
      - MCP Server URL
      - Authentication Server URL
      - Client ID and Client Secret (provided by Bookable)

## Building from Source (Optional)

If you prefer to build the installer yourself:

1. Prerequisites:
   - [Node.js (v16 or higher)](https://nodejs.org/en/download)
   - npm (comes with Node.js)

2. Clone the repository:
```bash
  git clone https://github.com/The-Bookings-Group/bookable-mcp-server-claude-desktop-installation
  cd bookable-mcp-server-claude-desktop-installation
```

3. Install dependencies:
```bash
  npm install
```

4. Build the package:
```bash
  npm run build
```

This will generate a `.dxt` file in the project directory that you can install in Claude Desktop.

## Additional Configuration

You can verify the current configuration or troubleshoot connection issues by:
1. Going to `Settings` > `Extensions`
2. Finding the Bookable MCP Server connector
3. Checking the extension's logs in the Claude Desktop developer tools

The extension will automatically reconnect whenever you update the configuration.

## Development

### Available Scripts

- `npm run build` - Build the package and generate the .dxt file
- `npm run clean` - Remove build artifacts (*.dxt files)
- `npm run authenticate` - Perform OAuth2 authentication
- `npm run start` - Connect to the MCP server with authentication

### Local Testing

You can test the authentication and MCP server connection locally without installing the extension in Claude Desktop.

#### Prerequisites for Testing

The following environment variables need to be set:
- `BOOKABLE_MCP_SERVER` - MCP server endpoint URL
- `BOOKABLE_AUTH_SERVER` - OAuth2 authorization server URL
- `BOOKABLE_CLIENT_ID` - OAuth2 client ID
- `BOOKABLE_CLIENT_SECRET` - OAuth2 client secret

#### Testing with Default Values

For testing purposes, you can use the default values from the manifest.json:

```bash
# Set environment variables with default test values
  export BOOKABLE_MCP_SERVER="http://localhost:8080/mcp"
  export BOOKABLE_AUTH_SERVER="https://bookabletech.uk.auth0.com"
  export BOOKABLE_CLIENT_ID="YOUR_CLIENT_ID"
  export BOOKABLE_CLIENT_SECRET="YOUR_CLIENT_SECRET"
```

#### Test Authentication Only

To test just the OAuth2 authentication flow:

```bash
  npm run authenticate
```

This will:
1. Make a POST request to the OAuth2 token endpoint
2. Extract the access token from the response
3. Save the token to `.bookable_token` file
4. Display success/error messages

###### Verify the Access Token

You can inspect the generated token:

```bash
  # Check if token file exists and view its size
  ls -la .bookable_token

  # View first 50 characters of the token (should start with 'eyJ' for JWT)
  head -c 50 .bookable_token
```

#### Test Full MCP Server Connection

To test the complete flow including MCP server connection:

```bash
  npm run start
```

This will:
1. Run the authentication step
2. Read the saved token
3. Start the MCP remote client with the Bearer token
4. Attempt to connect to the MCP server

**Note:** The MCP server connection will fail if `localhost:8080/mcp` is not running, but you can verify that:
- Authentication works correctly
- Token is properly formatted and saved
- Authorization header is correctly set
- MCP client starts successfully

#### Clean Up

To remove test artifacts:

```bash
  npm run clean
```

## Support

For support, please contact Bookable at hello@bookabletech.com