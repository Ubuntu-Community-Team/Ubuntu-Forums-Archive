---
title: "New to ubuntu - installation issues"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by mattfitz on 2006-01-29
Hi,

After being a windows user for years I decided to install linux at home, primalrly to learn it better as i find myself having to use it more and more at work. I downloaded the 64bit installation iso, burnt it to cd and it appeared to install fine.

I dual booted it with XP sp2, and the boot loader works fine, windows works fine but i appear to have issues with ubuntu. When gettign to the login screen I input the name and password, and it appears to log into the desktop. However all i get is the standard desktop background and it appears to hang there. Both the mouse and keyboard stop working and i cannot do anything but reboot the machine.

Any ideas as to what i may have done wrong appreciated.

specs:
athlon 64 3500+ venice
MSI K8N neo diamond
1gb ddr400
80GB hitachi SATA
160GB hitachi SATA

Thanks in adavance

Matt

---

### Post by dickohead on 2006-01-29
Did you install Ubuntu for i386 or x86_64? The hanging could be a result of one of million things, so the best way to figure out what it is, is to login to the terminal (Ctrl+Alt+F2 at the login screen) and update your system (sudo apt-get update, then sudo apt-get upgrade).

Good luck.

---

### Post by mattfitz on 2006-01-29
thanks for that, will try it tonight. I used the 64bit edition.

Matt

---

