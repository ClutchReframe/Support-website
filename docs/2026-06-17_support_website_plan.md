# ClutchReframe Support URL MVP 方案

日期：2026-06-17

## 1. 结论

在 `/mnt/c/Dev/Support-website` 新建一个独立纯静态 support site，用于 Overwolf Store Listing 的 Support link：

```text
https://support.clutchreframe.com/
```

这个网站是 **Support URL MVP**，不是完整官网、帮助中心或客服系统。目标是给 Overwolf 和用户一个稳定、公开、Dota 2-only 的技术支持入口。

不要复用 `https://clips.clutchreframe.com/`。该站点已经用于 Riot / LoL 相关审核，当前 Overwolf OPK 提交目标是 Dota 2-only，两个口径必须隔离。

## 2. 目标

Support URL MVP 只需要满足：

- 可公网访问，不需要登录。
- 可填入 Overwolf Developer Console 的 Support link。
- 页面标题明确为 `ClutchReframe Clips Support`。
- 页面副标题明确为 `Support for the Dota 2 Overwolf app`。
- 内容只承诺 Dota 2 support，不出现 LoL / Riot support。
- 提供联系邮箱：`clutchreframe@gmail.com`。
- 提供 Dota 2 setup、no clips / empty Library、recorder conflict 的最小排障说明。
- 提供 Privacy Policy / Terms 链接。

## 3. 非目标

本阶段不做：

- 不做完整帮助中心。
- 不做营销型 landing page。
- 不接入账号系统或 ticket 系统。
- 不做搜索、复杂 FAQ、博客或知识库。
- 不加载外部字体、外部 CSS、外部 JS、analytics 或 tracking。
- 不放 `riot.txt`。
- 不写 LoL / Riot support。
- 不承诺 Premium、subscription、remove ads、cloud sync、自动上传、自动发布或 AI 剪辑。
- 不引入 React / Next.js / Vite 等构建框架。

## 4. 文件结构

```text
/mnt/c/Dev/Support-website/
  index.html
  privacy.html
  terms.html
  CNAME
  .nojekyll
  README.md
  docs/
    2026-06-17_support_website_plan.md
```

说明：

- `index.html`：极简 support 首页。
- `privacy.html`：与当前 ClutchReframe Clips Dota 2-only app 事实一致的隐私页。
- `terms.html`：极简 terms / EULA 入口。
- `CNAME`：内容为 `support.clutchreframe.com`。
- `.nojekyll`：保证 GitHub Pages 原样发布静态文件。
- `README.md`：记录本地预览、部署和验证命令。

## 5. 首页内容

`index.html` 只保留以下区块。

### Header

- `ClutchReframe Clips Support`
- `Support for the Dota 2 Overwolf app`
- `clutchreframe@gmail.com`

### Dota 2 Setup

保留最小说明：

```text
-gamestateintegration
```

文案要点：

- 在 Steam launch options 添加该参数。
- 添加后重启 Dota 2。
- 该设置帮助 app 识别 Dota 2 match state、kills、deaths 和 assists。

### No Clips / Empty Library

保留最小排障步骤：

- 启动 Dota 2。
- 确认已经添加 `-gamestateintegration` 并重启 Dota 2。
- 触发 kill / death / assist 高光。
- 结束 match 或 demo session 后回到 Library 查看 clips。
- 如果仍为空，联系支持。

### Recorder Conflict

使用中性文案，不点名具体第三方 app：

- 其他 Overwolf 录制 app 可能会占用 recorder，导致 ClutchReframe Clips 无法录制新 clips。
- 关闭或禁用其他 Overwolf 录制 app。
- 从系统托盘完全退出 Overwolf。
- 重新打开 Overwolf / ClutchReframe Clips。
- 重启 Dota 2。

不要公开写成 “Outplayed 导致问题”。如需举例，只使用中性表达：`other Overwolf recording apps, such as gameplay recorders`。

### Contact Support

联系支持时，请用户提供：

- app version
- Overwolf version
- screenshot
- short description of what happened
- steps to reproduce

暂不写具体 Diagnostics Export 步骤。等 app 内 Diagnostics Export MVP 上线后，再更新本区块。

### Footer

- `Privacy Policy`
- `Terms`
- `Contact`
- 独立第三方 companion app 免责声明。

## 6. 不放进首页的内容

首页不放：

- 复杂 FAQ。
- Diagnostics Export 详细教程。
- Outplayed 点名。
- LoL / Riot 内容。
- Premium / subscription / remove ads。
- cloud sync、账号、自动上传、AI 剪辑。
- 营销 hero、视频、下载按钮、未上线功能路线图。
- analytics / tracking / third-party embeds。

## 7. Metadata 口径

页面 metadata 必须是 Dota 2 support 口径，不要复用 LoL 官网 metadata。

建议：

```text
title: ClutchReframe Clips Support
description: Support for ClutchReframe Clips, a Dota 2 Overwolf app for capturing highlights and creating vertical clips.
canonical: https://support.clutchreframe.com/
og:url: https://support.clutchreframe.com/
og:site_name: ClutchReframe Support
```

避免出现：

- League of Legends
- Riot
- LoL Highlight Auto-Clipper
- Riot approval / Riot verification

## 8. Privacy / Terms 口径

`privacy.html` 和 `terms.html` 必须按当前 app 事实写，不要复制 LoL 官网页面。

Privacy 至少覆盖：

- app 处理 gameplay video 和 local metadata 主要在用户本机完成。
- app 不会自动上传 gameplay videos 到 developer servers。
- app 使用 Overwolf platform capabilities。
- 当前 Overwolf app 使用 Overwolf Ads SDK。
- 当前包含 optional uninstall survey。
- 用户联系支持时，只有用户主动发送的截图、描述、诊断材料会被开发者接收。

Terms 至少覆盖：

- ClutchReframe Clips 是独立 companion app。
- 当前 support site 和 app 不隶属于或不受 game publisher 背书。
- 用户需遵守游戏和平台条款。
- support 内容不承诺服务永久可用或覆盖所有故障。

## 9. 视觉方案

可以参考 `/mnt/c/Dev/Clips-website` 的基本品牌风格，但不要复制 LoL 文案、metadata 或外部资源加载。

要求：

- 深色背景。
- 使用 ClutchReframe 现有 cyan / purple 品牌色。
- 使用 system font。
- 不加载 Google Fonts 或其他外部字体。
- 页面偏 support 文档，不做大型 landing hero。
- 移动端 375px 宽度下文字和按钮不溢出。

## 10. 部署方案

建议使用 GitHub Pages 独立仓库：

```text
ClutchReframe/support-website
```

`CNAME` 内容：

```text
support.clutchreframe.com
```

Cloudflare DNS：

| 字段 | 内容 |
| --- | --- |
| Type | `CNAME` |
| Name | `support` |
| Target | `clutchreframe.github.io` |
| Proxy status | `DNS only` |
| TTL | `Auto` |

GitHub Pages：

1. Repository Settings -> Pages。
2. Source 选择 main branch / root。
3. Custom domain 填 `support.clutchreframe.com`。
4. DNS 检查通过后启用 `Enforce HTTPS`。

## 11. 本地预览与验证

本地预览：

```bash
cd /mnt/c/Dev/Support-website
python -m http.server 8080
```

浏览器访问：

```text
http://localhost:8080/
http://localhost:8080/privacy.html
http://localhost:8080/terms.html
```

上线后验证：

```bash
curl -I https://support.clutchreframe.com/
curl -I https://support.clutchreframe.com/privacy.html
curl -I https://support.clutchreframe.com/terms.html
```

预期：

- 三个 URL 返回 `200 OK`。
- HTTPS 正常。
- 不跳转到 `clips.clutchreframe.com`。
- 页面中不出现 LoL / Riot support 承诺。

## 12. 验收清单

- [ ] `CNAME` 为 `support.clutchreframe.com`。
- [ ] 首页标题为 `ClutchReframe Clips Support`。
- [ ] 首页明确写 `Support for the Dota 2 Overwolf app`。
- [ ] 页面提供 `clutchreframe@gmail.com`。
- [ ] 页面说明 `-gamestateintegration` setup。
- [ ] 页面说明 no clips / empty Library 基础排障。
- [ ] 页面用中性语言说明其他 Overwolf 录制 app / recorder conflict 恢复步骤。
- [ ] 页面说明联系支持时需要提供 app version、Overwolf version、截图和复现步骤。
- [ ] `privacy.html` 可访问。
- [ ] `terms.html` 可访问。
- [ ] 不包含 `riot.txt`。
- [ ] 不出现 LoL / Riot support 承诺。
- [ ] 不出现订阅、Premium、remove ads、cloud sync 等未上线承诺。
- [ ] 不加载外部字体、外部 JS、analytics 或 tracking。
- [ ] 移动端 375px 宽度下文本和按钮不溢出。
- [ ] 桌面端首屏能清楚看到 support 入口和 contact。

## 13. 后续更新点

当 ClutchReframe Clips app 内 Diagnostics Export MVP 上线后，再更新 support page 的 Contact Support 区块：

- 增加 `Copy Diagnostics Summary` 步骤。
- 增加 `Export Diagnostics File` 步骤。
- 说明用户如何把诊断 JSON 发给支持邮箱。

当 Overwolf QA 通过并进入 Store Listing 阶段后：

- 将 `https://support.clutchreframe.com/` 填入 Developer Console 的 Support link。
- 在 Store Listing 截图和描述中保持 Dota 2-only 口径。

