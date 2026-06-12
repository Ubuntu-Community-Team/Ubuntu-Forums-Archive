---
title: "syslogd : disabling IRQ #17"
date: 2007-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by remi_2 on 2007-10-04
Hello,

Still getting to grisps with 7.04 after upgrading from 6.06.1, on a AMD64x2 5200+/M2N4-SLI mobo.

I  have an IRQ problem : a syslogd message was printed in the console I was working in, saying that IRQ # 17 had been disabled.

It seems like IRQ #17 was that of my D-LINK Ehternet network card cause after that the network totally stopped working, and the eth0 disappeared from the gnome network panel.

In that PC I have two eth cards, the computer is connected to the internet  via eth0 and to a LAN via eth1.

I had to reconfigure eth1  to regain access to  internet to post this message.

What can I do to revive my regretted eth0? :confused:

Thanks

EDIT :
I just switched to tty1 with <CTRL+SHIFT+F1>, and saw this error message written at the top of the screen :

MP BIOS BUG : 8254 timer not connected to IO-APIC

Would this have to do with the noapic  nolapic story? could this be linked with my eth0 problem ?

---

### Post by Yellow Pasque on 2007-10-04
See if this thread helps:
[http://ubuntuforums.org/archive/index.php/t-450748.html](http://ubuntuforums.org/archive/index.php/t-450748.html)

---

