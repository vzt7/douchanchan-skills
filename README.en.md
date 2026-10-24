<p align="center">
  <a href="https://github.com/vzt7/douchanchan-skills"><img src="assets/douchanchan-logo.png" alt="Douchanchan" width="96"></a>
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
| Tasks and feedback | Cancel an unstarted analysis and record adoption decisions and real validation results | Cancel the analysis I just submitted; record the recommendations I actually adopted and my validation results. |
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

Add this remote server in your client, then sign in and authorize the capabilities you need. No API key is needed:

```text
https://douchanchan.app/mcp
```

**Availability (checked 2026-10-24):** Production currently exposes 4 tools: balance, task list, task status and report reads. The complete 13-tool version has passed staging acceptance; video submission, cancellation and feedback have not yet been released to production. The table below covers the complete capability set. Agents must use tools actually discovered on the connected server; updating the skill does not release new production tools.

| Tool | Purpose | Scope |
| --- | --- | --- |
| `get_coin_balance` | Read the coin balance and check time | `coins:read` |
| `list_analysis_tasks` | Browse tasks with pagination | `analysis:read` |
| `get_analysis_task` | Check task status and progress | `analysis:read` |
| `get_analysis_report` | Read a report or selected chapters | `analysis:read` |
| `get_video_analysis_config` | Read video submission requirements | `analysis:submit` |
| `prepare_video_analysis` | Prepare a video analysis and get its quote | `analysis:submit` |
| `confirm_video_analysis` | Confirm the quote and submit the analysis | `analysis:submit` |
| `resume_video_analysis_upload` | Resume the original upload without another coin freeze | `analysis:submit` |
| `complete_video_analysis_upload` | Complete upload and check queue admission | `analysis:submit` |
| `cancel_analysis_task` | Cancel a task before processing starts | `analysis:manage` |
| `get_analysis_feedback` | Read report adoption and validation feedback | `analysis:read` |
| `save_analysis_adoption` | Save a recommendation's adoption status | `analysis:manage` |
| `save_analysis_observation` | Save or clear a real validation observation | `analysis:manage` |

Balance reads do not require Max; all other analysis tools require active Max. Omitted scope defaults to `coins:read`. Submission through report reading needs `analysis:submit` + `analysis:read`; reading before cancellation or feedback saves needs `analysis:read` + `analysis:manage`. Additional scopes require fresh consent; an existing grant or token refresh does not expand access. A balance is a snapshot, not a quote or spending approval.

The video flow is: read configuration → prepare the actual file and quote → user approves the amount → upload bytes → check queue admission → read task progress and report. The client needs compatible file preparation, fingerprint calculation and upload support. This skill does not bundle a file bridge; an MCP-only chat client cannot upload a local path or attachment URI. Use the website's **New analysis** flow when file support is unavailable. See the [MCP guide](skills/douchanchan/references/mcp.md) for recovery, cancellation and feedback.

Only unstarted tasks can be cancelled; report the amount actually released by the server. Feedback records the user's real decisions and observations without model calls, coin charges or changes to the generated report. Resolve conflicts with the user before saving again.

Creator-post lists, downloads, clipping and live recording use the extension. Payments, report file exports, sharing and deletion use the website. Creator profiles are not an MCP capability.

## 🛠️ Troubleshooting

| Issue | Action |
| --- | --- |
| The agent cannot find the extension | Check that the extension is installed in the browser profile it controls |
| MCP tools are missing | Check client compatibility, OAuth connection and the server's release scope; do not switch environments to obtain missing tools |
| MCP reports insufficient scope | Reconnect and authorize the required read, submission or management scope |
| Analysis MCP reports missing membership | Confirm that your Max membership is active |
| A service is unavailable or rate-limited | Keep the task and connection, follow the retry delay, and avoid duplicate submissions |
| Upload is interrupted after quote confirmation | Keep the original task and file, then resume; do not create a second paid task |
| Feedback save conflicts | Read the current record and agree what to keep before saving again; do not overwrite automatically |
| A downloaded file is missing | Check browser downloads or the destination; starting a download does not prove it finished |

## 🔄 Update or remove

To update the skill, send the installation prompt above again, preserving local edits. Update the extension through its store. To remove the skill, use the original installer or remove only its skill directory. CLI installations also support:

```bash
npx skills update douchanchan -g
npx skills remove douchanchan -g
```
