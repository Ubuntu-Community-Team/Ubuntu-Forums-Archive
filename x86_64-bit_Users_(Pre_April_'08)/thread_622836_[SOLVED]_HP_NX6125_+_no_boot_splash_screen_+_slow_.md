---
title: "[SOLVED] HP NX6125 + no boot splash screen + slow boot + no console"
date: 2007-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by hlm_worker on 2007-11-25
After Gutsy fresh install on HP NX6125 laptop (ATI Xpress 200M graphics card) from Live-CD, some issues were remaining:
 - no splash screen on boot
 - booting was very slow
 - no functional console switching with Alt-Ctrl-F[1-6] (huge font or garbage screen)

All these were solved by changing the usplash default screen resolution to the native screen resolution.
 - edit the usplash.conf file:
   ```
sudo gedit /etc/usplash.conf
```
   and change 1280 768 to 1024 728

 - apply changes
```
sudo dpkg-reconfigure usplash
```

 - reboot

Everythink is working fine now except suspend modes... Seems also that fglx restricted ATI driver is running slower than 32bits driver on feisty.

I hope this could help other X86 laptop users.

---

### Post by vickyr111 on 2007-12-31
thanks it helped me.:)

---

### Post by homerhomer on 2007-12-31
Thanks

Worked for me too,

---

### Post by Wizaado on 2007-12-31
This also work for me on my desktop. Acer Aspire AM5630 with 22" Flat Panel. uplash's resolution was set to 1680 x 1680 which caused the problem.

Thanks for the help!

---

