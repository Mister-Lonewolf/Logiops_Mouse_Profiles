# MX Vertical Advanced — Button Mapping Overview

## DPI Setting
- Default DPI: **1800**

## Button CID 0x56 (Forward Button)

| Gesture Direction | Trigger Mode | Action Type     | Effect                                      |
|-------------------|--------------|-----------------|---------------------------------------------|
| None              | OnRelease    | Keypress       | Sends `Alt + Right Arrow` (Next page)       |
| Up                | OnRelease    | ChangeDPI      | Increase DPI by 500                          |
| Down              | OnRelease    | ChangeDPI      | Decrease DPI by 500                          |

## Button CID 0xfd (Gesture Button)

| Gesture Direction | Trigger Mode | Action Type     | Effect                                                        |
|-------------------|--------------|-----------------|---------------------------------------------------------------|
| None              | OnRelease    | Keypress        | Sends `Meta + A` (Open activities overview)                  |
| Right             | OnRelease    | Keypress        | Sends `Ctrl + Alt + Right Arrow` (Switch to next virtual desktop) |
| Left              | OnRelease    | Keypress        | Sends `Ctrl + Alt + Left Arrow` (Switch to previous virtual desktop) |
| Up                | OnRelease    | Keypress        | Sends `Meta + Up Arrow` (Maximize window)                     |
| Down              | OnRelease    | Keypress        | Sends `Meta + Down Arrow` (Minimize window)                   |

---

# Wireless Mobile Mouse MX Vertical Configurations Overview

This mouse supports following configuration files:

| Config Name    | Description                  | Link                               |
|----------------|------------------------------|----------------------------------|
| default        | Balanced default mapping      | [default.cfg](../devices/mx_vertical/default.cfg) |

Refer to the linked files for button mappings and DPI settings.