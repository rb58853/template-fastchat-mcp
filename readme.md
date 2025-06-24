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

1. **Clone the repository**

    ```shell
    git clone https://github.com/rb58853/template_mcp_llm_client.git
    ```

2. **Install dependencies**

    ```shell
    cd template_mcp_llm_client
    pip install -r requirements.txt
    ```

## Configuration

### 1. MCP Servers Configuration

Edit the [config.json](config.json) file to add the MCP servers you intend to use. For details on the required format, refer to the [official `mcp-llm-client` package documentation](https://github.com/rb58853/mcp-llm-client). For this template, a [simple MCP server](https://github.com/rb58853/simple-mcp-server) is used as an example for testing purposes.

Example configuration:

    {
        "mcp_servers": {
            "public-example-server": {
                "http": "http://0.0.0.0:8000/public-example-server/mcp",
                "name": "public-example-server",
                "description": "This server specializes in operations with numbers, such as addition and text conversion."
            }
        }
    }

### 2. Environment Variables Configuration

Add your OpenAI API key to the [.env](.env) file:

```env
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
