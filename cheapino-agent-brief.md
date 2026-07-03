# Agent Brief — Cheapino v2 Keymap Alignment

## Mission

Fork `https://github.com/getreu/vial-config-musclememory-cheapino2` and update its
keymap to align with the rectified Totem ZMK layout described below, so both
keyboards can be used interchangeably. The Cheapino is wired (no Bluetooth) and
has 36 keys instead of the Totem's 38.

The sole file to modify is:
```
vial-config/vial-musclememory-config-cheapino.vil
```
This is a JSON file loaded into the **Vial GUI app** at runtime — it is not compiled
firmware. The Vial app writes it to the keyboard's EEPROM. Do not create or modify
any QMK C source files unless the existing `.vil` file cannot express a required
behaviour (see note on tap-dance below).

---

## Background: the Totem ZMK layout (source of truth)

The Totem is a 38-key split BLE keyboard running ZMK firmware.
Repository: `https://github.com/BelongaGezza/zmk-config-musclememory-totem`
Active keymap: `config/totem.keymap`

### Physical layout (38 keys)

```
         ┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
         │  0  │  1  │  2  │  3  │  4  │   │  5  │  6  │  7  │  8  │  9  │
         ├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
         │ 10  │ 11  │ 12  │ 13  │ 14  │   │ 15  │ 16  │ 17  │ 18  │ 19  │
    ┌────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼────┐
    │ 20 │ 21  │ 22  │ 23  │ 24  │ 25  │   │ 26  │ 27  │ 28  │ 29  │ 30  │ 31 │
    └────┴─────┴─────┴──┬──┴─────┴─────┘   └─────┴─────┴──┬──┴─────┴─────┴────┘
                        │ 32  │ 33  │ 34  │   │ 35  │ 36  │ 37  │
                        └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

Positions 20 and 31 are the outer pinky keys on the bottom row. **The Cheapino
omits these two keys.** All other positions are identical.

### Layer definitions (Totem)

**Layer 0 — BASE**

```
Q    W    E    R    T  │  Y    U    I    O    P
A    S    D    F    G  │  H    J    K    L    ;
▾LSFT▾RALT▾SYMB▾LCTL▾LALT│▾LALT▾RCTL▾SYMB▾RALT▾RSFT

[TAB  Z    X    C    V    B  │  N    M    ,    .    /  ENT]
[▾LSFT               ▾LGUI  │       ▾RGUI              ▾RSFT]
← pos 20/21-25 left row      │ pos 26-30/31 right row →

FN   ESC  SPC  │  SPC  BSP  CMP
sl   ▾MOU ▾GUI │  ▾GUI      ▾NPD
```

*Notation: `▾MOD` = hold-tap, hold activates MOD. `sl` = sticky layer.
`MOU`=MOUSE layer, `GUI`=⌘/⊞ modifier, `NPD`=NUMPAD layer double-tap.*

The two outer keys (pos 20 = TAB▾LSFT, pos 31 = ENT▾RSFT) exist on Totem but
not on Cheapino. Shift is already covered by `A`▾LSFT and `;`▾RSFT. TAB and ENT
are accessible on SYMB layer (see below). No substitution is required.

**Layer 1 — SYMB** (access: hold D or K; or toggle via ESC+BSP combo)

```
1    2    3    4    5  │  6    7    8    9    0
ESC  INS  DEL  TAB  BSP│  ←    ↓    ↑    →   ENT
▾SFT ▾RALT▾NPD▾CTL▾ALT │▾ALT  ▾CTL ▾NPD▾RALT▾SFT

[▽   `    -    =    [    ]  │  \    '    ,    .    /   ▽]
[         ▾GUI            │       ▾GUI                ]

▽   BASE  ▽  │   ▽    ▽   BASE
```

*Arrow keys ←↓↑→ on H J K L (Vim-style), with same modifiers as home row.*

**Layer 2 — NPAD** (access: double-tap CMP to lock; exit via CMP or ESC thumb)

Left side is **fully transparent** — all keys fall through to BASE so home row
modifiers remain usable while entering numbers.

```
▽    ▽    ▽    ▽    ▽  │  -÷   7    8    9   0=
▽    ▽    ▽    ▽    ▽  │ NLCK  4   5▾SYMB 6  KPENT
[▽   ▽    ▽    ▽    ▽    ▽  │  +×   1    2    3   .,   ▽]

▽    ▽    ▽  │   ▽    ▽   BASE
```

*Tap-dance operators: tap once = primary, tap twice = secondary:
`-`/÷   `+`/×   `.`/`,`   `0`/`=`*

**Layer 3 — FUNC** (access: tap FN thumb key, sticky)

```
F1   F2   F3   F4   F5 │  F6   F7   F8   F9  F10
F11  F12  F13  F14  F15│  F16  F17  F18  F19  F20
▾SFT ▾RALT      ▾CTL▾ALT│▾ALT  ▾CTL      ▾RALT▾SFT
[▽   F21  F22  F23  F24  · │   ·  RGUI   ·    ·    ·   ▽]
[              ▾GUI        │                              ]

▽    ▽    ▽  │   ▽    ▽    ▽
```

**Layer 4 — NAVI** (access: pinch right-thumb SPC+BSP, sticky)

```
·    ·    ·    ·    · │ HOME  DEL  INS  END  BSP
ESC  INS  DEL  TAB  BSP│  ←    ↓    ↑    →   ENT
[▽    ·    ·    ·    ·    · │   ·  PGDN PGUP   ·    ·   ▽]

▽    ▽    ▽  │   ▽    ▽    ▽
```

**Layer 5 — MOUS** (access: hold ESC thumb)

```
·    ·    ·    ·    · │   ·    ·    ·    ·    ·
MB4 LCLK MCLK RCLK MB5│ MV←  MV↓  MV↑  MV→ LCLK
[▽    ·    ·    ·    ·    · │ SC←  SC↓  SC↑  SC→   ·   ▽]

▽    ▽    ▽  │   ▽    ▽    ▽
```

**Layer 6 — SYST** (access: hold V+SPC or M+SPC simultaneously)

On Totem this layer contains Bluetooth controls, reset, and media keys.
**On Cheapino, omit all Bluetooth bindings.** Retain:

```
·    ·    ·    ·   RST │ RST BRI↓ BRI↑  ·    ·
·    ·   USB*  ·    · │ MUTE VOL↓ VOL↑  ·    ·
[·    ·    ·    ·    ·    · │ PLAY PREV NEXT   ·    ·   ·]

▽    ▽    ▽  │   ▽    ▽    ▽
```

*`USB*` = output switch (relevant if board supports USB/BLE toggle; otherwise `·`).*
*RST = QK_RBT (soft reset) or QK_BOOT as appropriate.*

### Combos (Totem reference)

| Keys | Timeout | Action |
|------|---------|--------|
| Q+W+E+T | 100 ms | Bootloader |
| Y+I+O+P | 100 ms | Bootloader |
| ESC+BSP (pos 33+36) | 100 ms | Toggle SYMB |
| right-SPC+BSP (pos 35+36) | 50 ms | Sticky NAVI (OSL) |
| V+left-SPC (pos 24+34) | 100 ms | Momentary SYST |
| M+right-SPC (pos 27+35) | 100 ms | Momentary SYST |
| FN+CMP (pos 32+37) | 100 ms | Caps Lock |
| outer-TAB+outer-ENT (pos 20+31) | 100 ms | Caps Lock — **Cheapino: omit** (keys absent) |

The Caps Lock combo using the outer keys does not exist on Cheapino. The FN+CMP combo
(pos 32+37) is sufficient.

### Home row mod behaviour (Totem ZMK)

- `balanced` flavour hold-tap
- `tapping-term-ms = 280`
- `require-prior-idle-ms = 150` (hold does not fire if typed quickly after another key)
- `quick-tap-ms = 175` (double-tap repeats)
- `hold-trigger-on-release` — hold fires when the hold-tap key is **released**, not when
  the other key is first pressed
- Positional: left-hand HRM fires hold only when a right-hand key is involved, and
  vice versa

### Thumb cluster (Totem, post-rectification)

| Pos | Tap | Hold | Notes |
|-----|-----|------|-------|
| 32 | — | FUNC layer (sticky) | `sl 3` |
| 33 | ESC | MOUSE layer | `lt 5 ESC` |
| 34 | Space | GUI | `hml LGUI SPACE` — left thumb |
| 35 | Space | GUI | `hmr LGUI SPACE` — right thumb |
| 36 | Backspace | — | plain `kp BACKSPACE` — no layer activation |
| 37 | Compose/App | — | double-tap: toggle NPAD |

---

## The Cheapino v2

### Hardware differences from Totem

| Property | Totem | Cheapino v2 |
|----------|-------|-------------|
| Key count | 38 | 36 |
| Missing keys | — | Outer pinky keys on row 2 (Totem pos 20 and 31) |
| Connectivity | BLE split | USB wired split |
| Firmware | ZMK | QMK + Vial |
| Config format | Devicetree `.keymap` | Vial `.vil` JSON |

The Cheapino row 2 is therefore:

```
Z    X    C    V    B  │  N    M    ,    .    /
```

(no outer TAB or outer ENT keys)

### Existing Cheapino config

The upstream file `vial-config/vial-musclememory-config-cheapino.vil` already
implements a version of this muscle-memory layout. It has:
- 12 layer slots defined
- 7 active tap-dance entries
- 8 active combos
- Base layer with home row mods
- Numpad, navigation, function, mouse, media layers

**The existing config reflects the layout as it was before the Totem rectifications
described in this brief.** Your task is to bring the Cheapino config into alignment
with the rectified Totem layout.

---

## What to change

### 1. Thumb cluster alignment

Update thumb keys to mirror the rectified Totem:

| Thumb position | Current Cheapino | Target |
|----------------|-----------------|--------|
| Left-inner (SPC) | likely SPC▾GUI or similar | SPC▾GUI (confirm direction: hold fires on RIGHT-hand key press) |
| Right-inner (SPC/ENT) | may produce ENT | **Change tap to SPC**, keep GUI hold |
| Right-middle (BSP) | may activate a layer on hold | **Remove any layer-hold from BSP** — plain Backspace only |
| Right-outer (CMP) | tap=App, double=NPAD toggle | keep as-is |

### 2. NAVI layer access

The Totem activates NAVI via a **combo**: right-SPC + BSP (50 ms timeout) → sticky
NAVI (OSL in QMK terms).

Remove any layer-activation from the BSP key itself. Add or update a combo:
- Keys: right-thumb SPC position + BSP position
- Timeout: 50 ms
- Action: `OSL(NAVI_LAYER)` (one-shot layer)

Verify this combo does not conflict with the ESC+BSP → toggle-SYMB combo.

### 3. Numpad layer — left side transparent

Make all left-half positions in the NPAD layer `KC_TRNS`. This allows home row
modifiers to pass through from BASE while the numpad is active.

### 4. Numpad tap-dance operators

The four arithmetic keys in the NPAD layer should use tap-dance:

| Key position | Single tap | Double tap |
|-------------|-----------|-----------|
| `-` (right col 0, row 0) | `KC_KP_MINUS` | `KC_KP_SLASH` |
| `0` (right col 4, row 0) | `KC_KP_0` | `KC_KP_EQUAL` |
| `+` (right col 0, row 2) | `KC_KP_PLUS` | `KC_KP_ASTERISK` |
| `.` (right col 4, row 2) | `KC_KP_DOT` | `KC_KP_COMMA` |

Check whether the existing `.vil` file's tap-dance slots can accommodate four
additional entries, or whether some existing entries can be reused/repurposed.
Vial supports up to 32 tap-dance entries; tapping-term of 200 ms is appropriate.

### 5. SYST layer — remove Bluetooth bindings

Replace any BT_SEL, BT_CLR, OUT_USB, OUT_BLE keycodes with `KC_TRNS` or `KC_NO`.
Retain: reset, media (play/pause, prev, next, volume, brightness).

### 6. Remove the outer-key Caps Lock combo

The combo that uses Totem positions 20+31 (outer TAB + outer ENT) for Caps Lock
does not apply to the Cheapino. Remove or replace it with an alternative if desired
(e.g. a triple-tap or an unused combo position).

### 7. Verify remaining combos

Confirm that all surviving combos reference valid Cheapino key positions (accounting
for the 36-key layout). Cheapino positions are Totem positions 0–19, 21–30, 32–37
(positions 20 and 31 are absent).

---

## Vial `.vil` file format notes

The `.vil` file is JSON with these relevant top-level keys:

```json
{
  "version": 1,
  "uid": "...",
  "layout": [                      // array of layers; each layer is a flat array of QMK keycodes
    ["KC_Q", "KC_W", ...]          // layer 0
  ],
  "encoder_layout": [...],
  "tap_dance": [                   // tap-dance entries
    {
      "tap": "KC_KP_MINUS",
      "hold": "KC_NO",
      "double_tap": "KC_KP_SLASH",
      "tap_hold": "KC_NO",
      "tapping_term": 200
    }
  ],
  "combo": [                       // combo entries
    {
      "key1": 33,                  // key position index (0-based)
      "key2": 36,
      "key3": 65535,               // 65535 = unused slot
      "key4": 65535,
      "keycode": "OSL(4)"          // QMK keycode string
    }
  ],
  "macro": [...]
}
```

**Keycodes** use QMK string format: `KC_A`, `LSFT_T(KC_A)`, `LT(1, KC_D)`,
`OSL(4)`, `TO(0)`, `TG(1)`, `MO(1)`, `TD(0)` etc.

**Mod-tap** (home row mods): `LSFT_T(KC_A)`, `RALT_T(KC_S)`, `LT(1, KC_D)`,
`LCTL_T(KC_F)`, `LALT_T(KC_G)` etc.

**Hold behaviour** in QMK is controlled by per-key or global settings in the
QMK firmware (not in the `.vil` file). The existing Cheapino QMK firmware
presumably already has `PERMISSIVE_HOLD` or `HOLD_ON_OTHER_KEY_PRESS` configured
appropriately. **Do not assume you need to re-implement hold behaviour in the `.vil`
— only the keycode assignments change.**

**One-shot layer** (sticky): `OSL(layer_number)`

**Layer position indices** in the `.vil` layout array: positions are listed
left-to-right, top-to-bottom, matching the Cheapino's physical key order.
Confirm the exact index mapping by cross-referencing the existing layer 0 keycodes
against the known QWERTY positions before editing other layers.

---

## QMK ↔ ZMK concept mapping

| ZMK concept | QMK / Vial equivalent |
|-------------|----------------------|
| `hml LSHIFT A` | `LSFT_T(KC_A)` |
| `hml RIGHT_ALT S` | `RALT_T(KC_S)` |
| `hml2 1 D` (layer-tap) | `LT(1, KC_D)` |
| `hml LCTRL F` | `LCTL_T(KC_F)` |
| `hml LEFT_ALT G` | `LALT_T(KC_G)` |
| `hmr LEFT_ALT H` | `LALT_T(KC_H)` |
| `hmr RCTRL J` | `RCTL_T(KC_J)` |
| `hmr2 1 K` | `LT(1, KC_K)` |
| `hmr RIGHT_ALT L` | `RALT_T(KC_L)` |
| `hmr RSHIFT ;` | `RSFT_T(KC_SCLN)` |
| `hml RGUI V` | `LGUI_T(KC_V)` |
| `hmr RGUI M` | `LGUI_T(KC_M)` |
| `hml LGUI SPACE` (left thumb) | `LGUI_T(KC_SPC)` |
| `hmr LGUI SPACE` (right thumb) | `LGUI_T(KC_SPC)` |
| `sl 3` (sticky FUNC) | `OSL(3)` |
| `lt 5 ESC` (MOUSE layer tap) | `LT(5, KC_ESC)` |
| `kp BACKSPACE` | `KC_BSPC` |
| `tog SYMB` | `TG(1)` |
| `to 0` | `TO(0)` |
| `mo SYST` | `MO(6)` |
| `&sl NAVI` (sticky, from combo) | `OSL(4)` |
| `&bootloader` | `QK_BOOT` |
| `&sys_reset` | `QK_RBT` |
| `&trans` | `KC_TRNS` |
| `&none` | `KC_NO` |
| tap-dance behavior | `TD(n)` referencing tap_dance array entry n |
| `mkp LCLK` | `KC_MS_BTN1` |
| `mkp RCLK` | `KC_MS_BTN2` |
| `mkp MCLK` | `KC_MS_BTN3` |
| `mkp MB4` | `KC_MS_BTN4` |
| `mkp MB5` | `KC_MS_BTN5` |
| `mmv MOVE_LEFT/RIGHT/UP/DOWN` | `KC_MS_LEFT/RIGHT/UP/DOWN` |
| `msc SCRL_LEFT/RIGHT/UP/DOWN` | `KC_MS_WH_LEFT/RIGHT/UP/DOWN` |
| `kp C_VOL_UP/DN` | `KC_VOLU / KC_VOLD` |
| `kp C_MUTE` | `KC_MUTE` |
| `kp K_PLAY_PAUSE` | `KC_MPLY` |
| `kp K_PREV / C_NEXT` | `KC_MPRV / KC_MNXT` |
| `kp C_BRIGHTNESS_INC/DEC` | `KC_BRIU / KC_BRID` |
| `kp K_APP` (Compose) | `KC_APP` |
| `kp KP_NUMLOCK` | `KC_NUM` |
| `kp KP_ENTER` | `KC_KP_ENTER` |

---

## Deliverable

A single updated file:
```
vial-config/vial-musclememory-config-cheapino.vil
```

The file must be valid JSON that Vial can load without error. After loading, the
keymap should match the Totem layout described above, adjusted for 36 keys and
wired-only operation.

Do not modify `flake.nix`, `flake.lock`, `README.md`, or any other file unless
the README requires updating to reflect changed layer behaviour.
