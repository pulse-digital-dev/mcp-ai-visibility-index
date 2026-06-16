# AI Visibility Index - MCP Server

> AIエージェントから日本EC業界104社のAI可視性ランキングデータに直接アクセス

## Quick Start

### Claude Desktop

`claude_desktop_config.json` に以下を追加して再起動:

```json
{
  "mcpServers": {
    "ai-visibility-index": {
      "url": "https://ai-visibility-index.dev/mcp"
    }
  }
}
```

### Cursor
Settings -> MCP -> Add Server -> Type: http -> URL: `https://ai-visibility-index.dev/mcp`

## Available Tools

| Tool | Description |
|------|-------------|
| `check_ai_visibility` | 特定ドメインのAI可視性スコアを照会 |
| `list_ai_visibility_industries` | 9業界のサマリー一覧 |
| `get_ai_visibility_methodology` | スコアリング方法論を取得 |

## Links
- Site: https://ai-visibility-index.dev/
- Docs: https://ai-visibility-index.dev/docs/mcp/
- Pricing: https://ai-visibility-index.dev/pricing/

MIT License - [Pulse Digital](https://pulse-digital.dev/)
