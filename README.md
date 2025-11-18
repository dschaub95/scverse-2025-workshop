# scverse conference 2025 workshop

This workshop provides a hands-on introduction to building and utilizing biomedical MCP servers as well contributing them to the [BioContextAI MCP registry](https://biocontext.ai/registry).

## Setup

We will be using [uv](https://github.com/astral-sh/uv) Python package management throughout the workshop.

1. Install `uv` if you haven't already:
   ```bash
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```
   Or using pip:
   ```bash
   pip install uv
   ```

2. Install project dependencies:
   ```bash
   uv sync
   ```

3. Activate the virtual environment:
   ```bash
   source .venv/bin/activate
   ```
   Or use `uv run` to execute commands in the environment:
   ```bash
   uv run python script.py
   ```

To follow along it would also be good to have an MCP client such as [Cursor](https://www.cursor.com/) or [VSCode](https://code.visualstudio.com/) installed.

## 1. MCP Servers in Action

See MCP servers in action at [biocontext.ai/chat](https://biocontext.ai/chat). You will be given an API key but the amount of tokens is limited, so please be mindful of your usage.

Example query:
```
Given the following upregulated marker genes for single-cell cluster in a PBMC dataset, what cell type could this cluster be? Marker genes: NKG7, GZMB, GNLY, PRF1, CTSW. Make sure to use your available tools and analyze what cell type each gene could belong to. Output a summary of your analysis.
```
## 2. Build Your Own MCP Server

We use our [cookiecutter MCP server template](https://github.com/biocontext-ai/mcp-server-template). The task is to build an AnnData MCP server that can extract marker gene information for a cluster/cell type of interest from an AnnData `h5ad` file.

You can find the reference implementation [here](https://github.com/dschaub95/anndata-mcp-workshop).

## 3. Submit Your MCP Server

This step will only be illustrated. We hope you will make use of it after the workshop.

- **Submission Editor**: [biocontext.ai/submit](https://biocontext.ai/submit)

- **Registry**: [biocontext.ai/registry](https://biocontext.ai/registry)

## 4. Test Your MCP Server

Add the following configuration to your Cursor/VSCode settings (`mcp.json`):

```json
{
  "mcpServers": {
    "your-mcp-server": {
      "command": "uv",
      "args": [
        "run",
        "--directory",
        "path/to/your-mcp-server",
        "your-mcp-server"
      ]
    }
  }
}
```

Replace `path/to/your-mcp-server` with the path to your MCP server implementation and `your-mcp-server` with your actual server name.