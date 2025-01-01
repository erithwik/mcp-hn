# Hacker News MCP Server

[![smithery badge](https://smithery.ai/badge/mcp-hn)](https://smithery.ai/server/mcp-hn)

A Model Context Protocol (MCP) server that provides tools for fetching information from Hacker News.

## Tools

- `get_stories` Fetching (top, new, ask_hn, show_hn) stories
- `get_story_info` Fetching comments associated with a story
- `search_stories` Searching for stories by query
- `get_user_info` Fetching user info

## Example Usage

Use prompts like the following:

```
User: Get the top stories of today
  Output: Uses `get_stories` tool and returns a story about AI
User: What does the details of the story today that talks about the future of AI
  Output: Uses `get_story_info` tool based on the results of the previous tool
User: What has the user `pg` been up to?
  Output: Uses `get_user_info` tool and returns a summary of the user's activity
User: What does hackernews say about careers in AI?
  Output: Uses `search_stories` tool and returns a summary of the comments
```

A more detailed example with the puppeteer MCP server:

```
User: What are the top stories of today?
  Output: Uses `get_stories` tool and returns a story about AI
User: Can you use the puppeteer tool to read the article about <AI> and also use the hackernews tool to view the comments and give me a summary of what the main comments are about the article?
  Output: Uses puppeteer tool to read the article about AI and then uses the `get_story_info` hn tool to get the comments and returns a summary of the comments
```

## Quickstart

### Installing via Smithery

To install Hacker News MCP Server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/mcp-hn):

```bash
npx -y @smithery/cli install mcp-hn --client claude
```

### Claude Desktop:

Update the following:

On MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`

On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

With the following for production:

```json
{
  "mcpServers": {
    "mcp-hn": {
      "command": "uvx",
      "args": ["mcp-hn"]
    }
  }
}
```


