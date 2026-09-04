# 第三方组件来源与许可说明

本文记录 XHS-FB 0.4.39 便携包中主要第三方运行组件的来源。实际分发包还会携带对应许可证与第三方声明；发布清单和校验文件用于确认下载内容未被替换。

## 专用浏览器

| 项目 | 内容 |
| --- | --- |
| 项目 | `ungoogled-software/ungoogled-chromium-windows` |
| 上游仓库 | <https://github.com/ungoogled-software/ungoogled-chromium-windows> |
| Release | <https://github.com/ungoogled-software/ungoogled-chromium-windows/releases/tag/151.0.7922.71-1.1> |
| 版本 | 151.0.7922.71-1.1，Windows x64 |
| 上游文件 | `ungoogled-chromium_151.0.7922.71-1.1_windows_x64.zip` |
| 上游文件 SHA-256 | `f49303e9b61aab632e399a12c36b72b184158e965b6d6373105f19f2e884fd6e` |
| Chromium 许可证 | <https://chromium.googlesource.com/chromium/src/+/refs/tags/151.0.7922.71/LICENSE> |

XHS-FB 使用这一独立浏览器运行发布自动化，不读取目标电脑日常 Chrome 的资料。此构建与随包自动化组件一起接受运行验证；它不是对 Playwright 官方浏览器文件的逐字节复刻。

Chromium 包含多个第三方项目。便携包内保留该精确浏览器发行物随附的许可证和第三方声明，并另外保存浏览器文件校验清单。不要从解压目录中删除这些许可资料。

## 桌面运行与界面组件

XHS-FB 便携包使用下列第三方项目。精确版本以分发包内的清单为准，许可证原文随包保存。

| 组件 | 上游来源 | 许可证 |
| --- | --- | --- |
| Electron | <https://github.com/electron/electron> | MIT；Electron 同时分发 Chromium 等第三方声明 |
| Node.js | <https://github.com/nodejs/node> | MIT 与随发行物列出的第三方许可证 |
| Playwright | <https://github.com/microsoft/playwright> | Apache-2.0 |
| React | <https://github.com/facebook/react> | MIT |
| React DOM | <https://github.com/facebook/react> | MIT |
| Scheduler | <https://github.com/facebook/react> | MIT |
| Zod | <https://github.com/colinhacks/zod> | MIT |

## 校验与隐私边界

- Git 仓库不保存 EXE、DLL、浏览器文件或发布 ZIP；正式二进制只作为 GitHub Release 附件提供。
- Release 应同时包含 `XHS-FB-0.4.39-Windows-x64.zip`、同名 `.sha256` 和 `release-manifest.json`。
- 发布工作流会重新下载 Release 的真实附件，并核对 ZIP 实际 SHA-256、清单和校验文件。
- 公开包不得包含 Cookie、浏览器 Profile、API Key、访问令牌、任务数据库、日志或用户素材。
