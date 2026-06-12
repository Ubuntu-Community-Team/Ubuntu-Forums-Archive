---
title: "Can't Use Clamshell iBook's Internal Modem"
date: 2006-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by berniej on 2006-02-18
I'm a complete newbie and I just successfully installed Breezy on my Clamshell iBook (300 MHz with 288 MB RAM).  When I attempted to configure the modem, the configuration doesn't seem to "stick".  I'm pretty confident that the configuration for the internal NIC is good (can't test it 'till Monday) but what I can't understand is why I can't configure my modem.

Any help would be appreciated.

Thanks!

---

### Post by Ptero-4 on 2006-02-18
Are you using sudo pppconfig to configure your modem? It strikes me that you can't configure it b/c every iBook earlier (and including) the G3 500MHz uses a hardware modem. The G3 600MHz and later are the ones that use softmodems. Also do you leave the configuration name as the default "provider" one? b/c leaving it set at the default will provide an easy dialing using pon (if you change that name you'll have to use pon "name" every time you dial to your ISP)

---

### Post by berniej on 2006-02-19
Thanks PTero-4.  It just turned out that I *can't* configure the modem if my phone line is not connected to it.  As I've said, I'm a relative n00b in Linux since I use Windows at work and OS X on other occassions.  This will be my first time to fully immerse on Linux.

Thanks and *Mabuhay!*

---

