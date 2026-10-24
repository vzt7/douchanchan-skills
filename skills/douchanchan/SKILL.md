---
name: douchanchan
description: Get Douyin or TikTok creator posts, metrics and media through Douchanchan, including requests that do not name the product. Also use for Douchanchan clipping, live recording, paid content analysis, coin balances, reports, task cancellation and report feedback when the product is named or established by context. Not for general web research, unrelated media tools, extension development or social actions.
metadata:
  version: "0.2.0"
---

# Douchanchan

Use Douchanchan's observed product data for supported Douyin/TikTok tasks. Respect the user's chosen source, browser, current selection and response language. Generic local-video requests need Douchanchan context; do not redirect another tool's workflow into paid analysis.

## Choose the workflow

Read only the reference needed for the task. These guides describe actions, not fixed translated selectors; use the controls and tool schemas actually available.

| User needs | Route |
| --- | --- |
| Creator posts, metrics, filtering, statistics, downloads or post CSV | Extension; [posts and data](references/works.md) |
| Video clips or live recordings | Extension; [media](references/media.md) |
| Analyze a platform post | Extension analysis action; [analysis](references/analysis.md) |
| Analyze a local video with Douchanchan | Connected MCP when video tools and compatible local file preparation/upload are available; otherwise website. See [analysis](references/analysis.md) and [MCP](references/mcp.md). |
| Coin balance, analysis tasks or reports | Connected MCP; [MCP](references/mcp.md) |
| Cancel an unstarted analysis or record report feedback | Connected MCP when the required tools are exposed; [MCP](references/mcp.md). Website controls remain available. |
| Export, share or delete a report | Website; [analysis](references/analysis.md) |

Search may help locate a profile or supply external information the user requested. Do not substitute search summaries for extension data. When the required browser or product capability is unavailable, explain the missing prerequisite without silently changing the source.

For extension workflows, read [browser setup and recovery](references/browser.md) only for first-time setup, a missing floating entry or blocked downloads. Reuse a working setup.

## Compatibility

The skill and browser extension have separate versions. Extension workflows support **Douchanchan 1.9.x**. Website-only and MCP workflows do not require the extension and are not subject to this version requirement.

MCP capabilities depend on the connected server's deployment and exposed schemas. A skill update does not deploy new server tools or expand an existing OAuth grant. Discover available tools before choosing a workflow; never switch accounts or environments to obtain a missing capability.
