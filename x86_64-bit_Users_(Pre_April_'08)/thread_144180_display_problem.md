---
title: "display problem"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by dragon0010 on 2006-03-13
ok, im a little new ubuntu but i tried the live CD and i liked it so i decided to install it. Once the installation was done and it was about to show the desktop the screen went blank. So i restarted it and the same thing happened again. Then i decided to try it without the moniter bieng turned on until it was fully booted up and played the sound, for some reason it showed picture but it was extremly messed up. So can anyone help me with this problem?

oops forgot to mention that i was doing this on a G3 if that helps any.

---

### Post by pfhortran on 2006-03-13
[QUOTE=dragon0010]ok, im a little new ubuntu but i tried the live CD and i liked it so i decided to install it. Once the installation was done and it was about to show the desktop the screen went blank. So i restarted it and the same thing happened again. Then i decided to try it without the moniter bieng turned on until it was fully booted up and played the sound, for some reason it showed picture but it was extremly messed up. So can anyone help me with this problem?

oops forgot to mention that i was doing this on a G3 if that helps any.[/QUOTE]

 I got a similar problem with iMac G3 333 , a black screen after I logged in.
It worked fine with a G4 I have

---

### Post by linear on 2006-03-13
You don't say exactly what model you have, but the problem is often incorrect settings in xorg.conf. The fix, after you get to that black screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

For an iMac G3 you'd need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section. Others models? Don't know.

If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by dragon0010 on 2006-03-13
ok, i followed those directions except once i got to restarting Gnome all i got was a black screen. So any other suggestions?

---

### Post by linear on 2006-03-14
What I should have suggested first (if you have a monitor with its own power switch, it's not an iMac) is: ctrl-option-F1 to get to a shell prompt, then type this command:
 
**sudo dpkg-reconfigure xserver-xorg**
 
If this process doesn't work, post details of hardware (include video adapter, if known). Someone might recognize a known problem.

---

### Post by dragon0010 on 2006-03-14
Thank you so much, the autoconfiguration was a sucess...Thanks alot:)

---

