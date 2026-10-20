# Keyboard layout

**English** | [繁體中文](keyboard-layout.zh-TW.md)

These optional mappings were documented in the original keyboard setup. Configure them manually in Karabiner Simple Modifications; they are not included in the eight JSON files in `karabiner/`.

## Simple Modifications

The original setup applied these mappings to the **Apple Internal Keyboard / Trackpad**, rather than to every external keyboard.

| From | To |
| --- | --- |
| `fn` (Globe) | `left_command` |
| `left_command` | `left_control` |
| `left_control` | `fn` (Globe) |

To reproduce the original physical layout, add these three mappings for the built-in keyboard in Karabiner's Simple Modifications. Check the actual device and key positions before using the same layout on an external keyboard.

Karabiner applies Simple Modifications before Complex Modifications. With the mappings above:

- Rule 01's logical Left Cmd + Y is triggered by physical Fn + Y.
- Rule 06's logical Left Ctrl + Tab is triggered by physical Left Cmd + Tab and sends Cmd + Tab.
- Left Option, Right Option, F5, and Shift are unaffected by this three-key remapping.

Without these Simple Modifications, the rules use the standard physical keys shown in the main README.

## Before enabling rules

- Rule 06 was explicitly left disabled in the original setup. The enabled states of the other rules were not exported.
- Rule 06 sends Cmd + Tab to switch apps; its filename is `06-ctrl-tab-switch-apps.json`.
- Rules 03 and 04 are not restricted to VS Code. Rule 05 is not restricted to Teams. They send the same shortcuts in other apps.
- Rules 07 and 08 send Ctrl + Space. The input sources and shortcut configured on your Mac determine whether this switches between English and Chinese.
- A complete profile, device identifiers, original macOS and Karabiner versions, and an input method list are not available, so these cannot be reconstructed automatically.

The files in `karabiner/` preserve the original keyboard mapping behavior.
