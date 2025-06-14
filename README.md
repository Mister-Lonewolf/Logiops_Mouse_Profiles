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

## 🖱 Features

This config includes custom button mappings and sensitivity settings tailored for both devices. Example features may include:

- Horizontal scroll on side buttons
- Button remapping (e.g., gesture button → middle click)
- Custom DPI levels
- Per-device behavior customization

Refer to the `logid.cfg` for full details and modify as needed.

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
