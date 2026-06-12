---
title: "Network Intensive Computer Freeze"
date: 2006-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by leboff on 2006-06-29
Hey, first post...

So anyway.. I've been running ubuntu for about a month, and everything is fine.  Except, if I run anything that is network intensive (say Bittorrent, streaming video, vnc, secondlife...) the computer will completely freeze.  It seems to have no problem with large downloads over HTTP.  
Nothing shows up in the dmesg log
My wireless card uses the RTL8185 chip.

Any other info you need to help me out.. just ask. Any support or suggestions are greatly appreciated.

I leave the country in a week , and I'd really like to be able to use vnc among other things.

Thanks
-leboff

---

### Post by hajk on 2006-07-02
You must be using the r8187 kernel driver for your wireless device, since a 64-bit Windows driver is not available for use with ndiswrapper... The r8187 driver is specifically billed as having "experimental support" for your chipset, and you have now experienced that these are not fatuous words. Be glad that you have at least some use out of your wireless device with this driver, people with rtl8187 chips (like my NetGear WG111v2 USB dongle) are totally out of luck. This is well-documented and bugs filed in LaunchPad.

I'm afraid you'll have to wait till an updated kernel module becomes available, or perhaps a 64-bit Windows module for use with 64-bit ndiswrapper. OTOH, there is no problem using ndiswrapper with the Windows driver in 32-bit Dapper.

---

