# Logiops Configurations

This repository contains a working configuration file for [Logiops (logid)](https://github.com/PixlOne/logiops), specifically tuned for:

- **Logitech MX Anywhere 2**
- **Logitech MX Vertical**
- **Logitech MX Master**

## Table of Contents

- [Device Features Overview](#device-features-overview)
- [Config File Location](#config-file-location)
- [Adjust config file](#adjust-config-file)
- [Autoscroll](#autoscroll)
- [Fixing Missing Logiops Service](#fixing-missing-service)
- [Requirements](#requirements)
- [Credits](#credits)
- [License](#license)
- [Contributions](#contributions)

## Device Features Overview

| Device                         | Documentation Link                  |
|-------------------------------|-----------------------------------|
| MX Anywhere 2 | [docs/mx_anywhere_2.md](docs/mx_anywhere_2.md) |
| MX Vertical | [docs/mx_vertical.md](docs/mx_vertical.md)    |
| MX Master	|	[docs/mx_master.md](docs/mx_master.md) |


## Config File Location

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

## Adjust config file
Ofcourse, you can adjust these files to fit your own needs. However, to do this, you will need to experiment a lot and lookup a lot of information in the **logid** repository and in general on the world wide web. One hint i can give you is to use the logid command to check your button id's and the exact name of your mouse.

By using the following command you get a nice overview of the devices and buttons logid could find. Be sure to check the **logid** repository! (you can find the link in the [Credits](#credits)).

```bash
sudo logid -v
```

Ps: For this command you need to be sure the logid service is stopped, otherwise your devices will not be recognised. You can stop it with the next command:
```bash
sudo systemctl stop logid
```

## Autoscroll
Windows offers a OS wide feature to autoscroll at a certain speed by clicking your vertical mouse wheel and draging the mouse. Sadly, some Linux distros, like Ubuntu 24.04 where most of these configs are designed on, does not support this out of the box. You can solve this easely with some scripts on X11. However, on Wayland it's a different story.

Thats why I would recommend to do this at a browser level, since by my knowledge it is mainly used there. There are different browsers to use and each has their own way to achieve this to a certain degree.

### Brave
For the Brave browser it is as simple as setting a flag in it's settings. It's as simple as pasting the *flag location* (which you can find in the table below) in your adress bar and enabeling the marked entry.

|                          Browser version                            |              Flag location              |
| ------------------------------------------------------------------- | --------------------------------------- |
| Brave 1.88.138 (Official Build) (64-bit) - Chromium: 146.0.7680.178 | brave://flags/#middle-button-autoscroll |

## Fixing Missing Service

If `systemctl status logiops` gives:

```
Unit logiops.service could not be found
```

Then the systemd service file wasn't installed or registered. You can create it manually:

### Create the Service File

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

> Adjust `ExecStart` if `which logid` gives a different path.

Then enable and start it:

```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl enable --now logiops
```

Now Logiops will run on boot, and your MX profile should work consistently.

## Requirements

- Linux system with `systemd`
- `logid` daemon running (via Logiops)
- Appropriate udev permissions (see [Logiops repo](https://github.com/PixlOne/logiops#permissions) if needed)

## Credits

- This config is for use with [Logiops (logid)](https://github.com/PixlOne/logiops), an open-source user-space driver for Logitech devices.
- All credit for the Logiops project goes to [PixlOne](https://github.com/PixlOne).
- This repo contains only configuration data, **no source code from Logiops**.
- README formatting and structure by [ChatGPT (OpenAI)](https://openai.com/chatgpt)

## License

This configuration is released under the MIT License. You are free to use, modify, and share it. Please credit this repo if it helps you.

## Contributions

Feel free to fork, modify, or submit improvements for different Logitech mice.
