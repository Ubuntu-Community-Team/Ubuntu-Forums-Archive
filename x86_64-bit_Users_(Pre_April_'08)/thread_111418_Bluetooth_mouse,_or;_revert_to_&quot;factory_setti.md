---
title: "Bluetooth mouse, or; revert to &quot;factory settings&quot;"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sunnan on 2006-01-02
When I installed Ubuntu 5.10 on my computer (an iBook) a couple of months ago, it immediately found my bluetooth mouse and it worked fine. (A welcome change from a couple of years ago where I had to mess around with daemons and modules myself.)

But something must've happened, maybe I uninstalled a package or something, because it no longer works. (Among other things, the little icon in the top panel is gone, and the cursor doesn't move when I move the mouse.) How do I get the  bluetooth mouse working again simply?

Sure, I could go back and re-read all the bluez-documentation and make awkward little scripts all over the place, but it seems like a bit of a waste when it worked so simply and smoothly automagically when the installation was "fresh".

I did try some messing about with sudo hidd and it found the mouse's address but couldn't connect. This was only a brief try since I want to do it the Gnome/Ubuntu way.

(As a side topic, I often find it hard to fix things like this on Ubuntu. I had a similar problem where the nautilus/hal/pmount-mounting of a removable USB-device had some hangup or something, and I couldn't find a way to fix it other than rebooting. If I had done the mounting the "old, geeky way" with fstab/mtab and so on, I probably could've fixed the error, too. But I don't really know how Ubuntu is connected to the hardware, the OS has an additional layer of mystery that I haven't grokked yet. Is there a "welcome to the new world" guide available somewhere for us old fogeys that used to spend sunday evenings reading HOWTOs, and want to understand Ubuntu enough to fix it when we break it?)

---

### Post by hentaidan on 2006-01-02
Have you any other blue tooth devices to try?

When did it stop working? I know, on my iBook G4 at least, there is a bug with bluetooth which means I have to "sudo hid2hci" to get it to work after each boot, otherwise I get "Device not found" from the bluetooth manager.

---

### Post by Sunnan on 2006-01-02
No, I only got the mouse.
I guess something happened with the packages, I de-installed Evince because I wanted to run the developement version of Evince, I was interested in that programs code and some metapackages got uninstalled and so on.

I think metacity got uninstalled at some point, and so on. It's all back now (except for the BT), but it was a mess there for a while.
Still need it, because I don't have another mouse.

---

