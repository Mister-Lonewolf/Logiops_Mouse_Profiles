# Logiops Configuration for MX Anywhere 2 & MX Vertical

This repository contains a working configuration file for [Logiops (logid)](https://github.com/PixlOne/logiops), specifically tuned for:

- **Logitech MX Anywhere 2**
- **Logitech MX Vertical**

---

## 📂 Config File Location

Logiops looks for its configuration at:

```
/etc/logid.cfg
```

To use this config, copy `logid.cfg` from this repository into that location (with root permissions):

```bash
sudo cp logid.cfg /etc/logid.cfg
```

Then restart the Logiops service:

```bash
sudo systemctl restart logid
```

---

## ❗ Fixing Missing Service

If `systemctl status logiops` gives:

```
Unit logiops.service could not be found
```

Then the systemd service file wasn't installed or registered. You can create it manually:

### ➕ Create the Service File

```bash
sudo nano /etc/systemd/system/logiops.service
```

Paste this:

```
[Unit]
Description=Logitech HID++ userspace daemon
After=network.target

[Service]
ExecStart=/usr/bin/logid
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

> 🛠 Adjust `ExecStart` if `which logid` gives a different path.

Then enable and start it:

```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl enable --now logiops
```

Now Logiops will run on boot, and your MX Vertical’s top button should work consistently.

---

## 🖱 Device Features Overview
The following mappings are examples.

### Wireless Mobile Mouse MX Anywhere 2
- Default DPI: 1400
- Forward button:
  - Tap: Next page shortcut (Alt + Right Arrow)
  - Gesture Up/Down: Increase/Decrease DPI by 500
- Gesture button:
  - Tap: Open activities overview (Meta + A)
  - Swipe Left/Right: Switch virtual desktops (Ctrl + Alt + Left/Right)
  - Swipe Up/Down: Maximize/Minimize windows (Meta + Up/Down)

### MX Vertical Advanced Ergonomic Mouse
- Default DPI: 1800
- Forward button: Same as MX Anywhere 2
- Gesture button: Same mappings as MX Anywhere 2’s gesture button

---

For full button mapping details and code, see the [device-specific documentation](docs/).

---

## 🔧 Requirements

- Linux system with `systemd`
- `logid` daemon running (via Logiops)
- Appropriate udev permissions (see [Logiops repo](https://github.com/PixlOne/logiops#permissions) if needed)

---

## 📚 Credits

- This config is for use with [Logiops (logid)](https://github.com/PixlOne/logiops), an open-source user-space driver for Logitech devices.
- All credit for the Logiops project goes to [PixlOne](https://github.com/PixlOne).
- This repo contains only configuration data, **no source code from Logiops**.
- README formatting and structure by [ChatGPT (OpenAI)](https://openai.com/chatgpt)

---

## 🔒 License

This configuration is released under the MIT License. You are free to use, modify, and share it. Please credit this repo if it helps you.

---

## ✨ Contributions

Feel free to fork, modify, or submit improvements for different Logitech mice.
