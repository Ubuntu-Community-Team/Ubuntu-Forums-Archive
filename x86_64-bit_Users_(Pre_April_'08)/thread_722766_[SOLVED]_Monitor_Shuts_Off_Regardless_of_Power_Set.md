---
title: "[SOLVED] Monitor Shuts Off Regardless of Power Settings"
date: 2008-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by GMaq on 2008-03-12
Hello,

I'm running WinXP/Gutsy 64bit,onboard ATI Xpress 1250 with fglrx driver. XP side doesn't have this issue

Problem:

Monitor shuts down at 10 min intervals regardless of power settings (set at Never)

Have tried the following:

The obvious Power Management Settings
Running sudo gconf-editor and messing with gnome-power-manager settings and rebooting
Commenting out DPMS in xorg.conf and rebooting
Adding a timeout value to xorg.conf & rebooting
Disabling ACPI in bios
Disabling S1 and S3 in bios
Checking monitor for any sleep mode (none found)

This system is an Audio/Video Workstation and I don't want anything to do with shutdowns and screensavers.

BTW Screensavers don't work either even if the value is set as low as possible...Related Issue?

I'm getting very frustrated with this issue, Considering a different distro

Help, Time and Expertise greatly appreciated. TIA!

---

### Post by GMaq on 2008-03-15
BUMP!

C'mon,:( nobody else has this issue?

---

### Post by GMaq on 2008-03-19
Hello, Is this thing on?

Posting this solution in case anyone else has this issue.

I got it working, In my case I wanted the monitor stay on with the ability for a screensaver if wanted.

First I queried my x settings:

```
pcuser@ubuntu:~$ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfffef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /home/pcuser/.gnome2/share/cursor-fonts,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/,/home/pcuser/.gnome2/share/fonts
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Display is not capable of DPMS
pcuser@ubuntu:~$ 


```

This told me my monitor doesn't support DPMS, which was the problem, so I edited my /etc/X11/xorg.conf file like this:

Section "Monitor"
	Identifier	"MICRON 700Ex"
	Option		"DPMS" "false"

And also added this section to my xorg.conf:

       # To prevent Blank Screen from popping up every 10 minutes
        # when xgl is run as a session on display :1,
        # when all the power management settings
        # you normally find only concerns display :0

Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
EndSection

Now my monitor stays on, and the screensaver works when it is supposed to.

---

