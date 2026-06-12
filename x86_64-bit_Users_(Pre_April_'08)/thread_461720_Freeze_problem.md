---
title: "Freeze problem"
date: 2007-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-06-02
Ok well I've been using 7.04 Ubuntu for a while and I kept getting this little freeze problem where my computer would lock up and I could move the mouse around but not click on anyting but everything was still running.  Now back then after a few seconds the system would unlock somehow and I could keep using it.  Now I installed Beryl and I was playing around with that and I get the same problem but it doesn't come back. everything still runs, I can watch the time pass by on the clock.  I don't get it.

---

### Post by tgalati4 on 2007-06-02
Will control-alt-backspace reset the xserver?

---

### Post by Cappy on 2007-06-02
It's a bug since ubuntu dapper. Alt+Tab always fixes it right away for me. you can turn off ACPI and it will fix this problem if it annoys you.
Add "noapic acpi=off" onto the end of your /boot/grub/menu.lst line that you use to boot and it will fix it.
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

---

### Post by DaGGer on 2007-06-02
No I can't use ctrl+alt+backspace Now what is turning off ACPI going to do.  Do I need it or anything? Thanks for your help I just want to know what I'm doing so I can tell if something else gets messed up because of it.

---

### Post by Cappy on 2007-06-02
If you turn off ACPI you won't be able to use Suspend or Hibernate and that's the only thing it affects.

---

### Post by DaGGer on 2007-06-02
Oh ok, thats fine. I don't use those anyways. Well we'll see if this fixes it and I just want to say thanks for your help everyone. This forum is so fast at responding, which is why I havn't used windows in about a month I think.

*UPDATE* Ok well it seems to have fixed it thanks a lot.

---

