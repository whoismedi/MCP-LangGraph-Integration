# MCP–LangGraph Integration 

The project builds an interactive AI assistant that:

* Uses **GPT-4.1** as the underlying language model
* Connects to several **MCP servers** to extend its capabilities
* Relies on **LangGraph** to manage dialogue and decision flow
* Supports **streamed outputs** for live, real-time responses

---

## Requirements

* **Python 3.13 or later**
* **Node.js** (required for the filesystem MCP server)
* **Docker** (needed for the GitHub MCP server)
* **UV** as the package manager
* A valid **OpenAI API key**

---

## Directory Layout

```
scout/
├── graph.py            # Defines the LangGraph agent logic
├── client.py           # MCP client and streaming handler
├── client_utils.py     # Shared helper functions
├── main.py             # Application entry point
└── my_mcp/             # MCP server configuration files
    ├── config.py       # Environment and config loading
    ├── mcp_config.json # MCP server definitions
    └── local_servers/  # Custom MCP server implementations
```

---

## Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd mcp-intro
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\\Scripts\\activate
```

3. Install the project dependencies:

```bash
uv pip install -e .
```

4. Configure environment variables:
   Create a `.env` file containing:

```
OPENAI_API_KEY=your_openai_api_key
MCP_FILESYSTEM_DIR=/path/to/your/projects
MCP_GITHUB_PAT=your_github_access_token
```

---

## Integrated MCP Servers

The application connects to four MCP servers:

1. **Dataflow Server** – A custom server for loading and querying datasets
2. **Filesystem Server** – Powered by `@modelcontextprotocol/server-filesystem` for file management
3. **Git Server** – Uses `mcp-server-git` to handle local Git actions
4. **GitHub Server** – Official MCP server for interacting with GitHub repositories

---

## Running the App

1. Launch the assistant:

```bash
python -m scout.client
```

2. Chat with Scout by entering questions or tasks, for example:

```
USER: Can you help me create a new data science project?
```

3. Scout can:

* Set up and organize project folders
* Load, process, and transform data
* Manage Git repositories
* Interact with GitHub


