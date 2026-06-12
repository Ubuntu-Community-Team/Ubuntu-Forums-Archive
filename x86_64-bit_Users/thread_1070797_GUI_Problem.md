---
title: "GUI Problem"
date: 2009-02-15
forum: x86 64-bit Users
---

### Post by PT145 on 2009-02-15
Hi All,  Run multi-boot 32Bit XP Pro, 64Bit XP Pro and 64Bit Ubuntu 8.10, all on their own dedicated drives.  New clean install of all three OSs due to building new PC.  Everything has been working fine until last night.  Also, I'm totally new to Ubuntu.  While trying to use "nicer" graphics in the GUI was told to obtain nVIDIA accelerated graphics driver (version 177).  Agreed to let "system" search for and install driver.  After reboot the GUI does not come up.  Instead I get command line prompt and I'm able to log on.  I haven't used a command line since my old CP/M days.  Anyway, I've searched the forum and have printed out various possible solutions to try.  My problem is and please don't laugh but when I'm using "dir" "ls" and such it will flash everything up at once.  How do you "pause" the screen to see entire contents of a directory if it exceeds what can be shown on the screen.  I've used "Man" for the various commands but can't or just don't see any options to cause a scroll delay of some sort.  Also, one of the solutions stated to look for a "xorg.conf" file in /etc/X11/ but I don't seem to have a X11 directory.

---

### Post by joey-elijah on 2009-02-15
Have you tried running

*dpkg*-*reconfigure* xserver-[I]xorg
[/I]

---

### Post by PT145 on 2009-02-15
> **joey-elijah said:**
> Have you tried running

*dpkg*-*reconfigure* xserver-[I]xorg
[/I]

Thanks, I haven't but will give it a try.  As I said I'm new to Ubuntu and have been letting the update manager handle things so now learning how to use the CLI.  Again, any comment on my scrolling questions?

---

### Post by Stunts on 2009-02-15
Hi! Sorry to hear about your issues.
Just so you know, in order to be able to scroll, just type in your command and add this:
```
user@computer$command |less
```
use the arrow keys to scroll up and down, spacebar to go down one full page, and "q" to go back to the cli.
Hope it can be of some help!

---

### Post by PT145 on 2009-02-16
> **Stunts said:**
> Hi! Sorry to hear about your issues.
Just so you know, in order to be able to scroll, just type in your command and add this:
```
user@computer$command |less
```
use the arrow keys to scroll up and down, spacebar to go down one full page, and "q" to go back to the cli.
Hope it can be of some help!

Thanks!  Update on my other issue....since this was a clean install I just installed everything again and all seems to be well.  I'm going to stay away from the nVidia drivers for now.

---

### Post by Stunts on 2009-02-16
OK! I'm glad I could be of assistance.
Maybe when you get more experienced you give it another try!
Anyway, good luck with your new system.

---

