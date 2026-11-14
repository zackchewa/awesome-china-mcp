# Awesome China MCP 🇨🇳

> The curated index of **Model Context Protocol (MCP) servers for Chinese apps & services** — give your AI agent the ability to actually *use* 高德地图, 百度地图, 12306, 小红书, 飞书, 语雀, 支付宝, 阿里云, A股 data and more.
>
> 收录可连接「中国应用」的 MCP Server —— 让你的 AI Agent 真正能调用高德地图、百度地图、12306、小红书、飞书、语雀、支付宝、阿里云、A股行情等国内服务。**优先收录官方 MCP。**

<p align="center">
  <a href="https://github.com/zackchewa/awesome-china-mcp/stargazers"><img src="https://img.shields.io/github/stars/zackchewa/awesome-china-mcp?style=flat-square" alt="stars"></a>
  <img src="https://img.shields.io/badge/MCP-Model%20Context%20Protocol-blue?style=flat-square" alt="mcp">
  <img src="https://img.shields.io/badge/🏢%20official--first-orange?style=flat-square" alt="official">
  <img src="https://img.shields.io/badge/lang-中文%20%2F%20EN-green?style=flat-square" alt="lang">
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square" alt="prs">
</p>

---

## Why this exists / 为什么有这个仓库

In the West, [Composio](https://composio.dev), [Nango](https://nango.dev) and friends give an AI agent one place to connect 1000+ apps. **There is no open-source equivalent that covers Chinese apps** — the ecosystem is scattered, with each service shipping (or not shipping) its own MCP server. This list collects them in one place, **official servers first**, so you don't have to hunt.

国外有 Composio 这样的「一个平台连上千个 app」。**国内没有对应的开源索引** —— 各家服务各自为政，MCP Server 散落各处。这个清单把它们汇总到一处，官方优先。

> ℹ️ **Hosted alternative:** for a managed click-to-connect experience (OAuth handled for you), the closest is Alibaba's [百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) (~184 official + 2900+ third-party) or [魔搭 ModelScope MCP 广场](https://modelscope.cn/brand/view/MCP) (1400+ servers, biggest Chinese MCP community). Both are closed platforms; this list is the open, self-host route.

---

## How to use / 如何使用

Configure an MCP-compatible client for the servers below — Claude Desktop, Cursor, Cline, VS Code, or an agent runtime with MCP support. Transport, authentication and local dependencies vary by entry. Entries explicitly labelled API, CLI or Agent Skill use their own integration path.

```jsonc
// Example: Claude Desktop / Cursor mcp config
{
  "mcpServers": {
    "amap":  { "command": "npx", "args": ["-y", "@amap/amap-maps-mcp-server"], "env": { "AMAP_MAPS_API_KEY": "<key>" } },
    "baidu-map": { "command": "npx", "args": ["-y", "@baidumap/mcp-server-baidu-map"], "env": { "BAIDU_MAP_API_KEY": "<key>" } }
  }
}
```

> ⚠️ **BYO credentials.** Most Chinese-platform APIs (微信 / 支付宝 / 钉钉 / 电商 / 券商) require your own registered app credentials and, for the big ones, enterprise (营业执照) verification. These servers connect the API — you supply the keys.

> 🧩 **Also in here:** a [gap map](#gap-map) recording 78 official-API services from the 2026-10-10 survey, plus separately labelled [official Skills and APIs](#official-skills-and-apis). An API or Skill is not automatically an MCP server.

> 🗓️ Full links, stars & archive survey: **2026-10-10** · selected catalog additions and official documentation checked **2026-11-05** · gap map last re-swept **2026-10-10**. The latest update is a documentation review, not an authenticated end-to-end test of every service.

### Legend
`🏢` official / first-party · `👥` community · `⭐` GitHub stars (approx, drift over time) · `🌐` hosted / docs link (not a repo)

`授权 Auth` (the small line under each note): 🆓 无需 none · 🔑 API Key / Token · 🔐 OAuth 登录 · ☁️ 云 AccessKey · 🪪 AppID / Secret (开放平台应用) · 📱 扫码 / Cookie (personal login) — the vendor's docs are the authority for what each credential can do.

---

## ☁️ 云服务与基础设施 · Cloud & Infra

The deepest official coverage in the whole ecosystem — Alibaba Cloud alone ships 15+.

| Service | Server | Notes |
|---|---|---|
| 阿里云 CloudOps | 🏢 [`aliyun/alibaba-cloud-ops-mcp-server`](https://github.com/aliyun/alibaba-cloud-ops-mcp-server) ⭐131 | ECS / 运维 operations<br><sub>☁️&nbsp;AccessKey</sub> |
| 阿里云 Tablestore | 🏢 [`aliyun/alibabacloud-tablestore-mcp-server`](https://github.com/aliyun/alibabacloud-tablestore-mcp-server) ⭐157 | NoSQL / vector store<br><sub>☁️&nbsp;AccessKey</sub> |
| 阿里云 可观测 Observability | 🏢 [`aliyun/alibabacloud-observability-mcp-server`](https://github.com/aliyun/alibabacloud-observability-mcp-server) ⭐166 | metrics, traces, logs<br><sub>☁️&nbsp;AccessKey</sub> |
| 阿里云 云效 DevOps (Yunxiao) | 🏢 [`aliyun/alibabacloud-devops-mcp-server`](https://github.com/aliyun/alibabacloud-devops-mcp-server) ⭐175 | CI/CD, repos, work items<br><sub>🔑&nbsp;Token</sub> |
| 阿里云 容器服务 ACK | 🏢 [`aliyun/alibabacloud-ack-mcp-server`](https://github.com/aliyun/alibabacloud-ack-mcp-server) ⭐118 | Kubernetes ops<br><sub>☁️&nbsp;AccessKey</sub> |
| 阿里云 RDS | 🏢 [`aliyun/alibabacloud-rds-openapi-mcp-server`](https://github.com/aliyun/alibabacloud-rds-openapi-mcp-server) ⭐54 | managed databases<br><sub>☁️&nbsp;AccessKey</sub> |
| 阿里云 DMS (40+ data sources) | 🏢 [`aliyun/alibabacloud-dms-mcp-server`](https://github.com/aliyun/alibabacloud-dms-mcp-server) ⭐54 | universal data access<br><sub>☁️&nbsp;AccessKey</sub> |
| 阿里云 DataWorks | 🏢 [`aliyun/alibabacloud-dataworks-mcp-server`](https://github.com/aliyun/alibabacloud-dataworks-mcp-server) ⭐52 | data dev / governance<br><sub>☁️&nbsp;AccessKey</sub> |
| 阿里云 (full OpenAPI) | 🏢 [`aliyun/alibabacloud-api-mcp-server`](https://github.com/aliyun/alibabacloud-api-mcp-server) ⭐35 | all Alibaba Cloud APIs<br><sub>🔐&nbsp;OAuth · ☁️&nbsp;AccessKey</sub> |
| 阿里云 Hologres / ADB / PolarDB / OpenSearch / ESA | 🏢 [hologres](https://github.com/aliyun/alibabacloud-hologres-mcp-server) · [adb-mysql](https://github.com/aliyun/alibabacloud-adb-mysql-mcp-server) · [polardb](https://github.com/aliyun/alibabacloud-polardb-mcp-server) · [opensearch](https://github.com/aliyun/alibabacloud-opensearch-mcp-server) · [esa](https://github.com/aliyun/mcp-server-esa) | per-product servers<br><sub>☁️&nbsp;AccessKey · 🔑&nbsp;DB&nbsp;密码</sub> |
| 腾讯云 COS | 🏢 [`Tencent/cos-mcp`](https://github.com/Tencent/cos-mcp) ⭐38 | object storage + 数据万象 CI<br><sub>☁️&nbsp;SecretId&nbsp;/&nbsp;Key</sub> |
| 腾讯云 CLS 日志 | 🏢 [`Tencent/cls-mcp-server`](https://github.com/Tencent/cls-mcp-server) | log service<br><sub>☁️&nbsp;SecretId&nbsp;/&nbsp;Key</sub> |
| 火山引擎 Volcengine | 🏢 [`volcengine/mcp-server`](https://github.com/volcengine/mcp-server) ⭐328 | multi-product (TOS, ECS, …)<br><sub>☁️&nbsp;AccessKey</sub> |
| 火山引擎 VOD / ImageX | 🏢 [`volcengine/mcp-vod`](https://github.com/volcengine/mcp-vod) · [`volcengine/mcp-imagex`](https://github.com/volcengine/mcp-imagex) | video / image services<br><sub>☁️&nbsp;AccessKey</sub> |
| 七牛云 Qiniu | 🏢 [`qiniu/qiniu-mcp-server`](https://github.com/qiniu/qiniu-mcp-server) ⭐39 | storage, upload, CDN<br><sub>☁️&nbsp;AccessKey</sub> |
| 华为云 Huawei Cloud | 🏢 official remote MCP — endpoint issued per-account from your console ([dev portal](https://developer.huaweicloud.com/)) | BYO endpoint URL; hosts under `huaweicloud.com` / `myhuaweicloud.com`<br><sub>☁️&nbsp;AccessKey</sub> |
| 腾讯云开发 CloudBase | 🏢 official remote MCP — `https://tcb-api.cloud.tencent.com/mcp/v1?env_id=<EnvId>` · 🏢 [`TencentCloudBase/CloudBase-AI-Toolkit`](https://github.com/TencentCloudBase/CloudBase-AI-Toolkit) ⭐1.1k | the backend most 微信小程序 run on: cloud database, functions, storage, hosting, logs. Keys go in `X-TencentCloud-SecretId/SecretKey` headers; use a sub-account key scoped to TCB only; the default toolset can mint credentials<br><sub>☁️&nbsp;SecretId&nbsp;/&nbsp;Key · 🔐&nbsp;OAuth</sub> |
| 百智云浏览器 Baizhi Cloud Browser (CapyBrowser, 长亭科技) | 🏢 official remote MCP — `https://capybrowser.app.baizhi.cloud/mcp` ([docs](https://capybrowser.app.baizhi.cloud/docs/installation.md)) | cloud browser sessions and saved profiles (存档); MCP/HTTP only manages runs, page control needs a separate CDP client (e.g. Playwright `connectOverCDP`). Bearer API key; billed while a browser is running, including idle and hand-off time. ⚠️ saved profiles keep your website logins on the vendor's cloud — use one profile per site and only for accounts you are willing to delegate<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 百度智能云 Mochow (向量库) | 🏢 [`baidu/mochow-mcp-server-python`](https://github.com/baidu/mochow-mcp-server-python) | vector database<br><sub>🔑&nbsp;API&nbsp;Key</sub> |

## 🗺️ 地图与出行 · Maps & Travel

| App | Server | Notes |
|---|---|---|
| 高德地图 Amap | 🏢 [official MCP](https://lbs.amap.com/api/mcp-server/gettingstarted) · 👥 [`sugarforever/amap-mcp-server`](https://github.com/sugarforever/amap-mcp-server) ⭐131 | geocode, routing, POI, weather; free tier<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 百度地图 Baidu Maps | 🏢 [`baidu-maps/mcp`](https://github.com/baidu-maps/mcp) ⭐447 | location, routing, weather, place search<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 腾讯地图 Tencent Maps | 🏢 [official MCP](https://lbs.qq.com/service/MCPServer/MCPServerGuide/overview) — `https://mcp.map.qq.com/mcp?key=<KEY>` | geocode, POI, routing, weather; remote MCP, key from [console](https://lbs.qq.com/dev/console/application/mine)<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 滴滴出行 DiDi | 🏢 official remote MCP — `https://mcp.didichuxing.com/mcp-servers?key=<KEY>` ([portal](https://mcp.didichuxing.com/)) | hail a ride: fare estimate, place order, trip status, cancel + maps; sandbox endpoint `…/mcp-servers-sandbox`<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 飞常准 Variflight | 🏢 [`variflight/variflight-mcp`](https://github.com/variflight/variflight-mcp) ⭐33 · [`variflight/tripmatch-mcp`](https://github.com/variflight/tripmatch-mcp) | real-time flight info<br><sub>🔑&nbsp;API&nbsp;Key · 🔐&nbsp;OAuth</sub> |
| 12306 火车票 | 👥 [`Joooook/12306-mcp`](https://github.com/Joooook/12306-mcp) ⭐2.3k · [`drfccv/mcp-server-12306`](https://github.com/drfccv/mcp-server-12306) ⭐406 | train ticket search<br><sub>🆓&nbsp;无需</sub> |
| 携程 Ctrip | 👥 [`bianwuqiong/ctrip-hotel-skill`](https://github.com/bianwuqiong/ctrip-hotel-skill) | hotel price — Agent Skill via Playwright (not a native MCP server)<br><sub>📱&nbsp;扫码登录</sub> |
| 途牛旅游 Tuniu | 🏢 official remote MCP — `https://openapi.tuniu.cn/mcp/hotel` · `…/mcp/flight` ([开放平台](https://open.tuniu.com/mcp/login)) · 🏢 [`tuniucorp/tuniu-cli`](https://github.com/tuniucorp/tuniu-cli) ⭐9 | hotels, domestic flights, tickets, trains, cruises; auth is an `apiKey` request header, not `Authorization: Bearer`<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 美团 Meituan | 👥 [`LewisChen1219/Meituan-Mcp-Server-WIP`](https://github.com/LewisChen1219/Meituan-Mcp-Server-WIP) | food ordering (WIP)<br><sub>📱&nbsp;登录态&nbsp;session</sub> |

## 💳 支付 · Payments

| App | Server | Notes |
|---|---|---|
| 支付宝 Alipay+ (global) | 🏢 [`alipay/global-alipayplus-mcp`](https://github.com/alipay/global-alipayplus-mcp) | Alipay+ global payment APIs<br><sub>🪪&nbsp;商户&nbsp;ID&nbsp;/&nbsp;私钥</sub> |
| 支付宝 (国内, 托管) | 🌐 [百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) | hosted-only, first-launch on 百炼<br><sub>🌐&nbsp;在百炼开通</sub> |

## 📱 内容与社交 · Content & Social

| App | Server | Notes |
|---|---|---|
| 小红书 Xiaohongshu | 👥 [`xpzouying/xiaohongshu-mcp`](https://github.com/xpzouying/xiaohongshu-mcp) ⭐16.2k · [`iFurySt/RedNote-MCP`](https://github.com/iFurySt/RedNote-MCP) ⭐1.1k · [`aki66938/xhs-toolkit`](https://github.com/aki66938/xhs-toolkit) ⭐1.4k | read / search / publish<br><sub>📱&nbsp;扫码登录</sub> |
| 微信公众号 (发布) | 👥 [`caol64/wenyan-mcp`](https://github.com/caol64/wenyan-mcp) ⭐1.3k | auto-format & publish Markdown<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 微信公众号 (下载) | 👥 [`qiye45/wechatDownload`](https://github.com/qiye45/wechatDownload) ⭐9.7k | batch article download — tool with MCP/Skill support<br><sub>📱&nbsp;微信登录态</sub> |
| 微信公众号 (AI 阅读) | 👥 [ReadGZH](https://github.com/sweesama/readgzh) · [接入文档](https://readgzh.site/docs) | hosted remote MCP: public article URL → Markdown; search cached articles only; limited anonymous access, optional API key; ⚠️ every article read is cached and publicly listed on readgzh.site<br><sub>🔑&nbsp;API&nbsp;Key · 🔐&nbsp;OAuth</sub> |
| 微信读书 WeRead | 👥 [`freestylefly/mcp-server-weread`](https://github.com/freestylefly/mcp-server-weread) ⭐579 | books, notes, highlights<br><sub>📱&nbsp;Cookie</sub> |
| Bilibili | 👥 [`huccihuang/bilibili-mcp-server`](https://github.com/huccihuang/bilibili-mcp-server) ⭐190 · [`34892002/bilibili-mcp-js`](https://github.com/34892002/bilibili-mcp-js) ⭐194 | search, video info<br><sub>🆓&nbsp;无需</sub> |
| 知乎 Zhihu | 👥 [`meurz/zhihu-mcp-server`](https://github.com/meurz/zhihu-mcp-server) (API, archived) · [`Douyh123/zhihu-mcp`](https://github.com/Douyh123/zhihu-mcp) (search/publish) · [`JasonJarvan/Zhihu-Collections-MCP`](https://github.com/JasonJarvan/Zhihu-Collections-MCP) ⭐182 (export) | API access, search, publish, export<br><sub>📱&nbsp;Cookie · 扫码登录</sub> |
| 微博 Weibo | 👥 [`qinyuanpei/mcp-server-weibo`](https://github.com/qinyuanpei/mcp-server-weibo) ⭐63 | user / content / hot-search<br><sub>🆓&nbsp;无需 · 📱&nbsp;可选扫码</sub> |
| 抖音 Douyin (发布) | 👥 [`lancelin111/douyin-mcp-server`](https://github.com/lancelin111/douyin-mcp-server) ⭐35 | automated video upload<br><sub>📱&nbsp;扫码登录</sub> |
| 抖音 / B站 / 公众号 / 播客 (采集) | 👥 [`chubbyguan/chubbyskills`](https://github.com/chubbyguan/chubbyskills) ⭐1.2k | content-ingestion Agent Skills + a knowledge-base MCP (not per-app servers)<br><sub>🆓&nbsp;无需 · 📱&nbsp;可选&nbsp;Cookie</sub> |
| 抖音 / 小红书 / 公众号 / 视频号 / B站 / 微博 / 快手 (数据) | 👥 [`okdataapi/okdata`](https://github.com/okdataapi/okdata) · [接入文档](https://okdata.online/zh/docs/mcp/) | third-party data service, not affiliated with the platforms: hosted Streamable HTTP — `https://api.okdata.online/mcp`, or local stdio `npx -y @okdata/mcp`; public data from 17 platforms (about 200 endpoints, also TikTok, X, YouTube); Bearer API key, paid per call from $0.0001, failed calls are free; `find` / `describe` / `account` work without a key<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| AIHOT（中文 AI 资讯） | 🏢 🌐 [官方 MCP 文档](https://aihot.news/agent?tab=mcp) · source [`KKKKhazix/AIHOT`](https://github.com/KKKKhazix/AIHOT) ⭐7.1k | hosted Streamable HTTP — `https://aihot.news/api/mcp`; anonymous read-only topic search, hot events, daily / weekly / monthly briefs<br><sub>🆓&nbsp;无需</sub> |

## 🛒 电商 · E-commerce

| App | Server | Notes |
|---|---|---|
| 淘宝 / 闲鱼 | 👥 [`Tsinglung-Tseng/ali-mcp`](https://github.com/Tsinglung-Tseng/ali-mcp) | Taobao + Xianyu automation<br><sub>📱&nbsp;扫码登录</sub> |
| 京东 JD | 👥 [`mako202605/mcp-jd-super-deals`](https://github.com/mako202605/mcp-jd-super-deals) · [`mako202605/mcp-jd-seckill`](https://github.com/mako202605/mcp-jd-seckill) | deals, seckill<br><sub>🆓&nbsp;无需</sub> |
| 1688 | 👥 [`QuoVadis86/ai-reverse`](https://github.com/QuoVadis86/ai-reverse) ⭐24 | product / image search<br><sub>📱&nbsp;Cookie</sub> |

## 🍜 生活服务 · Local Life

| App | Server | Notes |
|---|---|---|
| 瑞幸咖啡 Luckin | 🏢 official remote MCP — `https://gwmcp.lkcoffee.com/order/user/mcp` ([open platform](https://open.lkcoffee.com/)) | find nearby stores, browse products, place a coffee order<br><sub>🔑&nbsp;Token</sub> |
| 麦当劳 McDonald's China | 🏢 official remote MCP — `https://mcp.mcd.cn` ([授权 auth](https://open.mcd.cn/mcp/auth)) · 🏢 [`M-China/mcd-mcp-server`](https://github.com/M-China/mcd-mcp-server) ⭐192 | nutrition lookup, nearby stores, menu; Bearer token from the auth endpoint<br><sub>🔑&nbsp;Token</sub> |
| 滴滴出行 DiDi | see 地图与出行 · Maps & Travel above | ride-hailing via official MCP<br><sub>🔑&nbsp;API&nbsp;Key</sub> |

## 🏢 办公协作 · Office & Collaboration

| App | Server | Notes |
|---|---|---|
| MinerU 文档解析 | 🏢 [`opendatalab/MinerU-Ecosystem/mcp`](https://github.com/opendatalab/MinerU-Ecosystem/tree/main/mcp) | PDF, Office and image parsing to Markdown; stdio / Streamable HTTP; documents go to MinerU cloud, with anonymous Flash mode or own API token<br><sub>🆓&nbsp;无需 · 🔑&nbsp;API&nbsp;Key</sub> |
| 滴答清单 Dida | 🏢 [official MCP guide](https://help.dida365.com/articles/7438132116019216384) — `https://mcp.dida365.com` | Tasks, lists, habits and focus records; Streamable HTTP, OAuth or API token; includes write operations<br><sub>🔐&nbsp;OAuth · 🔑&nbsp;Token</sub> |
| 飞书项目 Feishu Project | 🏢 [official MCP connection guide](https://project.feishu.cn/b/helpcenter/1ykiuvvj/wzb3ycsc) | Project/work-item queries and updates; enable MCP access in the product; HTTP OAuth, `X-Mcp-Token` or stdio setup; capabilities depend on edition and permissions<br><sub>🔐&nbsp;OAuth · 🔑&nbsp;Token</sub> |
| Doc2X 文档解析 | 🏢 [`NoEdgeAI/doc2x-mcp`](https://github.com/NoEdgeAI/doc2x-mcp) | PDF/image parsing, formula/table extraction, document export & layout JSON; MIT stdio server, own API key required, cloud API usage billed<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 飞书 / Lark | 🏢 [`larksuite/lark-openapi-mcp`](https://github.com/larksuite/lark-openapi-mcp) ⭐838 · 👥 [`ztxtxwd/open-feishu-mcp-server`](https://github.com/ztxtxwd/open-feishu-mcp-server) ⭐87 | docs, sheets, IM, calendar<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret · 🔐&nbsp;OAuth</sub> |
| 语雀 Yuque | 🏢 [`yuque/yuque-mcp-server`](https://github.com/yuque/yuque-mcp-server) ⭐248 (server) · [`yuque/yuque-ecosystem`](https://github.com/yuque/yuque-ecosystem) ⭐230 (server+skills+plugin bundle) · 👥 [`yehuoshun/yuque-ai-mcp`](https://github.com/yehuoshun/yuque-ai-mcp) ⭐7 (62 tools; 17 need a browser session cookie) | knowledge base CRUD, search, boards, statistics, recycle<br><sub>🔑&nbsp;Token&nbsp;/&nbsp;📱&nbsp;Cookie</sub> |
| 钉钉 DingTalk (企业内部应用) | 🏢 [`open-dingtalk/dingtalk-mcp`](https://github.com/open-dingtalk/dingtalk-mcp) ⭐28 · [auth docs](https://open.dingtalk.com/document/orgapp/obtain-orgapp-token) | Contacts, departments, work notifications, todos, calendar, check-in, bot messages; stdio via npx, in-house app Client ID/Secret; modules enabled via ACTIVE_PROFILES. Existing README 钉钉 row lists community servers only: merge or add this as the official entry<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 钉钉 DingTalk | 👥 [`hykfft/mcp-dingtalk-doc`](https://github.com/hykfft/mcp-dingtalk-doc) ⭐56 (docs) · [`keithyt06/quick-dingtalk-mcp`](https://github.com/keithyt06/quick-dingtalk-mcp) ⭐8 (user identity, wraps the official `dws` CLI) · [`Shawyeok/mcp-dingding-bot`](https://github.com/Shawyeok/mcp-dingding-bot) ⭐12 (群机器人) | docs, personal identity, group robot<br><sub>📱&nbsp;Cookie&nbsp;/&nbsp;🔐&nbsp;OAuth&nbsp;/&nbsp;🔑&nbsp;Token</sub> |
| 腾讯文档 Tencent Docs | 🏢 official remote MCP — `https://docs.qq.com/openapi/mcp` ([auth docs](https://docs.qq.com/open/auth/mcp.html)) | read/write docs, sheets, slides<br><sub>🔑&nbsp;Token</sub> |
| 腾讯会议 Tencent Meeting | 🏢 official remote MCP — `https://mcp.meeting.tencent.com/mcp/wemeet-open/v1` ([docs](https://meeting.tencent.com/ai-skill.html)) | schedule meetings, participants, recordings, transcripts<br><sub>🔑&nbsp;Token</sub> |
| WPS 365 / 金山文档 | 🏢 official remote MCP — `https://openapi.wps.cn/mcp/v2/kso-yundoc/message` ([guide](https://open.wps.cn/documents/app-integration-dev/mcp-server/use-guide)) | enterprise cloud docs: search, read, share, permissions<br><sub>🔐&nbsp;OAuth</sub> |
| 简道云 JianDaoYun | 🏢 [official personal MCP](https://hc.jiandaoyun.com/open/25090) | apps, forms, data, todos — read-only<br><sub>🔑&nbsp;个人授权链接</sub> |
| MasterGo | 🏢 [`mastergo-design/mastergo-magic-mcp`](https://github.com/mastergo-design/mastergo-magic-mcp) ⭐286 | design-to-code: read MasterGo board structure, styles and specs<br><sub>🔑&nbsp;Token</sub> |
| 腾讯乐享 Lexiang | 🏢 official remote MCP — `https://mcp.lexiang-app.com/mcp?company_from=<企业标识>` ([token page](https://lexiangla.com/mcp)) · 🏢 [`tencent-lexiang/lexiang-mcp-skill`](https://github.com/tencent-lexiang/lexiang-mcp-skill) | enterprise knowledge base: search, semantic snippets, browse folders; `lxmcp_` token per company<br><sub>🔑&nbsp;Token</sub> |
| 腾讯微云 Weiyun | 🏢 official remote MCP — `https://www.weiyun.com/api/v3/mcpserver` ([token page](https://www.weiyun.com/act/openclaw)) | personal cloud drive: list, create folders, rename — Bearer token scoped to the folders you authorise<br><sub>🔑&nbsp;Token</sub> |
| 氚云 H3 Yun | 🏢 official remote MCP — `https://www.h3yun.com/v1/agent/mcp` ([docs](https://help.h3yun.com/280976225/)) | low-code apps: apps, forms, schemas, records, todos; personal access token inherits your company role, public cloud only<br><sub>🔑&nbsp;Token</sub> |
| 墨刀 Modao | 🏢 official remote MCP — `https://modao.cc/agent-py/ai/mcp` ([docs](https://modao.cc/feature/ai-mcp.html)) | generate prototypes, React apps and PRDs; OAuth or personal-space token, calls spend your 墨刀 AI quota<br><sub>🔐&nbsp;OAuth · 🔑&nbsp;Token</sub> |
| Pixso | 🏢 official remote MCP — `https://pixso.cn/mcp` ([docs](https://pixso.cn/developer/zh/mcp/remote-mcp.html)) · stdio proxy `@pixso/pixso-stdio-mcp` | design-to-code: layer DSL, variants, design variables, styles (read-only); personal access token in a `Token` header<br><sub>🔑&nbsp;Token</sub> |
| 金数据 Jinshuju | 🏢 official remote MCP — `https://jinshuju.net/mcp` (OAuth; [docs](https://open.jinshuju.net/mcp/)) | forms and entries — ⚠️ tools can create, edit and delete forms and entries<br><sub>🔐&nbsp;OAuth</sub> |
| 百度网盘 Baidu Netdisk | 🏢 [`baidu-netdisk/mcp`](https://github.com/baidu-netdisk/mcp) ⭐137 | list, search, upload, share — ⚠️ the README puts `access_token` in the SSE URL, and upload reads any file the process can read<br><sub>🔐&nbsp;OAuth · 🔑&nbsp;Token</sub> |
| 印象笔记 Yinxiang | 👥 [`yinxiang-team/YXBJ-MCP`](https://github.com/yinxiang-team/YXBJ-MCP) ⭐15 | search / read / create notes via Developer Token; we could not confirm the org is first-party, and it logs note contents<br><sub>🔑&nbsp;Token</sub> |
| flomo 浮墨 | 👥 [`chatmcp/mcp-server-flomo`](https://github.com/chatmcp/mcp-server-flomo) ⭐58 | write notes to flomo (write-only); set `FLOMO_API_URL` yourself — in hosted REST mode an unset URL is taken from the request<br><sub>🔑&nbsp;Webhook&nbsp;URL</sub> |
| wolai 我来 | 👥 [`LittlePeter52012/wolai-mcp`](https://github.com/LittlePeter52012/wolai-mcp) ⭐9 | read / write a wolai knowledge base<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 石墨文档 Shimo | 👥 [`kanyun-inc/rush-shimo-cli`](https://github.com/kanyun-inc/rush-shimo-cli) | read Shimo docs — CLI + SDK + MCP<br><sub>🔑&nbsp;Token</sub> |
| 企业微信 WeCom (群机器人) | 👥 [`gotoolkits/mcp-wecombot-server`](https://github.com/gotoolkits/mcp-wecombot-server) ⭐37 · [`loonghao/wecom-bot-mcp-server`](https://github.com/loonghao/wecom-bot-mcp-server) ⭐104 | send text/markdown/image/news to a WeCom group robot webhook · loonghao adds files/images; ⚠️ a failed send logs the full webhook URL (the secret), and image URLs are fetched from any host<br><sub>🔑&nbsp;Webhook&nbsp;Key</sub> |
| 企业微信 WeCom (API 连接器) | — still none · ops-bot: [`opsre/ZenOps`](https://github.com/opsre/ZenOps) ⭐165 | no server covers the WeCom app API (contacts, approvals, messages to members). ZenOps queries ops resources via 钉钉/飞书/企微 bots — not an API connector. PR one if you build it<br><sub>—</sub> |
| 教务宝 JWB | 🏢 official remote MCP — `https://card.jwbpro.com/open/jwb/mcp` ([guide](https://www.jwbpro.com/mcp/)) | education / training-institution SaaS: students, classes, timetables, contracts, payments, reports; OAuth 2.1 + PKCE or an institution `jwb-sk-` key (key needs an active subscription) — ⚠️ write tools such as CRM lead follow-up change real business data<br><sub>🔐&nbsp;OAuth · 🔑&nbsp;API&nbsp;Key</sub> |
| 问卷星 Wenjuanxing (WJX) | 🏢 [`wjxcom/wjx-ai-kit`](https://github.com/wjxcom/wjx-ai-kit) ⭐23 · [API docs](https://www.wjx.cn/help/help.aspx?catid=140) | TypeScript SDK + CLI + MCP server over the WJX OpenAPI: surveys, questions, responses, pause/resume collection (tools can modify surveys); API key needs account API access<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 问卷网 Wenjuan | 🏢 [official MCP](https://mcp.wenjuan.com) — `https://mcp.wenjuan.com` | Create surveys, edit questions, view and export responses; WJ-API-Key from 个人中心 → API 对接 → MCP 对接<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| FlowUs 息流 | 🏢 official remote MCP — `https://mcp.flowus.cn/message` | Read/write workspace pages, databases and blocks; OAuth 2.1 (scope `all`); paid workspace required per FlowUs developer page<br><sub>🔐&nbsp;OAuth</sub> |

## 💻 开发工具 · DevTools

| App | Server | Notes |
|---|---|---|
| Sealos | 🏢 [official MCP guide](https://sealos.io/docs/AI/mcp/) | Regional Streamable HTTP services for DevBox, databases, billing and observability; workspace KubeConfig authentication; infrastructure operations may write or incur costs<br><sub>🔑&nbsp;KubeConfig</sub> |
| Gitee | 🏢 [`oschina/mcp-gitee`](https://github.com/oschina/mcp-gitee) ⭐66 | repos, issues, PRs<br><sub>🔑&nbsp;Token</sub> |
| Apifox | 🏢 [official MCP](https://docs.apifox.com/apifox-mcp-server) | API specs into agents<br><sub>🔑&nbsp;Token</sub> |
| GitCode | 👥 [`Trenza1ore/GitCode-API`](https://github.com/Trenza1ore/GitCode-API) ⭐7 | GitCode REST SDK + CLI shipping MCP / agent tool definitions<br><sub>🔑&nbsp;Token</sub> |
| TAPD | [`tapd_mcp/mcp-server-tapd`](https://cnb.cool/tapd_mcp/mcp-server-tapd) (cnb.cool, PyPI `mcp-server-tapd`) | stories, bugs, tasks, iterations, comments; Tencent-hosted but published by an individual, so untagged — ⚠️ the optional HTTP mode binds `0.0.0.0` with no auth, and upload tools read any absolute path; no LICENSE<br><sub>🔑&nbsp;Token</sub> |
| 融云 RongCloud | 🏢 [`rongcloud/rongcloud-server-mcp-python`](https://github.com/rongcloud/rongcloud-server-mcp-python) ⭐1 | IM server API: users, groups, messages — ⚠️ issues user tokens and dismisses groups without confirmation; no push since 2025-06<br><sub>🪪&nbsp;AppKey&nbsp;/&nbsp;Secret</sub> |
| 百度 AI Guard | 🏢 [`baidu/mcp-server-baidu-ai-guard`](https://github.com/baidu/mcp-server-baidu-ai-guard) | content moderation<br><sub>☁️&nbsp;AccessKey</sub> |
| HarmonyOS | 👥 [`XixianLiang/HarmonyOS-mcp-server`](https://github.com/XixianLiang/HarmonyOS-mcp-server) | HarmonyOS dev/test<br><sub>🆓&nbsp;无需</sub> |
| LeetCode | 👥 [`jinzcdev/leetcode-mcp-server`](https://github.com/jinzcdev/leetcode-mcp-server) | problems, submissions<br><sub>🆓&nbsp;无需 · 📱&nbsp;可选&nbsp;Cookie</sub> |

## 📈 金融与数据 · Finance & Data (A股)

| App | Server | Notes |
|---|---|---|
| FinanceMCP (综合) | 👥 [`guangxiangdebizi/FinanceMCP`](https://github.com/guangxiangdebizi/FinanceMCP) ⭐858 | Tushare + Binance — A股/macro/crypto, real-time<br><sub>🔑&nbsp;Token · 🔑&nbsp;可选&nbsp;Key</sub> |
| AKShare | 👥 [`aahl/mcp-aktools`](https://github.com/aahl/mcp-aktools) ⭐390 · [`zwldarren/akshare-one-mcp`](https://github.com/zwldarren/akshare-one-mcp) ⭐233 | stocks, crypto, analysis<br><sub>🆓&nbsp;无需</sub> |
| Tushare | 👥 [`zlinzzzz/finData-mcp-server`](https://github.com/zlinzzzz/finData-mcp-server) ⭐57 · [`hanxuanliang/tsrs-mcp-server`](https://github.com/hanxuanliang/tsrs-mcp-server) ⭐27 | financial data<br><sub>🔑&nbsp;Token</sub> |
| 东方财富 / 同花顺 | 👥 [`noimank/FNewsCrawler`](https://github.com/noimank/FNewsCrawler) ⭐111 (archived) · [`27dream/mcp-eastmoney`](https://github.com/27dream/mcp-eastmoney) | quotes, news, fund flow<br><sub>📱&nbsp;扫码登录&nbsp;/&nbsp;🆓&nbsp;无需</sub> |
| 华尔街见闻 / 选股宝 | 🏢 official remote MCP — `https://xgb-mcp-api.xuangubao.cn/mcp` ([token page](https://wallstreetcn.com/org-mcp/token)) | 大涨股 sectors + reasons, global finance articles and full text (rolling ~2 months); no live quotes<br><sub>🔑&nbsp;Token</sub> |
| 熔岩 Lava (A股消息面热度) | 🏢 official remote MCP — `https://lava.ai-dolphin.com/subscribe/v1/mcp` ([docs](https://lava.ai-dolphin.com/subscribe/docs)) · [`dustinliang666-blip/lava-mcp`](https://github.com/dustinliang666-blip/lava-mcp) (Agent Skill) | news-flow heat for A股 stocks and concept boards: hot lists, first mentions, hourly windows, daily panels, institution/KOL coverage; read-only. Bearer `lvk_` key or OAuth; ¥100 starter voucher, then about ¥0.005 per call. No live quotes<br><sub>🔑&nbsp;API&nbsp;Key · 🔐&nbsp;OAuth</sub> |
| A股 Skill 集合 | 👥 [`shouldnotappearcalm/a-share-skill`](https://github.com/shouldnotappearcalm/a-share-skill) ⭐243 | quant, K-line, indicators — Agent Skills collection (not an MCP server)<br><sub>🆓&nbsp;无需</sub> |
| 长桥证券 Longbridge | 🏢 [`longbridge/longbridge-mcp`](https://github.com/longbridge/longbridge-mcp) ⭐15 · [official MCP docs](https://open.longbridge.com/docs/mcp) — `https://openapi.longportapp.com/mcp` | Account, positions, watchlist, orders, quotes and news; hosted Streamable HTTP, OAuth 2.1 (Longbridge docs list the longportapp.com domain; older listings show openapi.longbridge.com). Account has trading tools: check scope before authorizing<br><sub>🔐&nbsp;OAuth</sub> |

> 💡 **券商 (brokerages):** 广发证券, 国泰君安, 中信 etc. have launched internal AI "Skills" (智能投顾 贝塔牛, 易淘金, GF-Quant…), but these are app-internal agent capabilities, **not public MCP servers** you can connect to. For programmatic A股 market data, use AKShare / Tushare / 东方财富 above. PR a row if/when any brokerage ships a public MCP.

## ⚖️ 法律 · Legal (China)

| Domain | Server | Notes |
|---|---|---|
| 中国法律法规 | 👥 [`Yuhamixli/Law-Crawler-RPA-RAG-MCP`](https://github.com/Yuhamixli/Law-Crawler-RPA-RAG-MCP) ⭐32 | crawl 中国法律法规 + RAG Q&A<br><sub>🆓&nbsp;无需</sub> |
| 华宇元典 Yuandian | 🏢 official remote MCP ×5 — `https://open.chineselaw.com/mcp/{law,case,company,securities,hallucination}/stream` ([config](https://open.chineselaw.com/mcp-config)) | statutes, cases, company and securities law, plus a legal hallucination check; OAuth<br><sub>🔐&nbsp;OAuth</sub> |
| 法规检索 / 案例 | 👥 [`moyupeng0422/legal-tools`](https://github.com/moyupeng0422/legal-tools) ⭐32 | Chinese-law MCP + Skills: statutes, cases<br><sub>🆓&nbsp;无需&nbsp;/&nbsp;🔑&nbsp;Token</sub> |

## 📚 学术 · Academic & Research

| Source | Server | Notes |
|---|---|---|
| 多源论文 (arXiv/PubMed/…) | 👥 [`openags/paper-search-mcp`](https://github.com/openags/paper-search-mcp) ⭐2.8k · [nodejs](https://github.com/Dianel555/paper-search-mcp-nodejs) ⭐186 | search + download academic papers<br><sub>🆓&nbsp;无需 · 🔑&nbsp;可选&nbsp;Key</sub> |
| 智慧芽 PatSnap | 🏢 official remote MCP (beta) — `https://connect.zhihuiya.com/2b0355/logic-mcp` ([API keys](https://open.zhihuiya.com/dashboard/api-keys)) | patent + paper search and detail fetch; Bearer API key, billed against your account quota<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 知网 CNKI | 👥 [`xxxxchaos/cnki-mcp-server`](https://github.com/xxxxchaos/cnki-mcp-server) | Chinese academic search<br><sub>🆓&nbsp;无需</sub> |
| AMiner | 👥 [`huanghuoguoguo/aminer-mcp`](https://github.com/huanghuoguoguo/aminer-mcp) | scholars, papers, patents (free tier)<br><sub>🔑&nbsp;Token</sub> |

## 🌦️ 天气 · Weather

| App | Server | Notes |
|---|---|---|
| 彩云天气 Caiyun | 👥 [`caiyunapp/mcp-caiyun-weather`](https://github.com/caiyunapp/mcp-caiyun-weather) | minute-level forecast<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 心知天气 Seniverse | 👥 [`sugarforever/mcp-seniverse-weather`](https://github.com/sugarforever/mcp-seniverse-weather) | city weather<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 高德 / 百度天气 | (via Amap / Baidu Map tools, see Maps) | city weather<br><sub>🔑&nbsp;API&nbsp;Key</sub> |

## 🎵 音乐 · Music

| App | Server | Notes |
|---|---|---|
| 网易云 / QQ音乐 / 酷狗 / 酷我 | 👥 [`ELDment/Meting-Agent`](https://github.com/ELDment/Meting-Agent) ⭐112 | multi-platform music API proxy for AI<br><sub>🆓&nbsp;无需</sub> |
| 网易云音乐 NetEase | 👥 [`Cheiineeey/netease-music-mcp`](https://github.com/Cheiineeey/netease-music-mcp) ⭐114 | play, lyrics sync, playlist mgmt<br><sub>📱&nbsp;Cookie</sub> |

## 🏠 智能家居 / IoT · Smart Home

| App | Server | Notes |
|---|---|---|
| 小米 米家 Mijia | 👥 [`handsomejustin/mijia-control`](https://github.com/handsomejustin/mijia-control) ⭐73 | 米家 × MCP × HomeKit smart-home bridge<br><sub>📱&nbsp;扫码登录</sub> |

## 🤖 大模型与 AI 服务 · LLM & AI Services

| Provider | Server | Notes |
|---|---|---|
| LifeVerse | 🏢 official remote MCP — `https://lifeverse.gufreelancer.com/api/mcp` ([guide](https://lifeverse.gufreelancer.com/mcp)) · 🏢 [`lifeversegu/lifeverse-mcp`](https://github.com/lifeversegu/lifeverse-mcp) | discover, search and recommend 11 public LifeVerse AI products; Streamable HTTP, anonymous, read-only<br><sub>🆓&nbsp;无需</sub> |
| MiniMax | 🏢 [`MiniMax-AI/MiniMax-MCP`](https://github.com/MiniMax-AI/MiniMax-MCP) ⭐1.6k · [JS](https://github.com/MiniMax-AI/MiniMax-MCP-JS) ⭐130 | TTS, voice clone, image & video gen<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 魔搭 ModelScope | 🏢 [`modelscope/modelscope-mcp-server`](https://github.com/modelscope/modelscope-mcp-server) · 🌐 [MCP 广场 1400+](https://modelscope.cn/brand/view/MCP) | models + biggest CN MCP hub<br><sub>🔑&nbsp;Token</sub> |
| 智谱 Zhipu (GLM) | 🏢 official remote MCP ×3 — `https://open.bigmodel.cn/api/mcp/{web_search_prime,web_reader,zread}/mcp` ([docs](https://docs.bigmodel.cn/cn/coding-plan/mcp/search-mcp-server); needs a GLM Coding Plan key) · 👥 [`wnzzer/zhipu-tools-coding-plan`](https://github.com/wnzzer/zhipu-tools-coding-plan) · [`NanguangChou/zhipu_image_mcp`](https://github.com/NanguangChou/zhipu_image_mcp) | web search, page reader, Zread (read any GitHub repo's docs, tree and files), image gen<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 通义千问 Qwen | 👥 [`zk-b612/mcp-qwen-omni`](https://github.com/zk-b612/mcp-qwen-omni) | multimodal (image/audio/voice)<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 可灵 AI Kling (快手) | 🏢 🌐 [China MCP / guide](https://klingai.com/app/mcp) · [Global MCP / guide](https://kling.ai/app/mcp) · official integrations: [WorkBuddy (CN)](https://github.com/klingai-tech/workbuddy-plugin), [Claude (Global)](https://github.com/klingai-tech/claude-plugin) · 👥 [`199-mcp/mcp-kling`](https://github.com/199-mcp/mcp-kling) | Official hosted OAuth MCP: `https://klingai.com/mcp/plugin` (CN), `https://kling.ai/mcp/plugin` (Global); image/video generation and task queries; generation consumes credits, and regional accounts, credits and tasks are separate. Community wrapper uses separate API credentials.<br><sub>🔐&nbsp;OAuth (official) · 🔑&nbsp;Access&nbsp;/&nbsp;Secret&nbsp;Key (community)</sub> |
| LibTV 哩布哩布 | 🏢 [`libtv-labs/libtv-skills`](https://github.com/libtv-labs/libtv-skills) | image / video gen, inpainting, short drama — official Agent Skill, not an MCP server<br><sub>🔑&nbsp;Access&nbsp;Key</sub> |
| Flova | 🏢 [official Skill on ClawHub](https://clawhub.ai/flova/skills/flova-video-generator) | script → storyboard → footage → export video agent; official Agent Skill, not an MCP server<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| Meshy | 🏢 [`meshy-dev/meshy-mcp-server`](https://github.com/meshy-dev/meshy-mcp-server) · [official guide](https://docs.meshy.ai/en/api/ai) | Text/image-to-3D, texturing, rigging and task queries; own Meshy API key; generation consumes credits<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| Tripo3D | 🏢 [`Tripo-Developer/tripo-mcp`](https://github.com/Tripo-Developer/tripo-mcp) · [official guide](https://www.tripo3d.ai/blog/cursor-tripo-mcp-tutorial) | Alpha MCP for generating 3D assets and importing them into Blender; requires Blender, Tripo add-on and API key; API credits apply<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| Hyper3D / Rodin | 🏢 [official remote MCP](https://hyper3d.ai/features/mcp) — `https://api.hyper3d.com/api/mcp` | 3D generation, progress queries and result links; browser authorization selects the billing workspace; plan, credits and permissions apply<br><sub>🔐&nbsp;OAuth</sub> |
| Mureka | 🏢 [`SkyworkAI/Mureka-mcp`](https://github.com/SkyworkAI/Mureka-mcp) | Lyrics, songs and instrumental music; own API key and credits; upstream setup targets international `api.mureka.ai`, while Launch's API connection uses the China service<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| DeepSeek / Moonshot Kimi | model providers (OpenAI-compatible) — add via your client's model config | <sub>🔑&nbsp;API&nbsp;Key</sub> |
| Vidu 生数科技 | 🏢 [`shengshu-ai/vidu-mcp`](https://github.com/shengshu-ai/vidu-mcp) ⭐5 | Text-to-video, image-to-video, reference-to-video and start-end-frame video; stdio via uvx, Python 3.10+; Vidu platform API credits required<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| FastGPT | 🏢 [official MCP server feature](https://doc.fastgpt.cn/docs/introduction/guide/dashboard/mcp_server) — `https://<host>/api/mcp/app/<MCP_KEY>/mcp` | Expose your published FastGPT apps/agents as MCP tools (Streamable HTTP; SSE for self-hosted); MCP_KEY in the URL is the credential; running apps consumes credits<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 讯飞星辰 Agent 工作流 iFlytek Astron | 🏢 [`iflytek/ifly-workflow-mcp-server`](https://github.com/iflytek/ifly-workflow-mcp-server) ⭐28 | Call a published iFlytek Agent workflow as an MCP tool; needs flow_id and API Key:API Secret in config.yaml; simple implementation, activity unclear<br><sub>🔑&nbsp;API&nbsp;Key</sub> |

## 🧰 实用工具 · Utilities

| Tool | Server | Notes |
|---|---|---|
| AntV 图表 | 🏢 [`antvis/mcp-server-chart`](https://github.com/antvis/mcp-server-chart) | Chart generation; stdio / SSE / Streamable HTTP; default public renderer needs no key and receives chart data; private renderer configurable<br><sub>🆓&nbsp;无需 · 🔑&nbsp;可选&nbsp;Key</sub> |
| 秘塔AI搜索 Metaso | 🏢 [official API portal](https://metaso.cn/search-api/playground) · [MCP guide](https://www.modelscope.cn/mcp/servers/metasota/metaso-search) — `https://metaso.cn/api/mcp` | Multi-source search, webpage reading and RAG Q&A; remote HTTP MCP; own Bearer API key and quota<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 工商企业大数据 | 👥 [`handaas/mcp-server`](https://github.com/handaas/mcp-server) ⭐12 · [`handaas/enterprise-mcp-server`](https://github.com/handaas/enterprise-mcp-server) | 工商信息 / 风险 / 股权 / 知识产权 (旷湖)<br><sub>🔑&nbsp;SecretId&nbsp;/&nbsp;Key · Token</sub> |
| 企查查 Qichacha | 🏢 official remote MCP ×10 — `https://agent.qcc.com/mcp/{company,risk,ipr,operation,history,executive,regulation,case,tender,document}/stream` ([guide](https://agent.qcc.com/guide)) | 工商 / 风险 / 知识产权 / 司法 / 招投标; Bearer API key or OAuth, billed per call<br><sub>🔑&nbsp;API&nbsp;Key · 🔐&nbsp;OAuth</sub> |
| 天眼查 Tianyancha | 🏢 official remote MCP — `https://mcp.tianyancha.com/mcp` · 🏢 [`tyc-tech/tyc-cli`](https://github.com/tyc-tech/tyc-cli) ⭐19 (CLI client for it) | 工商 / 股东 / 风险 / 诉讼; OAuth<br><sub>🔐&nbsp;OAuth</sub> |
| 快递100 Kuaidi100 | 🏢 [`kuaidi100-api/kuaidi100-MCP`](https://github.com/kuaidi100-api/kuaidi100-MCP) ⭐14 | parcel tracking across carriers (read-only); enterprise API account — ⚠️ the key travels in the query string and can surface in error messages<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| PushPlus 推送加 | 🏢 [`pushplus/pushplus-MCP-Server-TypeScript`](https://github.com/pushplus/pushplus-MCP-Server-TypeScript) ⭐3 | push to 微信 / email / app — ⚠️ also exposes account tools (AccessKey, token minting, points) with no confirmation; give the agent only what it needs<br><sub>🔑&nbsp;Token</sub> |
| 小牛翻译 NiuTrans | 🏢 [`NiuTrans/MCP-TextTranslation`](https://github.com/NiuTrans/MCP-TextTranslation) ⭐8 | text translation, 380+ languages<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 快递 / 工商 / 发票 / 三要素 | 👥 [`FLYKID/THMCP`](https://github.com/FLYKID/THMCP) ⭐7 | 瞳虎 — logistics, biz-reg, invoice, ID verify<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 中国法定节假日 / 调休 | 👥 [`zackchewa/china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers) | 某天是否放假/调休上班 + 整年假期表；零配置无需凭证 — ⚠️ repo archived, unmaintained<br><sub>🆓&nbsp;无需</sub> |
| Server酱 (微信推送) | 👥 [`zackchewa/china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers) | 主动推送通知到你自己的微信；SendKey 免费自助 — ⚠️ repo archived, unmaintained<br><sub>🔑&nbsp;SendKey</sub> |
| 百度翻译 | 👥 [`zackchewa/china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers) | 多语种文本翻译（标准版免费额度） — ⚠️ repo archived, unmaintained<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 腾讯 Web 搜索 | 🏢 [`Tencent/WebSearchMCP`](https://github.com/Tencent/WebSearchMCP) | web search<br><sub>☁️&nbsp;SecretId&nbsp;/&nbsp;Key</sub> |
| 博查 AI 搜索 Bocha | 🏢 [`BochaAI/bocha-search-mcp`](https://github.com/BochaAI/bocha-search-mcp) ⭐185 | Chinese web search — pages, news, images; the practical way to give a CN agent fresh sources<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| TextIn 合合信息 (IntSig) | 🏢 [`intsig-textin/textin-mcp`](https://github.com/intsig-textin/textin-mcp) ⭐29 | document parsing: PDF / image → Markdown, preserving headings, tables and layout<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 多平台通知推送 | 👥 [`aahl/mcp-notify`](https://github.com/aahl/mcp-notify) ⭐28 | one server pushes to Bark / 微信 / 钉钉 / 飞书 / Telegram<br><sub>🔑&nbsp;Token</sub> |
| Everything2MCP 本地/私网协议聚合 | 👥 [`shcdwz1234/Everything2MCP`](https://github.com/shcdwz1234/Everything2MCP) | OpenAPI/gRPC/MQTT/queues; hot-reload; business writes disabled by default; experimental, limited 飞书/钉钉/企业微信 adapters; `npx everything2mcp`<br><sub>🆓&nbsp;无需 · 🔑&nbsp;可选&nbsp;Token</sub> |
| 腾讯云联网搜索 Tencent Cloud Web Search | 🏢 [`Tencent/WebSearchMCP`](https://github.com/Tencent/WebSearchMCP) ⭐8 | Web search over Sogou sources via Tencent Cloud Web Search API; SecretId/SecretKey, API must be enabled and is billed per call<br><sub>☁️&nbsp;AccessKey</sub> |
| 百度搜索 Baidu AI Search | 🏢 [`baidubce/app-builder` ai_search](https://github.com/baidubce/app-builder/tree/master/python/mcp_server/ai_search) — `https://qianfan.baidubce.com/v2/ai_search/mcp` | Real-time web search for pages and news via Qianfan AppBuilder; Streamable HTTP/SSE/stdio; Qianfan API Key; free daily quota per vendor console (100/day reported)<br><sub>🔑&nbsp;API&nbsp;Key</sub> |

---

<a id="official-skills-and-apis"></a>

## 🧩 官方 Skills 与 API · Official Skills & APIs

These complement the MCP catalog. The linked integrations below are Skills, CLIs or HTTP APIs; they are not presented as MCP servers, nor as evidence that no MCP implementation exists. Upstream capabilities can differ from the subset available in a hosted product.

这些条目补充官方 Skill、CLI 和 HTTP API 接入方式，不计入 MCP Server 或下方历史空缺清单。上游功能与托管产品实际开放的操作范围可能不同。

| Service | Official source | Integration and requirements |
|---|---|---|
| ima | 🏢 [official Skill and credentials](https://ima.qq.com/agent-interface) | Search/read/create notes and query/import knowledge-base content; own ima API credentials; official Agent Skill<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 百度文库 AI PPT | 🏢 [personal PPT Skill](https://github.com/baidu-netdisk/bdpan-storage/tree/main/skills/baidu-wenku-aippt-personal) | Generate a presentation from a topic with the bdpan CLI and return a preview link; personal Baidu authorization and account quota apply<br><sub>🔐&nbsp;OAuth</sub> |
| 中国移动云盘 | 🏢 [official platform](https://open.yun.139.com/) · [cm-cloud-manage Skill](https://skillhub.cn/skills/org-vt43r0t0/cm-cloud-manage) | File search, browsing and management with account authorization; upstream includes writes, while Launch's reviewed integration currently exposes read-only file queries<br><sub>🔐&nbsp;OAuth</sub> |
| AiPPT | 🏢 [official Skill guide](https://open.aippt.cn/docs/zh/claw/docs.html) · [API access](https://open.aippt.cn/docs/zh/guide/access.html) | PPT generation and download; official guide links `huiyuan1234/aipptskill`; platform application and enterprise verification for App Key / Secret Key<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 美图 / MeituHub | 🏢 [official API and CLI guide](https://www.meituhub.com/zh-cn/docs?id=150) | Image/video creative APIs and meitu-cli; OpenAPI uses AK/SK request signing; usage consumes account credits<br><sub>🔑&nbsp;AK&nbsp;/&nbsp;SK</sub> |
| PicWish / 佐糖 | 🏢 [China API docs](https://picwish.cn/background-removal-api-doc) · [API plans](https://picwish.cn/api-pricing) | Background removal and image enhancement; China-site API key and developer API credits<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| LiblibAI 哩布哩布 | 🏢 [official API platform](https://www.liblib.art/apis) | Model/workflow image generation; API credits are separate from website membership credits; model and workflow licensing applies<br><sub>🔑&nbsp;Access&nbsp;/&nbsp;Secret&nbsp;Key</sub> |
| 网易企业邮箱 NetEase Qiye Mail | 🏢 [official client setup docs](https://qiye.163.com/help/af988e.html) | IMAP/SMTP mailbox access with a client authorization code; admin must enable client access<br><sub>🔑&nbsp;授权码</sub> |
| 阿里企业邮箱 Alibaba Mail | 🏢 [official client setup docs](https://help.aliyun.com/zh/document_detail/444269.html) | IMAP mailbox access with a client-specific security password; admin must enable it<br><sub>🔑&nbsp;授权码</sub> |
| 微信小程序发布 WeChat Mini Program CI | 🏢 [official miniprogram-ci docs](https://developers.weixin.qq.com/miniprogram/dev/devtools/ci.html) | Official Node package to build, preview and upload mini programs without the desktop DevTools; needs the mini program AppID and an upload private key, plus an IP whitelist if enabled<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 腾讯企业邮箱 Tencent Exmail | 🏢 [official client password docs](https://open.work.weixin.qq.com/help2/pc/19902) | IMAP/SMTP mailbox access with a client-specific password; admin must enable it<br><sub>🔑&nbsp;授权码</sub> |
| 微信支付 WeChat Pay | 🏢 [official merchant API v3 docs](https://pay.weixin.qq.com/doc/v3/merchant/4012365336) | Direct-merchant APIv3: orders, refunds, bill downloads; requests signed with merchant certificate and private key (merchant ID, cert serial, platform public key)<br><sub>🪪&nbsp;商户号&nbsp;/&nbsp;证书</sub> |
| 友盟+ U-App Umeng | 🏢 [official OpenAPI docs](https://developer.umeng.com/open-api/ns/com.umeng.uapp/apply) | App list and install/active/launch statistics via OpenAPI; apiKey and apiSecurity from the Umeng console, OpenAPI access must be applied for<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 即梦AI 图片生成 Jimeng (Volcengine) | 🏢 [official API docs](https://www.volcengine.com/docs/6444/2697409) | Jimeng 4.0/4.6 text-to-image, image-to-image and multi-image composition up to 4K; Volcengine API key, billed per image<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 微信小店 WeChat Shop | 🏢 [official Mini Shop API docs](https://developers.weixin.qq.com/doc/store/API/) | Merchant self-developed access to own orders and products; AppID/AppSecret, server IP must be whitelisted<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 有赞 Youzan | 🏢 [official open API docs](https://doc.youzanyun.com/resource/doc/3011/3011) | Self-use merchant app: shop orders, logistics and products; client_id/client_secret plus shop kdt_id<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 乐橙 Imou | 🏢 [official open platform docs](https://open.imou.com/document/introduction/) | Camera list/online status, snapshots, PTZ and privacy mode via open platform; AppId/AppSecret from a developer account<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 云之家群机器人 Yunzhijia | 🏢 [official bot docs](https://www.yunzhijia.com/opendocs/docs.html) | Send text notifications to a group chat via webhook URL; group admin must create the bot (public cloud). Write-only<br><sub>🔑&nbsp;Webhook&nbsp;URL</sub> |
| 微伴助手 Weiban | 🏢 [official open API docs](https://openapi.weibanzhushou.com/) | Read departments, staff, customer tags and material library; corp ID and open-platform secret, requires Weiban base seat and API authorization<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 网易七鱼 Qiyu | 🏢 [official open API docs](https://qiyukf.apifox.cn/doc-437010) | Query customer-service groups and agents; AppKey/AppSecret, Professional edition or above<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| 123云盘 123pan | 🏢 [official Open API docs](https://123yunpan.yuque.com/org-wiki-123yunpan-muaork/cr6ced) | Browse directories, search files by name, read file details; read-only use; needs a developer entitlement pack; Client ID + Client Secret<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |
| V2EX | 🏢 [official API 2.0 docs](https://www.v2ex.com/help/api) | Read node topics, replies, notifications and profile; read-only; Personal Access Token from settings<br><sub>🔑&nbsp;Token</sub> |
| 通义万相 Wan (Tongyi Wanxiang) | 🏢 [official API docs](https://help.aliyun.com/zh/model-studio/text-to-image-v2-api-reference) · [video](https://help.aliyun.com/zh/model-studio/text-to-video-api-reference) | Text-to-image and text-to-video via Alibaba Cloud Model Studio (百炼); billed per use<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 通义千问语音合成 Qwen-TTS | 🏢 [official API docs](https://help.aliyun.com/zh/model-studio/qwen-tts-api) | Text-to-speech with multiple voices and dialects (e.g. Beijing, Shanghai, Cantonese) via Alibaba Cloud Model Studio; billed per use<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 通义语音识别 Fun-ASR | 🏢 [official API docs](https://help.aliyun.com/zh/model-studio/fun-asr-recorded-speech-recognition-http-api) | Transcribe recorded audio/video files with timestamps and speaker separation (up to 12 hours); via Alibaba Cloud Model Studio; billed by duration<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 豆包 Seedance 视频生成 | 🏢 [official API docs](https://www.volcengine.com/docs/82379/1520757) | Seedance 2.0 / 2.5 text-to-video and image-to-video (first/last frame, multi-image reference) with optional audio via Volcengine Ark; billed by resolution and duration<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 百度千帆应用 Qianfan App | 🏢 [official API docs](https://cloud.baidu.com/doc/qianfan-api/s/7m7wqq361) | Run apps/agents published on Qianfan AppBuilder via API; app ID + API Key; usage consumes quota<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 阿里云百炼应用 Model Studio Apps | 🏢 [official API docs](https://help.aliyun.com/zh/model-studio/call-single-agent-application) | Call agent/workflow applications published in Model Studio via API; app ID + API Key; usage consumes quota<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 火山方舟应用 Ark Bot | 🏢 [official API docs](https://www.volcengine.com/docs/82379/1526787) | Call no-code apps (Bots) built on Volcengine Ark, with their web-search and knowledge-base plugins; Bot ID + Ark API Key; usage consumes quota<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 理杏仁 Lixinger | 🏢 [official Open API docs](https://www.lixinger.com/open/api/doc) | A-share / HK / US valuation percentiles, financial statements, announcements and macro data; read-only; token from the open platform<br><sub>🔑&nbsp;Token</sub> |
| 得到大脑 / Get笔记 | 🏢 [official OpenAPI](https://www.biji.com/openapi) | List and read personal notes and knowledge bases via the official OpenAPI; API Key + Client ID; active membership required; community MCP: [`iswalle/getnote-mcp`](https://github.com/iswalle/getnote-mcp)<br><sub>🔑&nbsp;API&nbsp;Key</sub> |
| 阿里云短信 Alibaba Cloud SMS | 🏢 [official API docs](https://help.aliyun.com/zh/sms/developer-reference/api-dysmsapi-2017-05-25-overview) | Query approved signatures/templates, send domestic SMS by template, check delivery status; billed per message; reachable via the generic Alibaba Cloud OpenAPI MCP (product code Dysmsapi)<br><sub>☁️&nbsp;AccessKey</sub> |
| 腾讯云短信 Tencent Cloud SMS | 🏢 [official API docs](https://cloud.tencent.com/document/product/382/13444) | Query approved signatures/templates and send domestic SMS by template; SecretId/SecretKey plus SmsSdkAppId and region; billed per message<br><sub>☁️&nbsp;SecretId&nbsp;/&nbsp;Key</sub> |
| 赛邮 SUBMAIL | 🏢 [official API docs](https://www.mysubmail.com/documents) | Read SMS delivery logs and remaining SMS quota for your own app; read-only; SMS AppID + AppKey<br><sub>🪪&nbsp;AppID&nbsp;/&nbsp;Secret</sub> |

---

<a id="gap-map"></a>

## 🧩 官方 API，暂无 MCP Server · Official API, no MCP server (yet)

78 widely-used Chinese services that ship a documented first-party API, but for which we could not find a maintained MCP server while compiling this list (last re-swept 2026-10-10). That is the actual shape of the gap: the ecosystem's problem is not a missing index, it is missing servers.

78 个国内常用服务：官方 API 齐全，但截至 2026-10-10 我们没能找到可用且有人维护的 MCP Server。列在这里有两个用处 —— 一是告诉你这条路目前得自己写，二是每一行都是一个可以动手的项目。

> ✅ Twenty rows have graduated so far. 节假日, Server酱 and 百度翻译 got servers in [`china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers); the 2026-09-02 re-sweep found servers that already existed for four more — MasterGo (🏢 official, ⭐283), wolai, GitCode and Bark — and moved them up into the main list too. The 2026-10-10 re-sweep moved thirteen more up: 企查查, 天眼查, 金数据, 华宇元典, 快递100, PushPlus, 小牛翻译, 百度网盘 and 融云 now ship official servers, and maintained community servers turned up for 企业微信群机器人, 印象笔记, flomo and TAPD. Every repo had its source read for security first, and each hosted endpoint was matched against the vendor's own docs; warnings are inline.
>
> 🛠️ **Build one and it moves up.** Ship an MCP server for any row here, open a PR, and the row graduates into the main list above with your repo on it. Know of one we missed? Same thing — PR it, we'd rather be corrected than tidy.
>
> 💡 **Related product catalog:** [OpenClaw Launch 的 /zh/china-apps](https://openclawlaunch.com/zh/china-apps) offers selected managed connections through MCP, HTTP APIs, mail protocols and reviewed agent Skills. Proxy credentials are encrypted server-side; some Skills authorize inside the selected bot. Check each card for supported actions, account requirements and availability. This GitHub directory and the product catalog are maintained separately; a listing here does not mean Launch supports every upstream capability.

### 💬 消息通知 / 群机器人 · Messaging & Push

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 钉钉群机器人 | 🌐 [开发者文档](https://open.dingtalk.com/document/dingstart/custom-bot-creation-and-installation) | 向钉钉群推送文本/Markdown（官方自定义机器人） |
| 企业微信自建应用 | 🌐 [开发者文档](https://developer.work.weixin.qq.com/document/path/91039) | 通过企业自建应用向可见成员发送消息（官方 API） |
| 飞书群机器人 | 🌐 [开发者文档](https://open.feishu.cn/document/ukTMukTMukTM/ucTM5YjL3ETO24yNxkjN) | 向飞书群推送文本/富文本（官方自定义机器人） |
| WxPusher | 🌐 [开发者文档](https://wxpusher.zjiecode.com/docs/) | 向微信推送个人通知（官方 SPT 接口） |
| PushDeer | 🌐 [开发者文档](https://www.pushdeer.com/official.html) | 向自己的手机与 Mac 推送消息（官方在线版） |
| 极光推送 | 🌐 [开发者文档](https://docs.jiguang.cn/jpush/server/push/server_overview) | 向指定 App 用户发送通知（JPush 官方服务端 API） |
| 个推 | 🌐 [开发者文档](https://docs.getui.com/getui/server/rest_v2/standard/) | 向指定 App 客户端发送通知（官方 RestAPI V2） |
| 小米推送 | 🌐 [开发者文档](https://dev.mi.com/xiaomihyperos/documentation/detail?pId=1542) | 向单个小米设备发送应用通知（官方服务端 API） |
| 华为推送 | 🌐 [开发者文档](https://developer.huawei.com/consumer/cn/hms/huawei-pushkit/) | 向单个华为设备发送应用通知（官方 Push Kit API） |
| vivo 推送 | 🌐 [开发者文档](https://dev.vivo.com.cn/documentCenter/doc/362) | 向单个 vivo 设备发送应用通知（官方 UPS API） |
| OPPO 推送 | 🌐 [开发者文档](https://open.oppomobile.com/) | 向单个 OPPO 设备发送应用通知（官方 PUSH API） |
| 荣耀推送 Honor | 🌐 [开发者文档](https://developer.honor.com/) | 向单个荣耀设备发送应用通知（官方 Push REST API） |
| 云片短信 | 🌐 [开发者文档](https://www.yunpian.com/official/document/sms/zh_CN/domestic_single_send) | 使用已审核签名与模板发送国内短信（官方 API） |
| SendCloud | 🌐 [开发者文档](https://www.sendcloud.net/doc/email_v2/apiuser_do/) | 查询邮件 API_USER 与发信域配置（官方 API） |

### 📧 邮箱 · Email

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| QQ邮箱 | 🌐 [开发者文档](https://help.mail.qq.com/detail/106/985) | 收件箱查询/搜索/读取/发信（IMAP/SMTP 授权码） |
| 网易163邮箱 | 🌐 [开发者文档](https://help.mail.163.com/) | 收件箱查询/搜索/读取/发信（IMAP/SMTP 授权码） |
| 网易126邮箱 | 🌐 [开发者文档](https://help.mail.126.com/) | 收件箱查询/搜索/读取/发信（IMAP/SMTP 授权码） |
| 新浪邮箱 | 🌐 [开发者文档](https://help.sina.com.cn/comquestiondetail/view/1566/) | 收件箱查询/搜索/读取/发信（@sina.com 授权码） |

### 📝 笔记 / 网盘 / 设计 · Notes, Drive & Design

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 坚果云 | 🌐 [开发者文档](https://help.jianguoyun.com/) | 云盘文件管理（列目录/读写/上传，WebDAV） |
| 夸克网盘 † | 🌐 [开发者文档](https://pan.quark.cn/open/v1/oauth/agent) | 文件搜索、上传下载、分享转存（官方开放 API + 官方运行包） |

### 📋 表单 / 低代码 / 项目管理 · Forms, Low-code & PM

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 维格表 | 🌐 [开发者文档](https://vika.cn/developers) | 查询与写入维格表记录（官方 Fusion API） |
| 明道云 † | 🌐 [开发者文档](https://help.mingdao.com/api/introduction/) | 查询与写入 HAP 工作表记录（官方应用 API） |
| 轻流 Qingflow † | 🌐 [开发者文档](https://help-center.qingflow.com/docs/building-guides/qogxhcuwxvn19f2m/) | 查询应用、表单字段与业务数据（公有云 OpenAPI） |
| 伙伴云 Huoban | 🌐 [开发者文档](https://openapi.huoban.com/doc-661256) | 查询工作区、表格字段与业务记录（官方 OpenAPI，需付费企业版） |
| 钉钉宜搭 | 🌐 [开发者文档](https://dingtalk-yida.github.io/developer-site/docs/api/serverAPI/) | 查询宜搭表单实例（专业版官方 API） |
| PingCode | 🌐 [开发者文档](https://pingcode.apifox.cn/api-101722138) | 查询研发项目详情（官方开放 API） |
| Worktile | 🌐 [开发者文档](https://worktile.apifox.cn/api-101771895) | 分页查询项目任务（官方开放 API） |
| Teambition | 🌐 [开发者文档](https://open.teambition.com/docs/documents/5d89a927a55fbd000120c30c) | 分页查询组织成员（官方企业应用 API） |

### 🛍️ 电商 / ERP / 财务 · Commerce, ERP & Finance ops

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 聚水潭 | 🌐 [开发者文档](https://open.jushuitan.com/) | 查询已授权店铺列表（官方 ERP 开放 API） |
| 畅捷通好会计 | 🌐 [开发者文档](https://open.chanjet.com/) | 查询账套资产负债表（官方企业开放 API） |
| 用友 U8 | 🌐 [开发者文档](https://u8open.yonyoucloud.com/apiCenter/token_get) | 查询 U8 Cloud 账套列表（官方开放 API） |
| 小鹅通 | 🌐 [开发者文档](https://api-doc.xiaoe-tech.com/develop_guide/get_access_token.html) | 分页查询店铺课程（官方开放 API） |

### 🤝 CRM / HR / 客服 · CRM, HR & Support

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 纷享销客 | 🌐 [开发者文档](https://developer.fxiaoke.com/openapi_v2/start/quickstart/start.html) | 分页查询 CRM 客户（官方 OpenAPI） |
| Moka | 🌐 [开发者文档](https://www.mokahr.com/docs/api/index.html) | 查询招聘申请与候选人进度（官方开放 API） |
| 2号人事部 | 🌐 [开发者文档](https://openapi.2haohr.com/doc/openapi/start/) | 搜索企业员工档案（官方 OpenAPI） |
| 中智关爱通 | 🌐 [开发者文档](https://open.guanaitong.com/doc/token-create/) | 按账号查询企业员工（官方开放平台） |
| Udesk | 🌐 [开发者文档](https://www.udesk.cn/doc/apiv2/intro/) | 分页查询客服工单（官方开放 API） |
| 美洽 | 🌐 [开发者文档](https://www.meiqia.com/help/article/apiv2-0/) | 读取客服会话详情（官方 API） |

### ✍️ 电子签 · E-signature

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| e签宝 | 🌐 [开发者文档](https://open.esign.cn/doc/opendoc/dev-guide3/tggw2e) | 查询电子合同签署流程详情（官方开放 API） |
| 法大大 | 🌐 [开发者文档](https://developer.fadada.com/portal/doc/SFUINCMCT9) | 查询电子合同签署任务详情（官方开放 API v3） |
| 腾讯电子签 | 🌐 [开发者文档](https://cloud.tencent.com/document/product/1323/70377) | 批量查询合同流程状态（官方企业 API） |

### 📦 物流快递 · Logistics

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 快递鸟 | 🌐 [开发者文档](https://www.kdniao.com/) | 快递单号物流轨迹查询 |
| 顺丰速运 † | 🌐 [开发者文档](https://open.sf-express.com/) | Beta · 需顺丰月结企业客户及生产凭证；运单查询（只读） |

### 📈 金融 / 数据 / 企业信息 · Finance, Data & Company info

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 国信证券 | 🌐 [开发者文档](https://www.guosen.com.cn/gs/xxskills) | A股实时行情/K线/财务/选股（官方数据） |
| 老虎证券 | 🌐 [开发者文档](https://quant.itigerup.com/openapi/en/python/quickStart/prepare.html) | 券商持仓与资产查询（只读） |
| AllTick | 🌐 [开发者文档](https://alltick.co/) | 全球行情（股票/外汇/加密/商品） |
| 麦蕊智数 | 🌐 [开发者文档](https://mairuiapi.com/getlicence) | A股实时行情/K线/技术指标（MACD/KDJ/BOLL） |
| 聚合数据 | 🌐 [开发者文档](https://www.juhe.cn/) | 星座运势/彩票开奖/身份证核验 |
| 天行数据 | 🌐 [开发者文档](https://www.tianapi.com/console/) | 汇率/油价/新闻/黄历/归属地 |

### ⚖️ 法律 · Legal

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|

### 🌦️ 天气 · Weather

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 和风天气 † | 🌐 [开发者文档](https://console.qweather.com/) | 天气预报与空气质量 |

### 🌏 翻译 / OCR · Translation & OCR

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 有道翻译 | 🌐 [开发者文档](https://ai.youdao.com/) | 文本翻译（有道智云） |
| 腾讯翻译 | 🌐 [开发者文档](https://console.cloud.tencent.com/cam/capi) | 文本翻译（腾讯机器翻译） |
| 讯飞翻译 | 🌐 [开发者文档](https://console.xfyun.cn/) | 文本翻译（讯飞机器翻译） |
| 百度OCR | 🌐 [开发者文档](https://console.bce.baidu.com/) | 图片文字识别（OCR） |

### 💻 DevTools / 身份 · DevTools & Identity

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| AtomGit † | 🌐 [开发者文档](https://docs.atomgit.com/) | 查询当前账号的代码仓库（官方开放 API） |
| 极狐 GitLab | 🌐 [开发者文档](https://jihulab.com/-/user_settings/personal_access_tokens) | 查询项目与 Issue（官方 GitLab API）。极狐是 GitLab 的中国发行版，API 兼容，所以通用的 [`zereight/gitlab-mcp`](https://github.com/zereight/gitlab-mcp) ⭐2k 指向自建实例通常可直接用 |
| 蒲公英 | 🌐 [开发者文档](https://www.pgyer.com/doc/en/view/api) | 查询已发布的 App 与版本详情（官方 API 2.0） |
| Authing | 🌐 [开发者文档](https://core.authing.cn/openapi/) | 分页查询身份云用户目录（官方管理 API） |

### ☁️ 云 / 可观测 · Cloud & Observability

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| UCloud | 🌐 [开发者文档](https://console.ucloud.cn/uaccount/api_manage) | 项目与云主机查询（官方 OpenAPI） |
| 又拍云 | 🌐 [开发者文档](https://console.upyun.com/) | 对象存储目录与文件元数据查询（官方 REST API） |
| DNSPod | 🌐 [开发者文档](https://console.cloud.tencent.com/cam/capi) | 域名与 DNS 解析记录查询（腾讯云 API 3.0） |
| 青云 QingCloud | 🌐 [开发者文档](https://docsv4.qingcloud.com/user_guide/development_docs/api/overview/) | 查询云服务器实例（官方 IaaS API） |
| 京东云 JDCloud | 🌐 [开发者文档](https://docs.jdcloud.com/) | 查询云主机等资源（官方 OpenAPI）。⭐3 [`Algovate/lingjing-cli`](https://github.com/Algovate/lingjing-cli) covers 灵境 image/video gen — a different product, not the IaaS API |
| 金山云 Kingsoft Cloud | 🌐 [开发者文档](https://docs.ksyun.com/) | 查询云服务器实例（官方 KEC API） |
| 观测云 | 🌐 [开发者文档](https://docs.guance.com/open-api/) | 查询监控仪表板与监控器（官方 OpenAPI） |
| 百度统计 | 🌐 [开发者文档](https://tongji.baidu.com/api/manual/) | 查询商业账号下的网站列表（官方 Tongji API） |

### 📡 实时通信 / IoT · RTC & IoT

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 声网 Agora † | 🌐 [开发者文档](https://doc.shengwang.cn/archive/0.0.9/faq/integration-issues/restful-authentication) | 查询开发者项目列表（官方 RESTful API） |
| 环信 | 🌐 [开发者文档](https://doc.easemob.com/document/server-side/enable_and_configure_IM.html) | 查询即时通讯用户资料（官方服务端 REST API） |
| 网易云信 | 🌐 [开发者文档](https://doc.commsease.com/messaging/server-apis/TE0ODUzMDI?platform=server) | 批量查询 IM 用户资料（官方服务端 API） |
| 涂鸦智能 † | 🌐 [开发者文档](https://developer.tuya.com/cn/docs/cloud/) | 查询状态并控制已绑定的智能设备（官方云 API） |
| 萤石云 | 🌐 [开发者文档](https://open.ys7.com/) | 查询已绑定智能设备信息与在线状态（官方开放 API） |
| 中国移动 OneNET | 🌐 [开发者文档](https://iot.10086.cn/doc/v5/develop/detail/278) | 查询物联网设备最新属性（官方物模型 API） |

### 💳 支付 · Payments

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| Ping++ | 🌐 [开发者文档](https://www.pingxx.com/api/) | 查询聚合支付 Charge 列表（官方支付 API） |

### 📱 小程序 · Mini Programs

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 微信小程序 | 🌐 [开发者文档](https://mp.weixin.qq.com/) | 查询小程序每日访问趋势（官方数据分析 API） |
| 微信小程序 构建发布 | 🌐 [开发者文档](https://developers.weixin.qq.com/miniprogram/dev/devtools/ci.html) | 不开桌面开发者工具直接构建/上传/发布（官方 miniprogram-ci Node 包，无 MCP 封装） |

### 🧳 出行 · Travel

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 携程问道 Ctrip Wendao | 🌐 [开发者文档](https://www.ctrip.com/wendao/openclaw) | 酒店 / 机票 / 火车票 / 攻略自然语言问答（官方只读 API，Beta 名额有限） |

### 🎬 AI 内容创作 · AI content creation

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 讯飞智文 AI PPT | 🌐 [开发者文档](https://www.xfyun.cn/doc/spark/PPTv2.html) | 一句话生成 PPT 并下载 pptx（讯飞智文官方 API） |

### 🎈 免费公共 API · Free public APIs

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 今日诗词 | 🌐 — | 古诗词一言（随机名句） |

#### † 早期尝试 · Early attempts (unmaintained or near-zero traction)

Not promoted into the main list — listed so you don't redo the work, and so you can fork instead of starting cold:

| App | Repo | State |
|---|---|---|
| 轻流 Qingflow | [`853046310/qingflow-mcp`](https://github.com/853046310/qingflow-mcp) ⭐1 · [`qingflow76/qingflow-skill`](https://github.com/qingflow76/qingflow-skill) ⭐1 | 2026-03 / 2026-08; the `qingflow76` account is 1 repo old and we could not confirm it is first-party |
| 夸克网盘 Quark | [`ButterFuture/GoQuark`](https://github.com/ButterFuture/GoQuark) ⭐10 | 2026-08; unofficial CLI/TUI/MCP client, AGPL-3.0 |
| AtomGit | [`xiongjiamu/dsh-atomgit`](https://github.com/xiongjiamu/dsh-atomgit) ⭐6 | 2026-08; a DeepSeek-Harness skills bundle, not a standalone MCP server |
| 明道云 Mingdao | [`mingdaocloud/mcp-mingdao`](https://github.com/mingdaocloud/mcp-mingdao) ⭐0 | 2025-10; org looks vendor-adjacent but we could not confirm first-party — untagged on purpose |
| 顺丰速运 SF Express | [`asgard-ai-platform/mcp-sf-express`](https://github.com/asgard-ai-platform/mcp-sf-express) ⭐0 | 2026-05 |
| 涂鸦智能 Tuya | [`Elyd0wn/mcp-tuya-local`](https://github.com/Elyd0wn/mcp-tuya-local) ⭐0 | 2026-03; local-network control, not the cloud API |
| 和风天气 QWeather | [`NovaVoyager/mcp_qweather`](https://github.com/NovaVoyager/mcp_qweather) ⭐2 · [`xjtuwangke/mcp-qweather`](https://github.com/xjtuwangke/mcp-qweather) ⭐0 | 2025-05 / 2026-05 |
---

## 🌐 Hosted unified platforms (closed-source) / 托管统一平台

If you'd rather not self-host, these proprietary platforms act as the "Composio for China" (managed auth, one console):

| Platform | What | Open-source? |
|---|---|---|
| [阿里云百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) | ~184 official + 2900+ third-party MCP, managed OAuth/KMS | ❌ |
| [魔搭 ModelScope MCP 广场](https://modelscope.cn/brand/view/MCP) | 1400+ servers, biggest Chinese MCP community | ❌ |
| [扣子 Coze 插件市场](https://www.coze.cn/store/plugin) | 700+ plugins, bound to Coze agents | ❌ |
| 腾讯元器 / 火山引擎 MCP | cloud MCP marketplaces | ❌ |

## 🧭 MCP 资源站 / Hubs · Registries & discovery

Directories to *find* servers (not app connectors themselves):

| Hub | What |
|---|---|
| [魔搭 ModelScope MCP 广场](https://modelscope.cn/mcp) | 1400+ servers, biggest Chinese MCP community, SSE / local |
| [腾讯 SkillHub](https://skillhub.cn/) · [`Tencent/skillhub`](https://github.com/Tencent/skillhub) | Agent Skill discovery, versions and downloads through the official public API; a Skill registry, not an MCP server; review third-party packages before installing |
| [mcp.so](https://mcp.so) | global "app store", 10,000+ servers, STDIO + SSE |
| [AIbase MCP 资源站](https://www.aibase.com/zh/repos/topic/mcp) | 400+ production servers, Chinese tutorials, beginner-friendly |
| [Glama — Awesome MCP Servers (中文)](https://glama.ai/mcp/servers) | curated 200+ ready-to-use servers, categorized |
| [`LeslieLeung/awesome-mcp-server-cn`](https://github.com/LeslieLeung/awesome-mcp-server-cn) · [`yzfly/Awesome-MCP-ZH`](https://github.com/yzfly/Awesome-MCP-ZH) | open-source awesome-lists |

*See also (global hubs, not China-specific):* [PulseMCP](https://www.pulsemcp.com) (servers + clients + trends) · [Smithery](https://smithery.ai) (beginner-friendly, copy-paste install) · [mcpservers.org](https://mcpservers.org) (curated, quality-focused).

## 🖥️ 客户端与开发平台 · Clients & Dev Platforms

Where you *run* MCP servers — connect any entry above to one of these:

| Tool | What |
|---|---|
| [OpenClaw Launch](https://openclawlaunch.com) | hosted OpenClaw / Hermes agents with selected Chinese-app connections; supported actions and setup vary by catalog entry |
| [Cherry Studio](https://github.com/CherryHQ/cherry-studio) ⭐52.5k | 国产 desktop AI client, visual MCP config + auto-install |
| Cursor / Cline / VS Code | dev tools — add servers via `mcp.json` |
| [扣子 Coze](https://www.coze.cn) / [Trae](https://www.trae.ai) | ByteDance agent builder + AI IDE, both with MCP markets |
| [百度千帆 AppBuilder](https://appbuilder.cloud.baidu.com) | Baidu AI app platform, MCP Server config + SSE |
| [腾讯云大模型知识引擎](https://cloud.tencent.com/product/lke) | Tencent Cloud agent builder, add MCP plugins on demand |

---

## 🤝 Contributing / 贡献

Know a Chinese-app MCP server that's missing — especially an **official** one? **PRs welcome.** Add a row in the right category with: app name, repo/docs link, official (🏢) or community (👥), and a one-line note followed by how you sign in as a small second line (授权 Auth, see the [Legend](#legend)), e.g. `city weather<br><sub>🔑 API Key</sub>`. It does **not** have to be a GitHub repo — official MCPs published on a vendor's dev portal or marketplace count too (use a 🌐 docs link). Keep entries to real, working servers.

发现遗漏的国内服务 MCP Server（尤其是官方的）？欢迎提 PR。不一定非得是 GitHub 仓库 —— 厂商开发者平台 / 市场上的官方 MCP 同样收录（用 🌐 文档链接）。新增条目请在 Notes 说明后另起一行用小字写明授权方式（「授权 Auth」，如 `城市天气<br><sub>🔑 API Key</sub>`）。请只收录真实可用的 server。

## License

[CC0-1.0](LICENSE) — public domain. Use freely.

---

<p align="center"><sub>Maintained by <a href="https://openclawlaunch.com">OpenClaw Launch</a> — hosted OpenClaw and Hermes agents with selected Chinese-app integrations. · 星标 ⭐ 让更多人发现这个清单。</sub></p>
