---
title: "USB storage devices cause PC to freeze"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by NickD-NLUG on 2009-11-01
If I plug any USB storage device into my Ubuntu 9.04 PC, the PC waits a few seconds and then I get a kernel panic ( caps lock and scroll lock lights flash, nothing responds ). I've tried three different USB keys and my IPod,

I've had a *quick* look... it being bedtime and all... and I can't see any obvious solutions online.  Seeing as the diagnostics process is pain, does anyone have any suggestions on what to try?  I've tried killing gvfsd, as that only seems to work some of the time, but that's not it.

If I manually load the "usb-storage" module with modprobe nothing untoward happens, until I plug in a device.

Entries in /var/log look normal for plugging in a USB device... any ideas what I should look for, or anything I should try disabling or modifying?

Thanks.

---

### Post by Arup on 2009-11-01
Try turning off USB Legacy mode in BIOS if its there and enabled.

---

### Post by NickD-NLUG on 2009-11-02
> **Arup said:**
> Try turning off USB Legacy mode in BIOS if its there and enabled.

Hi,

Thanks for this - I disabled "Legacy USB storage detect" in the BIOS, rebooted, but still have the same problem.

I do have a BIOS option for "USB onboard controller", which is OHCI, USB 1.1, but if I disable that, I disable my USB controller altogether.

What made you suggest disabling legacy support?  Is there a known bug I can read up on?

---

### Post by Arup on 2009-11-02
> **NickD-NLUG said:**
> Hi,

Thanks for this - I disabled "Legacy USB storage detect" in the BIOS, rebooted, but still have the same problem.

I do have a BIOS option for "USB onboard controller", which is OHCI, USB 1.1, but if I disable that, I disable my USB controller altogether.

What made you suggest disabling legacy support?  Is there a known bug I can read up on?

Its a complex issue, some boards give out less power in USB specially when heavy drain peripherals are used. What happens is that the ports revert back to 1.1 mode but in your case, its a total freeze which makes me think that its a separate issue here. If your system freezes when you attach the USB device, it could be that power is not being supplied sufficiently to the USB port. The only way to find out is to borrow a powered USB hub and then connect that to see if this problem goes away.

---

### Post by NickD-NLUG on 2009-11-02
> **Arup said:**
> Its a complex issue, some boards give out less power in USB specially when heavy drain peripherals are used. What happens is that the ports revert back to 1.1 mode but in your case, its a total freeze which makes me think that its a separate issue here. If your system freezes when you attach the USB device, it could be that power is not being supplied sufficiently to the USB port. The only way to find out is to borrow a powered USB hub and then connect that to see if this problem goes away.

I've sort of found the issue.... if I stop everything to do with running virtual systems in /etc/init.d... the problem goes away.  So there's something going on with virtualbox or vmplayer... I'll investigate further.

Thanks for brainstorming though, much appreciated :)

---

