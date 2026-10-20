# macos-windows-keymap

[English](README.md) | **繁體中文**

Windows-style keyboard shortcuts and input switching for macOS, powered by Karabiner-Elements.

透過 Karabiner-Elements，讓 macOS 的快捷鍵與中英輸入切換更符合 Windows 使用習慣，供其他 Mac 下載還原。另保留 f.lux 的個人偏好設定作為附加記錄。

## 內容

| 路徑 | 內容 |
| --- | --- |
| [karabiner/](karabiner/) | 可匯入 Karabiner 的 8 條 Complex Modifications JSON |
| [docs/keyboard-layout.zh-TW.md](docs/keyboard-layout.zh-TW.md) | Fn／Cmd／Ctrl 對調，以及鍵盤還原時需要注意的事項 |
| [docs/f-lux.zh-TW.md](docs/f-lux.zh-TW.md) | 附加記錄：f.lux 個人偏好設定 |

## 鍵盤規則

以下按鍵名稱指規則使用的「邏輯按鍵」。套用 Simple Modifications 後，實體鍵的位置會不同，詳見[鍵盤配置](docs/keyboard-layout.zh-TW.md)。

| 檔案 | 作用 | 原檔的作用範圍 |
| --- | --- | --- |
| [01-cmd-y-redo.json](karabiner/01-cmd-y-redo.json) | 左 Cmd + Y → Cmd + Shift + Z，重做 | 全域 |
| [02-vscode-toggle-comment.json](karabiner/02-vscode-toggle-comment.json) | 右 Option + / → Cmd + /，切換註解 | 僅 VS Code |
| [03-vscode-go-forward.json](karabiner/03-vscode-go-forward.json) | 左 Option + → → Ctrl + Shift + - | 全域；名稱以 VS Code 前進功能為例 |
| [04-vscode-go-back.json](karabiner/04-vscode-go-back.json) | 左 Option + ← → Ctrl + - | 全域；名稱以 VS Code 返回功能為例 |
| [05-f5-teams-mic.json](karabiner/05-f5-teams-mic.json) | F5 → Cmd + Shift + M，原用途為 Teams 麥克風 | 全域；沒有 Teams 限定條件 |
| [06-ctrl-tab-switch-apps.json](karabiner/06-ctrl-tab-switch-apps.json) | 左 Ctrl + Tab → Cmd + Tab，切換 App | 全域；舊設定記錄為未啟用 |
| [07-left-shift-en-zh.json](karabiner/07-left-shift-en-zh.json) | 單按左 Shift → Ctrl + Space | 全域 |
| [08-right-shift-en-zh.json](karabiner/08-right-shift-en-zh.json) | 單按右 Shift → Ctrl + Space | 全域 |

03、04、05 雖然以特定 App 的功能命名，JSON 並沒有把觸發範圍限制在該 App。這些規則保留原本行為。

Shift 規則會送出 Ctrl + Space，不會直接指定英文或中文。實際切換結果取決於 macOS 的輸入來源與快捷鍵設定；配合其他按鍵使用 Shift 時，仍保留修飾鍵行為。

## 在 Mac 還原

先安裝 [Karabiner-Elements](https://karabiner-elements.pqrs.org/)，再從 GitHub 下載 ZIP 並解壓縮，或在終端機執行以下指令：

```sh
git clone https://github.com/x1417641995/macos-windows-keymap.git
cd macos-windows-keymap
```

1. 準備好 Karabiner-Elements，再依[鍵盤配置](docs/keyboard-layout.zh-TW.md)決定是否還原實體鍵對調。
2. 在此 repo 根目錄執行下面的指令，只複製需要的規則。目的地若有同名檔，`cp -i` 會先詢問。
3. 在 Karabiner 的 Complex Modifications 中新增並啟用需要的規則；只有複製檔案並不會啟用規則。舊設定記錄為規則 06 未啟用，其餘規則的實際啟用狀態沒有匯出紀錄。
4. 若使用 Shift 切換輸入法，確認 macOS 的輸入來源切換快捷鍵是 `Ctrl + Space`，並配置需要的英文／中文輸入來源。
5. 按照 [f.lux 記錄](docs/f-lux.zh-TW.md)手動還原色溫和起床時間。

```sh
mkdir -p "$HOME/.config/karabiner/assets/complex_modifications"
# 範例：只複製重做與單按左 Shift 切換輸入來源的規則
cp -i karabiner/01-cmd-y-redo.json karabiner/07-left-shift-en-zh.json \
  "$HOME/.config/karabiner/assets/complex_modifications/"
```

若不再使用某條規則，可在 Karabiner 的 Complex Modifications 中停用或移除。此 repo 提供獨立規則，沒有完整 `karabiner.json`、裝置設定或 profile。f.lux 設定以文件記錄，沒有可匯入的原生偏好設定檔，因此仍有手動還原步驟。

JSON 格式及規則內容已核對；尚未在目標 Mac 上實際驗證快捷鍵或 f.lux 行為。
