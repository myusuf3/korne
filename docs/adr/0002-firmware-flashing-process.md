# ADR 0002: Firmware Flashing Process

## Status

Accepted

## Context

The Eyelash Corne is a wireless split keyboard using ZMK firmware on nice!nano v2 controllers. Flashing new firmware requires a specific process that differs from wired QMK keyboards.

Key facts:
- Wireless keyboards use ZMK (not QMK)
- The nice!nano v2 uses UF2 bootloader
- Split keyboards require flashing both halves separately
- Bluetooth pairings are cleared after flashing

## Decision

### Build Process

Firmware is built automatically via GitHub Actions when changes are pushed to the repository.

1. **Modify keymap** - Edit `config/eyelash_corne.keymap`
2. **Commit and push** - Changes trigger the build workflow
3. **Download artifacts** - Get firmware from GitHub Actions

```bash
# Trigger build manually if needed
gh workflow run build.yml -R myusuf3/korne

# Watch build progress
gh run watch <run-id> -R myusuf3/korne

# Download firmware
gh run download <run-id> -R myusuf3/korne -D ~/Downloads/korne-firmware
```

### Firmware Files

The build produces three files:

| File | Purpose |
|------|---------|
| `settings_reset-nice_nano_v2-zmk.uf2` | Clears settings, use before flashing each side |
| `eyelash_corne_studio_left.uf2` | Left half firmware (with ZMK Studio) |
| `nice_view-eyelash_corne_right-zmk.uf2` | Right half firmware |

### Flashing Order

**Critical: Always flash settings_reset before the main firmware on each side.**

#### Left Keyboard

1. **Double-tap reset button** on bottom of left keyboard
2. Keyboard mounts as `NICENANO` USB drive
3. Copy `settings_reset-nice_nano_v2-zmk.uf2` to the drive
4. Drive ejects automatically (error messages about "device not configured" are normal)
5. **Double-tap reset button** again
6. Copy `eyelash_corne_studio_left.uf2` to the drive

#### Right Keyboard

1. **Double-tap reset button** on bottom of right keyboard
2. Copy `settings_reset-nice_nano_v2-zmk.uf2` to the drive
3. **Double-tap reset button** again
4. Copy `nice_view-eyelash_corne_right-zmk.uf2` to the drive

### Automated Flashing Script

Watch for keyboard mount and copy automatically:

```bash
# Wait for keyboard and copy file
for i in {1..30}; do
  if [ -d "/Volumes/NICENANO" ]; then
    cp firmware.uf2 /Volumes/NICENANO/
    echo "Flashed!"
    break
  fi
  sleep 0.5
done
```

### Verification

1. Turn on both keyboard halves
2. Connect left half to computer via USB
3. Test typing

### Post-Flash: Bluetooth Re-pairing

Flashing clears all Bluetooth pairings. To re-pair:

1. On previously paired devices, forget the keyboard
2. Hold `lwr` + `A` (or S/D/F for profiles 1-3) to select a Bluetooth profile
3. Pair from your device's Bluetooth settings

## Consequences

### Benefits
- Versioned firmware in `releases/` directory provides rollback capability
- GitHub Actions ensures reproducible builds
- Automated flashing reduces manual errors

### Considerations
- Must remember to flash settings_reset first
- Bluetooth devices need re-pairing after each flash
- Error messages during copy are misleading but harmless

## Version History

| Version | Date | Changes |
|---------|------|---------|
| v1 | 2026-02-03 | Initial working firmware |
| v2 | 2026-02-03 | Top right key changed from ESC to BACKSPACE |
