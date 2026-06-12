---
title: "Floppy drive in menu, but does not exist."
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by joshuabuild on 2009-11-13
I just rebuilt, or reinstalled Ubuntu 9.10 on a friends computer but a floppy drive is reported in the places/computer area, but there is no floppy connected. Any leads on what to do with this ghost floppy would be appreciated.

[IMG]http://lh4.ggpht.com/_6_na6AOoz8I/Sv2gdc0JcjI/AAAAAAAAAtY/AvT_gJSzMMU/s400/Screenshot-Floppy%20Drive%20Properties.png[/IMG]

---

### Post by nixed242 on 2009-11-13
> **joshuabuild said:**
> I just rebuilt, or reinstalled Ubuntu 9.10 on a friends computer but a floppy drive is reported in the places/computer area, but there is no floppy connected. Any leads on what to do with this ghost floppy would be appreciated.

[IMG]http://lh4.ggpht.com/_6_na6AOoz8I/Sv2gdc0JcjI/AAAAAAAAAtY/AvT_gJSzMMU/s400/Screenshot-Floppy%20Drive%20Properties.png[/IMG]

I have a floppy drive reported on my system too, and also don't have one installed. My bios recognizes the connector for it on my motherboard, so when I installed Ubuntu, it recognizes a floppy drive being present. I think if I would have turned off the bios feature for floppy drives before installing Ubuntu, the OS never would have picked it up. Same goes for my Windows XP.

With that said, It's safe to just ignore it. That's what I do.

---

### Post by joshuabuild on 2009-11-13
cool, thanks!

---

### Post by falconindy on 2009-11-13
You can blacklist the 'floppy' module in /etc/modprobe.d/blacklist.conf -- that should stop it from being created on boot.

edit: oops... that doesn't *quite* work... i'll dig around to find where else its mentioned.

---

### Post by Yellow Pasque on 2009-11-13
If the lsmod command shows the 'floppy' kernel module loading, you could try blacklisting it.

EDIT: Beaten to it.

---

### Post by falconindy on 2009-11-13
Well, it **should** work, but it doesn't seem to take effect. Googling around, there's evidence of this not working for other people, and for unrelated modules. Not sure where to go with this short of recompiling the kernel w/o floppy support (lol?).

---

### Post by MonkeyWrench32 on 2009-11-14
> **joshuabuild said:**
> I just rebuilt, or reinstalled Ubuntu 9.10 on a friends computer but a floppy drive is reported in the places/computer area, but there is no floppy connected. Any leads on what to do with this ghost floppy would be appreciated.

[IMG]http://lh4.ggpht.com/_6_na6AOoz8I/Sv2gdc0JcjI/AAAAAAAAAtY/AvT_gJSzMMU/s400/Screenshot-Floppy%20Drive%20Properties.png[/IMG]

What I did to stop the floppy drive from showing up is to edit my fstab file (gksudo gedit /etc/fstab) and delete the line that corresponds to the floppy drive.  Mine was this:

/dev/sdg        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

