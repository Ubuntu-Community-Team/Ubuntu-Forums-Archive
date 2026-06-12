---
title: "ubuntu 8.04 problem with Geforce 8600 gt on XPS M1530"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by 4minab on 2008-04-27
ubuntu 8.04 problem with Geforce 8600 gt on XPS M1530

i install new ubuntu 8.04 64bit

and i have problem with my Video Card

 

when i install driver ([http://www.nvidia.com/object/linux_display_amd64_171.06.01.html]("http://www.nvidia.com/object/linux_display_amd64_171.06.01.html")) 

after reboot Gdm , my screen go WITHE , i tryed many ways :mansad:

what is the Problem and solution ?

please Help me !

---

### Post by fogcat on 2008-04-28
I have the 8600GT...PCIe type w/512MB.

I just used the ubuntu restricted install...the ubuntu "new" nvidia driver as supplied by the community.

This is an experimental installation for me (64bit) but so far there have been no "big" problems with it..

have you tried the supplied driver? (found in the Add/Remove section of your menu)

fogcat

---

### Post by lamborghiniwang on 2008-04-28
> **4minab said:**
> ubuntu 8.04 problem with Geforce 8600 gt on XPS M1530
i install new ubuntu 8.04 64bit
and i have problem with my Video Card
when i install driver ([http://www.nvidia.com/object/linux_display_amd64_171.06.01.html]("http://www.nvidia.com/object/linux_display_amd64_171.06.01.html")) 
after reboot Gdm , my screen go WITHE , i tryed many ways :mansad:
what is the Problem and solution ?
please Help me !

Not sure how to fix this, but I guess you can change your xorg.conf into vesa, which should be able to bring the gdm back to normal, and then you may try to install the Nvidia driver again, or install the [**newer driver**]("http://www.nvidia.com/object/linux_display_amd64_173.08.html").

---

### Post by kingtaurus on 2008-04-28
Can you post the following: Xorg log file (/var/log/Xorg.0.log), xorg.conf (/etc/X11/xorg.conf).

Do you still have a mouse cursor when the screen goes white? If so: try the following,
<Alt>-F2
and type:
metacity --replace

---

### Post by jespdj on 2008-04-29
Why did you crosspost this to so many of the forums here?

I already answered in one of your other posts and I'm too lazy to find it for you.

---

### Post by 4minab on 2008-04-29
becouse my problem will not fix :((

---

