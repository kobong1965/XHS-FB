# XHS-FB

XHS-FB 是面向 Windows 10/11 x64 的小红书图文发布桌面工具。本仓库只用于公开分发经过校验的 Windows 成品，不公开应用源码，也不包含开发电脑上的账号、任务或素材数据。

## 推荐下载：安装版

日常使用建议安装 `XHS-Publisher-0.4.43-x64.exe`。安装版会注册当前用户的安装位置，后续可以在软件内检查、下载并原位安装更新；任务、账号、素材、AI 设置和专用浏览器 Profile 保存在独立数据目录，不随程序更新被替换。

1. 打开本仓库右侧的 **Releases**，进入最新版 `XHS-FB 0.4.43`。
2. 下载 `XHS-Publisher-0.4.43-x64.exe`、同名 `.sha256` 和 `installer-update-manifest.json`。
3. 在 PowerShell 中运行 `Get-FileHash .\XHS-Publisher-0.4.43-x64.exe -Algorithm SHA256`，确认结果与校验文件及安装清单一致。
4. 退出正在运行的旧版软件，再运行安装程序。已有安装请覆盖到原安装位置，不要先卸载。
5. 从原来的桌面快捷方式重新打开软件。

安装版已经包含 Electron/Node.js 桌面运行组件、Playwright 发布自动化组件和专用开源浏览器，不需要另装 Node.js、npm、Electron、Playwright 或系统 Chrome。

## 便携版

不希望安装时，可以下载 `XHS-FB-0.4.43-Windows-x64.zip`、同名 `.sha256` 和 `release-manifest.json`。核对 SHA-256 后，将 ZIP 完整解压到一个可写目录，再双击其中的 `XHS-FB.exe`。不要直接在压缩包预览窗口中运行，也不要只复制单个 EXE；程序、自动化组件和专用浏览器必须保留在同一目录结构中。

## 首次启动仍需完成

- 在软件打开的专用浏览器中登录自己的小红书账号。
- 如需 AI 文案或图片功能，在设置中填写自己拥有的 API Key。
- 正式批量发布前，先用一条已人工检查的任务验证当前账号和小红书网页状态。

登录资料和本机设置会在新电脑上重新建立。公开安装包和便携包不会替你迁移旧电脑的账号会话或私密配置。

## 软件更新

`0.4.43` 是首个强制校验 Ed25519 签名更新清单的正式版本：

- 检查更新时，程序会先验证与安装包类型匹配的签名域和内置公钥，再接受版本、文件名、大小与 SHA-256。
- 下载可以在后台进行；发布任务或图片生成任务仍在运行时，程序不会强制退出安装。
- 用户确认后，外置更新助手会原位切换程序并重新打开新版。
- 新版首屏健康检查失败时，更新助手会恢复旧版并重新打开。
- 安装版与便携版分别使用自己的更新清单，两个签名域不能互相替代。

`0.4.41` 及更早版本不具备这套签名协议，无法可信地自动引导到新通道。请先手动下载 `XHS-Publisher-0.4.43-x64.exe`，退出软件后覆盖原位置安装一次；从 `0.4.43` 起，后续稳定版即可使用“设置 > 软件更新”完成签名更新。

Ed25519 在这里保护的是更新清单真实性，防止伪造清单把程序引向未授权文件。它**不等于** Windows Authenticode 可执行文件代码签名，也不会自动消除 SmartScreen 的来源提示。

## 正式 Release 文件

从 `0.4.43` 起，每个正式版本只允许发布以下六个文件：

- `XHS-FB-<版本>-Windows-x64.zip`
- `XHS-FB-<版本>-Windows-x64.zip.sha256`
- `release-manifest.json`
- `XHS-Publisher-<版本>-x64.exe`
- `XHS-Publisher-<版本>-x64.exe.sha256`
- `installer-update-manifest.json`

仓库根目录的 `release-manifest.json` 必须与同版本 Release 中的便携清单逐字节一致。两个 JSON 清单都包含独立的 Ed25519 签名；SHA-256 文件仍用于核对实际大文件内容。

## 包内运行组件

- XHS-FB 0.4.43 Windows x64 桌面程序
- Electron 与 Node.js 桌面运行组件
- Playwright 发布自动化组件
- `ungoogled-chromium-windows` 151.0.7922.71-1.1 x64 专用浏览器
- 第三方许可证、来源和校验资料

内置浏览器来自 `ungoogled-software/ungoogled-chromium-windows` 项目的正式 GitHub Release，而不是开发电脑上的 Chrome。使用的上游压缩包为 `ungoogled-chromium_151.0.7922.71-1.1_windows_x64.zip`，SHA-256 为 `f49303e9b61aab632e399a12c36b72b184158e965b6d6373105f19f2e884fd6e`。

该浏览器与 XHS-FB 的自动化流程一起完成便携包验证。这里的“兼容”表示实际打包组合已经过检查，不表示它与 Playwright 自带的浏览器文件逐字节相同。完整来源见 [THIRD_PARTY_SOURCES.md](THIRD_PARTY_SOURCES.md)。

专用浏览器使用 XHS-FB 自己的资料目录，不读取日常 Chrome 的 Cookie 或 User Data。另一台电脑上的账号资料、任务和设置默认保存在该 Windows 用户的 `%LOCALAPPDATA%\XHS-FB` 中。

## 隐私边界

公开仓库和公开下载包不包含开发电脑上的：

- 小红书 Cookie、登录 Profile、密码或账号会话
- AI API Key、访问令牌、更新私钥或其他凭证
- 商品图片、生成图片、个人素材或媒体文件
- 任务数据库、草稿、发布记录或运行日志

首次换机使用必须由本人登录账号并配置所需服务。不要把 `%LOCALAPPDATA%\XHS-FB`、任何浏览器 Profile 或更新签名私钥重新打包后公开上传。

## Windows SmartScreen

当前版本未承诺 Authenticode 代码签名，Windows SmartScreen 仍可能显示“Windows 已保护你的电脑”。遇到提示时，请先核对发布仓库、版本号、清单签名状态和 SHA-256；确认下载来源无误后，再选择“更多信息”继续运行。若校验值不一致，请删除文件并停止运行。

## 平台说明

小红书商家网页可能改版。若软件显示“需人工核验”，请先到笔记管理页确认远端状态，避免重复提交。首次在新电脑使用或更新版本后，建议先执行一条测试任务。

## 授权说明

本仓库公开可见是为了分发成品，不代表授予 XHS-FB 源代码或程序的开源许可。包内第三方组件继续遵循各自的许可证与使用条款；第三方项目的公开许可证不改变 XHS-FB 本体的授权状态。
