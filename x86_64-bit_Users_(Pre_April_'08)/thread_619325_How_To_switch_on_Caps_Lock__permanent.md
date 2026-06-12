---
title: "How To switch on Caps Lock  permanent"
date: 2007-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by harvey186 on 2007-11-21
Hi toegther,

where can I permanent switch the Num lock key on (Kubuntu Gutsy 64bit) ? 

Thanks for help, Harvey

---

### Post by chippy99 on 2007-11-21
There is usually an option in your bios settings to do this.

---

### Post by harvey186 on 2007-11-21
> **chippy99 said:**
> There is usually an option in your bios settings to do this.

Yes, there is one and it is enabled, 
I'm so sorry, I don't mean Caps Lock, I mean the num lock key :(

Harvey

---

### Post by Em-Buntu on 2007-11-21
Depending on your motherboard, this too should be a BIOS option.

---

### Post by david_2001 on 2007-11-21
In addition to the possible bios setting, there's kcontrol (or should be - I don't use kubuntu and don't have a full KDE desktop installed).  Anyway, run kcontrol and goto Peripherals | Keyboard and look for the NumLock on KDE Startup setting.  The gconf-editor alternative for Gnome is desktop | gnome | peripherals | keyboard | host-your_hostname | 0 | numlock_on.

---

### Post by harvey186 on 2007-11-21
> **david_2001 said:**
> In addition to the possible bios setting, there's kcontrol (or should be - I don't use kubuntu and don't have a full KDE desktop installed).  Anyway, run kcontrol and goto Peripherals | Keyboard and look for the NumLock on KDE Startup setting.  The gconf-editor alternative for Gnome is desktop | gnome | peripherals | keyboard | host-your_hostname | 0 | numlock_on.

Yepp, in the kcontrol I can/have now activated the nun lock at startup.

Thanks, Harvey

---

