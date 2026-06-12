---
title: "keyboard works for login, but not in KDE"
date: 2009-06-11
forum: x86 64-bit Users
---

### Post by dh003i on 2009-06-11
Hi all,

I'm having a problem with my Northgate Omnikey Evolution keyboard. When my computer boots up, I can type in my password and login from the login manager. But then when KDE loads, and I open Firefox or other programs, the keyboard is non-responsive (nothing happens when I type). 

It an AT-keyboard, with an AT => PS/2 => USB conversion. 

What's going on here?

---

### Post by dh003i on 2009-06-12
FYI, I experience the same problems even if I plug the keyboard directly into the PS/2 port on the computer.

Also, I can use the keyboard fine when I login via terminal login.

---

### Post by dh003i on 2009-06-12
Relevant lines from **/var/log/Xorg.0.log**:

(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
.
.
.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
.
.
.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "wacom"
(II) UnloadModule: "wacom"
(II) UnloadModule: "wacom"
(II) UnloadModule: "wacom"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"[/code]

The Logitech USB Receiver is for my wireless Logitech hyper-scroll mouse.

---

### Post by dh003i on 2009-06-12
Also, I have the same problem with my MS Ergonomic keyboard. Plugged into the USB port, it works fine in the KDM login manager, but doesn't work when I'm logged into KDE -- except for the CTRL key (I can hold that down and zoom in on web-pages or images using the scroll wheel; but if I don't hold that down, the scroll wheel scrolls down).

---

### Post by dh003i on 2009-06-12
One more thing: This ONLY occurs in one of my accounts (but unfortunately the one setup with all my preferences, etc). If I login via my other account, I have no such issues and can use the keyboard. 

What is going on?

---

### Post by Artemis3 on 2009-06-14
Did you try turning off "slow/sticky/bounce keys" in Accessibility options?

---

### Post by dh003i on 2009-11-17
> **Artemis3 said:**
> Did you try turning off "slow/sticky/bounce keys" in Accessibility options?

What I ended up doing the first time around was deleting the ~/.kde directory; however, I think that made everyone really slow. So I copied all of the settings from another user's directory to the relevant user.

However, this problem came up again, and what I did is to uncheck the slow, sticky, bounce, and all accessibility options in "System Settings".

Why did the accessibility features make my keyboard stop responding?

---

