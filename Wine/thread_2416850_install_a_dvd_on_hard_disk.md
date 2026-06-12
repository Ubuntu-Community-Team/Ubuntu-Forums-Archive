---
title: "install a dvd on hard disk"
date: 2019-04-16
forum: Wine
---

### Post by jduns on 2019-04-16
Hi everyone. I would like to install a DVD (of an English course) on hard drive. 
I have already successfully given the following commands

```
mkdir path/to/dir
sudo mount -o loop "name-of-iso.iso" /path/to/dir
```

And I have successfully installed with wine (using the setup.exe file) the program in another folder (not in /home). 
From the new folder **the installed program** (file.exe) **starts**, it correctly asks the user credentials **but** then there is an error message (it cannot find the "language" of the course).
In fact, the installed course folder is only 80 mb, compared to an ISO of 5 GB ... I tried to link the ISO folder to the installed program folder, but it didn't resolve. If the ISO is not mounted I get an error message and the program does not start.
It is possible that the problem is that the ISO is root? Maybe I should mount the ISO as a user? In that case, how is do it?
Thank you

---

### Post by TheFu on 2019-04-16
Not all programs work under WINE.
Most need 5+ tweaks to WINE to get working. These tweaks are extremely specific to the exact program.

And after all that, some programs don't work, ever. To use them, only MS-Windows will work.

As for permissions, there isn't any shortcut to learning and understanding file and directory permissions.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) - be certain to work through this. Reading it isn't enough.

---

### Post by jduns on 2019-04-16
Thank you. But the program seems start grafically very well. The only problem is the data (lesson language) it cannot find. Any way what's "5+ tweaks"?

EDIT

Installed successfully under virtualbox! It works, but it's not the best (I have always to start virtualbox).

---

### Post by Mark Phelps on 2019-04-16
What @TheFu meant was that several different tweaks were needed for each and every Windows app in Wine -- to get each working, if they ever DO work.

Wine is a HACK that allows SOME Windows apps to run in Linux, and if the WineHQ database either does not list your apps, or rates it less than Gold, you're wasting your time: [https://appdb.winehq.org](https://appdb.winehq.org)

---

### Post by jduns on 2019-04-17
Thank you. 
From Wine site: **Latest Rating **(of this program)**: Gold. ****What works **All works. **What does not **Nothing.
But for me there is always that error (language data not available), even the folder when is data is setted as cd-rom.
Tried also with playonlinux and the latest wine release (3.20): nothing to do.

---

### Post by howefield on 2019-04-17
Thread moved to the "*Wine*" forum.

---

### Post by mastablasta on 2019-04-17
ratings are badly maintained. TES game Oblivion has platinum, is even featured on their website yet many users have problem running it. i got at least the film to run but they it crashed.

sometimes if you can't install it you can manually unpack the installer file and then run it. game Hearts of Iron 2 - i could not get it to install. i remembered i had an installed version on windows side of disk. i moved that to wine just ot see what would happen if i run it.  BOOM! running out of the box, no issues whatsoever.

---

