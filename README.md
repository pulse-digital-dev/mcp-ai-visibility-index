# AI Visibility Index — MCP Server

> AIエージェントから日本EC業界104社のAI可視性ランキングデータに直接アクセス

[![MCP](https://img.shields.io/badge/MCP-Compatible-blue)](https://modelcontextprotocol.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

AI Visibility Indexは、日本のEC企業104社が4大AIエンジン（ChatGPT・Claude・Gemini・Perplexity）にどれだけ引用されているかを月次で計測・公開するベンチマークメディアです。

このMCPサーバーに接続することで、Claude Desktop・Cursor・Windsurf等のMCP対応AIエージェントから、ランキングデータを直接取得できます。

- **エンドポイント**: `https://ai-visibility-index.dev/mcp`
- **トランスポート**: Streamable HTTP（JSON-RPC 2.0 over HTTP POST）
- **認証**: 匿名アクセスで月10回まで無料。APIキー不要。

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

Settings → MCP → Add Server:

- **Name**: `ai-visibility-index`
- **Type**: `http`
- **URL**: `https://ai-visibility-index.dev/mcp`

### その他のMCPクライアント

エンドポイントURLを指定するだけで接続できます:

```
https://ai-visibility-index.dev/mcp
```

## Available Tools

### 1. `check_ai_visibility`

特定ドメインのAI可視性スコアを照会します。

| パラメータ | 型 | 必須 | 説明 |
|------------|------|------|------|
| `domain` | string | ✓ | 照会するドメイン（例: `zozo.jp`） |

**レスポンス例:**

```json
{
  "company": "ZOZOTOWN",
  "domain": "zozo.jp",
  "overallScore": 72.5,
  "rank": 3,
  "totalCompanies": 104,
  "engines": {
    "chatgpt": 85.0,
    "claude": 70.0,
    "gemini": 65.0,
    "perplexity": 70.0
  }
}
```

### 2. `list_ai_visibility_industries`

9業界のAI可視性サマリーを一覧で返します。パラメータ不要。

### 3. `get_ai_visibility_methodology`

スコアリング方法論（計算式・対象エンジン・クエリ種別・データ更新頻度）を返します。パラメータ不要。

## Authentication

| プラン | 月間コール数 | バーストレート | 月額 |
|--------|------------|-------------|------|
| 匿名（キーなし） | 10 | 5/分 | 無料 |
| MCP Dev | 200 | 20/分 | ¥980 |
| Starter | 100 | 10/分 | ¥2,980 |
| Pro | 500 | 50/分 | ¥9,800 |
| Enterprise | 2,000 | 100/分 | ¥29,800 |

APIキーは `Authorization` ヘッダーで送信:

```
Authorization: Bearer avi_xxxxxxxxxxxxxxxxxxxxxxxx
```

APIキーの取得: [料金プラン](https://ai-visibility-index.dev/pricing/)

## Discovery

MCP Discovery Protocol対応:

```
GET https://ai-visibility-index.dev/.well-known/mcp.json
```

## Links

- **ランキングサイト**: https://ai-visibility-index.dev/
- **ドキュメント**: https://ai-visibility-index.dev/docs/mcp/
- **料金プラン**: https://ai-visibility-index.dev/pricing/
- **方法論**: https://ai-visibility-index.dev/methodology/
- **データ修正・異議申立**: https://ai-visibility-index.dev/data-correction/

## Data Usage

- 出典表記 **必須**: `AI Visibility Index by Pulse Digital`
- APIキーの共有・再販は禁止
- 詳細: [利用規約](https://ai-visibility-index.dev/terms/)

## License

MIT — see [LICENSE](LICENSE)

## Author

[Pulse Digital](https://pulse-digital.dev/) — AI × マーケティングの分析ツールを開発しています。
