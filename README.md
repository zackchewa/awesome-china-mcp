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

Point any MCP client at these servers — an [OpenClaw Launch](https://openclawlaunch.com) bot, OpenClaw/Hermes, Claude Desktop, Cursor, Cline, VS Code, or any MCP-speaking framework.

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

> 🧩 **Also in here:** a [gap map](#gap-map) of 91 Chinese services that have an official API but **no MCP server yet** — pick one and build it.

> 🗓️ Last refreshed **2026-09-02**.

### Legend
`🏢` official / first-party · `👥` community · `⭐` GitHub stars (approx, drift over time) · `🌐` hosted / docs link (not a repo)

---

## ☁️ 云服务与基础设施 · Cloud & Infra

The deepest official coverage in the whole ecosystem — Alibaba Cloud alone ships 15+.

| Service | Server | Notes |
|---|---|---|
| 阿里云 CloudOps | 🏢 [`aliyun/alibaba-cloud-ops-mcp-server`](https://github.com/aliyun/alibaba-cloud-ops-mcp-server) ⭐130 | ECS / 运维 operations |
| 阿里云 Tablestore | 🏢 [`aliyun/alibabacloud-tablestore-mcp-server`](https://github.com/aliyun/alibabacloud-tablestore-mcp-server) ⭐157 | NoSQL / vector store |
| 阿里云 可观测 Observability | 🏢 [`aliyun/alibabacloud-observability-mcp-server`](https://github.com/aliyun/alibabacloud-observability-mcp-server) ⭐165 | metrics, traces, logs |
| 阿里云 云效 DevOps (Yunxiao) | 🏢 [`aliyun/alibabacloud-devops-mcp-server`](https://github.com/aliyun/alibabacloud-devops-mcp-server) ⭐165 | CI/CD, repos, work items |
| 阿里云 容器服务 ACK | 🏢 [`aliyun/alibabacloud-ack-mcp-server`](https://github.com/aliyun/alibabacloud-ack-mcp-server) ⭐116 | Kubernetes ops |
| 阿里云 RDS | 🏢 [`aliyun/alibabacloud-rds-openapi-mcp-server`](https://github.com/aliyun/alibabacloud-rds-openapi-mcp-server) ⭐55 | managed databases |
| 阿里云 DMS (40+ data sources) | 🏢 [`aliyun/alibabacloud-dms-mcp-server`](https://github.com/aliyun/alibabacloud-dms-mcp-server) ⭐52 | universal data access |
| 阿里云 DataWorks | 🏢 [`aliyun/alibabacloud-dataworks-mcp-server`](https://github.com/aliyun/alibabacloud-dataworks-mcp-server) ⭐50 | data dev / governance |
| 阿里云 (full OpenAPI) | 🏢 [`aliyun/alibabacloud-api-mcp-server`](https://github.com/aliyun/alibabacloud-api-mcp-server) ⭐30 | all Alibaba Cloud APIs |
| 阿里云 Hologres / ADB / PolarDB / OpenSearch / ESA | 🏢 [hologres](https://github.com/aliyun/alibabacloud-hologres-mcp-server) · [adb-mysql](https://github.com/aliyun/alibabacloud-adb-mysql-mcp-server) · [polardb](https://github.com/aliyun/alibabacloud-polardb-mcp-server) · [opensearch](https://github.com/aliyun/alibabacloud-opensearch-mcp-server) · [esa](https://github.com/aliyun/mcp-server-esa) | per-product servers |
| 腾讯云 COS | 🏢 [`Tencent/cos-mcp`](https://github.com/Tencent/cos-mcp) ⭐38 | object storage + 数据万象 CI |
| 腾讯云 CLS 日志 | 🏢 [`Tencent/cls-mcp-server`](https://github.com/Tencent/cls-mcp-server) | log service |
| 火山引擎 Volcengine | 🏢 [`volcengine/mcp-server`](https://github.com/volcengine/mcp-server) ⭐321 | multi-product (TOS, ECS, …) |
| 火山引擎 VOD / ImageX | 🏢 [`volcengine/mcp-vod`](https://github.com/volcengine/mcp-vod) · [`volcengine/mcp-imagex`](https://github.com/volcengine/mcp-imagex) | video / image services |
| 七牛云 Qiniu | 🏢 [`qiniu/qiniu-mcp-server`](https://github.com/qiniu/qiniu-mcp-server) ⭐39 | storage, upload, CDN |
| 华为云 Huawei Cloud | 🏢 official remote MCP — endpoint issued per-account from your console ([dev portal](https://developer.huaweicloud.com/)) | BYO endpoint URL; hosts under `huaweicloud.com` / `myhuaweicloud.com` |
| 百度智能云 Mochow (向量库) | 🏢 [`baidu/mochow-mcp-server-python`](https://github.com/baidu/mochow-mcp-server-python) | vector database |

## 🗺️ 地图与出行 · Maps & Travel

| App | Server | Notes |
|---|---|---|
| 高德地图 Amap | 🏢 [official MCP](https://lbs.amap.com/api/mcp-server/gettingstarted) · 👥 [`sugarforever/amap-mcp-server`](https://github.com/sugarforever/amap-mcp-server) ⭐127 | geocode, routing, POI, weather; free tier |
| 百度地图 Baidu Maps | 🏢 [`baidu-maps/mcp`](https://github.com/baidu-maps/mcp) ⭐440 | location, routing, weather, place search |
| 腾讯地图 Tencent Maps | 🏢 [official MCP](https://lbs.qq.com/service/MCPServer/MCPServerGuide/overview) — `https://mcp.map.qq.com/mcp?key=<KEY>` | geocode, POI, routing, weather; remote MCP, key from [console](https://lbs.qq.com/dev/console/application/mine) |
| 滴滴出行 DiDi | 🏢 official remote MCP — `https://mcp.didichuxing.com/mcp-servers?key=<KEY>` ([portal](https://mcp.didichuxing.com/)) | hail a ride: fare estimate, place order, trip status, cancel + maps; sandbox endpoint `…/mcp-servers-sandbox` |
| 飞常准 Variflight | 🏢 [`variflight/variflight-mcp`](https://github.com/variflight/variflight-mcp) ⭐31 · [`variflight/tripmatch-mcp`](https://github.com/variflight/tripmatch-mcp) | real-time flight info |
| 12306 火车票 | 👥 [`Joooook/12306-mcp`](https://github.com/Joooook/12306-mcp) ⭐1.2k · [`drfccv/mcp-server-12306`](https://github.com/drfccv/mcp-server-12306) ⭐377 | train ticket search |
| 携程 Ctrip | 👥 [`biaowuqiong/ctrip-hotel-skill`](https://github.com/biaowuqiong/ctrip-hotel-skill) | hotel price — Agent Skill via Playwright (not a native MCP server) |
| 途牛旅游 Tuniu | 🏢 official remote MCP — `https://openapi.tuniu.cn/mcp/hotel` · `…/mcp/flight` ([开放平台](https://open.tuniu.com/mcp/login)) · 🏢 [`tuniucorp/tuniu-cli`](https://github.com/tuniucorp/tuniu-cli) ⭐8 | hotels, domestic flights, tickets, trains, cruises; auth is an `apiKey` request header, not `Authorization: Bearer` |
| 美团 Meituan | 👥 [`LewisChen1219/Meituan-Mcp-Server-WIP`](https://github.com/LewisChen1219/Meituan-Mcp-Server-WIP) | food ordering (WIP) |

## 💳 支付 · Payments

| App | Server | Notes |
|---|---|---|
| 支付宝 Alipay+ (global) | 🏢 [`alipay/global-alipayplus-mcp`](https://github.com/alipay/global-alipayplus-mcp) | Alipay+ global payment APIs |
| 支付宝 (国内, 托管) | 🌐 [百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) | hosted-only, first-launch on 百炼 |

## 📱 内容与社交 · Content & Social

| App | Server | Notes |
|---|---|---|
| 小红书 Xiaohongshu | 👥 [`xpzouying/xiaohongshu-mcp`](https://github.com/xpzouying/xiaohongshu-mcp) ⭐15.6k · [`iFurySt/RedNote-MCP`](https://github.com/iFurySt/RedNote-MCP) ⭐1.1k · [`aki66938/xhs-toolkit`](https://github.com/aki66938/xhs-toolkit) ⭐1.3k | read / search / publish |
| 微信公众号 (发布) | 👥 [`caol64/wenyan-mcp`](https://github.com/caol64/wenyan-mcp) ⭐1.3k | auto-format & publish Markdown |
| 微信公众号 (下载) | 👥 [`qiye45/wechatDownload`](https://github.com/qiye45/wechatDownload) ⭐9.2k | batch article download — tool with MCP/Skill support |
| 微信公众号 (AI 阅读) | 👥 [ReadGZH](https://github.com/sweesama/readgzh) · [接入文档](https://readgzh.site/docs) | hosted remote MCP: public article URL → Markdown; search cached articles only; limited anonymous access, optional API key |
| 微信读书 WeRead | 👥 [`freestylefly/mcp-server-weread`](https://github.com/freestylefly/mcp-server-weread) ⭐574 | books, notes, highlights |
| Bilibili | 👥 [`huccihuang/bilibili-mcp-server`](https://github.com/huccihuang/bilibili-mcp-server) ⭐190 · [`34892002/bilibili-mcp-js`](https://github.com/34892002/bilibili-mcp-js) ⭐192 | search, video info |
| 知乎 Zhihu | 👥 [`iteng007/zhihu-mcp-server`](https://github.com/iteng007/zhihu-mcp-server) (API) · [`Douyh123/zhihu-mcp`](https://github.com/Douyh123/zhihu-mcp) (search/publish) · [`JasonJarvan/Zhihu-Collections-MCP`](https://github.com/JasonJarvan/Zhihu-Collections-MCP) ⭐169 (export) | API access, search, publish, export |
| 微博 Weibo | 👥 [`qinyuanpei/mcp-server-weibo`](https://github.com/qinyuanpei/mcp-server-weibo) ⭐61 | user / content / hot-search |
| 抖音 Douyin (发布) | 👥 [`lancelin111/douyin-mcp-server`](https://github.com/lancelin111/douyin-mcp-server) ⭐36 | automated video upload |
| 抖音 / B站 / 公众号 / 播客 (采集) | 👥 [`chubbyguan/chubbyskills`](https://github.com/chubbyguan/chubbyskills) ⭐657 | content-ingestion Agent Skills + a knowledge-base MCP (not per-app servers) |

## 🛒 电商 · E-commerce

| App | Server | Notes |
|---|---|---|
| 淘宝 / 闲鱼 | 👥 [`Tsinglung-Tseng/ali-mcp`](https://github.com/Tsinglung-Tseng/ali-mcp) | Taobao + Xianyu automation |
| 京东 JD | 👥 [`mako202605/mcp-jd-super-deals`](https://github.com/mako202605/mcp-jd-super-deals) · [`mako202605/mcp-jd-seckill`](https://github.com/mako202605/mcp-jd-seckill) | deals, seckill |
| 1688 | 👥 [`QuoVadis86/ai-reverse`](https://github.com/QuoVadis86/ai-reverse) ⭐19 | product / image search |

## 🍜 生活服务 · Local Life

| App | Server | Notes |
|---|---|---|
| 瑞幸咖啡 Luckin | 🏢 official remote MCP — `https://gwmcp.lkcoffee.com/order/user/mcp` ([open platform](https://open.lkcoffee.com/)) | find nearby stores, browse products, place a coffee order |
| 麦当劳 McDonald's China | 🏢 official remote MCP — `https://mcp.mcd.cn` ([授权 auth](https://open.mcd.cn/mcp/auth)) · 🏢 [`M-China/mcd-mcp-server`](https://github.com/M-China/mcd-mcp-server) ⭐133 | nutrition lookup, nearby stores, menu; Bearer token from the auth endpoint |
| 滴滴出行 DiDi | see 地图与出行 · Maps & Travel above | ride-hailing via official MCP |

## 🏢 办公协作 · Office & Collaboration

| App | Server | Notes |
|---|---|---|
| 飞书 / Lark | 🏢 [`larksuite/lark-openapi-mcp`](https://github.com/larksuite/lark-openapi-mcp) ⭐816 · 👥 [`ztxtxwd/open-feishu-mcp-server`](https://github.com/ztxtxwd/open-feishu-mcp-server) ⭐85 | docs, sheets, IM, calendar |
| 语雀 Yuque | 🏢 [`yuque/yuque-mcp-server`](https://github.com/yuque/yuque-mcp-server) ⭐234 (server) · [`yuque/yuque-ecosystem`](https://github.com/yuque/yuque-ecosystem) ⭐221 (server+skills+plugin bundle) | knowledge base CRUD |
| 钉钉 DingTalk | 👥 [`hykfft/mcp-dingtalk-doc`](https://github.com/hykfft/mcp-dingtalk-doc) ⭐55 (docs) · [`keithyt06/quick-dingtalk-mcp`](https://github.com/keithyt06/quick-dingtalk-mcp) ⭐8 (user identity, wraps the official `dws` CLI) · [`Shawyeok/mcp-dingding-bot`](https://github.com/Shawyeok/mcp-dingding-bot) ⭐12 (群机器人) | docs, personal identity, group robot |
| 腾讯文档 Tencent Docs | 🏢 official remote MCP — `https://docs.qq.com/openapi/mcp` ([auth docs](https://docs.qq.com/open/auth/mcp.html)) | read/write docs, sheets, slides |
| 腾讯会议 Tencent Meeting | 🏢 official remote MCP — `https://mcp.meeting.tencent.com/mcp/wemeet-open/v1` ([docs](https://meeting.tencent.com/ai-skill.html)) | schedule meetings, participants, recordings, transcripts |
| WPS 365 / 金山文档 | 🏢 official remote MCP — `https://openapi.wps.cn/mcp/v2/kso-yundoc/message` ([guide](https://open.wps.cn/documents/app-integration-dev/mcp-server/use-guide)) | enterprise cloud docs: search, read, share, permissions |
| 简道云 JianDaoYun | 🏢 [official personal MCP](https://hc.jiandaoyun.com/open/25090) | apps, forms, data, todos — read-only |
| MasterGo | 🏢 [`mastergo-design/mastergo-magic-mcp`](https://github.com/mastergo-design/mastergo-magic-mcp) ⭐283 | design-to-code: read MasterGo board structure, styles and specs |
| wolai 我来 | 👥 [`LittlePeter52012/wolai-mcp`](https://github.com/LittlePeter52012/wolai-mcp) ⭐8 | read / write a wolai knowledge base |
| 石墨文档 Shimo | 👥 [`kanyun-inc/rush-shimo-cli`](https://github.com/kanyun-inc/rush-shimo-cli) | read Shimo docs — CLI + SDK + MCP |
| 企业微信 WeCom (群机器人) | 👥 [`gotoolkits/mcp-wecombot-server`](https://github.com/gotoolkits/mcp-wecombot-server) ⭐37 | send text/markdown/image/news to a WeCom group robot webhook |
| 企业微信 WeCom (API 连接器) | — still none · ops-bot: [`opsre/ZenOps`](https://github.com/opsre/ZenOps) ⭐164 | no server covers the WeCom app API (contacts, approvals, messages to members). ZenOps queries ops resources via 钉钉/飞书/企微 bots — not an API connector. PR one if you build it |

## 💻 开发工具 · DevTools

| App | Server | Notes |
|---|---|---|
| Gitee | 🏢 [`oschina/mcp-gitee`](https://github.com/oschina/mcp-gitee) ⭐65 | repos, issues, PRs |
| Apifox | 🏢 [official MCP](https://docs.apifox.com/apifox-mcp-server) | API specs into agents |
| GitCode | 👥 [`Trenza1ore/GitCode-API`](https://github.com/Trenza1ore/GitCode-API) ⭐7 | GitCode REST SDK + CLI shipping MCP / agent tool definitions |
| 百度 AI Guard | 🏢 [`baidu/mcp-server-baidu-ai-guard`](https://github.com/baidu/mcp-server-baidu-ai-guard) | content moderation |
| HarmonyOS | 👥 [`XixianLiang/HarmonyOS-mcp-server`](https://github.com/XixianLiang/HarmonyOS-mcp-server) | HarmonyOS dev/test |
| LeetCode | 👥 [`jinzcdev/leetcode-mcp-server`](https://github.com/jinzcdev/leetcode-mcp-server) | problems, submissions |

## 📈 金融与数据 · Finance & Data (A股)

| App | Server | Notes |
|---|---|---|
| FinanceMCP (综合) | 👥 [`guangxiangdebizi/FinanceMCP`](https://github.com/guangxiangdebizi/FinanceMCP) ⭐660 | Tushare + Binance — A股/macro/crypto, real-time |
| AKShare | 👥 [`aahl/mcp-aktools`](https://github.com/aahl/mcp-aktools) ⭐393 · [`zwldarren/akshare-one-mcp`](https://github.com/zwldarren/akshare-one-mcp) ⭐226 | stocks, crypto, analysis |
| Tushare | 👥 [`zlinzzzz/finData-mcp-server`](https://github.com/zlinzzzz/finData-mcp-server) ⭐58 · [`hanxuanliang/tsrs-mcp-server`](https://github.com/hanxuanliang/tsrs-mcp-server) ⭐27 | financial data |
| 东方财富 / 同花顺 | 👥 [`noimank/FNewsCrawler`](https://github.com/noimank/FNewsCrawler) ⭐109 · [`27dream/mcp-eastmoney`](https://github.com/27dream/mcp-eastmoney) | quotes, news, fund flow |
| A股 Skill 集合 | 👥 [`shouldnotappearcalm/a-share-skill`](https://github.com/shouldnotappearcalm/a-share-skill) ⭐232 | quant, K-line, indicators — Agent Skills collection (not an MCP server) |

> 💡 **券商 (brokerages):** 广发证券, 国泰君安, 中信 etc. have launched internal AI "Skills" (智能投顾 贝塔牛, 易淘金, GF-Quant…), but these are app-internal agent capabilities, **not public MCP servers** you can connect to. For programmatic A股 market data, use AKShare / Tushare / 东方财富 above. PR a row if/when any brokerage ships a public MCP.

## ⚖️ 法律 · Legal (China)

| Domain | Server | Notes |
|---|---|---|
| 中国法律法规 | 👥 [`Yuhamixli/Law-Crawler-RPA-RAG-MCP`](https://github.com/Yuhamixli/Law-Crawler-RPA-RAG-MCP) ⭐31 | crawl 中国法律法规 + RAG Q&A |
| 法规检索 / 案例 | 👥 [`moyupeng0422/legal-tools`](https://github.com/moyupeng0422/legal-tools) ⭐19 | Chinese-law MCP + Skills: statutes, cases |

## 📚 学术 · Academic & Research

| Source | Server | Notes |
|---|---|---|
| 多源论文 (arXiv/PubMed/…) | 👥 [`openags/paper-search-mcp`](https://github.com/openags/paper-search-mcp) ⭐2.6k · [nodejs](https://github.com/Dianel555/paper-search-mcp-nodejs) ⭐172 | search + download academic papers |
| 知网 CNKI | 👥 [`xxxxchaos/cnki-mcp-server`](https://github.com/xxxxchaos/cnki-mcp-server) | Chinese academic search |
| AMiner | 👥 [`huanghuoguoguo/aminer-mcp`](https://github.com/huanghuoguoguo/aminer-mcp) | scholars, papers, patents (free tier) |

## 🌦️ 天气 · Weather

| App | Server | Notes |
|---|---|---|
| 彩云天气 Caiyun | 👥 [`caiyunapp/mcp-caiyun-weather`](https://github.com/caiyunapp/mcp-caiyun-weather) | minute-level forecast |
| 心知天气 Seniverse | 👥 [`sugarforever/mcp-seniverse-weather`](https://github.com/sugarforever/mcp-seniverse-weather) | city weather |
| 高德 / 百度天气 | (via Amap / Baidu Map tools, see Maps) | city weather |

## 🎵 音乐 · Music

| App | Server | Notes |
|---|---|---|
| 网易云 / QQ音乐 / 酷狗 / 酷我 | 👥 [`ELDment/Meting-Agent`](https://github.com/ELDment/Meting-Agent) ⭐105 | multi-platform music API proxy for AI |
| 网易云音乐 NetEase | 👥 [`Cheiineeey/netease-music-mcp`](https://github.com/Cheiineeey/netease-music-mcp) ⭐95 | play, lyrics sync, playlist mgmt |

## 🏠 智能家居 / IoT · Smart Home

| App | Server | Notes |
|---|---|---|
| 小米 米家 Mijia | 👥 [`handsomejustin/mijia-control`](https://github.com/handsomejustin/mijia-control) ⭐63 | 米家 × MCP × HomeKit smart-home bridge |

## 🤖 大模型与 AI 服务 · LLM & AI Services

| Provider | Server | Notes |
|---|---|---|
| MiniMax | 🏢 [`MiniMax-AI/MiniMax-MCP`](https://github.com/MiniMax-AI/MiniMax-MCP) ⭐1.6k · [JS](https://github.com/MiniMax-AI/MiniMax-MCP-JS) ⭐125 | TTS, voice clone, image & video gen |
| 魔搭 ModelScope | 🏢 [`modelscope/modelscope-mcp-server`](https://github.com/modelscope/modelscope-mcp-server) · 🌐 [MCP 广场 1400+](https://modelscope.cn/brand/view/MCP) | models + biggest CN MCP hub |
| 智谱 Zhipu (GLM) | 👥 [`wnzzer/zhipu-tools-coding-plan`](https://github.com/wnzzer/zhipu-tools-coding-plan) · [`NanguangChou/zhipu_image_mcp`](https://github.com/NanguangChou/zhipu_image_mcp) | web search, image gen |
| 通义千问 Qwen | 👥 [`zk-b612/mcp-qwen-omni`](https://github.com/zk-b612/mcp-qwen-omni) | multimodal (image/audio/voice) |
| 可灵 AI Kling (快手) | 👥 [`199-mcp/mcp-kling`](https://github.com/199-mcp/mcp-kling) ⭐40 · 🌐 [official API docs](https://klingai.com/document-api/apiReference/commonInfo) | text-to-video / text-to-image; the vendor ships a REST API only — the MCP layer is community |
| LibTV 哩布哩布 | 🏢 [`libtv-labs/libtv-skills`](https://github.com/libtv-labs/libtv-skills) | image / video gen, inpainting, short drama — official Agent Skill, not an MCP server |
| Flova | 🏢 [official Skill on ClawHub](https://clawhub.ai/flova/skills/flova-video-generator) | script → storyboard → footage → export video agent; official Agent Skill, not an MCP server |
| DeepSeek / Moonshot Kimi | model providers (OpenAI-compatible) — add via your client's model config | — |

## 🧰 实用工具 · Utilities

| Tool | Server | Notes |
|---|---|---|
| 中国数据核验 | 👥 [`CCCpan/data-verify-mcp`](https://github.com/CCCpan/data-verify-mcp) ⭐165 | ID / 企业 / 车辆 / OCR / risk |
| 工商企业大数据 | 👥 [`handaas/mcp-server`](https://github.com/handaas/mcp-server) ⭐12 · [`handaas/enterprise-mcp-server`](https://github.com/handaas/enterprise-mcp-server) | 工商信息 / 风险 / 股权 / 知识产权 (旷湖) |
| 快递 / 工商 / 发票 / 三要素 | 👥 [`FLYKID/THMCP`](https://github.com/FLYKID/THMCP) ⭐6 | 瞳虎 — logistics, biz-reg, invoice, ID verify |
| 中国法定节假日 / 调休 | 👥 [`zackchewa/china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers) | 某天是否放假/调休上班 + 整年假期表；零配置无需凭证 |
| Server酱 (微信推送) | 👥 [`zackchewa/china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers) | 主动推送通知到你自己的微信；SendKey 免费自助 |
| 百度翻译 | 👥 [`zackchewa/china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers) | 多语种文本翻译（标准版免费额度） |
| 腾讯 Web 搜索 | 🏢 [`Tencent/WebSearchMCP`](https://github.com/Tencent/WebSearchMCP) | web search |
| 博查 AI 搜索 Bocha | 🏢 [`BochaAI/bocha-search-mcp`](https://github.com/BochaAI/bocha-search-mcp) ⭐177 | Chinese web search — pages, news, images; the practical way to give a CN agent fresh sources |
| TextIn 合合信息 (IntSig) | 🏢 [`intsig-textin/textin-mcp`](https://github.com/intsig-textin/textin-mcp) ⭐28 | document parsing: PDF / image → Markdown, preserving headings, tables and layout |
| 多平台通知推送 | 👥 [`aahl/mcp-notify`](https://github.com/aahl/mcp-notify) ⭐29 | one server pushes to Bark / 微信 / 钉钉 / 飞书 / Telegram |

---

<a id="gap-map"></a>

## 🧩 官方 API，暂无 MCP Server · Official API, no MCP server (yet)

91 widely-used Chinese services that ship a documented first-party API, but for which we could not find a maintained MCP server while compiling this list (last re-swept 2026-09-02). That is the actual shape of the gap: the ecosystem's problem is not a missing index, it is missing servers.

91 个国内常用服务：官方 API 齐全，但截至 2026-09-02 我们没能找到可用且有人维护的 MCP Server。列在这里有两个用处 —— 一是告诉你这条路目前得自己写，二是每一行都是一个可以动手的项目。

> ✅ Seven rows have graduated so far. 节假日, Server酱 and 百度翻译 got servers in [`china-mcp-servers`](https://github.com/zackchewa/china-mcp-servers); the 2026-09-02 re-sweep found servers that already existed for four more — MasterGo (🏢 official, ⭐283), wolai, GitCode and Bark — and moved them up into the main list too.
>
> 🛠️ **Build one and it moves up.** Ship an MCP server for any row here, open a PR, and the row graduates into the main list above with your repo on it. Know of one we missed? Same thing — PR it, we'd rather be corrected than tidy.
>
> 💡 **Need it working today?** An agent can call any of these over plain HTTP with your own credentials. If you'd rather not write the plumbing, [OpenClaw Launch 的 /zh/china-apps](https://openclawlaunch.com/zh/china-apps) wraps most of this table behind a hosted proxy (credentials stay server-side, encrypted) — that is where this table comes from.

### 💬 消息通知 / 群机器人 · Messaging & Push

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 钉钉群机器人 | 🌐 [开发者文档](https://open.dingtalk.com/document/dingstart/custom-bot-creation-and-installation) | 向钉钉群推送文本/Markdown（官方自定义机器人） |
| 企业微信群机器人 | 🌐 [开发者文档](https://intl.cloud.tencent.com/zh/document/product/1254/78645) | 向企业微信群推送文本/Markdown（官方群机器人） |
| 企业微信自建应用 | 🌐 [开发者文档](https://developer.work.weixin.qq.com/document/path/91039) | 通过企业自建应用向可见成员发送消息（官方 API） |
| 飞书群机器人 | 🌐 [开发者文档](https://open.feishu.cn/document/ukTMukTMukTM/ucTM5YjL3ETO24yNxkjN) | 向飞书群推送文本/富文本（官方自定义机器人） |
| WxPusher | 🌐 [开发者文档](https://wxpusher.zjiecode.com/docs/) | 向微信推送个人通知（官方 SPT 接口） |
| PushPlus 推送加 | 🌐 [开发者文档](https://www.pushplus.plus/doc/guide/api.html) | 微信/邮件/App 多渠道通知（官方消息 Token） |
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
| 印象笔记 | 🌐 [开发者文档](https://app.yinxiang.com/api/DeveloperToken.action) | 笔记本/笔记搜索与读写（Developer Token） |
| flomo 浮墨 | 🌐 [开发者文档](https://flomoapp.com/) | 快速记录到 flomo 笔记 |
| 坚果云 | 🌐 [开发者文档](https://help.jianguoyun.com/) | 云盘文件管理（列目录/读写/上传，WebDAV） |
| 百度网盘 | 🌐 [开发者文档](https://pan.baidu.com/union/doc) | 云盘文件管理（百度官方 Skill，支持 OpenClaw 与 Hermes） |
| 夸克网盘 † | 🌐 [开发者文档](https://pan.quark.cn/open/v1/oauth/agent) | 文件搜索、上传下载、分享转存（官方开放 API + 官方运行包） |

### 📋 表单 / 低代码 / 项目管理 · Forms, Low-code & PM

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 维格表 | 🌐 [开发者文档](https://vika.cn/developers) | 查询与写入维格表记录（官方 Fusion API） |
| 金数据 | 🌐 [开发者文档](https://open.jinshuju.net/api_v1/) | 读取与写入表单数据（企业版官方 API） |
| 明道云 † | 🌐 [开发者文档](https://help.mingdao.com/api/introduction/) | 查询与写入 HAP 工作表记录（官方应用 API） |
| 轻流 Qingflow † | 🌐 [开发者文档](https://help-center.qingflow.com/docs/building-guides/qogxhcuwxvn19f2m/) | 查询应用、表单字段与业务数据（公有云 OpenAPI） |
| 伙伴云 Huoban | 🌐 [开发者文档](https://openapi.huoban.com/doc-661256) | 查询工作区、表格字段与业务记录（官方 OpenAPI，需付费企业版） |
| 钉钉宜搭 | 🌐 [开发者文档](https://dingtalk-yida.github.io/developer-site/docs/api/serverAPI/) | 查询宜搭表单实例（专业版官方 API） |
| TAPD † | 🌐 [开发者文档](https://open.tapd.cn/document/api-doc/) | 项目/需求/缺陷查询（腾讯官方 OpenAPI，只读） |
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
| 快递100 | 🌐 [开发者文档](https://api.kuaidi100.com/manager/page/myinfo/enterprise) | Beta · 需企业版 API 账户；多快递公司实时物流查询 |
| 顺丰速运 † | 🌐 [开发者文档](https://open.sf-express.com/) | Beta · 需顺丰月结企业客户及生产凭证；运单查询（只读） |

### 📈 金融 / 数据 / 企业信息 · Finance, Data & Company info

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 国信证券 | 🌐 [开发者文档](https://www.guosen.com.cn/gs/xxskills) | A股实时行情/K线/财务/选股（官方数据） |
| 老虎证券 | 🌐 [开发者文档](https://quant.itigerup.com/openapi/en/python/quickStart/prepare.html) | 券商持仓与资产查询（只读） |
| 天眼查 | 🌐 [开发者文档](https://open.tianyancha.com/) | 企业工商/股东/风险/诉讼查询 |
| 企查查 | 🌐 [开发者文档](https://openapi.qcc.com/) | 企业检索（官方 API，按次计费） |
| AllTick | 🌐 [开发者文档](https://alltick.co/) | 全球行情（股票/外汇/加密/商品） |
| 麦蕊智数 | 🌐 [开发者文档](https://mairuiapi.com/getlicence) | A股实时行情/K线/技术指标（MACD/KDJ/BOLL） |
| 聚合数据 | 🌐 [开发者文档](https://www.juhe.cn/) | 星座运势/彩票开奖/身份证核验 |
| 天行数据 | 🌐 [开发者文档](https://www.tianapi.com/console/) | 汇率/油价/新闻/黄历/归属地 |

### ⚖️ 法律 · Legal

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| 华宇元典 | 🌐 [开发者文档](https://open.chineselaw.com/) | 法律法规与案例检索 |

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
| 小牛翻译 | 🌐 [开发者文档](https://niutrans.com/) | 文本翻译（380+ 语种） |
| 百度OCR | 🌐 [开发者文档](https://console.bce.baidu.com/) | 图片文字识别（OCR） |

### 💻 DevTools / 身份 · DevTools & Identity

| App | 官方 API 文档 · Official docs | 能力 · What an agent can do |
|---|---|---|
| AtomGit † | 🌐 [开发者文档](https://docs.atomgit.com/) | 查询当前账号的代码仓库（官方开放 API） |
| 极狐 GitLab | 🌐 [开发者文档](https://jihulab.com/-/user_settings/personal_access_tokens) | 查询项目与 Issue（官方 GitLab API）。极狐是 GitLab 的中国发行版，API 兼容，所以通用的 [`zereight/gitlab-mcp`](https://github.com/zereight/gitlab-mcp) ⭐1.9k 指向自建实例通常可直接用 |
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
| 融云 | 🌐 [开发者文档](https://webqa.rongcloud.net/static/documentation/docs/build/platform-chat-api/auth.html) | 查询 IM 用户资料（官方服务端 API） |
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
| 夸克网盘 Quark | [`ButterFuture/GoQuark`](https://github.com/ButterFuture/GoQuark) ⭐3 | 2026-08; unofficial CLI/TUI/MCP client, AGPL-3.0 |
| TAPD | [`OneCuriousLearner/MCPAgentRE`](https://github.com/OneCuriousLearner/MCPAgentRE) ⭐12 | 2025-09; pulls TAPD data for quality reports — real, but a year without a push |
| AtomGit | [`xiongjiamu/dsh-atomgit`](https://github.com/xiongjiamu/dsh-atomgit) ⭐7 | 2026-08; a DeepSeek-Harness skills bundle, not a standalone MCP server |
| 明道云 Mingdao | [`mingdaocloud/mcp-mingdao`](https://github.com/mingdaocloud/mcp-mingdao) ⭐0 | 2025-10; org looks vendor-adjacent but we could not confirm first-party — untagged on purpose |
| 顺丰速运 SF Express | [`asgard-ai-platform/mcp-sf-express`](https://github.com/asgard-ai-platform/mcp-sf-express) ⭐0 | 2026-05 |
| 涂鸦智能 Tuya | [`Elyd0wn/mcp-tuya-local`](https://github.com/Elyd0wn/mcp-tuya-local) ⭐0 | 2026-03; local-network control, not the cloud API |
| 声网 Agora | [`cioffiAI/mcp-agora`](https://github.com/cioffiAI/mcp-agora) ⭐5 | 2026-07 |
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
| [mcp.so](https://mcp.so) | global "app store", 10,000+ servers, STDIO + SSE |
| [AIbase MCP 资源站](https://www.aibase.com/zh/repos/topic/mcp) | 400+ production servers, Chinese tutorials, beginner-friendly |
| [Glama — Awesome MCP Servers (中文)](https://glama.ai/mcp/servers) | curated 200+ ready-to-use servers, categorized |
| [`LeslieLeung/awesome-mcp-server-cn`](https://github.com/LeslieLeung/awesome-mcp-server-cn) · [`yzfly/Awesome-MCP-ZH`](https://github.com/yzfly/Awesome-MCP-ZH) | open-source awesome-lists |

*See also (global hubs, not China-specific):* [PulseMCP](https://www.pulsemcp.com) (servers + clients + trends) · [Smithery](https://smithery.ai) (beginner-friendly, copy-paste install) · [mcpservers.org](https://mcpservers.org) (curated, quality-focused).

## 🖥️ 客户端与开发平台 · Clients & Dev Platforms

Where you *run* MCP servers — connect any entry above to one of these:

| Tool | What |
|---|---|
| [OpenClaw Launch](https://openclawlaunch.com) | deploy a hosted AI agent that uses these MCP tools in one click |
| [Cherry Studio](https://github.com/CherryHQ/cherry-studio) ⭐48k | 国产 desktop AI client, visual MCP config + auto-install |
| Cursor / Cline / VS Code | dev tools — add servers via `mcp.json` |
| [扣子 Coze](https://www.coze.cn) / [Trae](https://www.trae.ai) | ByteDance agent builder + AI IDE, both with MCP markets |
| [百度千帆 AppBuilder](https://appbuilder.cloud.baidu.com) | Baidu AI app platform, MCP Server config + SSE |
| [腾讯云大模型知识引擎](https://cloud.tencent.com/product/lke) | Tencent Cloud agent builder, add MCP plugins on demand |

---

## 🤝 Contributing / 贡献

Know a Chinese-app MCP server that's missing — especially an **official** one? **PRs welcome.** Add a row in the right category with: app name, repo/docs link, official (🏢) or community (👥), and a one-line note. It does **not** have to be a GitHub repo — official MCPs published on a vendor's dev portal or marketplace count too (use a 🌐 docs link). Keep entries to real, working servers.

发现遗漏的国内服务 MCP Server（尤其是官方的）？欢迎提 PR。不一定非得是 GitHub 仓库 —— 厂商开发者平台 / 市场上的官方 MCP 同样收录（用 🌐 文档链接）。请只收录真实可用的 server。

## License

[CC0-1.0](LICENSE) — public domain. Use freely.

---

<p align="center"><sub>Maintained by <a href="https://openclawlaunch.com">OpenClaw Launch</a> — deploy an AI agent that connects to all of these in one click. · 星标 ⭐ 让更多人发现这个清单。</sub></p>
