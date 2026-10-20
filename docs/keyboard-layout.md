# 鍵盤配置還原記錄

依舊鍵盤設定的 README 整理。這些對調需要手動設定，沒有包含在 `karabiner/` 的 8 個 JSON 檔內。

## Simple Modifications

舊設定的對象是 **Apple Internal Keyboard / Trackpad**，不是所有外接鍵盤。

| 原按鍵 | 轉換後 |
| --- | --- |
| `fn`（地球鍵） | `left_command` |
| `left_command` | `left_control` |
| `left_control` | `fn`（地球鍵） |

若要重現原先手感，在目標 Mac 的 Karabiner Simple Modifications 中，針對內建鍵盤手動設定上述對應。若使用外接鍵盤，先確認其實際鍵位與裝置，不直接假設配置相同。

依舊設定記錄，Simple Modifications 先於 Complex Modifications 生效。因此，套用上述配置後：

- 規則 01 的邏輯左 Cmd + Y，由實體 Fn + Y 觸發。
- 規則 06 的邏輯左 Ctrl + Tab，由實體左 Cmd + Tab 觸發，並送出 Cmd + Tab。
- 左 Option、右 Option、F5 與 Shift 不在上述三個對調按鍵之內。

## 還原時需要確認

- 舊設定明確記錄規則 06 關閉；沒有其他規則的實際啟用狀態紀錄。
- 規則 06 輸出的是 Cmd + Tab；原檔名稱寫「switch windows」，還原時應以實際輸出的快捷鍵為準。
- 03、04 沒有 VS Code 限定條件；05 沒有 Teams 限定條件，會在其他 App 中送出相同快捷鍵。
- 07、08 輸出 Ctrl + Space。是否在英文與中文間切換，取決於目標 Mac 的輸入來源與快捷鍵設定。
- 目前沒有完整 profile、裝置識別資訊、macOS 版本、Karabiner 版本或輸入法清單，不能從現有檔案自動重建這些資訊。

`karabiner/` 保留原始 JSON 的規則內容。
