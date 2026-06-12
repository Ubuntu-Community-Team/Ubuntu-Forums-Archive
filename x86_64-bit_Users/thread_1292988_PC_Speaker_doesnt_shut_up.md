---
title: "PC Speaker doesnt shut up"
date: 2009-10-16
forum: x86 64-bit Users
---

### Post by geerm on 2009-10-16
I recently updated to Ubuntu 9.10 from 9.04, at first it felt like Win 3.1 again with the pc speaker for simple errors like pressing backspace when there was nothing else to delete, or error alerts, it was anoying but not that big of a deal, today i have no idea what happened, but a few seconds when i log in the pc speaker just goes off and the only way i found to shut it up is to shut down the computer, had to boot from flash drive right now. I've been searching around for a whle and havent really found a actual fix, any help will be nice, and please let me know what you need to know about my pc to figure it out, cus' i would have to reboot and hear it for a couple of minutes again :(

---

### Post by ajgreeny on 2009-10-16
This way to blacklist the PC speaker works in jaunty, where a loud beep occurred in some machines when you hit the shutdown button, so it may also work in 9.10.

Stop Anoying Shutdown Beep
the file system in jaunty has changed slightly and the command will manually add "blacklist pcspkr" to the file /etc/modprobe.d/blacklist.conf
```
echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by jvdurme on 2009-10-31
> **ajgreeny said:**
> This way to blacklist the PC speaker works in jaunty, where a loud beep occurred in some machines when you hit the shutdown button, so it may also work in 9.10.

Stop Anoying Shutdown Beep
the file system in jaunty has changed slightly and the command will manually add "blacklist pcspkr" to the file /etc/modprobe.d/blacklist.conf
```
echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Thanks a lot. Worked for me!

---

