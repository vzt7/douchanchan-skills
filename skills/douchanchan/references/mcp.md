# MCP account reads

Prefer connected MCP for the current user's coin balance, analysis tasks and reports unless the user chose the website. When MCP is not connected and browser tools are available, use the website's account menu or [analysis tasks](https://douchanchan.app/analysis-tasks). If the user specifically requested MCP, explain the connection step instead of switching routes. MCP does not read the browser extension's creator-post cache.

Connect `https://douchanchan.app/mcp` through the client's OAuth flow. The client needs remote HTTP and MCP `2026-07-28` support; no API key or extension is needed.

| Tool | Authorization and use |
| --- | --- |
| `get_coin_balance` | `coins:read`, no Max required. No arguments; returns `totalCoins` and UTC `checkedAt`. Negative balances are valid. |
| `list_analysis_tasks` | `analysis:read` and active Max. Filter by status if needed; follow `pagination.nextCursor` while `hasMore` is true. |
| `get_analysis_task` | `analysis:read` and active Max. Read status and progress for an owned task ID. |
| `get_analysis_report` | `analysis:read` and active Max. Read an available report, optionally selecting `chapters`. |

Use the exposed schemas and names, which may have a client prefix. Request only the information needed: post downloads and report reads do not require a preliminary balance check. A balance is a point-in-time snapshot, not a quote or permission to spend, and cannot establish how many future analyses are affordable.

New connections default to balance access when no scope is specified. Missing scope requires explicit authorization for the requested access; missing Max affects analysis reads, not balance queries. For expired authorization, reconnect. For temporary failures, preserve the connection and follow retry guidance; do not call them missing membership or silently switch routes. Never interpret a failed balance query as zero.

Resolve ambiguous tasks by ID and date. For a large report, request fewer chapters. Retain relevant evidence and limitations, and do not poll pending tasks indefinitely.

Uploads, quote confirmation, exports, sharing, cancellation and deletion remain product-interface actions. Do not invent MCP write tools.
