---
title: "How do I get back init scripts?"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by lazloman on 2005-11-24
I stupidly removed the gdm initscript from /etc/init.d/. I hoped that re-installing gdm would restore it, but no go. Any ideas? By the way, I could not find sysvconfig in synaptic. I thought that was the 'ubertool' for managing initscripts.
TIA

---

### Post by ssam on 2005-11-24
if you have actually removed it then i am not sure how to get it back. you are safer making them unexecutable
```
sudo chmod -x /etc/init.d/gdm
```
or removing the symlinks from [FONT="Courier New"]/etc/rc1.d/[/FONT], [FONT="Courier New"]/etc/rc2.d/[/FONT] etc.

you can try my attached [FONT="Courier New"]/etc/init.d/gdm[/FONT] (i had to put a .txt on it to make the forum upload happy)

---

### Post by lazloman on 2005-11-24
Thanks, the script seems to work just fine, but do you have a copy of the rc script also? I dumped those also.

---

### Post by ssam on 2005-11-24
do you mean these?
/etc/rc0.d/K01gdm
/etc/rc1.d/K01gdm
/etc/rc2.d/S13gdm
/etc/rc3.d/S13gdm
/etc/rc4.d/S13gdm
/etc/rc5.d/S13gdm
/etc/rc6.d/K01gdm

they are all symlinks to /etc/init.d/gdm

---

