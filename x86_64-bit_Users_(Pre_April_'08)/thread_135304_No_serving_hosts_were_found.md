---
title: "No serving hosts were found"
date: 2006-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ottojschlosser on 2006-02-23
Hi, all. I updated several packages this morning, then went to reboot later after changing a CD drive. Now my system (Breezy on a B & W G3) boots, gets all the way through the basic load & initialization sequence, tries to put up a user login screen, then puts up an error dialog with the msg 'No serving hosts were found.' This is not hardware related - I put the old drive back in & same thing happened. The dialog refuses to cancel or go back; it simply clears the screen and reappears no matter what I try. I'm about a 4 or 5 on a 1 - 9 scale of Linux proficiency. Should I attack this via the rescue setup on the CD? I have another Linux box I can use to log into this one if that's necessary. Any help appreciated.

ojs

---

### Post by ssam on 2006-02-23
if you press ctrl+alt+F1 can you log in to a terminal?

---

### Post by ottojschlosser on 2006-02-23
Let's find out... yes.

---

### Post by danielph on 2006-07-31
Did you get an answer to this, I have the same problem this morning after a big update

thanks

Dan

---

### Post by maccan on 2006-09-15
I too have the same problem - 'no serving hosts were found' and I can't get rid of it.

---

### Post by MonteZ on 2006-10-17
i got this problem after installing Fluxbox which looked great :)
i used menumaker to populate applications menu and that went fine.
After i run Nautilus from the menu, it switched to the old gnome window manager with no toolbars but with icons on desktop.
Right click was bringing also gnome submenu.
Lucky for me i had firefox on desktop and i was able to search the web for problems.
Only this tread came out of searching.
I couldn't find the solution and i reseted the comp.
upon reboot i got the brown background and window poped up with: no service hosts were wound in the titlebar.
there's also Add hosts box that doesn't accept any user names or localhost.
After clicking the Help button i got message:
"The main area of this application shows the hosts on the local network that have XDMCP enabled. This allows users to login remotely to other comp. If they were logged on using the console.
You can Rescan the network for new hosts by clicking refresh.
When you have selected a host click Connect to open a session to that computer."
I was trying Ctrl+Alt + F1 thru F12 and i can get into terminal sassion.
AFter few tries as a root i can Startx and get into gnome Desktop as root.
Even after adding new user, same thing.
So far (two days) after reading a lot I'm not getting closer to solve this.

Any ideas ??

---

### Post by stuisodie on 2006-10-25
To all:

Thanks for your posts. They let me know i had not done this to the system myself. I was able to login via gdm after a couple edits.

# vi /etc/gdm/custom.conf


I set
[xdmcp]
Enable=false

from Enable=true 

then I set
[servers]
0=gdm

from 0=Chooser

I saved then ran gdm-restart and wham up came gdm.

I hope this helps. I'm like a 3 on a scale of 1 to 100 for unix knowledge.

Good luck.

S:mrgreen:

---

### Post by yitzle on 2008-01-29
It worked! Thanks!
(I added the Enable line myself. There was nothing there before.)

---

