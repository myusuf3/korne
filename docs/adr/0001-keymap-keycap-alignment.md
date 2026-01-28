# ADR 0001: Keymap and Keycap Legend Alignment

## Status

Proposed

## Context

![Current keyboard keycaps](img/keyboard.jpeg)

The Eyelash Corne keyboard's current `eyelash_corne.keymap` configuration does not match the physical keycap legends. This creates confusion when using the keyboard, as the printed labels don't reflect actual key behavior.

### Current Mismatches

| Position | Keycap Label | Actual Keymap Behavior |
|----------|--------------|------------------------|
| Left home row, leftmost | `ctrl` | Shift (tap-dance: tap=Shift, double-tap=Caps) |
| Left bottom row, leftmost | `shift` | LCTRL |
| Left inner thumb | `ctrl` | Space (tap) / Layer 3 (hold) |
| Right top row, rightmost | `esc` | Backspace |
| Right bottom row, rightmost | `shift` | ESC |
| Right inner thumb | `alt` | Enter (tap) / Layer 3 (hold) |
| Right outer thumb | `bksp` | RALT |

### What Currently Matches

- All alpha keys (Q-P, A-L, Z-M)
- `tab` key
- `sys` thumb key (LGUI/Cmd/Win)
- `lwr` thumb key (Layer 1 / Number layer)
- `rse` thumb key (Layer 2 / Symbol layer)

## Decision

**TBD** - One of the following options will be selected:

### Option A: Modify Keymap to Match Keycaps

Update `eyelash_corne.keymap` so all keys produce what their legends indicate.

**Pros:**
- Visual labels match behavior - no memorization needed
- Easier for others to use the keyboard
- Standard modifier positions (Ctrl on home row, Shift on bottom)

**Cons:**
- Lose Space/Enter on thumb keys (efficient for typing)
- Backspace moves from convenient top-right to thumb
- May require re-learning muscle memory

### Option B: Keep Current Keymap, Replace Keycaps

Order custom keycaps that match the current keymap behavior.

**Pros:**
- Keep current (potentially optimized) layout
- No re-learning required
- Space/Enter on thumbs is ergonomic

**Cons:**
- Cost of new keycaps
- Time to source/order correct legends
- Current layout may not be optimal anyway

### Option C: Hybrid Approach

Modify some mappings while keeping beneficial ones. For example:
- Match Ctrl/Shift positions to keycaps (left side)
- Keep Space/Enter on inner thumbs (ignore keycap labels there)
- Move Backspace/ESC to match keycaps (right side)

**Pros:**
- Best of both worlds
- Keep ergonomic thumb layout
- Fix the most confusing mismatches

**Cons:**
- Still some label mismatches on thumb cluster
- Requires deciding which mismatches are acceptable

## Consequences

Depends on chosen option. Key considerations:

- **Typing `?`**: With keycap-matched layout, use Left Shift (bottom-left) + `/` (cross-hand, comfortable)
- **Thumb ergonomics**: Space/Enter on thumbs reduces pinky strain
- **Learning curve**: Any change requires adjustment period
