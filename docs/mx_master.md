# MX Master — Button Mapping Overview

## Table of Contents

- [Default config](#Default-Config)
- [All configurations](#Wireless-Mouse-MX-Master-Configurations-Overview)

## Default Config

### Smartshift
- on: false
- threshold: 100

### Hirescroll
- hires: true
- invert: false
- target: false

### DPI Setting
- Default DPI: **3500**

### Button CID 0xc4 (Button above top scroll wheel)
- action type = ToggelSmartShift

### Button CID 0xfd (Gesture Button)

| Gesture Direction | Trigger Mode | Action Type     | Effect                                                        |
|-------------------|--------------|-----------------|---------------------------------------------------------------|
| None              | OnRelease    | Keypress        | Sends `Meta + A` (Open activities overview)                  |
| Right             | OnRelease    | Keypress        | **NOT SUPPORTED!!!!** Sends `Ctrl + Alt + Right Arrow` (Switch to next virtual desktop) |
| Left              | OnRelease    | Keypress        | **NOT SUPPORTED!!!!** Sends `Ctrl + Alt + Left Arrow` (Switch to previous virtual desktop) |
| Up                | OnRelease    | Keypress        | **NOT SUPPORTED!!!!** Sends `Meta + Up Arrow` (Maximize window)                     |
| Down              | OnRelease    | Keypress        | **NOT SUPPORTED!!!!** Sends `Meta + Down Arrow` (Minimize window)                   |

---

# Wireless Mouse MX Master Configurations Overview

This mouse supports following configuration files:

| Config Name    | Description                  | Link                               |
|----------------|------------------------------|----------------------------------|
| default        | Balanced default mapping      | [default.cfg](../devices/mx_master/default.cfg) |

Refer to the linked files for button mappings and DPI settings.
