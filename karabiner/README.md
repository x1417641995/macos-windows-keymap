# mac-windows-style-keymap

Karabiner-Elements complex modifications that bring Windows-style shortcuts and an EN/ZH input switcher to macOS.

Each rule lives in its own JSON file so you can pick and choose — copy only the ones you want.

## Rules

| File | What it does |
| --- | --- |
| [01-cmd-y-redo.json](01-cmd-y-redo.json) | `Cmd + Y` → Redo (like Windows `Ctrl + Y`) |
| [02-vscode-toggle-comment.json](02-vscode-toggle-comment.json) | VSCode only: `Right Option + /` → toggle comment (like Windows `Ctrl + /`) |
| [03-vscode-go-forward.json](03-vscode-go-forward.json) | `Option + →` → Go Forward (like Windows `Alt + →`) |
| [04-vscode-go-back.json](04-vscode-go-back.json) | `Option + ←` → Go Back (like Windows `Alt + ←`) |
| [05-f5-teams-mic.json](05-f5-teams-mic.json) | `F5` → toggle Microsoft Teams microphone (`Cmd + Shift + M`) |
| [06-ctrl-tab-switch-windows.json](06-ctrl-tab-switch-windows.json) | `Left Control + Tab` → `Cmd + Tab` (switch windows) — *⚠️ author keeps this disabled, see notes* |
| [07-left-shift-en-zh.json](07-left-shift-en-zh.json) | Tap **Left Shift** alone → `Ctrl + Space` (switch EN/ZH input) |
| [08-right-shift-en-zh.json](08-right-shift-en-zh.json) | Tap **Right Shift** alone → `Ctrl + Space` (switch EN/ZH input) |

> Rules 03 and 04 map to `Ctrl + Shift + -` / `Ctrl + -`, which is VSCode's default Go-Forward / Go-Back chord. They will work in any app, but the names assume VSCode.

## Install

Prerequisite: [Karabiner-Elements](https://karabiner-elements.pqrs.org/) is installed.

### Option A — copy individual files (recommended)

```bash
git clone <this repo>
cd mac-windows-style-keymap

# Copy only the rules you want, e.g.:
cp 01-cmd-y-redo.json 07-left-shift-en-zh.json \
   ~/.config/karabiner/assets/complex_modifications/
```

### Option B — copy everything

```bash
cp *.json ~/.config/karabiner/assets/complex_modifications/
```

### Enable in Karabiner

1. Open **Karabiner-Elements** → **Complex Modifications** → **Add predefined rule**
2. You'll see each title from the table above as a separate group
3. Click **Enable** next to the rule(s) you want

To disable later: **Complex Modifications** tab → toggle the rule off, or click **Edit** → **Remove**.

## ⚠️ Heads-up: author's keyboard layout affects which physical keys trigger these rules

The author runs the following **Simple Modifications** on the Apple Internal Keyboard / Trackpad (NOT included in this repo, but worth knowing about):

| From | To |
| --- | --- |
| `fn (globe)` | `left_command` |
| `left_command` | `left_control` |
| `left_control` | `fn (globe)` |

In other words, on the built-in keyboard the physical **Cmd** position behaves like **Ctrl**, the physical **Fn** position behaves like **Cmd**, and the physical **Ctrl** position becomes **Fn**. This is a Windows-style remap so the bottom-left key acts as Ctrl.

Because Karabiner runs Simple Modifications **before** Complex Modifications, this remap changes which physical key triggers some rules in this repo:

| Rule | Logical input | Physical key on author's setup | Physical key on a stock Mac |
| --- | --- | --- | --- |
| 01 (Cmd+Y → Redo) | `left_command + y` | **Fn + Y** | Cmd + Y |
| 03/04 (Option + ←/→) | `left_option + arrow` | Option + arrow (unchanged) | Option + arrow |
| 06 (Ctrl+Tab → switch windows) | `left_control + tab` | **physical Cmd + Tab** | Ctrl + Tab |

In short:
- If you don't apply the same Fn/Cmd/Ctrl swap, the rules still work — just from the **stock physical keys** (e.g. rule 01 fires on the real Cmd key, not on Fn).
- Rules 02, 05, 07, 08 are unaffected (they use `right_option`, `f5`, `shift`).
- This is also why the author keeps **rule 06 disabled** — combined with the swap, "Left Control + Tab" effectively becomes "physical Cmd + Tab", which is already what stock macOS does, so the rule would be a no-op.

If you want the same physical feel as the author, replicate the three Simple Modifications above in **Karabiner → Simple Modifications → Apple Internal Keyboard / Trackpad (Apple)**.

## Notes

- Rule 07/08 (Shift to switch input) only triggers when Shift is **tapped alone**. Holding Shift to capitalize still works normally.
- Rule 02 only fires when VSCode is the frontmost app (matched by bundle id `com.microsoft.VSCode`).
- **Rule 06 (`Left Control + Tab` → switch windows):** the author has this turned off in their own config. It's included here for completeness — feel free to enable it if it suits your physical key layout, otherwise you can skip the file entirely.
- These files contain **only** Complex Modifications — no device-specific simple modifications (Fn/Cmd/Ctrl swaps), profile, or virtual HID settings. Importing them will not change your existing key remaps.
