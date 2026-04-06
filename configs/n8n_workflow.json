{
  "name": "Google Meta Ads GA4 MCP Workflow",
  "nodes": [
    {
      "parameters": {
        "options": {}
      },
      "id": "mcp-trigger",
      "name": "MCP Server Trigger",
      "type": "n8n-nodes-langchain.mcpTrigger",
      "typeVersion": 1,
      "position": [250, 300]
    },
    {
      "parameters": {
        "url": "YOUR_MCP_ENDPOINT_URL",
        "authentication": "none",
        "options": {}
      },
      "id": "mcp-client",
      "name": "MCP Client - Ads & Analytics",
      "type": "n8n-nodes-langchain.mcpClientTool",
      "typeVersion": 1,
      "position": [500, 300]
    },
    {
      "parameters": {
        "model": "gpt-4",
        "options": {}
      },
      "id": "ai-agent",
      "name": "AI Agent",
      "type": "n8n-nodes-langchain.agent",
      "typeVersion": 1,
      "position": [750, 300]
    }
  ],
  "connections": {
    "MCP Server Trigger": {
      "main": [
        [
          {
            "node": "MCP Client - Ads & Analytics",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "MCP Client - Ads & Analytics": {
      "main": [
        [
          {
            "node": "AI Agent",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "settings": {
    "executionOrder": "v1"
  }
}
