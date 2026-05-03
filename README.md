<div align="center">
  <h1>Sonata</h1>
  <p>
    <img src="https://img.shields.io/badge/version-0.5.1-blue?style=flat-square" alt="Version">
    <img src="https://img.shields.io/badge/release-initial-green?style=flat-square" alt="Initial release">
    <img src="https://img.shields.io/badge/keys-28-blue?style=flat-square" alt="Keys">
    <img src="https://img.shields.io/badge/base-Colemak--DH-purple?style=flat-square" alt="Base">
    <img src="https://img.shields.io/badge/inherits%20from-Cadence%20v1.11.1-brightgreen?style=flat-square" alt="Inherits from Cadence">
    <img src="https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square" alt="License">
  </p>
</div>

---

> *Sonata (n.): a complete musical form — theme, development, resolution.*

**Sonata** is a 28-key split keyboard layout. It is the minimalist variant of [Cadence](https://github.com/one7two99/cadence), sharing Cadence's complete layer architecture but with a different Base Layer alpha grid optimised for the smaller 4-column-per-side keyboard.

> *28 keys. Cadence's layer architecture, half a column lighter.*

---

## ⚠ Project status

**v0.5.0 was the initial public release of the Sonata specification** (current version: v0.5.1, a documentation update). This repository defines the Sonata Base Layer and documents how all other layers are inherited from [Cadence v1.11.1](https://github.com/one7two99/cadence).

Sonata currently has **no dedicated Vial configuration**. It is a layout specification, not a flash-ready build. The next milestone, **v1.0**, will be tagged when a dedicated Vial configuration exists. From that point on, documentation will track two version numbers: the Sonata version (Base Layer state) and the inherited Cadence version.

---

## ✦ What Sonata is, and how it relates to Cadence

Sonata is built around two strict ergonomic constraints:

1. **No lateral inward movement of the index fingers** — drop the inner column entirely.
2. **Thumbs only move outward, never inward** — keyboard layouts often expect the thumb to push laterally toward the keyboard centre, which is biomechanically awkward.

Both constraints proved viable on a 28-key layout, and the design lessons that emerged carried over into Cadence:

- **The L1 Overflow + International concept** — the design pattern of putting low-frequency letters (X, Q) plus international characters (umlauts, ß, €) on a single thumb-activated layer originated in Sonata's overflow-letter problem. Cadence adopted it.
- **The L12 Symbol layer redesign** — Sonata's tighter constraints (4 columns instead of 5) forced a frequency-and-position-quality based symbol layout that Cadence then adopted. The L12 specification is shared between the two projects.
- **Validation of the thumb-outward-only principle** — Cadence's thumb-trigger conventions (`Spc tap+hold` for Mouse, `Tab-hold` for Overflow) honour Sonata's outward-only thumb constraint.

In other words: **Sonata supplied the design ideas, Cadence's iterative work refined them into a production layout, and Sonata now inherits the refined result back.** A clean cycle.

---

## ✦ The Family

| Project | Keys | Hardware | Status |
|---|---|---|---|
| **[Cadence](https://github.com/one7two99/cadence)** | 34 | Ferris Sweep | Daily driver, actively maintained |
| **Sonata** *(this repo)* | 28 | dedicated 28-key, or Sweep with unprogrammed inner column | Specification, initial release |
| [Coda](https://github.com/one7two99/coda) | 22 | dedicated 22-key | Concept-stage parallel exploration (independent design, not Cadence-aligned) |
| [Cadenza](https://github.com/one7two99/cadenza) *(archived)* | 36 | Corne Choc | Predecessor, archived |

Cadence and Sonata share the same layer architecture and trigger philosophy. Coda is a separate design exploration with its own layer system. Cadenza is the predecessor that started the family.

---

## ✦ The Sonata Base Layer

```
LEFT                         RIGHT
┌───┬───┬───┬───┐           ┌───┬───┬───┬───┐
│ Z │ W │ G │ M │           │ L │ Y │ P │ J │   ← top
├───┼───┼───┼───┤           ├───┼───┼───┼───┤
│ A │ R │ S │ T │           │ N │ E │ I │ O │   ← home (HRM)
├───┼───┼───┼───┤           ├───┼───┼───┼───┤
│ V │ C │ U │ D │           │ H │ F │ B │ K │   ← bot
└───┴───┴───┴───┘           └───┴───┴───┴───┘
              ┌───┬───┐ ┌───┬───┐
              │Spc│Tab│ │Ent│Bsp│   ← thumbs
              └───┴───┘ └───┴───┘
```

**Home Row Mods** (tap = letter, hold = modifier):

| Position | Tap | Hold | Term |
|---|---|---|---|
| L pinky home | A | Meta / Cmd / GUI | 250 ms |
| L ring home | R | Alt / Option | 200 ms |
| L mid home | S | Ctrl | 200 ms |
| L idx home | T | Shift | 200 ms |
| R idx home | N | Shift | 200 ms |
| R mid home | E | Ctrl | 200 ms |
| R ring home | I | AltGr | 200 ms |
| R pinky home | O | Meta / Cmd / GUI | 250 ms |

Identical to Cadence v1.11.1 — bilateral Meta+Alt is cross-hand, avoiding same-hand HRM conflicts.

**Overflow letters X and Q** are not on the Base Layer. They are reachable on L1 Overflow + International at the same positions as in Cadence: X on R_ring_home (I-position), Q on R_mid_home (E-position).

The alpha grid was optimised for SFB rate under the no-inner-column constraint. It is **not derivable by removing letters from Cadence's grid** — several letters are repositioned to columns they don't occupy in Cadence.

---

## ✦ Layer triggers — same physical positions as Cadence

The key design decision: layer triggers occupy the **same physical positions as in Cadence v1.11.1** — same finger, same row — even though the letter on that position differs. A user proficient with Cadence can move to Sonata hardware without retraining the layer-trigger fingers.

### Thumb triggers (1:1 identical to Cadence)

| Thumb | Tap | Hold | Tap+Hold |
|---|---|---|---|
| Spc | Space | → L4 Navigation | → L5 Mouse |
| Tab | Tab | → L1 Overflow + International | — |
| Ent | Enter | → L3 Numbers | — |
| Bsp | Backspace | → L12 Symbols | — |

### Bilateral letter triggers — same positions, different letters

| Layer | Position | Sonata letters | Cadence letters at same positions |
|---|---|---|---|
| L6 Fn + Media | mid top | Hold **G** or **Y** | F + U |
| L7 Code & CLI | ring top | Hold **W** or **P** | W + Y |
| L8 Tiling WM | pinky bot | Hold **V** or **K** | Z + / |
| L9 Brackets | ring bot | Hold **C** or **B** | X + . |
| L11 Firmware Control | pinky top | Long-hold (500 ms) **Z** or **J** | Q + ' |

The trigger position is what matters for muscle memory, not the letter on the key. The same finger doing the same hold motion activates the same layer on either keyboard.

---

## ✦ Layer reference — see Cadence

All layer contents (what each key produces while a layer is active) are inherited 1:1 from Cadence v1.11.1. This README does not duplicate that information.

**For the complete layer reference, see [Cadence's documentation](https://github.com/one7two99/cadence/blob/main/docs/index.html):**

| Layer | Purpose |
|---|---|
| L1 Overflow + International | Umlauts (ä/ö/ü), ß, €, dead-key fallback, X and Q overflow letters |
| L3 Numbers | Numpad layout |
| L4 Navigation | Arrows, word-skip, page navigation |
| L5 Mouse | Pointer, scroll, mouse buttons |
| L6 Fn + Media | F1–F12 plus media controls |
| L7 Code & CLI | Shell operators, path navigation, expansion macros |
| L8 Tiling WM | Workspaces 1–10, focus, window movement |
| L9 Brackets | Bilateral mirror of bracket pairs as Tap Dance, App/Menu on outer thumbs |
| L10 Clipboard | Present in firmware, no trigger by user choice |
| L11 Firmware Control | `QK_BOOT` and `QK_REBOOT`, safety-gated by long-hold |
| L12 Symbols | Frequency-and-strength symbol layout, specification shared with Cadence |

Cadence's layer contents are designed to leave the inner column (G/M/B/V/J/K positions in Cadence) free of layer content. This is what makes them directly compatible with Sonata's 28-key grid where the inner column doesn't exist physically.

---

## ✦ Hardware

Sonata can run on two hardware options:

### Option 1 — Dedicated 28-key split

A custom PCB with exactly 28 keys: 4 finger columns × 3 rows × 2 sides + 2 thumbs × 2 sides. No commercial off-the-shelf 28-key board exists with this exact geometry; this would be a custom build.

### Option 2 — Ferris Sweep with unprogrammed inner column

The Ferris Sweep has 34 keys (5 columns per side + 2 thumbs per side). Sonata can run on Sweep hardware by leaving the inner column physical keys (5th column each side: G, M, B, V, J, K positions on Cadence) **unprogrammed** — they exist physically but carry `KC_NO` and produce no output. The remaining 28 keys behave identically to a dedicated 28-key build.

This is the practical option for trying Sonata without commissioning custom hardware.

---

## ✦ Why Sonata exists alongside Cadence

If Cadence is the daily driver, what's the point of Sonata?

- **Design-research artifact.** Sonata is the proof that the constraints (no inner column, thumbs outward only) work in practice. Cadence is the productive realisation; Sonata is the source experiment.
- **Migration path for minimalists.** Users who reach Cadence and want even less hardware have a documented path: same layers, same trigger fingers, smaller alpha grid.
- **Cross-hardware muscle memory.** A user can in principle keep Cadence at one workstation and Sonata at another — same layer triggers, same thumb behaviour, only the base alpha differs.

Sonata is not a competitor to Cadence. It's the smaller variant of the same design family.

---

## ✦ Documentation

| Document | Description |
|---|---|
| **[docs/index.html](docs/index.html)** | Sonata Base Layer visualisation and design rationale, with links to Cadence for layer contents |
| **[sonata-spec.json](sonata-spec.json)** | Single source of truth for the Sonata Base Layer — alpha grid, HRM, layer triggers, inheritance from Cadence |

For all non-Base layer information, refer to **[Cadence's documentation](https://github.com/one7two99/cadence)**.

---

## ✦ Versioning

The current release is **v0.5.1**. Sonata uses a `0.x` series during the specification phase. The next major milestone is **v1.0**, tagged when a dedicated Vial configuration exists.

### Versioning policy

| Change type | Bump | Example |
|---|---|---|
| Documentation update (text, diagrams, fixes) | Patch | v0.5.0 → v0.5.1 |
| Configuration change (Base Layer, triggers, HRM) | Minor | v0.5.0 → v0.6.0 |
| Dedicated Vial configuration available | Major | v0.x.y → v1.0.0 |

**v0.5.0** was the initial public release. **v0.5.1** (this version) is a documentation update — the Base Layer keyboard visualisation in `index.html` now correctly places the thumb keys (Spc/Tab on the left, Ent/Bsp on the right) below the index columns, matching the physical Ferris Sweep geometry.

From v1.0 onward, documentation will reference two version numbers: the Sonata version (Base Layer state) and the inherited Cadence version (whose layer contents Sonata adopts).

---

## ✦ License

Designed by **one7two99** · [MIT](LICENSE) · 2026

> *Companion to [Cadence](https://github.com/one7two99/cadence) · Based on [Colemak-DH](https://colemakmods.github.io/mod-dh/) by stevep99*

> *28 keys. Cadence's layer architecture, half a column lighter.*
