---
title: "Total spaz attack"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by renegadesx on 2007-10-27
I just built a new box for myself, Core 2 Quad machine, I went to put in a 64-bit version of Ubuntu to put in and 5 seconds into loading it has a total spaz attack, weather normal mode, safe mode graphics and even "check cd for defects". Spaz attack followed by screen blackout

I am downloading currently re-downloading it (even though md5sum checked OK) and if that doesn't work will try alternate CD

Wondering if anybody knows why this would happen?

32-bit version runs and installs with no problems

---

### Post by renegadesx on 2007-10-27
OK, fresh copy, seems to boot OK, only I wouldn't know as my monitor isn't getting any signal.

Something in the default graphics settings? Splash boot screen or anything wont come up.

I have a 22" Widescreen Acer AL2216W hooked up to a 512Mb GeForce8600

As mentioned before, the 32-bit version runs without issues.

---

### Post by Therion on 2007-10-27
Boot from the LiveCD.
When the GRUB menu comes up hit "Escape" and select "Recovery Mode".
You'll seem some screens scroll by and wind up at a command prompt.
At the command prompt:
```
nano /boot/grub/menu.lst
```
Scroll down past all the # signs and look for the first line that starts with Kernel.  It's a long line of code that will go off the end of your display.  Use the arrow keys to get to the end where you'll see the word "splash".
Remove the word splash from that line.
Ctrl+X, confirm the overwrite and reboot.

This will get you to the desktop where you can install Ubuntu to your hard drive.  AFTER it's installed to your hard drive, you'll need to **re-edit** menu.lst because now you're booting from your hard drive and not the LiveCD. 

Follow the above steps again once you've booted from your hard drive and you should then be prompted about installing the Restricted Driver automatically.  Install the driver and you should be good to go from there.

Search the forums about how to get your boot-screen back.  Nothing worked for me, so I just live without a boot screen.

---

### Post by renegadesx on 2007-10-27
Well not exactly, It gives me an "OK/Cancel" menu to go into text mode and wants me to manually boot a kernel image

Thought I should throw in Ctrl-Alt-F1 which usually exits the slash screen and goes to text base doesn't help.

When I'm at the desktop I can hear the sounds fine, but no signal from the screen, again Ctrl-Alt-F1 will not help

---

### Post by Therion on 2007-10-27
> **renegadesx said:**
> Well not exactly, It gives me an "OK/Cancel" menu to go into text mode and wants me to manually boot a kernel image
I'm afraid I don't understand.  You're hitting "Escape" from the GRUB menu and you're not getting the option to use "Recovery Mode"?

---

### Post by renegadesx on 2007-10-27
No you summed it up perfectly.

There is no mention of recovery mode. just exit graphical and enter text mode

Goes straight into a boot prompt where it wants me to boot a kernel image, access to nano, vi, emacs, nothing, nada.

---

### Post by renegadesx on 2007-10-27
OK I installed via Alternate CD, and this time I was able to get into recovery mode and did what you said. All good so far

Is there a way to edit the splash screen so it will display?

---

### Post by Therion on 2007-10-28
> **renegadesx said:**
> Is there a way to edit the splash screen so it will display?
It's an issue with the 64bit version of Gutsy.  Join the crowd.  

Personally none of the posted solutions thus far have worked for me, and I've simply given up hope of having a boot screen.  But, peruse some of [[COLOR="Blue"]these threads[/color]]("http://ubuntuforums.org/search.php?searchid=30006466") (take your pick!), and maybe something will work for you.  

Good luck!!

---

