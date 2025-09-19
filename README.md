# 1Panel MCP Server

1Panel MCP Server is an implementation of the Model Context Protocol (MCP) server for 1Panel.

## Installation

### Prerequisites

- Go 1.23.0 or higher
- Existing 1panel 

### Build from Source

1. Clone the repository:
   ```bash
   git clone https://github.com/1Panel-dev/mcp-1panel.git
   cd mcp-1panel
   ```

2. Build the project:
   ```bash
   make build
   ```
   Move `./build/mcp-1panel` to the system environment path.

### Install using go install
   ```bash
   go install github.com/1Panel-dev/mcp-1panel@latest
   ```

## Usage

**Cursor** and **Windsurf** configuration example:

### stdio mode
```json
{
  "mcpServers": {
    "mcp tx-1panel ego": {
      "command": "mcp-1panel",
      "env": {
        "PANEL_ACCESS_TOKEN": "<your 1Panel access token>",
        "PANEL_HOST": "such as http://localhost:8080"
      }
    }
  }
}
```

### sse mode

start mcp server through sse
```
mcp-1panel -host <your 1Panel access address> -token <your 1Panel access token> -transport sse
```

```json
{
  "mcpServers": {
    "mcp-1panel": {
        "url": "http://localhost:8000/sse"
    }
  }
}
```

### Command Line Options

- `-token`: 1Panel access token
- `-host`: 1Panel access address
- `-transport`: Transport type (stdio or sse, default: stdio)
- `-sse-port`: Start SSE server port (default: 8000)

### Environment Variables

You can also configure the server using environment variables:

- `PANEL_HOST`: 1Panel access address
- `PANEL_ACCESS_TOKEN`: 1Panel access token

## Available Tools

The server provides various tools for interacting with 1Panel:

| Tool                        | Category | Description            |
|-----------------------------|----------|------------------------|
| **get_dashboard_info**      | System   | List dashboard status  |
| **get_system_info**         | System   | Get system information |
| **list_websites**           | Website  | List all websites      |
| **create_website**          | Website  | Create a website       |
| **list_ssls**               | Certificate | List all certificates |
| **create_ssl**              | Certificate | Create a certificate  |
| **list_installed_apps**     | Application | List all installed applications |
| **install_openresty**       | Application | Install OpenResty     |
| **install_mysql**           | Application | Install MySQL         |
| **list_databases**          | Database | List all databases     |
| **create_database**         | Database | Create a database      |

