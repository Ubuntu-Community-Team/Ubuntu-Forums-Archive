---
title: "Nothing happening: Starcraft (oldschool)"
date: 2011-10-17
forum: Wine
---

### Post by Pr0t3us on 2011-10-17
I have Ubuntu 11.10 and Wine 1.2.3

I have been trying to read various guides from google how to do only to now avail. from what i can seem to understand wine needs to know where the cdrom is? So with that from one of the more clear guides I went into wine config and in the drives tab I clicked "Add" and I set the path to "  /media/cdrom  " (parentheses not included) then when i pop in the cd to the drive..... nothing happens. I have tried copy pasting commands and just end up with command not found or cannot find whatever path i put in.

Halp me?

---

### Post by Toz on 2011-10-17
Open a terminal window and with the CD in the drive, post back the results of the following commands:
```
ls -l /media
ls -l /dev/cdrom
```

---

### Post by Pr0t3us on 2011-10-17
command = ls -1 /media
result = STARCRAFT

command =  ls -1 /dev/cdrom
result =  /dev/cdrom

---

### Post by Toz on 2011-10-17
Thats's actually a lowercase L, instead of the number one in that command. 
```
ls -l /media
ls -l /dev/cdrom
```

Could you run those commands again and copy/paste the results from the terminal back here?

---

### Post by Pr0t3us on 2011-10-17
proteus@proteus-RJ036AA-ABA-SR2030NX-NA680:~$ ls -l /media
total 2
dr-x------ 1 proteus proteus 2048 2004-08-12 07:41 STARCRAFT
proteus@proteus-RJ036AA-ABA-SR2030NX-NA680:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2011-10-17 11:45 /dev/cdrom -> sr0

---

### Post by Toz on 2011-10-17
/media/cdrom doesn't exist on your system. What happens if you set the path to **/dev/cdrom** or **/media/STARCRAFT** in wine config?

---

### Post by Pr0t3us on 2011-10-17
taking out the cd and then changing the path and clicking ok to apply and then popping in the cd back in? I did that with both, still nothing happens.

---

### Post by Toz on 2011-10-17
When you say "nothing happens", what are you expecting will happen? Is the game asking for the CD to continue? Is it about copy-protection?

Also, what is the result of the following command:
```
ls -l ~/.wine/dosdevices
```

---

### Post by Pr0t3us on 2011-10-17
When I say nothing happens thats exactly what I mean NOTHING happens. what I am expecting to happen is the installer window to come up like it would if I was in windows.

as for the command;  ls -l ~/.wine/dosdevices
 the result is:

 c: -> ../drive_c
 d: -> /media/STARCRAFT
 z: -> /

---

### Post by Toz on 2011-10-17
1. Put the CD in the drive.
2. Open your file manager and navigate to /media/STARCRAFT
3. Open a terminal window and type in "wine " (no quotes, note the space after the word wine)
4. Go back to your file manager, locate the setup program, and drag/drop it onto the terminal window. 
5. Back on the terminal window, press the Enter key

_OR_

Install PlayOnLinux (find it in your software Centre), click on Install, locate your program, and click "Install".

PlayOnLinux is a front-end to wine and greatly simplifies the installation and management of windows-based apps and games on Linux. See: [http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")

---

### Post by Pr0t3us on 2011-10-17
OMG! It worked! I did the thing like you said with the terminal.

one lil' caveat now... the cursor is sticky in the game; sticky/laggy performance in a game is a no beuno :(

any fixes to this issue?

---

### Post by Toz on 2011-10-18
**appdb.winehq.org** is a good resource for getting windows apps and games to work under wine. With respect to Starcraft, there is this page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=149]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=149"). Look at the "Cure for Slowness" section on that page. There are also a few more notes further below that on curing slowness.

---

