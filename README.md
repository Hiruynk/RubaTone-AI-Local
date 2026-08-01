<div align="center">
  <img src="assets/icon.png" width="168" alt="RubaTone AI Local 圖示">

  # RubaTone AI Local

  **在自己的電腦完成 AI 翻唱，並透過 Android 手機在內網遙控。**

  [繁體中文](README.md) · [English](README.en.md) · [简体中文](README.zh-CN.md)

  [![Release](https://img.shields.io/badge/release-v1.0.8-7c3aed?style=flat-square)](https://github.com/Hiruynk/RubaTone-AI-Local/releases/tag/v1.0.8)
  ![Windows](https://img.shields.io/badge/Windows-11%20x64-0078D4?style=flat-square&logo=windows11&logoColor=white)
  ![GPU](https://img.shields.io/badge/NVIDIA-RTX%2040%20%2F%2050-76B900?style=flat-square&logo=nvidia&logoColor=white)
  ![Android](https://img.shields.io/badge/Android-10%2B-3DDC84?style=flat-square&logo=android&logoColor=white)
  ![Mode](https://img.shields.io/badge/runtime-local--first-2563EB?style=flat-square)

  [下載 Windows Launcher](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-Launcher-Setup.exe)
  ·
  [下載 Android APK](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-1.0.2-arm64-release.apk)
  ·
  [所有發布檔案](https://huggingface.co/hiruynk/RubaTone-AI-Local/tree/main)
</div>

---

## 概覽

RubaTone AI Local 是 RubaTone AI 的本機 Windows 版本。歌曲、模型、工作與輸出都由你的電腦保存及處理；完成首次安裝後，主要功能不需要 Internet。Android App 是完整的遙控前端，與電腦配對後可在同一私人網路上操作工作流程。

這個 GitHub repository 是**無原始碼的官方發布入口**。大型安裝檔、APK、runtime 分卷、簽章 manifest 與檢查碼存放於 Hugging Face。

## 核心特色

| | 功能 |
|---|---|
| 🎙️ | 主唱、和聲、伴奏與殘響分離，支援男女合唱分析 |
| 🎛️ | RVC 模型匯入、驗證、推理、訓練與續訓 |
| 🎚️ | 平衡混音、移調、專業混音及批次歌曲處理 |
| ✨ | AudioSR 高頻補全與 Resemble Enhance 人聲自然化 |
| 📊 | 音域分析、異常偵測與推薦訓練集 |
| 🧭 | 工作進度、暫停、繼續、取消、失敗重試與背景運行 |
| 📱 | Android 內網遙控、即時事件同步及輸出下載 |
| 🔒 | 本機資料、裝置配對、簽章 manifest 與逐檔完整性驗證 |

## 運作方式

```text
Android App
    │  同一私人網路 · 四位碼配對 · 加密裝置連線
    ▼
Windows 桌面程式
    │
    ├── Core：資料庫、檔案、工作佇列與同步
    ├── Separation：UVR／Roformer／Demucs
    ├── RVC：推理、RMVPE、分析與訓練
    ├── AudioSR
    ├── Resemble Enhance
    └── FFmpeg／FFprobe
```

各 AI runtime 使用獨立環境，避免 Python、Torch、CUDA 與 NumPy 依賴互相衝突。GPU 工作由中央協調器管理，以降低同時搶佔顯存造成失敗的風險。

## 系統需求

### Windows

| 項目 | 首發支援 |
|---|---|
| 作業系統 | Windows 11 x64 |
| 顯示卡 | NVIDIA GeForce RTX 40／50 系列 |
| 顯存 | 至少 12 GB VRAM |
| 網路 | 首次安裝及檢查更新需要 Internet；安裝完成後主程式可離線使用 |
| 已驗證硬體 | RTX 5070 Ti 16 GB，NVIDIA 驅動 596.36 |

其他 RTX 40／50 型號屬正式發布範圍，但尚未逐一完成實體硬體驗證。RTX 10／20／30 系列目前不在首發支援範圍。

### Android

| 項目 | 需求 |
|---|---|
| 系統 | Android 10 或以上 |
| 架構 | arm64 |
| 使用條件 | 必須連接同一私人網路上的 RubaTone AI Local 電腦 |
| 離線狀態 | 未連接電腦時只可開啟首頁 |

APK 已發布，但目前尚未完成 Android 實體手機矩陣驗證。

## 快速開始

### 1. 安裝 Windows 版本

1. 下載並執行 [RubaTone AI Local Launcher 安裝器](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-Launcher-Setup.exe)。
2. 直接開始安裝，或按需要自訂位置；未選擇時 Launcher 會使用安全的預設位置，並自動偵測 GPU、推薦可用版本。
3. 下載完整 runtime。Launcher 最多同時取得四個分卷，並在其他分卷下載期間即時驗證已完成的分卷及重建已具備全部 chunks 的檔案；下載、處理、驗證與重建會顯示各自正確的速度及預計時間。
4. 驗證完成後啟動 RubaTone AI Local。

Launcher 支援暫停、續傳、修復、搬移、可選更新及更新失敗回復。啟動時會先檢查已儲存位置及常見磁碟位置，尋找經驗證且入口程式完整的既有 RubaTone AI Local；找到後不會要求重新下載。已有完整安裝時，即使沒有 Internet 也可直接啟動目前版本。

### 2. 配對 Android

1. 安裝 [Android arm64 APK](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/RubaTone-AI-Local-1.0.2-arm64-release.apk)。
2. 確保手機與電腦連接同一個私人網路。
3. 在電腦顯示四位配對碼。
4. 在手機選擇電腦並輸入配對碼。
5. 在電腦確認手機名稱及裝置指紋。

配對成功後，手機以可撤銷的裝置金鑰自動重連。電腦關閉主視窗時可選擇繼續在背景運行，讓手機仍能操作。

## 資料與私隱

- 新安裝永遠從空白工作區開始。
- 不會匯入雲端帳戶的歌曲、模型、訓練資料、輸出、紀錄、偏好或資料庫。
- 歌曲、模型、工作與輸出永久保存在電腦。
- Android 不保存完整歌曲庫或模型副本；只有使用者明確下載的輸出會進入手機 Downloads。
- 內網服務只供 Windows 私人網路使用，不提供公開 WAN 存取。
- Local 版沒有登入、帳戶切換或帳戶限額。

## 與雲端版本的差異

| 項目 | Local | 雲端 |
|---|:---:|:---:|
| 本機 AI 處理 | ✅ | — |
| Windows 離線使用 | ✅ | — |
| Android 內網遙控 | ✅ | — |
| 帳戶與雲端資產 | — | ✅ |
| 「轉換 MIDI」／MuScriptor | — | ✅ |

雲端正式版仍可於 [rubatone-ai.hiruynk.com](https://rubatone-ai.hiruynk.com) 使用。

## 更新與完整性

- Launcher 每次開啟時可檢查更新；所有更新都可以略過。
- manifest 使用發布金鑰簽署，Launcher 只接受內置公鑰所驗證的內容。
- runtime 採內容分塊與 SHA-256 驗證，只下載缺少或變更的資料。
- 更新只在 staging 重建變更檔案，未變更且已驗證的 runtime 以同磁碟硬連結沿用；成功後才切換。
- 更新失敗時保留並回復上一個可啟動版本。

你亦可下載 [`SHA256SUMS.json`](https://huggingface.co/hiruynk/RubaTone-AI-Local/resolve/main/SHA256SUMS.json) 手動核對發布檔案。

## 發布狀態

| 元件 | 版本 | 狀態 |
|---|---:|---|
| Windows Launcher | 1.0.8 | 已發布 |
| RTX 40／50 app／runtime | 1.0.4 | 已發布；RTX 5070 Ti 已驗證 |
| Android arm64 APK | 1.0.2 | 已發布；尚待實體手機矩陣驗證 |

查看 [GitHub Release](https://github.com/Hiruynk/RubaTone-AI-Local/releases/tag/v1.0.8) 或 [Hugging Face 檔案列表](https://huggingface.co/hiruynk/RubaTone-AI-Local/tree/main)。

## 常見問題

<details>
<summary><strong>安裝後仍需要 Internet 嗎？</strong></summary>

不需要。首次下載完整 GPU runtime 後，Windows 主程式可完全離線使用。只有主動檢查或下載更新時需要 Internet。
</details>

<details>
<summary><strong>可以直接在 Android 手機執行 AI 模型嗎？</strong></summary>

不可以。Android App 是遠端操作介面，AI 推理及資料儲存都在已配對的 Windows 電腦完成。
</details>

<details>
<summary><strong>關閉 Windows 視窗後，手機還能操作嗎？</strong></summary>

可以。關窗時選擇「關閉視窗並在背景運作」，核心服務、目前工作及手機連線會繼續運行。
</details>

<details>
<summary><strong>會自動搬移我原本的雲端歌曲或模型嗎？</strong></summary>

不會。Local 與雲端資產完全分開，新安裝不掃描或匯入既有帳戶資料。
</details>

## 使用範圍與第三方元件

目前建置供開發者與朋友作私人、非商業評估。此 repository 不提供應用程式原始碼，也不代表所有內含第三方模型均採相同授權。第三方 notices、授權文字與必要資訊隨安裝套件提供。

---

<div align="center">
  <strong>RubaTone AI Local</strong><br>
  本機運算 · 內網遙控 · 可選更新
</div>
