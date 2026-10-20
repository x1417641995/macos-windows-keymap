# mac-setup

整理舊 Mac 的鍵盤與 f.lux 設定，供日後在其他 Mac 上還原。原始檔案保存在 `sources/`，方便核對。

這份 repo 目前以 **macOS 設定備份**為主；Karabiner JSON 不能直接套用到 Windows。

## 內容

| 路徑 | 內容 |
| --- | --- |
| [karabiner/](karabiner/) | 原封不動保留的 8 條 Complex Modifications 與原始 README |
| [docs/keyboard-layout.md](docs/keyboard-layout.md) | Fn／Cmd／Ctrl 對調，以及鍵盤還原時需要注意的事項 |
| [docs/f-lux.md](docs/f-lux.md) | 從 Word 整理出的 f.lux 設定 |
| [sources/](sources/) | 原始 ZIP 與 Word 文件；ZIP 名稱移除了下載時的 ` (1)` |

## 鍵盤規則

以下按鍵名稱指規則使用的「邏輯按鍵」。套用 Simple Modifications 後，實體鍵的位置會不同，詳見[鍵盤配置](docs/keyboard-layout.md)。

| 檔案 | 作用 | 原檔的作用範圍 |
| --- | --- | --- |
| [01-cmd-y-redo.json](karabiner/01-cmd-y-redo.json) | 左 Cmd + Y → Cmd + Shift + Z，重做 | 全域 |
| [02-vscode-toggle-comment.json](karabiner/02-vscode-toggle-comment.json) | 右 Option + / → Cmd + /，切換註解 | 僅 VS Code |
| [03-vscode-go-forward.json](karabiner/03-vscode-go-forward.json) | 左 Option + → → Ctrl + Shift + - | 全域；名稱以 VS Code 前進功能為例 |
| [04-vscode-go-back.json](karabiner/04-vscode-go-back.json) | 左 Option + ← → Ctrl + - | 全域；名稱以 VS Code 返回功能為例 |
| [05-f5-teams-mic.json](karabiner/05-f5-teams-mic.json) | F5 → Cmd + Shift + M，原用途為 Teams 麥克風 | 全域；沒有 Teams 限定條件 |
| [06-ctrl-tab-switch-windows.json](karabiner/06-ctrl-tab-switch-windows.json) | 左 Ctrl + Tab → Cmd + Tab | 全域；原 README 註明作者未啟用 |
| [07-left-shift-en-zh.json](karabiner/07-left-shift-en-zh.json) | 單按左 Shift → Ctrl + Space | 全域 |
| [08-right-shift-en-zh.json](karabiner/08-right-shift-en-zh.json) | 單按右 Shift → Ctrl + Space | 全域 |

03、04、05 雖然以特定 App 的功能命名，JSON 並沒有把觸發範圍限制在該 App。這次整理保留原本行為。

## 在 Mac 還原

1. 準備好 Karabiner-Elements，再依[鍵盤配置](docs/keyboard-layout.md)決定是否還原實體鍵對調。
2. 在此 repo 根目錄執行下面的指令，只複製需要的規則。目的地若有同名檔，`cp -i` 會先詢問。
3. 在 Karabiner 的 Complex Modifications 中新增並啟用需要的規則。原 README 記載規則 06 未啟用，其餘規則的實際啟用狀態沒有匯出紀錄。
4. 若使用 Shift 切換輸入法，確認 macOS 的輸入來源切換快捷鍵是 `Ctrl + Space`，並配置需要的英文／中文輸入來源。
5. 按照 [f.lux 記錄](docs/f-lux.md)手動還原色溫和起床時間。

```sh
mkdir -p "$HOME/.config/karabiner/assets/complex_modifications"
# 範例：只複製重做與單按左 Shift 切換輸入來源的規則
cp -i karabiner/01-cmd-y-redo.json karabiner/07-left-shift-en-zh.json \
  "$HOME/.config/karabiner/assets/complex_modifications/"
```

原 ZIP 只有獨立規則，沒有完整 `karabiner.json`、裝置設定或 profile。f.lux 文件也只是文字記錄，沒有可匯入的原生偏好設定檔，因此仍有手動還原步驟。

## 來源

- [原始鍵盤設定 ZIP](sources/mac-windows-style-keymap-main.zip)
- [原始鍵盤 README](karabiner/README.md)
- [原始 f.lux Word 文件](sources/f.lux.docx)

本次整理已核對 JSON 格式及複製內容；尚未在目標 Mac 上實際驗證快捷鍵或 f.lux 行為。
