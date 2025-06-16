
# 🧠 MCP Server AI Agent

This repository implements an AI agent compatible with [Model Context Protocol (MCP)](https://github.com/anthropics/mcp), enabling seamless interaction with tools exposed by an MCP-compliant server.

The agent connects to a local or remote MCP server, automatically discovers available tools, and intelligently invokes them based on user input using chain-of-thought prompting and tool planning strategies.

---

## ✨ Features

- ✅ **Tool Auto-Discovery** via MCP protocol
- 🧩 **Tool Planning** using natural language reasoning
- 🔄 **Flexible Transport Support**: STDIO and HTTP/SSE
- 📦 **Modular Architecture** for extensibility
- 🗣️ **LLM-Powered Responses** that include tool results

---

## 🚀 Getting Started

### 1. Clone and Install

```bash
git clone https://github.com/Mehedy-Tanvir/mcp-server-ai-agent.git
cd mcp-server-ai-agent
npm install
```

### 2. Configuration

Create a `.env` file in the root directory with the following variables:

```env
MCP_TRANSPORT=stdio             # or "http"
MCP_SERVER_URL=http://localhost:3000
LLM_API_KEY=your-openai-or-anthropic-key
```

### 3. Run the Agent

```bash
npm start
```

The agent will connect to the MCP server and start handling inputs via the selected transport.

---

## 📁 Project Structure

```
mcp-server-ai-agent/
│
├── src/
│   ├── agent/         # Agent logic for reasoning, tool calling
│   ├── transports/    # Communication layer (STDIO, HTTP/SSE)
│   ├── tools/         # Tool invocation and handling
│   └── main.ts        # Entry point
│
├── .env               # Configuration file
├── package.json       # Node project metadata
└── README.md          # Project documentation
```

---

## 🧠 How It Works

1. Agent connects to the MCP server and fetches the list of available tools.
2. For each user prompt, it plans tool usage using LLM reasoning.
3. Tools are called via MCP, and the result is injected back into the conversation.
4. Final response is generated and returned to the user.

---

## 🧪 Example

**Prompt**:
```
What's the weather in Dhaka?
```

**Flow**:
- Agent finds a `getWeather(city)` tool
- Calls: `getWeather("Dhaka") → "32°C, sunny"`
- Responds: _"It’s currently 32°C and sunny in Dhaka."_

---

## 📌 Requirements

- Node.js 18+
- MCP server running locally or remotely
- An LLM API key (e.g. OpenAI, Anthropic)

---

## 🤝 Contributing

Contributions, improvements, and new ideas are welcome!

Please open issues or submit pull requests with your enhancements.

---

## 📄 License

This project is licensed under the [MIT License](./LICENSE).

---

## 🙌 Credits

Created by [Mehedy Tanvir](https://github.com/Mehedy-Tanvir)

Inspired by the [Anthropic MCP reference](https://github.com/anthropics/mcp)
