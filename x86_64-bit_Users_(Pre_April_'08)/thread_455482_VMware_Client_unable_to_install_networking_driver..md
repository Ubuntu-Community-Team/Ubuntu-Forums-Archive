---
title: "VMware Client unable to install networking driver."
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by SoulThief on 2007-05-26
Hey, I'm pretty new to this forum, and to Linux, as far as now I've hold my own, but I'm struggling now.

I've installed VMware, and installed a fresh copy of Windows XP Media Centre, on the client, with all the default vPC settings.
I've got through everything as I should, but I'm experiencing trouble with getting the network driver installed.

I'm running Ubuntu Feisty, the latest version of VMware Server.

And am Using a Gigabyte nForce 4 motherboard.

So has anyone experienced something similar, and found a solution?
It's mandatory I can access the internet with the vPC.

Thanks in advance!

---

### Post by firecat53 on 2007-05-27
Hmmm. Most times an XP virtual machine will have no issues connecting. You didn't specify laptop or desktop...on my laptop I had to select NAT networking as opposed to bridge networking due to the transient nature of the wireless connection.

Otherwise, try running the vmware-config.pl again and verifying your networking settings (default seems to work fine for most people -- NAT or bridged being the exception).

Good luck!

Scott

---

### Post by Twintop on 2007-05-29
I had the same issues with my Windows XP Professional x64 install under VMWare and noticed that there are some differences in a 64-bit Windows .vmx file from a normal 32-bit Windows one, specifically regarding ethernet and sound.

For one, the guestOS should be:

```
guestOS =  "winXPPro-64"
```

Since the ethernet settings vary between machine, I'd try using [http://www.easyvmx.com/]("http://www.easyvmx.com/") to generate your .vmx file for the VM. It should auto-detect your hardware and give you appropriate values.

Hope this helps you. :)

---

