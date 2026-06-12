---
title: "GNOME Theme Manager Issues"
date: 2006-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Electron Sponge on 2006-07-09
Hi, I've looked around the forum and Googled quite a bit on this, but I can't seem to find a solution. I'm running Dapper Drake on an AMD64 with an nVidia 6600LE. My gnome-theme-manager is acting quite strange. It isn't displaying any thumbnails (with the exception of one) and every time I change themes the clock app crashes. This has only started happening since I installed KDE to experiment a bit with it. Could there be some sort of corruption or conflict that has resulted?
When I run it from a terminal window, I get the following output:
> mike@goliath:~$ gnome-theme-manager &
[1] 16078
mike@goliath:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gnome-theme-manager:16078): capplet-common-WARNING **: Received EOF while reading thumbnail for gtk: 'Clear-Blue', metacity 'Bluecurve', icon: 'Flat-Blue', font: 'Sans 10'
The theme manager itself looks like this:
[IMG]http://img.photobucket.com/albums/v299/electronsponge/gnome-theme-manager.png[/IMG]
When I attempt to change a theme, I get an error message stating that *"Clock" has quit unexpectedly* and asking me if I want to reload it. Sometimes it allows me to reload it, other times it completely fails.

If anyone could point me in the right direction, I would really appreciate it.

---

### Post by RAOF on 2006-07-09
Hm.  Those look suspiciously like QT widgets...  The probable cause is the gtk-engine-qt package, which allows Gnome applications to look like KDE ones.  Except it doesn't work too well in gnome itself, apparently.  I'd **try** going into "theme preferences" (or something, I find KDE a horrible mess) in KDE and turning off the "Make GTK applications use KDE theme" (again, or something.  It's been a while ;)) setting.

Alternatively, you could just **sudo aptitude remove gtk2-engines-gtk-qt**.  I'm not sure if or how much that would break KDE, though :)

---

### Post by Electron Sponge on 2006-07-09
D'oh! That did it. Thanks for the help, RAOF.
BTW, I went with the second option because I now think KDE sucks. ;)



EDIT: The clock applet still crashes.

---

### Post by rutger83 on 2006-08-07
The solution also didn't work for me. The problem is bigger btw. It's not just the clock that crashes. If you leave the theme active and restart the computer (or gdm ofcourse), gnome doesn't start but keeps trying to load the panel. I had to start kde (yes, I have kde) and adjust the problem!

---

