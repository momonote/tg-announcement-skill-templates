# TG 公告生成 Skill · 脱敏模板

> 脱敏导出：所有品牌名、域名、Telegram 账号、渠道追踪参数与运营侧内部 ID 均已替换为占位符。
> 仅保留结构与文案框架，可直接作为模板复用。

## 文件清单

| 文件 | 说明 |
|---|---|
| `announcement-skill.csv` | 公告生成规则母版：通用硬规则、三个分区的品牌口径、场景示例（版本发布 / 热点借势 / 节点更新 / 节日 / 流媒体解锁）、语言区、Footer 规范 |
| `emoji-maintenance.workflow.json` | n8n 工作流：Telegram 自定义 emoji 解析 + 技能数据表更新 |
| `localization-translation.workflow.json` | n8n 工作流：多语言翻译子流程（按品牌分流） |

## 占位符对照

| 占位符 | 含义 |
|---|---|
| `[BRAND_A]` | 品牌 A（原 B1 线，官方/商务口径） |
| `[BRAND_B]` | 品牌 B（原 B2 线，社区化口径） |
| `[BRAND_C]` | 品牌 C（原 B3 线，运维/机场口径） |
| `[BRAND_B_DOMAIN]` | 品牌 B 官网域名 |
| `[BRAND_B_BOT]` / `[BRAND_B_GROUP]` | 品牌 B 的 Bot / Group 链接 |
| `[BRAND_C_CHANNEL]` / `[BRAND_C_BOT]` / `[BRAND_C_SUPPORT]` | 品牌 C 的频道 / Bot / 支持账号 |
| `[PROMO_URL]` | 促销落地页链接 |
| `[TRACKING_PARAMS]` | 渠道追踪参数（channel / utm_*） |
| `[CustomProtocol]` | 自有传输协议名 |
| `[BOT_NAME]` | Telegram Bot 名称 |
| `[REDACTED_*]` | 已移除的内部标识（凭据 / 会话 / 数据表 / 项目 / 实例 / 工作流 / Webhook 等） |

## 使用说明

1. **CSV**：可直接查看或用表格软件打开；复用前将占位符替换为你的品牌信息即可。
2. **n8n 工作流**：导入后需自行配置 Telegram、Google Drive、DataTable 等凭据；所有 `credentials` 仅保留引用占位，不含真实密钥。
3. **brand 入参**：翻译子流程的 `Switch` 条件已与提示词统一为 `[BRAND_A]` / `[BRAND_B]` / `[BRAND_C]`。若改成真实品牌名，**三处需同步改名**，否则会进错分支。

## 说明

- 本仓库不含任何真实凭据、密钥、会话 ID 或可访问的内部地址。
- 第三方平台与作品名（Telegram、Google Drive、YouTube、Disney+、Marvel 等）保留原文，不属于本模板品牌，未做替换。
