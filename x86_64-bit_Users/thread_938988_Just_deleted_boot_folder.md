---
title: "Just deleted /boot folder"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by pdiddypaul on 2008-10-05
I just deleted my entire /boot folder.  Long story.  Is there a good way to repair this without doing a complete re install

thanks in advance for the help.

rankin

Would it be possible to just copy /boot from another computer and paste it in.

Also I have not shut down the computer in question yet.

---

### Post by Yellow Pasque on 2008-10-06
Interesting.. Well, you can try to recreate the directory. Reinstalling the kernel might help with a lot of this.
```
cd /
sudo mkdir /boot
cd /boot
sudo mkdir grub
sudo apt-get reinstall linux-image-2.6.24-19
```

If Ubuntu is the only OS on the disk, then this should be safe:
```
sudo apt-get reinstall grub
```
Hopefully, between these two commands, the system configuration scripts you need will run and recreate the kernel image and menu.lst for you.

---

