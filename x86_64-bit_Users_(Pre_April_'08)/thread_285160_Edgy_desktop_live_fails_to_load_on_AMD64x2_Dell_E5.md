---
title: "Edgy desktop live fails to load on AMD64x2 Dell E521"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by dramage on 2006-10-26
Hi guys,

I'm trying to install a shiny new Ubuntu Edgy desktop AMD64 on a shiny new Dell E521.  The boot process hangs (for regular boot, safe graphical mode boot, and even for the media check).

Booting without quiet and splash gives me the following lines before hanging, suggesting an IRQ conflict on the SATA hard drive and SATA cd-rom drive:

  ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 209
  ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xE008 irq 209

Workaround: i added "noapic" as a boot option and got the installation rolling.  I think I'll probably need to add that option to grub.conf once I'm installed, too.  I don't really understand the implications of noapic - am I shooting myself in the foot?

For instance, the USB mouse and keyboard seem to die randomly in the live cd once booted (gotta unplug and replug) - any chance this is related to the noapic?  I'd be surprised, but you never know ...

dramage

---

### Post by pregoeater on 2006-11-02
use a usb hub....and if you got the monitor with the system with a built in usb hub use that. worked for me

---

