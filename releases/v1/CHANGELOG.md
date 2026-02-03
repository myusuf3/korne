# v1 - Initial Release

**Date:** 2026-02-03
**Build:** GitHub Actions Run #21645111576

## Firmware Files

| File | Description |
|------|-------------|
| `settings_reset-nice_nano_v2-zmk.uf2` | Reset firmware (use before flashing each side) |
| `eyelash_corne_studio_left.uf2` | Left half with ZMK Studio enabled |
| `nice_view-eyelash_corne_right-zmk.uf2` | Right half firmware |

## Keymap Summary

### Layer 0: QWERTY (Default)
- Standard QWERTY layout
- Left outer column: Tab, Ctrl, Shift
- Right outer column: Esc, Single Quote, Shift
- Left thumb: GUI, Lower (mo 1), Ctrl/Space (mod-tap)
- Right thumb: Alt/Enter (mod-tap), Raise (mo 2), Backspace
- Encoder: Volume Up/Down

### Layer 1: NUMBER (Lower)
- Number row (1-9, 0)
- Arrow keys on right home row (H=Left, J=Down, K=Up, L=Right)
- Bluetooth controls (BT_CLR_ALL, BT_SEL 0-3)
- RGB controls
- Navigation (Home, End, PgUp, PgDn)
- Encoder: Scroll Up/Down

### Layer 2: SYMBOL (Raise)
- Symbols (! @ # $ % ^ & * ( ))
- Brackets and braces
- Minus, Equal, Backslash, Grave, Tilde
- Mouse button controls
- Output toggle (USB/BLE)
- Encoder: Scroll Up/Down

### Layer 3: Fn (accessed via combo: keys 43+46)
- Function keys F1-F12
- Bootloader access
- System reset
- Print Screen, Scroll Lock, Pause/Break
- Studio unlock

## Combos
- **Soft off:** Keys 1+15+29 (hold 2 seconds)
- **Layer 3:** Keys 43+46 (both inner thumb keys)

## Flashing Order

**Left keyboard:**
1. `settings_reset-nice_nano_v2-zmk.uf2`
2. `eyelash_corne_studio_left.uf2`

**Right keyboard:**
1. `settings_reset-nice_nano_v2-zmk.uf2`
2. `nice_view-eyelash_corne_right-zmk.uf2`
