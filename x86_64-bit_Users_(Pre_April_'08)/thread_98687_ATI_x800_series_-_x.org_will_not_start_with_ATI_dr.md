---
title: "ATI x800 series - x.org will not start with ATI drivers"
date: 2005-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by illynova on 2005-12-03
Has there been ANY solution to this problem? I've tried the ATI drivers that came with Ubuntu, then tried the fglrx but the same error resutled. The only way I could get KDE to work is by setting xorg.conf to use vesa drivers... but then KDE only lets me use 1024 x 768 resolution!

I can't believe there isn't a solution to this problem yet. Many people have x800 series cards with an AMD64 motherboard. I've looked everywhere, x.org has TONS of bug complaints yet nothing.

Should I just go by one of those new shiny Nvidia 7800 GTs and never again buy an ATI card? I'm so very tempted...

---

### Post by abshnasko on 2005-12-03
I also would appreciate a solution or a fix to this problem...

I am trying to run the Live CD and the X Server says it cannot start due to my video card, and then the screen garbles.

I have a Radeon X700 Pro 256MB... I've looked for awhile, haven't found a solution.

Any help would be good. Thanks.

---

### Post by Robocoastie on 2005-12-04
This thread will solve your woes: [http://www.ubuntuforums.org/showthread.php?t=76116&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=76116&highlight=ATI)

Take note that you FIRST have to enable the multiverse and universe repositories. If, like my rig, after installing ubuntu you get an x-server crash then edit your /etc/X11/xorg.conf file to make the driver=vesa then you can get to desktop to enable those repositories. Then follow the HowTo step by step and skip NOTHING and it **will** work.

---

### Post by daradib on 2006-10-21
Try this:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

---

### Post by iLoVe.cF- on 2006-10-21
well.. YOU SHOULD NOT BUY NVIDIA.. SERIOUS.

Well.. just find an solution ;)

Cuz... you gotta stick with nvidia/intel if ur gonna have nvidia.. cuz amd-ati vs intel war now ^^

Ati is probaly gonna be better on the drivers soon ^^.. just wait.. 

a x800 card works in ubuntu.. somehow.. dont remember how i did it.. but gonna fix it now :p

well.. dont buy ati-intel .. or amd-nvidia.. cuz u cant switch cpu/motherboard if u do soon ..

---

