---
title: "Ubuntu server 8.10 x64 not booting"
date: 2009-04-08
forum: x86 64-bit Users
---

### Post by rickgomez2003 on 2009-04-08
I have a Ubuntu server and i installed some libs to get my game server up and running now I am unable to boot the server. I can get in to the grub portion of it.

---

### Post by Slim Odds on 2009-04-08
> **rickgomez2003 said:**
> I have a Ubuntu server and i installed some libs to get my game server up and running now I am unable to boot the server. I can get in to the grub portion of it.

What kind of help do you expect when you provide no details?

---

### Post by rickgomez2003 on 2009-04-08
I am new to this what kind of details do you need I will get them

---

### Post by Slim Odds on 2009-04-08
> **rickgomez2003 said:**
> I am new to this what kind of details do you need I will get them

Well... for starters... the obvious.... 

> ... I installed some libs...

What libs?

What kind of error messages to you see?

What actually happens when you try to boot?

---

### Post by rickgomez2003 on 2009-04-08
I get vesafb blacklisted and /dev/disk/by-uuid/57f5e207-6da0-4ef1-814c-a74d4a64ef2b does not exist the the screen gos black and i have to power off the server to get it back to that.

---

### Post by rickgomez2003 on 2009-04-08
I am able to get it to boot if I ESC to grub and select kernel 2.6.27-7-server in stead of kernel 2.6.27-11-server. Thanks for any help.

---

### Post by cariboo on 2009-04-08
If you have a LiveCD I would suggest booting from it and then follow [thread=224351]this[/thread] to repair grub. If you are using vesafb, I would remove it from /etc/modprobe.d/blacklist.

Jim

---

### Post by rickgomez2003 on 2009-04-08
> **cariboo907 said:**
> If you have a LiveCD I would suggest booting from it and then follow [thread=224351]this[/thread] to repair grub. If you are using vesafb, I would remove it from /etc/modprobe.d/blacklist.

Jim



We must have been typing at the same time will this still work.

---

### Post by cariboo on 2009-04-10
I just read that you can boot from an older kernel. I would suggest booting using the older kernel and remove the libraries you installed to see if that is what caused your problem. I would also suggest you check what video driver is being used when booting from the older kernel. At the prompt type:

```
cat /etc/X11/xorg.conf
```

you should see something similar to this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

If you have a different video card the driver will be different.

I also checked my server to see what the /etc/X11/xorg.conf file looks like, and of course because I don't run a gui there isn't one.

Jim

---

