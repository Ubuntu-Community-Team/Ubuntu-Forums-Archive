---
title: "video troubles w/ 64 bit feisty and 8600GTS"
date: 2007-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by whosmatt on 2007-10-05
Here's my issue:

Having installed the NVIDIA driver, the card now works great (had to switch to the vesa driver and then dl and install nvidia).  However (and this problem happens whether I'm using the nvidia driver or the vesa driver), between the grub menu and when gdm starts, i get no video (blank screen and my monitor switches off, or worse, switches to the other input, which has another computer hooked up). Can someone tell me how to edit my grub configuration so that i get text only during startup?

My monitor is a Sceptre 20" running @ 1680x1050.  

Thanks,

Matt

---

### Post by mitchej123 on 2007-10-07
I had a similar problem to what you're describing.  I haven't looked into it much but did come up with a solution that suits me --  I turned off the splash screen while booting and now it's working fine.  

To do this edit /boot/grub/menu.lst and remove all occurances of "quiet splash" 

ie: change ```
kernel          /boot/vmlinuz-2.6.22-13-generic root=UUID=72f45644-4d1a-4393-abbf-b021421e3c5f ro quiet splash
```
to 
```
kernel          /boot/vmlinuz-2.6.22-13-generic root=UUID=72f45644-4d1a-4393-abbf-b021421e3c5f ro
```


Hope this helps.

---

