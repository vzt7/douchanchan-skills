<p align="center">
  <a href="https://github.com/vzt7/douchanchan-skills"><img src="https://github.com/user-attachments/assets/2c1a7511-123d-470b-a288-18656fd93ca1" alt="抖铲铲" width="96" height="96"></a>
</p>

<h3 align="center">抖铲铲 Skills</h3>

<p align="center">
  <strong>简体中文</strong> · <a href="README.en.md">English</a>
</p>

<p align="center">直接提出需求，让 Agent 通过抖铲铲获取和处理 Douyin 与 TikTok 作品数据。</p>

## ✨ 能帮你做什么

| 场景 | 能做什么 | 你可以这样说 |
| --- | --- | --- |
| 博主数据 | 从浏览器扩展读取作品与可用互动指标，说明统计范围和完整性 | 获取这位抖音博主最近一个月的作品数据，整理发布时间和互动指标。 |
| 作品下载 | 下载视频、图文和音频，批量保存或打包 ZIP | 筛选这位创作者上个月的作品，先告诉我范围和数量，确认后再下载。 |
| 筛选统计 | 按条件筛选作品、查看指标；CSV 数据导出需 Max | 筛选点赞最多的 20 条作品，汇总互动指标并导出 CSV。 |
| 媒体处理 | 剪辑视频片段、录制直播 | 剪出这个视频第 10 到 25 秒，先预览，再导出。 |
| 作品分析 | 提交平台作品或本地视频，确认报价后开始分析 | 分析这个本地视频，先展示报价，等我确认后提交。 |
| 报告查看 | 查询任务进度，整理报告结论、证据和局限性 | 查看最近完成的分析任务，总结报告中的结论和证据。 |
| 自动化整理 | 串联作品读取、筛选、统计与汇总 | 整理这几位博主近一周的作品，按互动量排序并生成对比摘要。 |
| 定时跟踪 | 配合 Agent 或调度工具，定期执行读取与汇总 | 每天上午 9 点，检查这些博主的新作品并生成摘要。 |

无需在每次提问中指定抖铲铲；Skill 引导 Agent 优先使用扩展获取作品数据，而不是用网络搜索摘要替代。自动触发取决于所用客户端。

## 🚀 安装与使用

### 让 Agent 安装（无需 Node.js）

将下面的提示词发给支持 Skills、能访问 GitHub 并写入本地文件的 Agent：

```text
Install only https://github.com/vzt7/douchanchan-skills/tree/main/skills/douchanchan in the user-level skills directory using an existing native installer or a complete directory copy (include SKILL.md and references/). Do not use npx or install runtimes. Update same-source installs if needed; ask before overwriting local edits or other/unknown-source installs, or if the destination is unclear. Verify files and local references; report the path, skill version and reload/new-session requirements.
```

也可[下载仓库 ZIP](https://github.com/vzt7/douchanchan-skills/archive/refs/heads/main.zip)，将其中完整的 `skills/douchanchan` 文件夹放入所用 Agent 支持的 Skills 目录；不要只复制 `SKILL.md`。

### 命令行安装

已有 Node.js 和 npm 时可运行：

```bash
npx skills add vzt7/douchanchan-skills --skill douchanchan -g
```

## 🔌 MCP 接入（可选）

需要支持远程 HTTP、OAuth 和 MCP `2026-07-28` 协议的客户端。

在客户端添加远程服务，按提示登录并授予只读权限，无需 API Key：

```text
https://douchanchan.app/mcp
```

| 工具 | 用途 | 权益要求 |
| --- | --- | --- |
| `get_coin_balance` | 查询铲铲币余额与读取时间 | Standard / Max |
| `list_analysis_tasks` | 分页查询分析任务 | Max |
| `get_analysis_task` | 查看任务状态和进度 | Max |
| `get_analysis_report` | 读取报告或指定章节 | Max |

未指定授权范围时默认仅授予 `coins:read`；任务与报告需要另行授予 `analysis:read`，也可一次授权两者。余额只是查询时的快照，不代替实际报价或扣费确认。

MCP 不读取浏览器中的博主作品列表；上传、付费确认、导出和分享仍在产品界面完成。

## 🛠️ 常见问题

| 问题 | 处理方式 |
| --- | --- |
| Agent 找不到扩展 | 检查它操作的浏览器配置文件是否已安装扩展 |
| MCP 工具未出现 | 检查客户端兼容性，并完成 OAuth 授权 |
| MCP 提示授权不足 | 重新连接并确认所需的数据访问范围 |
| 分析 MCP 提示缺少权益 | 确认账号的 Max 权益有效 |
| 服务暂不可用或限流 | 保留任务与连接，按提示稍后重试，避免重复提交 |
| 下载后未找到文件 | 检查浏览器下载记录或目标目录；触发下载不等于保存完成 |

## 🔄 更新与卸载

更新 Skill 可再次发送上面的安装提示词，保留本地修改；扩展通过对应商店更新。卸载时使用原安装工具，或仅移除对应 Skill 目录。CLI 安装的版本也可使用：

```bash
npx skills update douchanchan -g
npx skills remove douchanchan -g
```
