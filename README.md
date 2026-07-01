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

### Legend
`🏢` official / first-party · `👥` community · `⭐` GitHub stars (approx, drift over time) · `🌐` hosted / docs link (not a repo)

---

## ☁️ 云服务与基础设施 · Cloud & Infra

The deepest official coverage in the whole ecosystem — Alibaba Cloud alone ships 15+.

| Service | Server | Notes |
|---|---|---|
| 阿里云 CloudOps | 🏢 [`aliyun/alibaba-cloud-ops-mcp-server`](https://github.com/aliyun/alibaba-cloud-ops-mcp-server) ⭐120 | ECS / 运维 operations |
| 阿里云 Tablestore | 🏢 [`aliyun/alibabacloud-tablestore-mcp-server`](https://github.com/aliyun/alibabacloud-tablestore-mcp-server) ⭐155 | NoSQL / vector store |
| 阿里云 可观测 Observability | 🏢 [`aliyun/alibabacloud-observability-mcp-server`](https://github.com/aliyun/alibabacloud-observability-mcp-server) ⭐142 | metrics, traces, logs |
| 阿里云 云效 DevOps (Yunxiao) | 🏢 [`aliyun/alibabacloud-devops-mcp-server`](https://github.com/aliyun/alibabacloud-devops-mcp-server) ⭐127 | CI/CD, repos, work items |
| 阿里云 容器服务 ACK | 🏢 [`aliyun/alibabacloud-ack-mcp-server`](https://github.com/aliyun/alibabacloud-ack-mcp-server) ⭐114 | Kubernetes ops |
| 阿里云 RDS | 🏢 [`aliyun/alibabacloud-rds-openapi-mcp-server`](https://github.com/aliyun/alibabacloud-rds-openapi-mcp-server) ⭐54 | managed databases |
| 阿里云 DMS (40+ data sources) | 🏢 [`aliyun/alibabacloud-dms-mcp-server`](https://github.com/aliyun/alibabacloud-dms-mcp-server) ⭐46 | universal data access |
| 阿里云 DataWorks | 🏢 [`aliyun/alibabacloud-dataworks-mcp-server`](https://github.com/aliyun/alibabacloud-dataworks-mcp-server) ⭐46 | data dev / governance |
| 阿里云 (full OpenAPI) | 🏢 [`aliyun/alibabacloud-api-mcp-server`](https://github.com/aliyun/alibabacloud-api-mcp-server) ⭐23 | all Alibaba Cloud APIs |
| 阿里云 Hologres / ADB / PolarDB / OpenSearch / ESA | 🏢 [hologres](https://github.com/aliyun/alibabacloud-hologres-mcp-server) · [adb-mysql](https://github.com/aliyun/alibabacloud-adb-mysql-mcp-server) · [polardb](https://github.com/aliyun/alibabacloud-polardb-mcp-server) · [opensearch](https://github.com/aliyun/alibabacloud-opensearch-mcp-server) · [esa](https://github.com/aliyun/mcp-server-esa) | per-product servers |
| 腾讯云 COS | 🏢 [`Tencent/cos-mcp`](https://github.com/Tencent/cos-mcp) ⭐37 | object storage + 数据万象 CI |
| 腾讯云 CLS 日志 | 🏢 [`Tencent/cls-mcp-server`](https://github.com/Tencent/cls-mcp-server) | log service |
| 火山引擎 Volcengine | 🏢 [`volcengine/mcp-server`](https://github.com/volcengine/mcp-server) ⭐301 | multi-product (TOS, ECS, …) |
| 火山引擎 VOD / ImageX | 🏢 [`volcengine/mcp-vod`](https://github.com/volcengine/mcp-vod) · [`volcengine/mcp-imagex`](https://github.com/volcengine/mcp-imagex) | video / image services |
| 七牛云 Qiniu | 🏢 [`qiniu/qiniu-mcp-server`](https://github.com/qiniu/qiniu-mcp-server) ⭐37 | storage, upload, CDN |
| 百度智能云 Mochow (向量库) | 🏢 [`baidu/mochow-mcp-server-python`](https://github.com/baidu/mochow-mcp-server-python) | vector database |

## 🗺️ 地图与出行 · Maps & Travel

| App | Server | Notes |
|---|---|---|
| 高德地图 Amap | 🏢 [official MCP](https://lbs.amap.com/api/mcp-server/gettingstarted) · 👥 [`sugarforever/amap-mcp-server`](https://github.com/sugarforever/amap-mcp-server) ⭐111 | geocode, routing, POI, weather; free tier |
| 百度地图 Baidu Maps | 🏢 [`baidu-maps/mcp`](https://github.com/baidu-maps/mcp) ⭐435 | location, routing, weather, place search |
| 腾讯地图 Tencent Maps | 🏢 [official MCP](https://lbs.qq.com/service/MCPServer/MCPServerGuide/overview) | location, routing, POI |
| 飞常准 Variflight | 🏢 [`variflight/variflight-mcp`](https://github.com/variflight/variflight-mcp) ⭐31 · [`variflight/tripmatch-mcp`](https://github.com/variflight/tripmatch-mcp) | real-time flight info |
| 12306 火车票 | 👥 [`Joooook/12306-mcp`](https://github.com/Joooook/12306-mcp) ⭐948 · [`drfccv/mcp-server-12306`](https://github.com/drfccv/mcp-server-12306) ⭐348 | train ticket search |
| 携程 Ctrip | 👥 [`biaowuqiong/ctrip-hotel-skill`](https://github.com/biaowuqiong/ctrip-hotel-skill) | hotel price — Agent Skill via Playwright (not a native MCP server) |
| 美团 Meituan | 👥 [`LewisChen1219/Meituan-Mcp-Server-WIP`](https://github.com/LewisChen1219/Meituan-Mcp-Server-WIP) | food ordering (WIP) |

## 💳 支付 · Payments

| App | Server | Notes |
|---|---|---|
| 支付宝 Alipay+ (global) | 🏢 [`alipay/global-alipayplus-mcp`](https://github.com/alipay/global-alipayplus-mcp) | Alipay+ global payment APIs |
| 支付宝 (国内, 托管) | 🌐 [百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) | hosted-only, first-launch on 百炼 |

## 📱 内容与社交 · Content & Social

| App | Server | Notes |
|---|---|---|
| 小红书 Xiaohongshu | 👥 [`xpzouying/xiaohongshu-mcp`](https://github.com/xpzouying/xiaohongshu-mcp) ⭐14.4k · [`iFurySt/RedNote-MCP`](https://github.com/iFurySt/RedNote-MCP) ⭐1k · [`aki66938/xhs-toolkit`](https://github.com/aki66938/xhs-toolkit) ⭐1.3k | read / search / publish |
| 微信公众号 (发布) | 👥 [`caol64/wenyan-mcp`](https://github.com/caol64/wenyan-mcp) ⭐1.3k | auto-format & publish Markdown |
| 微信公众号 (下载) | 👥 [`qiye45/wechatDownload`](https://github.com/qiye45/wechatDownload) ⭐8.3k | batch article download — tool with MCP/Skill support |
| 微信读书 WeRead | 👥 [`freestylefly/mcp-server-weread`](https://github.com/freestylefly/mcp-server-weread) ⭐560 | books, notes, highlights |
| Bilibili | 👥 [`huccihuang/bilibili-mcp-server`](https://github.com/huccihuang/bilibili-mcp-server) ⭐188 · [`34892002/bilibili-mcp-js`](https://github.com/34892002/bilibili-mcp-js) ⭐177 | search, video info |
| 知乎 Zhihu | 👥 [`iteng007/zhihu-mcp-server`](https://github.com/iteng007/zhihu-mcp-server) (API) · [`Douyh123/zhihu-mcp`](https://github.com/Douyh123/zhihu-mcp) (search/publish) · [`JasonJarvan/Zhihu-Collections-MCP`](https://github.com/JasonJarvan/Zhihu-Collections-MCP) ⭐145 (export) | API access, search, publish, export |
| 微博 Weibo | 👥 [`qinyuanpei/mcp-server-weibo`](https://github.com/qinyuanpei/mcp-server-weibo) ⭐50 | user / content / hot-search |
| 抖音 / B站 / 公众号 / 播客 (采集) | 👥 [`chubbyguan/chubbyskills`](https://github.com/chubbyguan/chubbyskills) ⭐496 | content-ingestion Agent Skills + a knowledge-base MCP (not per-app servers) |

## 🛒 电商 · E-commerce

| App | Server | Notes |
|---|---|---|
| 淘宝 / 闲鱼 | 👥 [`Tsinglung-Tseng/ali-mcp`](https://github.com/Tsinglung-Tseng/ali-mcp) | Taobao + Xianyu automation |
| 京东 JD | 👥 [`mako202605/mcp-jd-super-deals`](https://github.com/mako202605/mcp-jd-super-deals) · [`mako202605/mcp-jd-seckill`](https://github.com/mako202605/mcp-jd-seckill) | deals, seckill |
| 1688 | 👥 [`QuoVadis86/ai-reverse`](https://github.com/QuoVadis86/ai-reverse) ⭐10 | product / image search |

## 🏢 办公协作 · Office & Collaboration

| App | Server | Notes |
|---|---|---|
| 飞书 / Lark | 🏢 [`larksuite/lark-openapi-mcp`](https://github.com/larksuite/lark-openapi-mcp) ⭐748 · 👥 [`ztxtxwd/open-feishu-mcp-server`](https://github.com/ztxtxwd/open-feishu-mcp-server) ⭐85 | docs, sheets, IM, calendar |
| 语雀 Yuque | 🏢 [`yuque/yuque-mcp-server`](https://github.com/yuque/yuque-mcp-server) ⭐188 (server) · [`yuque/yuque-ecosystem`](https://github.com/yuque/yuque-ecosystem) ⭐186 (server+skills+plugin bundle) | knowledge base CRUD |
| 钉钉 DingTalk | 👥 [`hykfft/mcp-dingtalk-doc`](https://github.com/hykfft/mcp-dingtalk-doc) ⭐50 | DingTalk docs MCP |
| 石墨文档 Shimo | 👥 [`kanyun-inc/rush-shimo-cli`](https://github.com/kanyun-inc/rush-shimo-cli) | read Shimo docs — CLI + SDK + MCP |
| 企业微信 WeCom | — no dedicated MCP yet · ops-bot: [`opsre/ZenOps`](https://github.com/opsre/ZenOps) ⭐160 | ZenOps queries ops resources via 钉钉/飞书/企微 bots (not a WeCom API connector) — PR one if you build it |

## 💻 开发工具 · DevTools

| App | Server | Notes |
|---|---|---|
| Gitee | 🏢 [`oschina/mcp-gitee`](https://github.com/oschina/mcp-gitee) ⭐62 | repos, issues, PRs |
| Apifox | 🏢 [official MCP](https://docs.apifox.com/apifox-mcp-server) | API specs into agents |
| 百度 AI Guard | 🏢 [`baidu/mcp-server-baidu-ai-guard`](https://github.com/baidu/mcp-server-baidu-ai-guard) | content moderation |
| HarmonyOS | 👥 [`XixianLiang/HarmonyOS-mcp-server`](https://github.com/XixianLiang/HarmonyOS-mcp-server) | HarmonyOS dev/test |
| LeetCode | 👥 [`jinzcdev/leetcode-mcp-server`](https://github.com/jinzcdev/leetcode-mcp-server) | problems, submissions |

## 📈 金融与数据 · Finance & Data (A股)

| App | Server | Notes |
|---|---|---|
| AKShare | 👥 [`aahl/mcp-aktools`](https://github.com/aahl/mcp-aktools) ⭐382 · [`zwldarren/akshare-one-mcp`](https://github.com/zwldarren/akshare-one-mcp) ⭐196 | stocks, crypto, analysis |
| Tushare | 👥 [`zlinzzzz/finData-mcp-server`](https://github.com/zlinzzzz/finData-mcp-server) ⭐56 · [`hanxuanliang/tsrs-mcp-server`](https://github.com/hanxuanliang/tsrs-mcp-server) ⭐27 | financial data |
| 东方财富 / 同花顺 | 👥 [`noimank/FNewsCrawler`](https://github.com/noimank/FNewsCrawler) ⭐109 · [`27dream/mcp-eastmoney`](https://github.com/27dream/mcp-eastmoney) | quotes, news, fund flow |
| A股 Skill 集合 | 👥 [`shouldnotappearcalm/a-share-skill`](https://github.com/shouldnotappearcalm/a-share-skill) ⭐184 | quant, K-line, indicators — Agent Skills collection (not an MCP server) |

> 💡 **券商 (brokerages):** 广发证券, 国泰君安, 中信 etc. have launched internal AI "Skills" (智能投顾 贝塔牛, 易淘金, GF-Quant…), but these are app-internal agent capabilities, **not public MCP servers** you can connect to. For programmatic A股 market data, use AKShare / Tushare / 东方财富 above. PR a row if/when any brokerage ships a public MCP.

## 🌦️ 天气 · Weather

| App | Server | Notes |
|---|---|---|
| 彩云天气 Caiyun | 👥 [`caiyunapp/mcp-caiyun-weather`](https://github.com/caiyunapp/mcp-caiyun-weather) | minute-level forecast |
| 心知天气 Seniverse | 👥 [`sugarforever/mcp-seniverse-weather`](https://github.com/sugarforever/mcp-seniverse-weather) | city weather |
| 高德 / 百度天气 | (via Amap / Baidu Map tools, see Maps) | city weather |

## 🎵 音乐 · Music

| App | Server | Notes |
|---|---|---|
| 网易云 / QQ音乐 / 酷狗 / 酷我 | 👥 [`ELDment/Meting-Agent`](https://github.com/ELDment/Meting-Agent) ⭐94 | multi-platform music API proxy for AI |
| 网易云音乐 NetEase | 👥 [`Cheiineeey/netease-music-mcp`](https://github.com/Cheiineeey/netease-music-mcp) ⭐41 | play, lyrics sync, playlist mgmt |

## 🏠 智能家居 / IoT · Smart Home

| App | Server | Notes |
|---|---|---|
| 小米 米家 Mijia | 👥 [`handsomejustin/mijia-control`](https://github.com/handsomejustin/mijia-control) ⭐51 | 米家 × MCP × HomeKit smart-home bridge |

## 🤖 大模型与 AI 服务 · LLM & AI Services

| Provider | Server | Notes |
|---|---|---|
| MiniMax | 🏢 [`MiniMax-AI/MiniMax-MCP`](https://github.com/MiniMax-AI/MiniMax-MCP) ⭐1.5k · [JS](https://github.com/MiniMax-AI/MiniMax-MCP-JS) ⭐125 | TTS, voice clone, image & video gen |
| 魔搭 ModelScope | 🏢 [`modelscope/modelscope-mcp-server`](https://github.com/modelscope/modelscope-mcp-server) · 🌐 [MCP 广场 1400+](https://modelscope.cn/brand/view/MCP) | models + biggest CN MCP hub |
| 智谱 Zhipu (GLM) | 👥 [`wnzzer/zhipu-tools-coding-plan`](https://github.com/wnzzer/zhipu-tools-coding-plan) · [`NanguangChou/zhipu_image_mcp`](https://github.com/NanguangChou/zhipu_image_mcp) | web search, image gen |
| 通义千问 Qwen | 👥 [`zk-b612/mcp-qwen-omni`](https://github.com/zk-b612/mcp-qwen-omni) | multimodal (image/audio/voice) |
| DeepSeek / Moonshot Kimi | model providers (OpenAI-compatible) — add via your client's model config | — |

## 🧰 实用工具 · Utilities

| Tool | Server | Notes |
|---|---|---|
| 中国数据核验 | 👥 [`CCCpan/data-verify-mcp`](https://github.com/CCCpan/data-verify-mcp) ⭐167 | ID / 企业 / 车辆 / OCR / risk |
| 企业信息收集 | 👥 [`wgpsec/ENScan_GO`](https://github.com/wgpsec/ENScan_GO) ⭐4.5k | ICP备案 / 小程序 / 公众号 — intel tool with MCP support |
| 腾讯 Web 搜索 | 🏢 [`Tencent/WebSearchMCP`](https://github.com/Tencent/WebSearchMCP) | web search |

---

## 🌐 Hosted unified platforms (closed-source) / 托管统一平台

If you'd rather not self-host, these proprietary platforms act as the "Composio for China" (managed auth, one console):

| Platform | What | Open-source? |
|---|---|---|
| [阿里云百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) | ~184 official + 2900+ third-party MCP, managed OAuth/KMS | ❌ |
| [魔搭 ModelScope MCP 广场](https://modelscope.cn/brand/view/MCP) | 1400+ servers, biggest Chinese MCP community | ❌ |
| [扣子 Coze 插件市场](https://www.coze.cn/store/plugin) | 700+ plugins, bound to Coze agents | ❌ |
| 腾讯元器 / 火山引擎 MCP | cloud MCP marketplaces | ❌ |

---

## 🤝 Contributing / 贡献

Know a Chinese-app MCP server that's missing — especially an **official** one? **PRs welcome.** Add a row in the right category with: app name, repo/docs link, official (🏢) or community (👥), and a one-line note. It does **not** have to be a GitHub repo — official MCPs published on a vendor's dev portal or marketplace count too (use a 🌐 docs link). Keep entries to real, working servers.

发现遗漏的国内服务 MCP Server（尤其是官方的）？欢迎提 PR。不一定非得是 GitHub 仓库 —— 厂商开发者平台 / 市场上的官方 MCP 同样收录（用 🌐 文档链接）。请只收录真实可用的 server。

## License

[CC0-1.0](LICENSE) — public domain. Use freely.

---

<p align="center"><sub>Maintained by <a href="https://openclawlaunch.com">OpenClaw Launch</a> — deploy an AI agent that connects to all of these in one click. · 星标 ⭐ 让更多人发现这个清单。</sub></p>
