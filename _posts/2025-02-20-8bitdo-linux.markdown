---
layout: single
title: "8BitDo Ultimate 2C Wireless Controller in Linux"
date: 2025-01-15 22:04:48 +0800
categories: ["8bitdo", "linux", "udev", "controller", "joystick"]
---

Recently, I want to buy a joystick that support Linux, checked DualSense controller, but it's very expensive, well played s0ny.

So there is a cheaper controller which supports Linux, 8BitDo. It's a China company, they sell game controller, keyboard and accessories.

I picked the latest model, `8BitDo Ultimate 2C Wireless Controller`, support wireless 2.4G, bluetooth, or wired connection.

![Image](/assets/image/2025-02-20-8bitdo-01.webp)

![Image](/assets/image/2025-02-20-8bitdo-02.webp)

![Image](/assets/image/2025-02-20-8bitdo-03.webp)

I plugged in the 2.4G usb dongle, it just works out of the box. As per commit message in Linux kernel `v6.12`, somebody made a pull request to support `8BitDo Ultimate 2C Wireless Controller`, so if your Linux kernel is `v6.12` or later, you don't need to add udev rules manually. (Please refer to this [GitHub Gist][8bitdo-linux-gist] if your kernel version is too low)


[linux-kernel-v6.12]: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f9e4825524aaf28af6b2097776616f27c31d6847
[8bitdo-linux-gist]:  https://gist.github.com/ammuench/0dcf14faf4e3b000020992612a2711e2
