---
title: "Is it possible to have 1280x800 Resolution on the ATI Radeon Mobility 9600 AMD64"
date: 2006-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by strangerzero on 2006-12-07
I've be trying to get the native resolution of 1280x800 to work for weeks now. I'm having to use Ubuntu in 1024x768 resolution which makes the screen look elongated horizontally. When I switch to 1280x800 resolution the screen is not displaying correctly. It is out of synch and there are artifacts.

My System
emachines M6805 AMD 64
Ubuntu AMD64 6.10
ATI Radeon Mobility 9600

I'm using the drivers that were installed by default when I installed Ubuntu. I tried to figure out how to install the ATI propriety drivers but I'm a newbie and can't figure out how to do this or even if it will correct my problem.

Any help you can give me would be greatly appreciated. I like Ubuntu but this screen resolution problem is driving me crazy. ](*,)

---

### Post by drphilngood on 2006-12-07
Yes, it is.  Just see here:

[BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

and here:

[How to set you monitor resolution]("http://ubuntuforums.org/showthread.php?p=1566609#post1566609")

---

### Post by The Warlock on 2006-12-07
> **strangerzero said:**
> I've be trying to get the native resolution of 1280x800 to work for weeks now. I'm having to use Ubuntu in 1024x768 resolution which makes the screen look elongated horizontally. When I switch to 1280x800 resolution the screen is not displaying correctly. It is out of synch and there are artifacts.

My System
emachines M6805 AMD 64
Ubuntu AMD64 6.10
ATI Radeon Mobility 9600

I'm using the drivers that were installed by default when I installed Ubuntu. I tried to figure out how to install the ATI propriety drivers but I'm a newbie and can't figure out how to do this or even if it will correct my problem.

Any help you can give me would be greatly appreciated. I like Ubuntu but this screen resolution problem is driving me crazy. ](*,)

I have the same laptop as you.

Do the following:

sudo gedit /etc/X11/xorg.conf

look for a line that says

Modes     "1024x768" "800x600" "640x480"

change them all to

Modes     "1280x800" "1024x768" "800x600" "640x480"

and save the file

and restart X (ctrl-alt-backspace)

and you're done.

Hoary used to auto-detect this ****. I don't know what happened since then.

---

### Post by strangerzero on 2006-12-07
Thank you! I'm now displaying 1280x800.:D

---

