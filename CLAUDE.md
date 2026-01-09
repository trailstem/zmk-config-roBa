# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ZMK firmware configuration for "roBa" - a split keyboard using Seeeduino XIAO BLE with PMW3610 trackball sensor.

## Build Process

Firmware is built via GitHub Actions. Push to the repository triggers automatic build.
- Build artifacts (UF2 files) are available in GitHub Actions
- No local build commands required

## Architecture

```
boards/shields/roBa/
├── roBa.dtsi          # Hardware definition (matrix, physical layout, sensors)
├── roBa_L.overlay     # Left half overlay
├── roBa_L.conf        # Left half config
├── roBa_R.overlay     # Right half overlay (includes trackball/SPI config)
├── roBa_R.conf        # Right half config (trackball settings, ZMK Studio)

config/
├── roBa.keymap        # Keymap definition (layers, combos, behaviors)
├── roBa.json          # Physical layout for ZMK Studio
├── west.yml           # Zephyr manifest (ZMK + PMW3610 driver)
```

## Key Configuration Files

- **roBa_R.conf**: Trackball settings (CPI, scroll, polling rate) - these cannot be changed via ZMK Studio GUI
- **roBa.keymap**: Layers, combos, custom behaviors like `&mt` and `lt_to_layer_0`
- **FEATURE.md**: Documents non-GUI settings that require firmware rebuild

## Important Rule

When modifying settings that cannot be changed via ZMK Studio GUI (e.g., tapping-term-ms, CPI, polling rate), always document the changes in FEATURE.md as a bulleted list.

## External Dependencies

- ZMK firmware: `zmkfirmware/zmk` (v0.3-branch)
- Trackball driver: `kumamuk-git/zmk-pmw3610-driver`

## Layers

0. Default (QWERTY)
1. NUM (numbers/symbols)
2. FUNCTION (F1-F12)
3. ARROW (navigation)
4. MOUSE (auto-activated by trackball)
5. SCROLL (trackball scroll mode)
6. Bluetooth settings
