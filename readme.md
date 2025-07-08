# `mcp-llm-client` Template

Reference repository for evaluating and testing the [`mcp-llm-client`](https://github.com/rb58853/mcp-llm-client) package. This template enables quick verification of client integration and functionality, as well as testing your own or third-party MCP servers.

For detailed information about the MCP client with LLM integration, please refer to the [official repository](https://github.com/rb58853/mcp-llm-client).

## Table of Contents

- [Description](#description)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Execution](#execution)
- [Support](#support)

## Description

This project provides a minimal structure to test the [`mcp-llm-client`](https://github.com/rb58853/mcp-llm-client) package and associated MCP servers. It allows for agile and reproducible validation of features, serving as a starting point for further development or additional integrations.

## Requirements

- Python 3.11 or higher
- Access to an OpenAI API key
- Connection to compatible MCP servers

## Installation

Follow the steps below to install and set up your development environment:

### 1. Clone the repository

```shell
git clone https://github.com/rb58853/template_mcp_llm_client.git
```

### 2. Install dependencies

```shell
cd template_mcp_llm_client
pip install -r requirements.txt
```

### 3. Optional Servers

Optionally, you may install test MCP servers available in the [simple-mcp-server](https://github.com/rb58853/simple-mcp-server) repository. To do so from the terminal, open a terminal window in the directory where you wish to clone the test server project and then execute the following commands. This will start a functional Docker container with your MCP and OAuth servers.

```shell
# Clone the repository
git clone https://github.com/rb58853/simple-mcp-server

# Enter the project directory
cd simple-mcp-server

# Create the .env file with environment variables
cat <<EOF > .env
SUPERUSERNAME=user
SUPERUSERPASSWORD=password
EOF

# Install Python dependencies
pip install -r requirements.txt

# Start the Docker container with build
docker compose -f docker-compose.yml up -d --build
```

## Configuration

### 1. MCP Servers Configuration

Edit the [config.json](config.json) file to add the MCP servers you intend to use. For details on the required format, refer to the [official `mcp-llm-client` package documentation](https://github.com/rb58853/mcp-llm-client). For this template, a [simple MCP server](https://github.com/rb58853/simple-mcp-server) is used as an example for testing purposes.

Example configuration:

```json
{
    "mcp_servers": {
        "example_public_server": {
            "transport": "httpstream",
            "httpstream-url": "http://127.0.0.1:8000/public-example-server/mcp",
            "name": "example-public-server",
            "description": "Example public server."
        },
        "example_private_mcp": {
            "transport": "httpstream",
            "httpstream-url": "http://127.0.0.1:8000/private-example-server/mcp",
            "name": "example-private-server",
            "description": "Example private server with oauth required.",
            "auth": {
                "required": true,
                "server": "http://127.0.0.1:9000",
                "secrets": {
                    "username": "user",
                    "password": "password"
                }
            }
        }
    }
}
```

### 2. Environment Variables Configuration

Add your OpenAI API key to the [.env](.env) file:

```env
#CRIPTOGRAFY_KEY by token data storage
CRIPTOGRAFY_KEY=oBd-k41TmMqib1QYalke7HRCbk_HOtE0nw1YcdkibPc=

# OpenAI Authentication
OPENAI_API_KEY=<your_openai_api_key>
```

## Execution

Once the previous steps are completed, run the main file to start the client:

```shell
python3 main.py
```

## Support

For questions, issues, or feature requests, please refer to the [official documentation] or open an issue in the [official repository](https://github.com/rb58853/mcp-llm-client).

> **Note:** This template is intended for testing and development purposes. For production environments, adapt the configuration and security measures as needed.
