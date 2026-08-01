<div align="center">
  <img src="assets/icon.png" width="168" alt="RubaTone AI Local 图标">

  # RubaTone AI Local

  **在自己的电脑完成 AI 翻唱，并通过 Android 手机在局域网遥控。**

  [繁體中文](README.md) · [English](README.en.md) · [简体中文](README.zh-CN.md)

  [![Release](https://img.shields.io/badge/release-v1.0.1-7c3aed?style=flat-square)](https://github.com/Hiruynk/RubaTone-AI-Local/releases/tag/v1.0.1)
  ![Windows](https://img.shields.io/badge/Windows-11%20x64-0078D4?style=flat-square&logo=windows11&logoColor=white)
  ![GPU](https://img.shields.io/badge/NVIDIA-RTX%2040%20%2F%2050-76B900?style=flat-square&logo=nvidia&logoColor=white)
  ![Android](https://img.shields.io/badge/Android-10%2B-3DDC84?style=flat-square&logo=android&logoColor=white)
  ![Mode](https://img.shields.io/badge/runtime-local--first-2563EB?style=flat-square)

  [下载 Windows Launcher](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-Launcher-Setup.exe)
  ·
  [下载 Android APK](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-1.0.1-arm64-release.apk)
  ·
  [全部发布文件](https://huggingface.co/hiruynk/RubaTone-AI-Local/tree/main)
</div>

---

## 概览

RubaTone AI Local 是 RubaTone AI 的本地 Windows 版本。歌曲、模型、任务和输出都由你的电脑保存及处理；完成首次安装后，主要功能不需要 Internet。Android App 是完整的遥控前端，与电脑配对后可在同一私人网络上操作工作流程。

这个 GitHub repository 是**不含源代码的官方发布入口**。大型安装文件、APK、runtime 分卷、签名 manifest 和校验文件存放于 Hugging Face。

## 核心特色

| | 功能 |
|---|---|
| 🎙️ | 主唱、和声、伴奏和混响分离，支持男女合唱分析 |
| 🎛️ | RVC 模型导入、验证、推理、训练和继续训练 |
| 🎚️ | 平衡混音、移调、专业混音和批量歌曲处理 |
| ✨ | AudioSR 高频补全和 Resemble Enhance 人声自然化 |
| 📊 | 音域分析、异常检测和推荐训练集 |
| 🧭 | 任务进度、暂停、继续、取消、失败重试和后台运行 |
| 📱 | Android 局域网遥控、实时事件同步和输出下载 |
| 🔒 | 本地数据、设备配对、签名 manifest 和逐文件完整性验证 |

## 工作方式

```text
Android App
    │  同一私人网络 · 四位码配对 · 加密设备连接
    ▼
Windows 桌面程序
    │
    ├── Core：数据库、文件、任务队列和同步
    ├── Separation：UVR / Roformer / Demucs
    ├── RVC：推理、RMVPE、分析和训练
    ├── AudioSR
    ├── Resemble Enhance
    └── FFmpeg / FFprobe
```

各 AI runtime 使用独立环境，避免 Python、Torch、CUDA 和 NumPy 依赖互相冲突。GPU 任务由中央协调器管理，以降低同时抢占显存造成失败的风险。

## 系统要求

### Windows

| 项目 | 首发支持 |
|---|---|
| 操作系统 | Windows 11 x64 |
| 显卡 | NVIDIA GeForce RTX 40 / 50 系列 |
| 显存 | 至少 12 GB VRAM |
| 网络 | 首次安装和检查更新需要 Internet；安装完成后主程序可离线使用 |
| 已验证硬件 | RTX 5070 Ti 16 GB，NVIDIA 驱动 596.36 |

其他 RTX 40 / 50 型号属于正式发布范围，但尚未逐一完成实体硬件验证。RTX 10 / 20 / 30 系列目前不在首发支持范围。

### Android

| 项目 | 要求 |
|---|---|
| 系统 | Android 10 或以上 |
| 架构 | arm64 |
| 使用条件 | 必须连接同一私人网络上的 RubaTone AI Local 电脑 |
| 断开状态 | 未连接电脑时只能打开首页 |

APK 已发布，但目前尚未完成 Android 实体手机矩阵验证。

## 快速开始

### 1. 安装 Windows 版本

1. 下载并运行 [RubaTone AI Local Launcher 安装器](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-Launcher-Setup.exe)。
2. 直接开始安装，或按需自定义位置；未选择时 Launcher 会使用安全的默认位置，并自动检测 GPU、推荐可用版本。
3. 下载完整 runtime。Launcher 会验证 manifest、分卷和重建后的每个文件。
4. 验证完成后启动 RubaTone AI Local。

Launcher 支持暂停、续传、修复、移动、可选更新和更新失败回滚。已有完整安装时，即使没有 Internet 也可直接启动当前版本。

### 2. 配对 Android

1. 安装 [Android arm64 APK](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-1.0.1-arm64-release.apk)。
2. 确保手机和电脑连接同一个私人网络。
3. 在电脑显示四位配对码。
4. 在手机选择电脑并输入配对码。
5. 在电脑确认手机名称和设备指纹。

配对成功后，手机使用可撤销的设备密钥自动重连。电脑关闭主窗口时可选择继续在后台运行，让手机仍能操作。

## 数据和隐私

- 新安装始终从空白工作区开始。
- 不会导入云端账户的歌曲、模型、训练数据、输出、记录、偏好或数据库。
- 歌曲、模型、任务和输出永久保存在电脑。
- Android 不保存完整歌曲库或模型副本；只有用户明确下载的输出会进入手机 Downloads。
- 局域网服务只用于 Windows 私人网络，不提供公共 WAN 访问。
- Local 版没有登录、账户切换或账户限额。

## 与云端版本的区别

| 项目 | Local | 云端 |
|---|:---:|:---:|
| 本地 AI 处理 | ✅ | — |
| Windows 离线使用 | ✅ | — |
| Android 局域网遥控 | ✅ | — |
| 账户和云端资产 | — | ✅ |
| “转换 MIDI”/ MuScriptor | — | ✅ |

云端正式版仍可在 [rubatone-ai.hiruynk.com](https://rubatone-ai.hiruynk.com) 使用。

## 更新和完整性

- Launcher 每次打开时可检查更新；所有更新都可以跳过。
- manifest 使用发布密钥签名，Launcher 只接受内置公钥验证通过的内容。
- runtime 使用内容分块和 SHA-256 验证，只下载缺少或已变更的数据。
- 新版本先在 staging 目录完整重建和验证，成功后才切换。
- 更新失败时保留并恢复上一个可启动版本。

你也可以下载 [`SHA256SUMS.json`](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/SHA256SUMS.json) 手动核对发布文件。

## 发布状态

| 组件 | 版本 | 状态 |
|---|---:|---|
| Windows Launcher | 1.0.1 | 已发布 |
| RTX 40 / 50 app / runtime | 1.0.1 | 已发布；RTX 5070 Ti 已验证 |
| Android arm64 APK | 1.0.1 | 已发布；等待实体手机矩阵验证 |

查看 [GitHub Release](https://github.com/Hiruynk/RubaTone-AI-Local/releases/tag/v1.0.1) 或 [Hugging Face 文件列表](https://huggingface.co/hiruynk/RubaTone-AI-Local/tree/main)。

## 常见问题

<details>
<summary><strong>安装后仍需要 Internet 吗？</strong></summary>

不需要。首次下载完整 GPU runtime 后，Windows 主程序可完全离线使用。只有主动检查或下载更新时需要 Internet。
</details>

<details>
<summary><strong>可以直接在 Android 手机运行 AI 模型吗？</strong></summary>

不可以。Android App 是远程操作界面，AI 推理和数据存储都在已配对的 Windows 电脑完成。
</details>

<details>
<summary><strong>关闭 Windows 窗口后，手机还能操作吗？</strong></summary>

可以。关闭窗口时选择“关闭窗口并在后台运行”，核心服务、当前任务和手机连接会继续运行。
</details>

<details>
<summary><strong>会自动迁移我原有的云端歌曲或模型吗？</strong></summary>

不会。Local 和云端资产完全分开，新安装不会扫描或导入已有账户数据。
</details>

## 使用范围和第三方组件

当前构建供开发者和朋友作私人、非商业评估。这个 repository 不提供应用程序源代码，也不代表所有内置第三方模型均采用同一种许可证。第三方 notices、许可证文本和必要信息随安装包提供。

---

<div align="center">
  <strong>RubaTone AI Local</strong><br>
  本地处理 · 局域网遥控 · 可选更新
</div>
