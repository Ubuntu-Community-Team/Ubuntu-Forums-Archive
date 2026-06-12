---
title: "I can't view the terminal!"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by jturel on 2006-08-28
Here's my problem.

When I start my laptop (x64 Dapper 6.06) which is an Acer 3004WLMI
I get to grub and select Ubuntu. I see the "decompressing linux kernel" text or whatever it says then the screen goes blank until the X server starts. I can not see any of the boot sequence. When I hit CTRL+ALT+F1 to get to a terminal one X has started the screen is again blank, and I can use CTRL+ALT+F7 to get back to gnome.

When I select recovery mode from the list at startup I can see the boot sequence perfectly, like I do on my desktop from which I have installed ubuntu from the same CD.

I do not understand the logic behind this for two reasons: I am new to linux and do not know what is causing the screen to go blank at that point of the boot process, and two, afaik there should just be a standard vga driver that should be displaying the boot sequence so what's the problem?

Another note, upon installation when I boot from the CD after I select Install/Run the screen goes blank in the same manner. HOWEVER: I restarted it to test and I used the F4 menu to select a video mode (I used 800x600x32) and it showed everything as it should - but only that one time during the installation bootup.

Thanks in advance for any suggestions to this.

Video card is SiS (I can't recall the model 700 something?)

---

### Post by jturel on 2006-08-28
I did get my Broadcom 4318 wireless card connected though! :mrgreen:

---

### Post by KazuyaDarklight on 2006-08-29
I have the same model, same problem.  Bump

---

### Post by KazuyaDarklight on 2006-08-29
oops sorry, meant to subscribe.

---

### Post by jturel on 2006-08-29
> **KazuyaDarklight said:**
> I have the same model, same problem.  Bump

hopefully someone with a bit of knowledge will point us in the right direction!

](*,)

---

### Post by jturel on 2006-09-05
bump

---

### Post by kuja on 2006-09-05
So you say that you can see it fine when you boot into single user mode?
Well, it might be less "pretty", but this is worth a try.

```
sudo gedit /boot/grub/menu.lst
```

Scroll down until you see a section that looks similar to this (yours will be different, but keep in mind that I said "similar to"):

> 
title           Ubuntu, kernel 2.6.15-26-amd64-k8
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-amd64-k8 root=/dev/mapper/nvidia_gfdcfcfd5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-k8
savedefault
boot
Look at the line that starts with "kernel", at the end of that line, you likely see "ro quiet splash". Try removing splash from the line, saving the file, and rebooting. It's not the pretty way to fix it, but it should work, for now at the least.

---

