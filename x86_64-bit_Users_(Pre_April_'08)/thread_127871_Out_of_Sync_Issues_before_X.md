---
title: "Out of Sync Issues before X"
date: 2006-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by puck1230 on 2006-02-10
I have a minimac with 512 RAM and a 10gb partition for ext3, 512 for swap and 1 for boot. I downloaded breezy and went through the simple installation. When it reboots and ejects the cd, and yaboot comes up, i select "l" for linux and it proceeds to start loading. Then my monitor goes black and says Out of sync range. Nothing happens. I wait two minutes and press ctrl apple F1 and ctrl alt f1 and nothing happens. I'm assuming this is the 2nd part of the install phase, but for some reason it wont load correctly. I stick in the breezy live cd and that works great. Detects allll my hardware, 1600x1200 resolution, even my dsl connection is working. I mount my / partition to check what got installed and what didn't. In /etc there is no X11 folder. X hasn't even be configured yet. I don't understand why my monitor keeps thinking its out of sync range. I have a very old Micron 19" crt where the specs are listed as H30-85 V 50-170. That's a pretty big range. In live cd mode I check out the xorg.conf file and it says H28-80 and V43-60 for sync. I tried using the expert install feature of the install disk but when i try and complete the 2nd phase of installation in the 1st phase of installation I dont quite get all my options. It says "installation finishing" then brings me back to the same menu as the 1st stage of installation, but the cd has been ejected. Does anyone know what's wrong? Thanks in advance.

---

### Post by puck1230 on 2006-02-10
It was out of sync while in the 2nd phase of installation. I left it alone for 20 minutes and then it when to the gui login screen. No problems anymore. Thanks.

---

