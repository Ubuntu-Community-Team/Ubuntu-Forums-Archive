---
title: "Strange lockups with WoW/Wine"
date: 2008-02-02
forum: Wine
---

### Post by lordtyp0 on 2008-02-02
I just installed kubuntu gutsy fresh updates etc.
Tossed Wine one and have done little else aside from installing the proprietary NVidia driver. I also installed openssh-server because I am lazy and like my laptop more (no other frills yet.).

I tweaked WoW by setting as opengl and a couple basic optimizations like changing the sound delay.

The game launches fine and went through all the updates. It allows login and everything seems OK with FPS around 50. After a random length of time (anywhere from 1 minute to 15 minutes) the system freezes, or more accurately the UI freezes. Game halts (no sound stutter), mouse and KB are unresponsive including ctrl+alt+backspace and ctrl+alt+del.

The system though allows logins and interaction on ssh-only I can't kill the wow pid nor restart kdm. I have also found nothing odd in logs.

Troubleshooting steps:
I disconnected all USB devices and disabled sound support in Wine. I was debating installing Gnome and trying in it as opposed to KDE.

I can grab any settings people might be interested but was hoping for additional places to look. (I presume removing sound support in wine would remove the odds of it being an issue with ALSA/OSS or even sound driver in general.)

Any assistance would be rgeatly appreciated.

---

### Post by lordtyp0 on 2008-02-02
On further digging, looks to be this:

[http://bugs.winehq.org/show_bug.cgi?id=7229](http://bugs.winehq.org/show_bug.cgi?id=7229)

---

### Post by Trail on 2008-02-02
> **lordtyp0 said:**
>  the system freezes, or more accurately the UI freezes. Game halts (no sound stutter), mouse and KB are unresponsive including ctrl+alt+backspace and ctrl+alt+del.

Offtopic, but in this situation where even Ctrl-Al-tBackspace is unresponsive, you can press:

Alt-SysRq-R
Alt-SysRq-S
Alt-SysRq-E
Alt-SysRq-I
Alt-SysRq-U
Alt-SysRq-B

(Raising Skinny Elephants Is Utterly Boring)

to synchronise buffers with disks, unmount disks, kill processes and finally reboot.

Additionally, Alt-SysRq-F kills the process with the highest memory usage.

Or, of course, login through ssh :)

Ontopic: This issue somehow has not occurred to me oO. I guess it will be fixed eventually through a new wine version.

---

### Post by lordtyp0 on 2008-02-02
Adding : "schedtool -a 0x2 -e " to the wine launcher shortcut appears to have fixed it, the system is an X2 3800 or 4000+ cpu. Looks like its a class or threading issue.

woot

---

### Post by themusicalduck on 2008-05-21
Hey, sorry to bump up this old thread. I got here from google searching for the same problem.

If I add schedtool -a 0x2 -e to a desktop launcher, I get the error message : "Details: Failed to execute child process "schedtool" (No such file or directory)"

I have an X2 3800+, so it looks like it's definitely this issue.

Anyone have an idea what's up?

---

### Post by themusicalduck on 2008-05-21
Suddenly it hit me.. It should be on the end and not at the beginning..

However, with this extra code on the launcher, the game will always lockup the system on starting it. The WoW window will come up but the system will lock fairly soon after. Without the code, WoW runs as usual but with the random occasional lockups.

---

