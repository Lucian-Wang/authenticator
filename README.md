# 身份验证助手

安全高效的二步验证工具，支持 Google、GitHub、Steam 等多种平台。


## 正式版下载与构建

打开 [Signed Android release](https://github.com/Lucian-Wang/authenticator/actions/workflows/android-release.yml)，选择成功的运行，在 Artifacts 下载 `authenticator-signed-release`，内含正式签名 APK 和 SHA256SUMS.txt。已发布标签的安装包见 [Releases](https://github.com/Lucian-Wang/authenticator/releases)。

`main` 提交和手动运行会生成构建产物；推送 `v*` 标签后发布 Release。手动构建支持 `version_name`、`version_code`，配置说明见 [RELEASE.md](RELEASE.md)。当前流程使用 Lucian 签名并核验 APK 包名、证书指纹和非调试属性。相同包名但签名不同的 APK 不能覆盖安装。

## 功能特点

- 🔐 **扫码快速添加**：扫描标准 TOTP 二维码一键添加
- 🚀 **Google 迁移格式支持**：一键导入 Google Authenticator 导出的所有验证码
- ⏱️ **实时动态生成**：每30秒自动刷新，带倒计时进度条
- 📋 **一键复制验证码**：点击验证码自动复制到剪贴板
- ↕️ **拖动排序**：长按账号行上下拖动，边缘自动滚动，松手自动保存顺序
- 📤 **导出二维码备份**：方便在其他设备上添加
- 🔒 **本地存储安全**：所有数据保存在本地，不上云
- 🎨 **紧凑账号列表**：平台、账号和验证码并排显示，一屏容纳更多账号，点击行即可复制

## 快速开始

1. 在网站开启二步验证（TOTP）
2. 打开身份验证助手，扫描二维码
3. 使用生成的验证码登录

### 从 Google Authenticator 迁移

1. 在 Google Authenticator 中，进入设置 - 导出账号
2. 扫描导出的二维码，一次性导入所有验证码

## 下载

从 [Releases](https://github.com/Lucian-Wang/authenticator/releases) 页面下载最新 APK。

当前源码默认版本名为 `1.0.0`；构建流程可覆盖版本名与版本号，已发布版本以 Releases 记录为准。

## 项目结构

```
app/src/main/java/wang/lucian/authenticator/
├── MainActivity.kt           # 主界面
├── ScanActivity.kt           # 扫码界面
├── ExportActivity.kt         # 导出二维码界面
├── QRCodeGenerator.kt        # 二维码生成工具
├── GoogleMigrationParser.kt  # Google 迁移格式解析
├── TotpGenerator.kt          # TOTP 验证码生成
├── AuthStore.kt              # 数据存储
└── models.kt                 # 数据模型
```

## 技术栈

- **语言**：Kotlin
- **UI**：Jetpack Compose + Material Design 3
- **二维码**：ML Kit Barcode Scanning
- **相机**：CameraX
- **数据存储**：DataStore
- **最低支持**：Android 5.0 (API 21)
- **目标版本**：Android 14 (API 34)

## 隐私安全

- 所有数据存储在本地
- 不上传到任何服务器
- 使用 ML Kit、CameraX、Jetpack 等第三方/Android 组件；依赖清单见 `app/build.gradle.kts`
- 无广告
- 无追踪

当前仓库未包含独立的 `docs/privacy.html` 文件。

## 许可证

MIT License

## 相关链接

- [维护者网站](https://lucian.wang/)
- [问题反馈](https://github.com/Lucian-Wang/authenticator/issues)
- [版本历史](https://github.com/Lucian-Wang/authenticator/releases)

---

© 2026 [Lucian](https://lucian.wang/)


## 应用标识

应用 ID：`wang.lucian.authenticator`。本次包名变更后的 APK 会作为独立应用安装，不能覆盖升级旧包名版本；旧应用的数据和授权不会自动迁移，请先导出需要保留的数据，再安装并重新授权。

## 维护与反馈

维护者：[Lucian](https://lucian.wang/) · 邮箱：im@lucian.wang · [问题反馈](https://github.com/Lucian-Wang/authenticator/issues)
