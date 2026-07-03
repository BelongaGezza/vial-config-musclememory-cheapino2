# User Guide — Muscle Memory Home Row Mods (CHEAPINO)

This is the Cheapino counterpart to the Totem's `USER_GUIDE.md`. The two keymaps
are aligned so the same muscle memory works on both boards. Differences below are
driven purely by hardware: the Cheapino is a 36-key **wired** QMK/Vial board (no
outer pinky keys, no Bluetooth), configured through the Vial GUI rather than
compiled ZMK firmware.

## Notation

```
KEY          plain key
KEY ▾MOD     hold-tap: tap = KEY, hold = MOD
▽            transparent — passes through to the layer below
·            no action
BASE         tap returns to the BASE layer
```

Hold-tap keys activate their modifier (MOD) when held. Tapping them quickly
produces the primary character (KEY).

---

## Keyboard layout reference

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  Q  │  W  │  E  │  R  │  T  │   │  Y  │  U  │  I  │  O  │  P  │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │  A  │  S  │  D  │  F  │  G  │   │  H  │  J  │  K  │  L  │  ;  │
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │    │  Z  │  X  │  C  │  V  │  B  │   │  N  │  M  │  ,  │  .  │  /  │    │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │ FN  │ ESC │ SPC │   │ SPC │ BSP │ CMP │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

The empty outer corners mark where the Totem has its two extra pinky keys
(outer TAB / outer ENT). The Cheapino has 36 switches instead of 38 — those two
positions simply don't exist here. Shift is already covered by `A`▾SFT and
`;`▾SFT, and TAB/ENT are reachable from the SYMB layer, so nothing is lost.

Row 2 (`Z X C V B | N M , . /`) sits directly under the home row with no
extra pinky column on either side.

---

## Layer 0 — BASE

**Active by default.**

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  Q  │  W  │  E  │  R  │  T  │   │  Y  │  U  │  I  │  O  │  P  │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │  A  │  S  │  D  │  F  │  G  │   │  H  │  J  │  K  │  L  │  ;  │
         │▾SFT │▾RALT│▾SYMB│▾CTL │▾ALT │   │▾ALT │▾CTL │▾SYMB│▾RALT│▾SFT │
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │    │  Z  │  X  │  C  │  V  │  B  │   │  N  │  M  │  ,  │  .  │  /  │    │
    │    │     │     │     │▾GUI │     │   │     │▾GUI │     │     │     │    │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │ FN  │ ESC │ SPC │   │ SPC │ BSP │ CMP │
                        │ sl  │▾MOU │▾GUI │   │▾GUI │     │▾NPD │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

**Thumb keys:**

| Key | Tap | Hold |
|-----|-----|------|
| FN | enter FUNC layer (sticky, one-shot) | — |
| ESC | Escape | enter MOUSE layer |
| SPC (left) | Space | GUI (⌘/⊞) |
| SPC (right) | Space | GUI (⌘/⊞) |
| BSP | Backspace | — (plain key, no layer) |
| CMP | Compose / App key | double-tap: lock NUMPAD |

**Home row modifiers:**

| Left key | Hold = | | Right key | Hold = |
|----------|--------|-|-----------|--------|
| A | Shift | | ; | Shift |
| S | AltGr | | L | AltGr |
| D | SYMB layer | | K | SYMB layer |
| F | Ctrl | | J | Ctrl |
| G | Alt | | H | Alt |
| V | GUI | | M | GUI |
| SPC | GUI | | SPC | GUI |

*(No positional/cross-hand restriction is enforced by QMK the way ZMK enforces
it on the Totem — the underlying firmware's hold-tap flavor governs exactly
when a hold fires. Behave as if identical to the Totem unless you notice
otherwise.)*

---

## Thumb cluster on every other layer

Every layer below (SYMB, NPAD, FUNC, NAVI, MOUS, SYST) uses the **same** thumb
pattern, so it's described once here instead of six times:

- Both `SPC` keys stay **transparent** (`▽`) — Space/GUI still works from BASE.
- `FN` stays **transparent** (`▽`).
- `ESC` **taps back to BASE**, and still **holds into MOUSE**.
- `CMP` **taps back to BASE**, still **holds Compose/App**, and still
  **double-taps to toggle NUMPAD**.

So from any layer, tapping either `ESC` or `CMP` gets you home.

---

## Layer 3 (Vial slot) — SYMB (symbols, numbers, arrows)

**Access:**
- Hold `D` or `K` (momentary)
- `ESC`-thumb + `BSP` combo — toggle on/off

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  1  │  2  │  3  │  4  │  5  │   │  6  │  7  │  8  │  9  │  0  │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │ ESC │ INS │ DEL │ TAB │ BSP │   │  ←  │  ↓  │  ↑  │  →  │ ENT │
         │▾SFT │▾RALT│▾NPD │▾CTL │▾ALT │   │▾ALT │▾CTL │▾NPD │▾RALT│▾SFT │
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │    │  `  │  -  │  =  │  [  │  ]  │   │  \  │  '  │  ,  │  .  │  /  │    │
    │    │     │     │     │▾GUI │     │   │     │▾GUI │     │     │     │    │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │  ▽  │BASE │  ▽  │   │  ▽  │  ▽  │BASE │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

**Notes:**
- Arrow keys `←↓↑→` are on `H J K L` (Vim-style), carrying the same
  modifier holds as BASE — hold `H` for Alt+Arrow, `J` for Ctrl+Arrow, etc.
- Shifted symbols are reached by holding `A` (Shift) while tapping a
  number/bracket on this layer.
- `D`/`K` hold into **NPAD**, matching the Totem's `▾NPD` — lets you jump
  straight from SYMB into the numpad without returning to BASE first.

---

## Layer 2 (Vial slot) — NPAD (numpad)

**Access:**
- Double-tap `CMP` to lock on
- Tap `CMP` or `ESC`-thumb to exit (returns to BASE)

Left half is fully transparent, so home row mods stay usable with the left
hand while the right hand enters numbers.

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  ▽  │  ▽  │  ▽  │  ▽  │  ▽  │   │  -  │  7  │  8  │  9  │  0  │
         │     │     │     │     │     │   │ (÷) │     │     │     │ (=) │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │  ▽  │  ▽  │  ▽  │  ▽  │  ▽  │   │NLCK │  4  │  5  │  6  │KPENT│
         │     │     │     │     │     │   │▾ALT │▾CTL │▾SYMB│▾RALT│▾SFT│
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │    │  ▽  │  ▽  │  ▽  │  ▽  │  ▽  │   │  +  │  1  │  2  │  3  │  .  │    │
    │    │     │     │     │     │     │   │ (×) │▾GUI │     │     │ (,) │    │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │  ▽  │BASE │  ▽  │   │  ▽  │  ▽  │BASE │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

**Tap-dance operators** — tap for primary, **hold** for secondary (this is
the original ["muscle memory friendly" layout] design, not a Cheapino quirk —
see *Design notes* below):

| Key | Tap (primary) | Hold (secondary) | Tap-then-hold |
|-----|---------------|-------------------|----------------|
| `-` | − minus | ÷ divide | repeats `-` |
| `+` | + plus | × multiply | repeats `+` |
| `.` | . decimal | , comma | repeats `.` |
| `0` | 0 | = equals | repeats `0` |

["muscle memory friendly" layout]: https://blog.getreu.net/20250826-muscle-memory-friendly-home-row-mods/

Because the left side is transparent, `F`+`5` gives Ctrl+numpad-5, same idea
as on the Totem.

---

## Layer 4 (Vial slot) — FUNC (function keys)

**Access:** tap `FN` (sticky — auto-returns to BASE after the next key).

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  F1 │  F2 │  F3 │  F4 │  F5 │   │  F6 │  F7 │  F8 │  F9 │ F10 │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │ F11 │ F12 │ F13 │ F14 │ F15 │   │ F16 │ F17 │ F18 │ F19 │ F20 │
         │▾SFT │▾RALT│     │▾CTL │▾ALT │   │▾ALT │▾CTL │     │▾RALT│▾SFT │
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │    │ F21 │ F22 │ F23 │ F24 │  ·  │   │  ·  │RGUI │  ·  │  ·  │  ·  │    │
    │    │     │     │     │▾GUI │     │   │     │     │     │     │     │    │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │  ▽  │BASE │  ▽  │   │  ▽  │  ▽  │BASE │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

---

## Layer 5 (Vial slot) — NAVI (navigation)

**Access:** `SPC`-thumb + `BSP` combo (one-shot — stays active for one keypress).

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  ·  │  ·  │  ·  │  ·  │  ·  │   │HOME │ DEL │ INS │ END │ BSP │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │ ESC │ INS │ DEL │ TAB │ BSP │   │  ←  │  ↓  │  ↑  │  →  │ ENT │
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │    │  ·  │  ·  │  ·  │  ·  │  ·  │   │  ·  │PGDN │PGUP │  ·  │  ·  │    │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │  ▽  │BASE │  ▽  │   │  ▽  │  ▽  │BASE │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

---

## Layer 6 (Vial slot) — MOUS (mouse)

**Access:** hold `ESC`-thumb.

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  ·  │  ·  │  ·  │  ·  │  ·  │   │  ·  │  ·  │  ·  │  ·  │  ·  │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │ MB4 │LCLK │MCLK │RCLK │ MB5 │   │ ◄   │ ▼   │ ▲   │ ►   │LCLK │
         │(bck)│     │     │     │(fwd)│   │move │move │move │move │     │
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │    │  ·  │  ·  │  ·  │  ·  │  ·  │   │ ◄   │ ▼   │ ▲   │ ►   │  ·  │    │
    │    │     │     │     │     │     │   │scrl │scrl │scrl │scrl │     │    │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │  ▽  │BASE │  ▽  │   │  ▽  │  ▽  │BASE │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

---

## Layer 7 (Vial slot) — SYST (system / RGB, no Bluetooth)

**Access:** hold `V`+`SPC` **or** `M`+`SPC` (momentary, both hands).

The Cheapino is wired-only, so this layer has no Bluetooth controls. The
left half — empty on the Totem's SYST layer once BT is stripped out — is
used here for firmware reset and RGB underglow control instead:

```
         ┌──────┬──────┬──────┬──────┬──────┐   ┌──────┬──────┬──────┬──────┬──────┐
         │EECLR │  ·   │RGB−V │RGB+V │RGBTOG│   │  ·   │BRI ↓ │BRI ↑ │  ·   │  ·   │
         ├──────┼──────┼──────┼──────┼──────┤   ├──────┼──────┼──────┼──────┼──────┤
         │ BOOT │  ·   │RGB−H │RGB+H │  ·   │   │MUTE  │VOL ↓ │VOL ↑ │  ·   │  ·   │
    ┌────┼──────┼──────┼──────┼──────┼──────┤   ├──────┼──────┼──────┼──────┼──────┼────┐
    │    │REBOOT│  ·   │RGB−S │RGB+S │  ·   │   │ PLAY │ PREV │ NEXT │  ·   │  ·   │    │
    └────┴──────┴──────┴──┬───┴──────┴──────┘   └──────┴──────┴──┬───┴──────┴──────┴────┘
                          │  ▽  │BASE │  ▽  │   │  ▽  │  ▽  │BASE │
                          └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

| Key | Action |
|-----|--------|
| BOOT (`A`) | Enter bootloader (QK_BOOT) |
| REBOOT (`Z`) | Soft reset (QK_REBOOT) |
| EECLR (`Q`) | Clear EEPROM (QK_CLEAR_EEPROM) |
| RGB−V / +V (`E`/`R`) | RGB brightness down/up |
| RGB−H / +H (`D`/`F`) | RGB hue down/up |
| RGB−S / +S (`C`/`V`) | RGB saturation down/up |
| RGBTOG (`T`) | RGB underglow on/off |
| BRI ↓/↑, MUTE, VOL ↓/↑, PLAY/PREV/NEXT | same media controls as the Totem |

---

## Combos

| Keys | Result | Notes |
|------|--------|-------|
| `Q`+`W`+`E`+`T` | Bootloader (left half) | |
| `Y`+`I`+`O`+`P` | Bootloader (right half) | |
| `ESC`-thumb + `BSP` | Toggle SYMB | |
| `SPC`-thumb + `BSP` | Sticky NAVI | fires from **either** SPC thumb, see *Known quirks* |
| `V` + `SPC`-thumb | Momentary SYST | |
| `M` + `SPC`-thumb | Momentary SYST | |
| `FN`-thumb + `CMP`-thumb | Caps Lock | two combo slots cover both of CMP's tap-dance states, so it works from every layer |

There is no outer-key Caps Lock combo (the Totem's `outer TAB`+`outer ENT`
combo) — those two physical keys don't exist on the Cheapino, and `FN`+`CMP`
already covers Caps Lock.

---

## Common workflows

### Typing numbers and symbols

Hold `D` (or `K`) while typing on the other hand, or toggle SYMB with the
`ESC`-thumb+`BSP` combo for extended sessions.

### Cut, copy, paste (Ctrl+X/C/V)

```
Ctrl+Z   hold F, tap Z
Ctrl+X   hold F, tap X
Ctrl+C   hold F, tap C
Ctrl+V   hold F, tap V
```

Cross-hand is generally the most reliable: `hold J (Ctrl), tap Z/X/C`.

### Arrow keys

**Single press** — SPC-thumb+BSP combo for sticky NAVI, then `H J K L`.
**Extended** — toggle SYMB (`ESC`-thumb+`BSP`), then use `H J K L` continuously.

### Home, End, Page Up, Page Down

Trigger sticky NAVI, then:
- `Y` → Home, `P` → Backspace, `U` → Delete, `I` → Insert, `O` → End
- `M` → Page Down, `,` → Page Up, `;` → Enter

### GUI shortcuts (window management)

Hold either `SPC` for GUI, then tap a key. Toggle SYMB first if you need
arrow keys under GUI (e.g. tiling window managers):

```
Toggle SYMB (ESC-thumb+BSP)
Hold left SPC (GUI)
Tap H / J / K / L   → GUI+← / GUI+↓ / GUI+↑ / GUI+→
```

### Alt+Tab

There's no outer TAB key on the Cheapino, so this always goes through SYMB:
toggle SYMB, hold `G` (Alt), tap `F`-position (Tab) — same-hand, so allow the
tapping term to elapse on `G` before tapping `F`.

### Function keys

```
FN tap, then F5        → F5
FN tap, then A+F1      → Shift+F1
FN tap, then F+F5      → Ctrl+F5
```

### Numpad entry

```
CMP CMP      → lock NUMPAD
3 . 1 4      → right hand: 3 . 1 4
F + 5        → hold F (Ctrl) + 5 = Ctrl+KP5
CMP          → exit back to BASE
```

Arithmetic secondary symbols (÷ × , =) are on **hold** — press and hold past
the 200 ms tapping term to get them (this is by design, see *Design notes*).

### RGB / firmware maintenance

Hold `V`+`SPC` (or `M`+`SPC`) to enter SYST, then tap a key in the left
half for RGB or reset — release both thumbs to exit.

---

## Layer access summary

| Layer | Vial slot | Method | Stays active |
|-------|-----------|--------|---------------|
| SYMB | 3 | Hold `D` or `K` | While held |
| SYMB | 3 | `ESC`-thumb + `BSP` combo | Until toggled off |
| NPAD | 2 | Double-tap `CMP` | Until `CMP` or `ESC`-thumb exits |
| FUNC | 4 | Tap `FN` (sticky) | One keypress |
| NAVI | 5 | `SPC`-thumb + `BSP` combo (sticky) | One keypress |
| MOUS | 6 | Hold `ESC`-thumb | While held |
| SYST | 7 | Hold `V`+`SPC` or `M`+`SPC` | While both held |

---

## Design notes

**NPAD arithmetic tap-dance is hold-based, not double-tap-based, on purpose.**
`cheapino-agent-brief.md` (which drove the recent alignment work) describes
the Totem's version as "tap once = primary, tap twice = secondary." But the
underlying ["muscle memory friendly" layout] this whole keymap is built on —
linked from this repo's own `README.md` — specifies it the other way:

> Tapping sends the primary numpad key once. Holding sends the secondary
> operator and keeps it active for auto-repeat. Tapping and then holding
> repeats the primary numpad key.

That's exactly what the `.vil`'s `tap_dance` entries for `-`/`+`/`.`/`0`
already implement (`tap`=primary, `hold`=secondary, `tap_hold`=primary
repeating), confirmed against Vial's own tap-dance field semantics
(`On tap` / `On hold` / `On double tap` / `On tap+hold`, threshold set by
`tapping_term`) in the [Vial manual]. So this is the original author's
intended behavior, not a bug — it was **not** changed to match the brief's
double-tap description.

[Vial manual]: https://get.vial.today/manual/tap-dance.html
["muscle memory friendly" layout]: https://blog.getreu.net/20250826-muscle-memory-friendly-home-row-mods/

---

## Known quirks (Cheapino vs. Totem)

These were found while cross-referencing the current `.vil` file against the
Totem's rectified layout. Two earlier quirks (SYMB's `D`/`K` hold not
reaching NPAD, and mirrored MOUS back/forward buttons) have since been
fixed in the `.vil` and are no longer listed here.

1. **The NAVI and SYST combos can't distinguish left vs. right `SPC`.**
   Vial matches combos by keycode, not physical position, and both thumb
   `SPC` keys share the identical `LGUI_T(KC_SPACE)` binding. So "right-SPC
   + BSP → NAVI" also fires from the left SPC, and "V+SPC"/"M+SPC" → SYST
   will accept either thumb too. Fixing this would require distinct
   keycodes (or QMK-level combo logic) rather than a `.vil`-only change.

This one needs a firmware-level decision — it's not fixable purely in the
Vial JSON.
