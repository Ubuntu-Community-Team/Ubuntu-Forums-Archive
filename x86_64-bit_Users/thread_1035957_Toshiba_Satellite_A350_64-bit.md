---
title: "Toshiba Satellite A350 64-bit"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by bardu on 2009-01-10
Hi there,

I got myself a brand new Toshiba Satellite A350 64-bit today. Sadly, I'm not able to run Ubuntu 8.10 64-bit version from CD nor can I install it.

Both attempts ended with a blank screen.

I have also tried to install the 32-bit version but same thing.

Any ideas how to get Ubuntu installed?

Regards,
Stephan

---

### Post by paddy2706 on 2009-01-10
does your computer have any system installed, that can boot (maybe Windows(TM))?

can you boot anything from CD? TOSHIBA ships his notebooks usually with hdd as first boot device, so you would manually have to change this BIOS setting.

---

### Post by bardu on 2009-01-10
Windows Vista Home Premium is installed.

To boot from CD I have to changed the BIOS, but ended up with the problem described above.

---

### Post by paddy2706 on 2009-01-10
can you describe what happens? there should be at least some text message showing up, maybe before the screen turns black.

maybe you should try out the alternate installer: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by bardu on 2009-01-10
When I try to run Ubuntu from CD I get the screen with the Ubuntu logo and the progress bar. After booting, instead of the login screen, in the left upper corner a text starting with "Welcome ..." pops up shortly and then the screen turns blank.

I will give the alternated a shot later the day.

---

### Post by bardu on 2009-01-10
My understanding is that the alternate installer doesn't let you run Ubuntu from CD for testing.

As I re-call installations I have made on a number of different laptops and PC's over the past years, if Ubuntu is not running properly from the live CD it is not working properly when installed.

---

### Post by bardu on 2009-01-10
I'm not a hardware expert, but maybe the problem is a missing driver for the graphics controller ATI Mobility Radeon HD 3650. In Windows Vista display settings the default monitor on ATI has a resolution of 800x600 which can't be changed, while Vista is using a Generic PnP Monitor with a max resolution of 1366x768.

Any hints or ideas?

---

### Post by Sef on 2009-01-10
> My understanding is that the alternate installer doesn't let you run Ubuntu from CD for testing.

As I re-call installations I have made on a number of different laptops and PC's over the past years, if Ubuntu is not running properly from the live CD it is not working properly when installed.

Both are correct.  

Have you gone down the boot up list and done 'Check Disk for Errors' (or something similar to make sure the disks are good?)

---

### Post by bardu on 2009-01-10
Check Disk for Errors has past without problems.

---

### Post by bardu on 2009-01-11
I'm able to run OpenSolaris 2008.11 from Live CD, but here is also a problem with the screen resolution. It just recognize 800x600 which is the default monitor resolution on ATI. I can't change the default resolution, even in Vista.

Does someone know how to mod ATI Mobility Radeon HD 3650?

---

### Post by Yellow Pasque on 2009-01-11
I suspect the open-source ati driver included in 8.10 isn't recent enough to detect your GPU properly. Try an Ubuntu LiveCD again and add the following to the kernel line (i.e. extra options)
```
xdriver=vesa
```

---

### Post by bardu on 2009-01-11
Thanks for your suggestion, but same thing. After booting from CD the screen turn blank.

---

### Post by kibyegn on 2009-03-24
Hello, I also the same problem with my Toshiba A350 32 bit pre installed with Vista Home Basic. It just freezes when you try to boot it with the ubuntu intrepid live cd. Adding the xdriver=vesa option doesn't help either. Did someone find a solution to this. I think I would have to get the alternate cd.

---

### Post by Gralamin on 2009-03-29
I just stumbled on the this thread after successfully installing Ubuntu. I used the 8.10 64-bit CD and set it to boot in Safe-Graphics mode. I'm currently attempting to figure out what are the best display drivers to use for it, and will post when I know.

---

