<p align="center">
  <a href="https://github.com/vzt7/douchanchan-skills"><img src="assets/douchanchan-logo.png" alt="抖铲铲" width="96"></a>
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
| 任务与反馈 | 取消尚未开始的分析，记录建议采用情况及实际验证结果 | 取消刚提交的那项分析；把我实际采用的建议和验证结果记到报告里。 |
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

在客户端添加远程服务，按提示登录并授权所需能力，无需 API Key：

```text
https://douchanchan.app/mcp
```

**上线范围（2026-10-24）：** 生产已开放下列 13 个工具，支持视频提交、报告读取、任务取消和报告反馈。Agent 应按所连接服务实际发现的工具使用；新增权限需重新授权。

| 工具 | 用途 | 授权范围 |
| --- | --- | --- |
| `get_coin_balance` | 查询铲铲币余额与读取时间 | `coins:read` |
| `list_analysis_tasks` | 分页查询分析任务 | `analysis:read` |
| `get_analysis_task` | 查看任务状态和进度 | `analysis:read` |
| `get_analysis_report` | 读取报告或指定章节 | `analysis:read` |
| `get_video_analysis_config` | 读取视频提交要求 | `analysis:submit` |
| `prepare_video_analysis` | 准备视频分析并报价 | `analysis:submit` |
| `confirm_video_analysis` | 确认报价并提交视频分析 | `analysis:submit` |
| `resume_video_analysis_upload` | 恢复原视频上传，不重复冻结币 | `analysis:submit` |
| `complete_video_analysis_upload` | 完成上传并检查入队 | `analysis:submit` |
| `cancel_analysis_task` | 取消尚未开始处理的任务 | `analysis:manage` |
| `get_analysis_feedback` | 读取报告采用情况与验证反馈 | `analysis:read` |
| `save_analysis_adoption` | 保存报告建议采用情况 | `analysis:manage` |
| `save_analysis_observation` | 保存或清除实际验证观察 | `analysis:manage` |

余额读取无需 Max；其余分析工具均需有效 Max。未指定范围时默认仅 `coins:read`。视频提交到报告读取需要 `analysis:submit` + `analysis:read`；核对任务后取消、读取并保存反馈需要 `analysis:read` + `analysis:manage`。新增范围须重新授权，旧授权或刷新令牌不会自动扩权。余额只是快照，不代替报价或扣费确认。

视频流程是：读取配置 → 准备真实文件并报价 → 用户确认金额 → 上传字节 → 检查入队 → 查询任务与报告。客户端需具备兼容的文件预检、指纹计算和上传能力；本 Skill 不附带文件桥，仅连接 MCP 的纯聊天客户端不能直接上传本地路径或附件 URI。缺少文件支持时使用网站的「新建分析」。具体恢复、取消与反馈操作见 [MCP 使用指南](skills/douchanchan/references/mcp.md)。

取消只适用于尚未开始处理的任务，释放金额以服务端结果为准。反馈记录用户真实采用情况和观察，不调用模型、不使用铲铲币、不改写原报告；冲突需由用户决定后再保存。

博主作品列表、下载、剪辑和直播录制仍通过扩展；支付、报告文件导出、分享和删除通过网站。创作档案不属于 MCP 能力。

## 🛠️ 常见问题

| 问题 | 处理方式 |
| --- | --- |
| Agent 找不到扩展 | 检查它操作的浏览器配置文件是否已安装扩展 |
| MCP 工具未出现 | 检查客户端兼容性、OAuth 连接和当前服务的上线范围；不要切换环境来获得缺失工具 |
| MCP 提示授权不足 | 重新连接并确认所需的读取、提交或管理范围 |
| 分析 MCP 提示缺少权益 | 确认账号的 Max 权益有效 |
| 服务暂不可用或限流 | 保留任务与连接，按提示稍后重试，避免重复提交 |
| 视频已确认但上传中断 | 保留原任务和文件，恢复上传；不要新建第二个付费任务 |
| 反馈保存冲突 | 读取当前记录，确认要保留的内容后再保存，不能自动覆盖 |
| 下载后未找到文件 | 检查浏览器下载记录或目标目录；触发下载不等于保存完成 |

## 🔄 更新与卸载

更新 Skill 可再次发送上面的安装提示词，保留本地修改；扩展通过对应商店更新。卸载时使用原安装工具，或仅移除对应 Skill 目录。CLI 安装的版本也可使用：

```bash
npx skills update douchanchan -g
npx skills remove douchanchan -g
```
