---
title: "HP nx6125 on edgy"
date: 2006-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by alesdoc on 2006-10-18
Hello,

i don't know if i'm writing on the right forum-session.

I've just one question. Have you already tried to install edgy on HP nx6125? Are the kernel-options noapic nolapic still necessary to run a correct installation of the OS?

Thanks.

Bye

---

### Post by metasquier on 2006-10-30
I would also like to know, as Im keen to install ubuntu on my nx6125 for uni next year.

---

### Post by fatneck on 2006-11-06
6.06 was a disaster for me, cpu maxing out at 100% all the time made the machine unusable. added to that no ATI drivers installed properly and i hadn't even started on the wireless.

went away, came back and tried again with 6.10 and no more CPU problems. followed this to get the ATI drivers working fine:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

so now *all* i need to do is get wireless working. if anyone else has done it with the nx6125 i'd be keen to hear from them. if i get it working i'll repost back.

---

### Post by Denton on 2006-11-07
> **fatneck said:**
> 
so now *all* i need to do is get wireless working. if anyone else has done it with the nx6125 i'd be keen to hear from them. if i get it working i'll repost back.

hi,
i got it working with ndiswrapper, just get your windows driver file (bcmwl5.inf), install ndiswrapper-utils-1.8 and then in console do
```

sudo ndiswrapper-1.8 -i bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper-1.8 -m

```

---

### Post by alesdoc on 2006-11-08
As in breezy and dapper i've to use noapic nolapic to get it properly works.

For the video card i follwed also the howto suggested by fatneck

For the wireless i used bcm43xx-fwcutter.

I had an issue with nm-applet. I opened also a bug-report on lauchpad (bug 68364), but...non answer.

I had also anothe issue. The system is really slow when i transfer file from/to my usb-HD, but i think it's not a problem concerning only our laptop.

---

