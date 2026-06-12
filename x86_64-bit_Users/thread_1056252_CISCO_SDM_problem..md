---
title: "CISCO SDM problem."
date: 2009-01-31
forum: x86 64-bit Users
---

### Post by lucanuscervus on 2009-01-31
Hi,

I'm trying to use CISCO SDM to configure my router but it never starts. Firefox opens a new window and starts loading the CISCO SDM express but nothing happens. It runs for ages but the SDM interface never appears. Any idea?

Thanks

I'm using Ubuntu 8.10 64 bits

---

### Post by NoReflex on 2009-02-03
Hello!

Do you have Java installed? When I first started SDM I had to add an exception to for the popup blocker to allow popups from 192.168.1.1 or whatever IP you have on the router. 
Anyway I think you should use the command line interface to configure your router (telnet, ssh or serial).
Good luck!

Best wishes,
Ionut

---

### Post by lucanuscervus on 2009-02-09
Hi,

Thanks for your reply. I have java installed and the browsers have been correctly set up to allow popups. Also, I'm using the command line to configure the router. 

The reason for the post was to know if more people have the same or simnilar problem with SDM in linux.

---

### Post by kingharf on 2009-02-22
Hi,

I can confirm that I have the same problem too with 8.04 Hardy x64.

Whats even weirder, is that I try it in my VMware running XP 32bit, and it hangs once the second window shows up. (IE)

Oh by the way, it hangs after the little "Please wait while SDM loads" disappears.

I use an Cisco 1711 upgraded it just now to the newest IOS as well as a new SDM. (I know i shouldn't do that b/c of instability issues but I was experimenting and I got lazy to change it back)

I tried opening it from my other computer and all works well.

If anyone has some insight on this, it would be really helpful, but I guess I am stuck with CLI.

thanks

---

### Post by fouadatmeh on 2009-02-23
Hello,

I was able to run SDM locally by using firefox installed in wine...
open firefox in wine and enter the address to "launcher.html"..
the path I have looks something like:
file:///home/user/.wine/dosdevices/c:/Program%20Files/Cisco%20Systems/Cisco%20SDM/common/common/launcher.html

a popup will appear asking for the IP address.. ( I have disabled the whole popups in firefox for it to work.. I didn't try to disable it just for the sdm  yet)

---

### Post by fouadatmeh on 2009-02-24
Sorry, but I replied a bit too soon regarding the popups, so I deleted my post

---

