# 公告生成工作流 · 脱敏模板

> 已移除品牌名、Bot Token、频道 ID、内部标识，以及所有可识别业务类型的字样。
> Skill 内容已清空，仅保留表头结构。

## 文件清单

| 文件 | 说明 |
|---|---|
| `announcement-skill.csv` | 空壳：仅保留表头，无内容行 |
| `emoji-maintenance.workflow.json` | n8n 工作流：自定义 emoji 解析 + 数据表更新 |
| `localization-translation.workflow.json` | n8n 工作流：多语言翻译子流程（按品牌分流） |
| `announcement-main.workflow.json` | n8n 主流程：内容生成 → 一审 → 翻译 → 二审 → 多语言分发；含 Token 的 HTTP 节点已改为占位符，`pinData` 已清空，数据表工具已停用 |

## 占位符对照

| 占位符 | 含义 |
|---|---|
| `[BRAND_A]` | 品牌 A（原 B1 线，官方/商务口径） |
| `[BRAND_B]` | 品牌 B（原 B2 线，社区化口径） |
| `[BRAND_C]` | 品牌 C（原 B3 线，运维口径） |
| `[BRAND_B_DOMAIN]` | 品牌 B 官网域名 |
| `[BRAND_B_BOT]` / `[BRAND_B_GROUP]` | 品牌 B 的 Bot / Group 链接 |
| `[BRAND_C_CHANNEL]` / `[BRAND_C_BOT]` / `[BRAND_C_SUPPORT]` | 品牌 C 的频道 / Bot / 支持账号 |
| `[PROMO_URL]` | 促销落地页链接 |
| `[TRACKING_PARAMS]` | 渠道追踪参数 |
| `[CustomProtocol]` | 自定义名称 |
| `[BOT_NAME]` | Telegram Bot 名称 |
| `{{TELEGRAM_BOT_TOKEN}}` | 主流程 HTTP 发布节点的 Bot Token 占位 |
| `{{CHANNEL_CHAT_ID}}` | 主流程 HTTP 发布节点的频道 ID 占位 |
| `[REDACTED_*]` | 已移除的内部标识（凭据 / 会话 / 数据表 / 项目 / 实例 / 工作流 / Webhook 等） |

## 使用说明

1. **CSV**：仅表头，按需自行填入内容行。
2. **n8n 工作流**：导入后需自行配置 Telegram、Google Drive、DataTable 等凭据；所有 `credentials` 仅保留引用占位，不含真实密钥。
3. **主流程发布节点**：9 个 HTTP 节点中的 `{{TELEGRAM_BOT_TOKEN}}` 与 `{{CHANNEL_CHAT_ID}}` 需替换为你自己的值。
4. **brand 入参**：`Switch` 条件与提示词统一为 `[BRAND_A]` / `[BRAND_B]` / `[BRAND_C]`；改成真实品牌名时三处需同步，否则会进错分支。

## 说明

- 本仓库不含任何真实凭据、密钥、会话 ID 或可访问的内部地址。
- 主流程的 `pinData` 已整体清空，示例消息、用户名、图片 `file_id` 均不保留。
- 第三方平台名（Telegram、Google Drive 等）保留原文，不属于本模板品牌。
