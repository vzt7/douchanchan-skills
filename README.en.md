<p align="center">
  <a href="https://github.com/vzt7/douchanchan-skills"><img src="https://github.com/user-attachments/assets/2c1a7511-123d-470b-a288-18656fd93ca1" alt="Douchanchan" width="96" height="96"></a>
</p>

<h3 align="center">Douchanchan Skills</h3>

<p align="center">
  <a href="README.md">简体中文</a> · <strong>English</strong>
</p>

<p align="center">Describe your task. Let your agent use Douchanchan to get and process Douyin and TikTok post data.</p>

## ✨ What it helps with

| Workflow | Capabilities | Example request |
| --- | --- | --- |
| Creator data | Read posts and available engagement metrics through the extension, with scope and coverage explained | Get this Douyin creator's posts from the past month, with publication times and engagement metrics. |
| Downloads | Save videos, images, and audio individually, in batches, or as ZIP archives | Find this creator's posts from last month. Show the scope and count, then wait for approval before downloading. |
| Filters and metrics | Filter posts and inspect statistics; CSV data export requires Max | Find the 20 posts with the most likes, summarize their engagement metrics, and export them as CSV. |
| Media | Trim video clips and record live streams | Trim seconds 10–25 of this video. Preview the selection before exporting. |
| Content analysis | Submit platform posts or local videos after confirming the quote | Analyze this local video. Show the quote and wait for my approval before submitting. |
| Reports | Track tasks and summarize findings, evidence, and limitations | Review recently completed analysis tasks and summarize report findings and evidence. |
| Workflow automation | Combine post collection, filtering, statistics, and summaries | Collect the past week's posts from these creators, rank them by engagement, and produce a comparison. |
| Scheduled checks | Use an agent or scheduling tool to run recurring reads and summaries | Every day at 9 AM, check these creators for new posts and summarize them. |

You do not need to name Douchanchan in every request. The skill guides your agent toward extension data rather than web-search summaries; automatic discovery depends on your client.

## 🚀 Install and use

### Ask your agent to install (no Node.js)

Send this prompt to an agent that supports Skills, can access GitHub, and can write local files:

```text
Install only https://github.com/vzt7/douchanchan-skills/tree/main/skills/douchanchan in the user-level skills directory using an existing native installer or a complete directory copy (include SKILL.md and references/). Do not use npx or install runtimes. Update same-source installs if needed; ask before overwriting local edits or other/unknown-source installs, or if the destination is unclear. Verify files and local references; report the path, skill version and reload/new-session requirements.
```

Alternatively, [download the repository ZIP](https://github.com/vzt7/douchanchan-skills/archive/refs/heads/main.zip) and place the complete `skills/douchanchan` folder in a Skills directory supported by your agent. Do not copy only `SKILL.md`.

### Command-line installation

If Node.js and npm are already available:

```bash
npx skills add vzt7/douchanchan-skills --skill douchanchan -g
```

## 🔌 Connect MCP (optional)

Requires a client supporting remote HTTP, OAuth, and MCP protocol `2026-07-28`.

Add this remote server in your client, then sign in and approve read-only access. No API key is needed:

```text
https://douchanchan.app/mcp
```

| Tool | Purpose | Required plan |
| --- | --- | --- |
| `get_coin_balance` | Read the coin balance and check time | Standard / Max |
| `list_analysis_tasks` | Browse tasks with pagination | Max |
| `get_analysis_task` | Check task status and progress | Max |
| `get_analysis_report` | Read a report or selected chapters | Max |

When no scope is specified, authorization defaults to `coins:read`. Tasks and reports require `analysis:read`; you can also authorize both together. A balance is a snapshot, not a quote or spending approval.

MCP does not read creator-post lists from the browser. Uploads, payment confirmation, exports, and sharing stay in the product interface.

## 🛠️ Troubleshooting

| Issue | Action |
| --- | --- |
| The agent cannot find the extension | Check that the extension is installed in the browser profile it controls |
| MCP tools are missing | Check client compatibility and complete OAuth authorization |
| MCP reports insufficient scope | Reconnect and authorize the required data access |
| Analysis MCP reports missing membership | Confirm that your Max membership is active |
| A service is unavailable or rate-limited | Keep the task and connection, follow the retry delay, and avoid duplicate submissions |
| A downloaded file is missing | Check browser downloads or the destination; starting a download does not prove it finished |

## 🔄 Update or remove

To update the skill, send the installation prompt above again, preserving local edits. Update the extension through its store. To remove the skill, use the original installer or remove only its skill directory. CLI installations also support:

```bash
npx skills update douchanchan -g
npx skills remove douchanchan -g
```
