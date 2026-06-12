---
title: "New User's Wine Problems"
date: 2007-12-24
forum: Wine
---

### Post by whitenerdy92 on 2007-12-24
I was trying to install the game 'Rise of Nations'. I could not do this by double-clicking on the executables in the file browser. First, I got an error message saying something like 'cannot run DOS/Windows executable, please change the suffix to the correct file format'. After that, double-clicking did nothing.  So, I used the terminal to run what I believe to be the installation/run files (rise.exe, ronsetup.exe). Here is what happened:

> *:~$ cd /media/cdrom0
*:/media/cdrom0$ wine ronsetup.exe
*:/media/cdrom0$ err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
fixme:font:WineEngRemoveFontResourceEx :stub
Sharing violation




That's it. It didn't even bring the *:~$ prompt back up, just kept the blinking cursor. Anyone know how what this means? I'm pretty sure I got it to run a few months ago just by clicking on it, but then there were some library problems or something and I was to lazy to figure it out. Anyways, anyone know what this means? Thanks.

---

### Post by markharding557 on 2007-12-27
type'winefile' in the terminel to load winefile and try your install on that
winefile is wines file manager

---

