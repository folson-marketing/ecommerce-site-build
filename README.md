# E-commerce Site Build / 独立站新建与改版 Skill

An agent skill by **Folson Marketing** that builds a new e-commerce / D2C storefront or redesigns an existing one, from requirements to launch, gated by 5 explicit user approvals. It uses the open [Agent Skills](https://agentskills.io) format (`SKILL.md`), so it works in Claude, ChatGPT, Codex and other agents that support skills.

一个由 **Folson Marketing** 出品的 Agent Skill：独立站 / 跨境电商网站从需求到上线的新建与改版全流程，用 5 道用户确认闸门控制节奏。采用开放的 Agent Skills 格式（`SKILL.md`），可在 Claude、ChatGPT、Codex 及其他支持 Skills 的 Agent 中使用。

## 两个版本 / Two editions

| | English edition | 中文版 |
|---|---|---|
| Skill | `ecommerce-site-build` | `ecommerce-site-build-zh` |
| For | English-speaking teams | 中文团队（出海 / 跨境电商品牌） |
| Language | English instructions and reports | 中文说明与汇报；面向海外消费者的页面文案按目标市场语言写 |

Both editions share the same workflow, gates and rules. **Install one edition per team**; installing both means either one may answer a request.
两个版本流程、闸门和规则相同。**每个团队只安装一个版本**；两个都装的话，Agent 可能随机选用其中一个。

## 流程 / Workflow

```
G0 需求澄清 Requirements → G1 素材就绪 Assets → G2 HTML 方向稿 Design directions
→ G3 样板页 Pilot pages → G4 定稿 Sign-off → 批量铺开 Rollout → 上线验收 Live QA
```

| Gate | 阶段 | Stage | 出口 / Exit |
|---|---|---|---|
| G0 | 需求澄清（老站先做只读审计） | Requirements (read-only audit for existing sites) | 需求摘要 Requirements summary |
| G1 | 素材就绪 | Assets ready | 素材清单 Asset list |
| G2 | 2–3 版 HTML 方向稿 | 2–3 HTML design directions | 设计规范 Locked design spec |
| G3 | 每类模板一个样板页 + 自验收 | One pilot per template + self-QA | 用户确认样板 Pilots approved |
| G4 | 定稿与铺开方案 | Sign-off and rollout plan | 用户说"开始铺开" "Start the rollout" |
| — | 分批铺开、回读核对、上线验收、交接 | Batch rollout, read-back, live QA, handover | 交接文档 Handover doc |

可选阶段：产品文案重写与内容迁移（立标准 → 3 个试点 → 批量回读）。
Optional phase: product copy rewrite and content migration (set the standard → 3 pilots → batch with read-back).

## 支持的平台 / Platforms

Shopify（Admin GraphQL / 连接器）· 纯 HTML 静态站 static HTML（Vercel / Netlify / GitHub Pages）· WordPress / WooCommerce · Shopline、Shoplazza 等 SaaS 平台 · 其他框架 other frameworks (Next.js, etc.)

缺哪个连接器，Skill 都会提示你安装；也可以改用浏览器（你自己登录）或导出 / 导入文件。
If a connector is missing, the skill tells you how to install it, or falls back to a browser (you log in) or file export / import.

## 安装 / Install

### Claude.ai / Claude 桌面端 Desktop

1. Download this repo as a ZIP and unzip it. 下载本仓库 ZIP 并解压。
2. Zip the edition's folder on its own: `skills/ecommerce-site-build/` (English) or `skills/ecommerce-site-build-zh/` (中文). The ZIP must contain the folder, with `SKILL.md` directly inside it. 单独把对应版本的文件夹压缩成 ZIP（ZIP 里是这个文件夹，`SKILL.md` 直接在文件夹里）。
3. In claude.ai, open **Customize → Skills**, click **+**, choose **Create skill → Upload a skill**, upload the ZIP and toggle it on. 在 claude.ai 打开 **Customize → Skills**，点 **+**，选 **Create skill → Upload a skill** 上传 ZIP，然后打开开关。

### Claude Code

As a plugin (recommended, easy to update) / 作为插件安装（推荐，方便更新）:

```
/plugin marketplace add folson-marketing/ecommerce-site-build
/plugin install ecommerce-site-build@folson-marketing      # English edition
/plugin install ecommerce-site-build-zh@folson-marketing   # 中文版
```

Or with the open-source `skills` installer (also works for Codex, Cursor and 70+ agents) / 或用开源 `skills` 安装器（同样支持 Codex、Cursor 等）:

```bash
npx skills add folson-marketing/ecommerce-site-build --agent claude-code -g
```

Or copy the skill folder manually / 或手动复制：

```bash
git clone https://github.com/folson-marketing/ecommerce-site-build.git
cp -r ecommerce-site-build/skills/ecommerce-site-build ~/.claude/skills/      # English
cp -r ecommerce-site-build/skills/ecommerce-site-build-zh ~/.claude/skills/   # 中文
```

### OpenAI Codex and other agents / 其他 Agent

Use `npx skills add ... --agent codex`, or copy the edition's folder into the agent's skills directory (Codex: `~/.codex/skills/` or `.agents/skills/`). Check your agent's docs for the exact path.
用 `npx skills add ... --agent codex`，或把对应版本的文件夹复制到该 Agent 的 skills 目录（Codex 为 `~/.codex/skills/` 或 `.agents/skills/`），具体路径以该 Agent 文档为准。

### ChatGPT

**ChatGPT Skills** (Business, Enterprise, Edu workspaces): zip the edition's folder, then in ChatGPT open **Plugins → Skills**, click **+**, choose **Upload from your computer** and upload it.
**ChatGPT Skills**（Business、Enterprise、Edu 工作区）：把对应版本的文件夹压缩成 ZIP，在 ChatGPT 打开 **Plugins → Skills**，点 **+**，选 **Upload from your computer** 上传。

**Custom GPT** (Free, Plus, Pro): paste the instruction below into the GPT's Instructions field, and upload `SKILL.md` plus the `references/` files as Knowledge. Store and deploy steps need GPT Actions; otherwise the GPT outputs code and checklists for you to apply by hand.
**自定义 GPT**（Free、Plus、Pro）：把下面这段贴进 GPT 的 Instructions，把 `SKILL.md` 和 `references/` 里的文件作为 Knowledge 上传。店铺和部署操作需要配置 Actions，否则 GPT 会输出代码和清单让你手动操作。

> Follow the attached "SKILL.md" as your complete operating procedure whenever the user wants to build or redesign an e-commerce site or storefront. Read the whole document first, including "Running outside Claude". Never pass a gate without the user's explicit approval. / 用户要新建或改版独立站时，把附件 "SKILL.md" 作为完整操作流程执行。先通读全文，包括"在 Claude 之外运行"一节。没有用户明确确认，不过任何闸门。

### 开始使用 / Start

- English: say "build a Shopify store for my brand" or "redesign our product pages".
- 中文：说「帮我做一个独立站」或「我们的 Shopify 产品页要改版」。

## 仓库结构 / Repo layout

```
.claude-plugin/marketplace.json     Claude Code marketplace: one plugin per edition
skills/ecommerce-site-build/        English edition
  SKILL.md
  references/                       site structure, platforms, content rewrite
skills/ecommerce-site-build-zh/     中文版
  SKILL.md
  references/                       网站结构、各平台路线、文案重写
```

When you change the workflow, update both editions so they stay in step, and bump `version` in `.claude-plugin/marketplace.json`.
修改流程时请同步更新两个版本，并在 `.claude-plugin/marketplace.json` 里升级 `version`。

## Guardrails

- 没有你的明确确认，不过任何闸门；试点做完必须停下等确认再批量。No gate passes without your explicit approval; pilots stop and wait before any batch.
- 不碰线上、不发布、不输入密码；发布主题和上线由你自己点。Never touches the live site, never publishes, never types passwords; you click publish.
- 改前备份，改后从系统回读逐条核对。Backs up before every write and verifies by reading back from the system.
- 不编造评价、认证、数字和背书；缺的标【待用户补充】。Never invents reviews, certifications, numbers or endorsements; gaps are flagged for you.

## License

Released under the [MIT License](LICENSE).
