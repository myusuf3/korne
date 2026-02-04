# v2

**Date:** 2026-02-03
**Build:** GitHub Actions Run #21649091309

## Changes from v1

- **Top right key changed from ESC to BACKSPACE** - More ergonomic placement for backspace

## Firmware Files

| File | Description |
|------|-------------|
| `settings_reset-nice_nano_v2-zmk.uf2` | Reset firmware (use before flashing each side) |
| `eyelash_corne_studio_left.uf2` | Left half with ZMK Studio enabled |
| `nice_view-eyelash_corne_right-zmk.uf2` | Right half firmware |

## Flashing Order

**Left keyboard:**
1. `settings_reset-nice_nano_v2-zmk.uf2`
2. `eyelash_corne_studio_left.uf2`

**Right keyboard:**
1. `settings_reset-nice_nano_v2-zmk.uf2`
2. `nice_view-eyelash_corne_right-zmk.uf2`
