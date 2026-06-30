# Awesome China MCP 🇨🇳

> The curated index of **Model Context Protocol (MCP) servers for Chinese apps & services** — give your AI agent the ability to actually *use* 高德地图, 12306, 小红书, 飞书, 语雀, 支付宝, A股 data and more.
>
> 收录可连接「中国应用」的 MCP Server —— 让你的 AI Agent 真正能调用高德地图、12306、小红书、飞书、语雀、支付宝、A股行情等国内服务。

<p align="center">
  <a href="https://github.com/zackchewa/awesome-china-mcp/stargazers"><img src="https://img.shields.io/github/stars/zackchewa/awesome-china-mcp?style=flat-square" alt="stars"></a>
  <img src="https://img.shields.io/badge/MCP-Model%20Context%20Protocol-blue?style=flat-square" alt="mcp">
  <img src="https://img.shields.io/badge/lang-中文%20%2F%20EN-green?style=flat-square" alt="lang">
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square" alt="prs">
</p>

---

## Why this exists / 为什么有这个仓库

In the West, [Composio](https://composio.dev), [Nango](https://nango.dev) and friends give an AI agent one place to connect 1000+ apps. **There is no open-source equivalent that covers Chinese apps** — the ecosystem is scattered, with each service shipping (or not shipping) its own standalone MCP server. This list collects them in one place so you don't have to hunt.

国外有 Composio 这样的「一个平台连上千个 app」。**国内没有对应的开源索引** —— 各家服务各自为政，MCP Server 散落各处。这个清单把它们汇总到一处。

> ℹ️ **Hosted alternative:** if you want a managed, click-to-connect experience (OAuth handled for you) rather than wiring servers yourself, the closest thing is Alibaba's [百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) — but it's closed-source. This list is the open, self-host route.

---

## How to use / 如何使用

Most entries are standard MCP servers. Point any MCP client at them:

- **AI agents** — e.g. deploy a bot on [OpenClaw Launch](https://openclawlaunch.com) and add these as tools, or use [OpenClaw](https://github.com/openclaw/openclaw) / Hermes directly
- **IDEs / assistants** — Claude Desktop, Cursor, Cline, Continue, VS Code MCP
- **Frameworks** — anything that speaks MCP (LangChain, OpenAI Agents SDK, etc.)

```jsonc
// Example: Claude Desktop / Cursor mcp config
{
  "mcpServers": {
    "amap": {
      "command": "npx",
      "args": ["-y", "@amap/amap-maps-mcp-server"],
      "env": { "AMAP_MAPS_API_KEY": "<your-key>" }
    }
  }
}
```

> ⚠️ **BYO credentials.** Most Chinese-platform APIs (微信 / 支付宝 / 钉钉 / 电商) require your own registered app credentials and, for the big ones, enterprise (营业执照) verification. These servers connect the API — you supply the keys.

### Legend
`🏢` official / first-party · `👥` community · `⭐` GitHub stars (approx, changes over time) · `🌐` hosted service (docs link)

---

## 🗺️ 地图与出行 · Maps & Travel

| App | Server | Notes |
|---|---|---|
| 高德地图 Amap | 🏢 [official MCP](https://lbs.amap.com/api/mcp-server/gettingstarted) · 👥 [`sugarforever/amap-mcp-server`](https://github.com/sugarforever/amap-mcp-server) ⭐111 | geocode, routing, POI, weather; free tier |
| 腾讯地图 Tencent Maps | 🏢 [official MCP](https://lbs.qq.com/service/MCPServer/MCPServerGuide/overview) | location, routing, POI |
| 百度地图 Baidu Maps | 🏢 [official MCP](https://lbsyun.baidu.com/faq/api?title=mcpserver/base) | location, routing |
| 12306 火车票 | 👥 [`Joooook/12306-mcp`](https://github.com/Joooook/12306-mcp) ⭐948 · [`drfccv/mcp-server-12306`](https://github.com/drfccv/mcp-server-12306) ⭐348 | train ticket search |
| 携程 Ctrip | 👥 [`biaowuqiong/ctrip-hotel-skill`](https://github.com/biaowuqiong/ctrip-hotel-skill) | hotel price (Playwright) |
| 美团 Meituan | 👥 [`LewisChen1219/Meituan-Mcp-Server-WIP`](https://github.com/LewisChen1219/Meituan-Mcp-Server-WIP) | food ordering (WIP) |

## 📱 内容与社交 · Content & Social

| App | Server | Notes |
|---|---|---|
| 小红书 Xiaohongshu | 👥 [`xpzouying/xiaohongshu-mcp`](https://github.com/xpzouying/xiaohongshu-mcp) ⭐14.4k · [`iFurySt/RedNote-MCP`](https://github.com/iFurySt/RedNote-MCP) ⭐1k · [`aki66938/xhs-toolkit`](https://github.com/aki66938/xhs-toolkit) ⭐1.3k | read/search/publish |
| 微信公众号 (发布) | 👥 [`caol64/wenyan-mcp`](https://github.com/caol64/wenyan-mcp) ⭐1.3k | auto-format & publish Markdown |
| 微信公众号 (下载) | 👥 [`qiye45/wechatDownload`](https://github.com/qiye45/wechatDownload) ⭐8.3k | batch article download |
| 微信读书 WeRead | 👥 [`freestylefly/mcp-server-weread`](https://github.com/freestylefly/mcp-server-weread) ⭐560 | books, notes, highlights |
| Bilibili | 👥 [`huccihuang/bilibili-mcp-server`](https://github.com/huccihuang/bilibili-mcp-server) ⭐188 · [`34892002/bilibili-mcp-js`](https://github.com/34892002/bilibili-mcp-js) ⭐177 | search, video info |
| 知乎 Zhihu | 👥 [`JasonJarvan/Zhihu-Collections-MCP`](https://github.com/JasonJarvan/Zhihu-Collections-MCP) ⭐145 · [`iteng007/zhihu-mcp-server`](https://github.com/iteng007/zhihu-mcp-server) | export, search, publish |
| 微博 Weibo | 👥 [`qinyuanpei/mcp-server-weibo`](https://github.com/qinyuanpei/mcp-server-weibo) ⭐50 | user/content/hot-search |
| 抖音 / B站 / 公众号 / 播客 (采集) | 👥 [`chubbyguan/chubbyskills`](https://github.com/chubbyguan/chubbyskills) ⭐496 | content → knowledge base |

## 🛒 电商 · E-commerce

| App | Server | Notes |
|---|---|---|
| 淘宝 / 闲鱼 | 👥 [`Tsinglung-Tseng/ali-mcp`](https://github.com/Tsinglung-Tseng/ali-mcp) | Taobao + Xianyu automation |
| 京东 JD | 👥 [`mako202605/mcp-jd-super-deals`](https://github.com/mako202605/mcp-jd-super-deals) · [`mako202605/mcp-jd-seckill`](https://github.com/mako202605/mcp-jd-seckill) | deals, seckill |
| 1688 | 👥 [`QuoVadis86/ai-reverse`](https://github.com/QuoVadis86/ai-reverse) ⭐10 | product search, image search |

## 🏢 办公协作 · Office & Collaboration

| App | Server | Notes |
|---|---|---|
| 飞书 / Lark | 🏢 [`larksuite/lark-openapi-mcp`](https://github.com/larksuite/lark-openapi-mcp) ⭐748 · 👥 [`ztxtxwd/open-feishu-mcp-server`](https://github.com/ztxtxwd/open-feishu-mcp-server) ⭐85 | docs, sheets, IM, calendar |
| 语雀 Yuque | 🏢 [`yuque/yuque-ecosystem`](https://github.com/yuque/yuque-ecosystem) ⭐186 · 👥 [`suonian/yuque-mcp-server`](https://github.com/suonian/yuque-mcp-server) | knowledge base CRUD |
| 钉钉 DingTalk | 👥 [`hykfft/mcp-dingtalk-doc`](https://github.com/hykfft/mcp-dingtalk-doc) ⭐50 · [`opsre/ZenOps`](https://github.com/opsre/ZenOps) ⭐160 (钉钉+飞书+企微) | docs, ops bot |
| 企业微信 WeCom | 👥 [`opsre/ZenOps`](https://github.com/opsre/ZenOps) ⭐160 | natural-language ops queries |

## ☁️ 云服务与开发 · Cloud & DevTools

| App | Server | Notes |
|---|---|---|
| 阿里云 Alibaba Cloud | 🏢 [`aliyun/alibaba-cloud-ops-mcp-server`](https://github.com/aliyun/alibaba-cloud-ops-mcp-server) · [`aliyun/alibabacloud-api-mcp-server`](https://github.com/aliyun/alibabacloud-api-mcp-server) ⭐23 | ECS, ops, full API |
| 腾讯云 COS | 🏢 [`Tencent/cos-mcp`](https://github.com/Tencent/cos-mcp) ⭐37 | object storage + 数据万象 |
| 七牛云 Qiniu | 🏢 [`qiniu/qiniu-mcp-server`](https://github.com/qiniu/qiniu-mcp-server) ⭐37 | storage, upload, CDN |
| Gitee | 🏢 [`oschina/mcp-gitee`](https://github.com/oschina/mcp-gitee) ⭐62 | repos, issues, PRs |
| Apifox | 🏢 [official MCP](https://docs.apifox.com/apifox-mcp-server) | API specs into agents |
| HarmonyOS | 👥 [`XixianLiang/HarmonyOS-mcp-server`](https://github.com/XixianLiang/HarmonyOS-mcp-server) | HarmonyOS dev/test |

## 📈 金融与数据 · Finance & Data (A股)

| App | Server | Notes |
|---|---|---|
| AKShare | 👥 [`aahl/mcp-aktools`](https://github.com/aahl/mcp-aktools) ⭐382 · [`zwldarren/akshare-one-mcp`](https://github.com/zwldarren/akshare-one-mcp) ⭐196 | stocks, crypto, analysis |
| Tushare | 👥 [`zlinzzzz/finData-mcp-server`](https://github.com/zlinzzzz/finData-mcp-server) ⭐56 · [`hanxuanliang/tsrs-mcp-server`](https://github.com/hanxuanliang/tsrs-mcp-server) ⭐27 | financial data |
| 东方财富 / 同花顺 | 👥 [`noimank/FNewsCrawler`](https://github.com/noimank/FNewsCrawler) ⭐109 · [`27dream/mcp-eastmoney`](https://github.com/27dream/mcp-eastmoney) | quotes, news, fund flow |
| A股 Skill 集合 | 👥 [`shouldnotappearcalm/a-share-skill`](https://github.com/shouldnotappearcalm/a-share-skill) ⭐184 | quant, K-line, indicators |

## 🌦️ 天气 · Weather

| App | Server | Notes |
|---|---|---|
| 彩云天气 Caiyun | 👥 [`caiyunapp/mcp-caiyun-weather`](https://github.com/caiyunapp/mcp-caiyun-weather) | minute-level forecast |
| 高德天气 | (via Amap `maps_weather` tool, see Maps) | city weather |

## 🤖 大模型 · Chinese LLM Providers

| Provider | Server / Note |
|---|---|
| 通义千问 Qwen | use as model; multimodal MCP e.g. [`zk-b612/mcp-qwen-omni`](https://github.com/zk-b612/mcp-qwen-omni) |
| 智谱 Zhipu (GLM) | [`wnzzer/zhipu-tools-coding-plan`](https://github.com/wnzzer/zhipu-tools-coding-plan) · [`NanguangChou/zhipu_image_mcp`](https://github.com/NanguangChou/zhipu_image_mcp) |
| DeepSeek / Moonshot Kimi | primarily model providers (OpenAI-compatible); add via your client's model config |

## 🧰 实用工具 · Utilities

| Tool | Server | Notes |
|---|---|---|
| 中国数据核验 | 👥 [`CCCpan/data-verify-mcp`](https://github.com/CCCpan/data-verify-mcp) ⭐167 | ID / 企业 / 车辆 / OCR / risk |
| 企业信息收集 | 👥 [`wgpsec/ENScan_GO`](https://github.com/wgpsec/ENScan_GO) ⭐4.5k | ICP备案 / 小程序 / 公众号 |
| LeetCode | 👥 [`jinzcdev/leetcode-mcp-server`](https://github.com/jinzcdev/leetcode-mcp-server) | problems, submissions |

---

## 🌐 Hosted unified platforms (closed-source) / 托管统一平台

If you'd rather not self-host, these proprietary platforms act as the "Composio for China" (managed auth, one console):

| Platform | What | Open-source? |
|---|---|---|
| [阿里云百炼 MCP 市场](https://bailian.console.aliyun.com/?tab=mcp) | ~184 official + 2900+ third-party MCP, managed OAuth/KMS | ❌ |
| [扣子 Coze 插件市场](https://www.coze.cn/store/plugin) | 700+ plugins, bound to Coze agents | ❌ |
| 腾讯元器 / 火山引擎 MCP | cloud MCP marketplaces | ❌ |

---

## 🤝 Contributing / 贡献

Know a Chinese-app MCP server that's missing? **PRs welcome.** Add a row in the right category with: app name, repo/docs link, official (🏢) or community (👥), and a one-line note. Keep entries to real, working servers.

发现遗漏的国内服务 MCP Server？欢迎提 PR：在对应分类加一行（应用名、仓库/文档链接、官方/社区、一句话说明）。请只收录真实可用的 server。

## License

[CC0-1.0](LICENSE) — public domain. Use freely.

---

<p align="center"><sub>Maintained by <a href="https://openclawlaunch.com">OpenClaw Launch</a> — deploy an AI agent that connects to all of these in one click. · 星标 ⭐ 让更多人发现这个清单。</sub></p>
