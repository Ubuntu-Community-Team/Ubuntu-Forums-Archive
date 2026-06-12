---
title: "Oct 12 updates killed my Ubuntu!"
date: 2005-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by gratefulfrog on 2005-10-12
Since updating the kernel and whatever else was new since 2 days ago, I can no longer run Ubuntu on my AMD64.
On Boot:
- boot sequence looks unchanged,
- login screen appears,
- login is accepted,
- the metacity window manager desplays the 1st 2 icons, and
- ...
- that's it. a hang, and a hard reboot seems the only way to continue!

Anyone have any suggestions?

Thanks,
GF.

---

### Post by mlomker on 2005-10-12
Ctrl-Alt-F2 doesn't get you a terminal?  Generally I'd guess that's a video driver program.

Tried the good ole' **sudo dpkg-reconfigure xserver-xorg** thing?

---

### Post by mrdigital on 2005-10-12
I expiriance the the same problems here. I can kill the X-Server with ctrl-backspace and I can see a kernel panic message. If I try to log into the console, the login hangs. I could "revive" the machine by rebooting and starting in single user mode. In single user, I have reinstalled the kernel via aptitude and after that I could start the machine normally again, but... After I logged in, the machine crashed after a while, while it was serving a movie via network. I rebooted and had the same problems like in the very beginning :( 
Does anybody know a solution for this? How can I install a older version of the kernel again?

---

### Post by iank on 2005-10-13
Same here, box is now unstable since the kernel update, it has been rock solid for months previously.

3 crashes so far:

1st Just started BMP it played a couple of seconds then everything locked.  Mouse still moved, but no response - couldn't switch virtual consoles - reboot using brief push of power button worked.

2nd Left alone doing not much came back to a page of register values.  Could switch virtual consoles but not much else.

3rd Playing foobillard just hung, not even mouse working, hard powerdown required.

Using Nvidia 5700
Gigabyte GA-K8VT800M (Via K8T800)
Soundblaster Live!

Is there any way of backing out a kernel version update?  This is my media center/printer server ](*,)

---

### Post by mterlouw on 2005-10-13
Ugh... I'm afraid to reboot. I was hoping there would be a kernel update this morning to address the issue, but there doesn't seem to be one.  I havn't rebooted since before the Oct. 12 updates.

---

### Post by mrdigital on 2005-10-13
I just installed the 2.6.11 Kernel (the buggy one was the 2.6.10-5 Kernel), and the machine is running since 12 hours :-) The only bad thing with this kernel is, that there is no percompiled kernel-module for the ati driver, so I have to to this now by myself ;)

---

### Post by manfo on 2005-10-13
[QUOTE=gratefulfrog]Since updating the kernel and whatever else was new since 2 days ago, I can no longer run Ubuntu on my AMD64.
On Boot:
- boot sequence looks unchanged,
- login screen appears,
- login is accepted,
- the metacity window manager desplays the 1st 2 icons, and
- ...
- that's it. a hang, and a hard reboot seems the only way to continue!
[/QUOTE]

Uh... Same for me :(
The weird thing is that I'd *eventually* manage to start GNOME: that is, it often freezes just like you said, but sometimes everything works fine. I also noticed that I had the system crashing a couple of times just by clicking on the menu of gnome-panel...
So, I'll try to downgrade the kernel. Should that fix this?

---

### Post by mterlouw on 2005-10-14
It looks like the kernel I have installed is 2.6.12.  So maybe I shouldn't worry?

---

### Post by iank on 2005-10-14
Upgraded to 2.6.11-1-amd68-k8 and all now seems well.
Had to manually upgrade the nvidia driver (went for the latest from nvidia's website 7676).

Ah well, one bad update since I started using ubuntu isn't too bad. :???:

---

