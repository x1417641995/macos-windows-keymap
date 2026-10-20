# macos-windows-keymap

**English** | [繁體中文](README.zh-TW.md)

Windows-style keyboard shortcuts and input switching for macOS, powered by Karabiner-Elements.

Bring familiar Windows keyboard habits to your Mac with eight independent rules. Choose the shortcuts you need, including redo, editor navigation, app switching, and tapping Shift to switch input sources. Personal f.lux preferences are included as an optional reference.

## Contents

| Path | Contents |
| --- | --- |
| [karabiner/](karabiner/) | Eight JSON rulesets for Karabiner Complex Modifications |
| [docs/keyboard-layout.md](docs/keyboard-layout.md) | Optional Fn / Cmd / Ctrl remapping and physical key behavior |
| [docs/f-lux.md](docs/f-lux.md) | Optional personal f.lux preferences |

## Keyboard rules

The input keys below are **logical keys**. If you apply the optional Simple Modifications, the physical keys that trigger some rules change. See the [keyboard layout guide](docs/keyboard-layout.md) before enabling them.

| File | Mapping / intended use | Scope |
| --- | --- | --- |
| [01-cmd-y-redo.json](karabiner/01-cmd-y-redo.json) | Left Cmd + Y → Cmd + Shift + Z (redo) | Global |
| [02-vscode-toggle-comment.json](karabiner/02-vscode-toggle-comment.json) | Right Option + / → Cmd + / (toggle comment) | VS Code only |
| [03-vscode-go-forward.json](karabiner/03-vscode-go-forward.json) | Left Option + Right Arrow → Ctrl + Shift + - (VS Code Go Forward) | Global |
| [04-vscode-go-back.json](karabiner/04-vscode-go-back.json) | Left Option + Left Arrow → Ctrl + - (VS Code Go Back) | Global |
| [05-f5-teams-mic.json](karabiner/05-f5-teams-mic.json) | F5 → Cmd + Shift + M (intended for the Teams microphone) | Global |
| [06-ctrl-tab-switch-apps.json](karabiner/06-ctrl-tab-switch-apps.json) | Left Ctrl + Tab → Cmd + Tab (switch apps) | Global; left disabled in the original setup |
| [07-left-shift-en-zh.json](karabiner/07-left-shift-en-zh.json) | Tap Left Shift alone → Ctrl + Space (switch input source) | Global |
| [08-right-shift-en-zh.json](karabiner/08-right-shift-en-zh.json) | Tap Right Shift alone → Ctrl + Space (switch input source) | Global |

Rules 03, 04, and 05 have app-specific names but **no app restriction**: they send the same shortcuts in any foreground app. Rule 02 is restricted to the VS Code bundle identifier `com.microsoft.VSCode`.

The Shift rules send Ctrl + Space. Switching between English and Chinese depends on your configured input sources and macOS shortcut; the rules do not select a particular language directly. Holding Shift as part of a key combination retains its modifier behavior.

## Install on macOS

Install [Karabiner-Elements](https://karabiner-elements.pqrs.org/) first. Download and extract this repository's ZIP from GitHub, or clone it:

```sh
git clone https://github.com/x1417641995/macos-windows-keymap.git
cd macos-windows-keymap
```

1. Read the [keyboard layout guide](docs/keyboard-layout.md) and decide whether to apply the optional physical key remapping.
2. From the repository root, copy only the rules you want. The example below installs redo and Left Shift input switching; `cp -i` asks before overwriting an existing file.

```sh
mkdir -p "$HOME/.config/karabiner/assets/complex_modifications"
# Example: redo and tapping Left Shift to switch input sources
cp -i karabiner/01-cmd-y-redo.json karabiner/07-left-shift-en-zh.json \
  "$HOME/.config/karabiner/assets/complex_modifications/"
```

3. In Karabiner-Elements, open **Complex Modifications**, add the predefined rules, and enable the ones you want. Copying the files alone does not enable them. Rule 06 was left disabled in the original setup; the enabled states of the other rules were not exported.
4. For Shift input switching, configure the desired input sources and set the macOS input source switching shortcut to **Ctrl + Space**.
5. Optionally restore the [f.lux preferences](docs/f-lux.md) manually.

To stop using a rule, remove or disable its entry in Karabiner's Complex Modifications. These JSON files contain individual rulesets, not a complete `karabiner.json`, device configuration, or profile.

## Validation

JSON syntax, mapping preservation, and local documentation links have been checked. Shortcut behavior and f.lux preferences have not yet been tested on a target Mac. The f.lux guide records settings for manual restoration, not an importable preferences file.
