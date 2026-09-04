# XHS-FB 0.4.39

XHS-FB 0.4.39 是面向 Windows 10/11 x64 的跨电脑便携交付版本。

## 便携交付

- 程序、Electron/Node.js 运行组件、发布自动化组件和专用浏览器均包含在 ZIP 中。
- 另一台电脑完整解压后可直接双击 `XHS-FB.exe`，无需安装 Node.js、npm、Electron、Playwright 或系统 Chrome。
- 内置 `ungoogled-chromium-windows` 151.0.7922.71-1.1 x64，来源为该项目的正式 GitHub Release。
- 上游浏览器压缩包 SHA-256：`f49303e9b61aab632e399a12c36b72b184158e965b6d6373105f19f2e884fd6e`。
- 新电脑上的应用数据和专用浏览器资料默认保存在 `%LOCALAPPDATA%\XHS-FB`。

## 隐私与迁移边界

公开便携包不包含原电脑的 Cookie、浏览器 Profile、API Key、访问令牌、任务数据库、草稿、日志、商品图片或个人素材，也不会读取或迁移开发电脑的既有运行数据。

首次使用时需要：

1. 在专用浏览器中登录自己的小红书账号。
2. 按需在设置中填写自己的 AI API Key。
3. 先用一条已人工检查的任务验证当前网页流程。

## 下载校验

发布页同时提供 ZIP、同名 `.sha256` 和 `release-manifest.json`。三处记录的版本、文件名和 SHA-256 必须一致。GitHub Actions 会在 Release 发布后重新下载实际附件并核对这些值。

## 已知提示

当前版本未承诺代码签名，Windows SmartScreen 可能出现来源确认提示。请先核对发布来源和 SHA-256，再决定是否继续运行。
