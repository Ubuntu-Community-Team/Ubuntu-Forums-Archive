---
title: "Jaunty x86_64 freezes on USB"
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by ncubede on 2009-04-22
Hi,

I have a Dell Latitude E6500 with 8G RAM and the nVIDIA Quadro NVS 160M graphics card.  I always had quite a few USB issues, normally meaning I have to reload the uhci-hcd module every few hours to get USB working again.  This alone is annoying enough, but every day or two the system utterly locks up.  

After some thought I setup netconsole and got the follwing as the last messages before things froze:

```

Apr 22 17:45:24 10.1.100.104 [28467.331356] ehci_hcd 0000:00:1a.7: fatal error
Apr 22 17:45:24 10.1.100.104 [28467.337824] ehci_hcd 0000:00:1a.7: force halt; handhake ffffc20000c3c424 00004000 00004000 -> -110
Apr 22 17:45:25 10.1.100.104 [28467.830395] usb 3-2: new full speed USB device using uhci_hcd and address 5
Apr 22 17:45:25 10.1.100.104 [28467.994192] usb 3-2: not running at top speed; connect to a high speed hub
Apr 22 17:45:25 10.1.100.104 [28468.070564] usb 3-2: configuration #1 chosen from 1 choice
Apr 22 17:45:25 10.1.100.104 [28468.073326] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_0.3M (0c45:63f8)
Apr 22 17:45:25 10.1.100.104 [28468.088469] input: Laptop_Integrated_Webcam_0.3M as /devices/pci0000:00/0000:00:1a.2/usb3/3-2/3-2:1.0/input/input14

```

I tried a few kernels, but sadly Jaunty (from 2.6.28) does not make uhci a module, so instead of reloading the module I have to reboot every few hours.  So, I stick with 2.6.27 from Intrepid, so I can survive at all. I tried various nvidia drivers, even 185.19, but this had hardly any effect on the issue.

Any ideas?

Stephan

Thanks, Stephan

---

### Post by Yellow Pasque on 2009-04-22
Updated BIOS?
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R211200&SystemID=LAT_E6500&servicetag=&os=WLH&osl=en&deviceid=16473&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=297077](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R211200&SystemID=LAT_E6500&servicetag=&os=WLH&osl=en&deviceid=16473&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=297077)

---

### Post by ncubede on 2009-04-23
Will review the release notes and then apply the BIOS upgrade, I am running A11, so it is worth a try.

Thanks, Stephan

---

