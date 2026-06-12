---
title: "i think i have a virus"
date: 2009-02-15
forum: x86 64-bit Users
---

### Post by shaolinchamp on 2009-02-15
well nothing has been really giving me problems except for firefox.  everything i try to download somethin it tells me there is no room left on the drive, even though i have 40 gigs free.  i cant bo back to a previous page either.  i tried installing epiphany and it didnt show up in applications>internet section.  so i had to start epiphany through the terminal, and then everything i try to download something in that it closes. i cant start package manager  to remove firefox either because its unable to copy the xauthorization file.  everything else seems to work fine though. any ideas?

---

### Post by Ng Oon-Ee on 2009-02-15
Some things to try, off the top of my head...

Clearing the firefox cache?
Check if your trash has tons of files, I can't remember whether that counts as 'free' as it does in windows.

Run gparted (its called partition editor in the default menus) and see if any of your drives are full. It may be that your root is 100%, so your /tmp is not accessible.

---

### Post by sanderj on 2009-02-16
OP, post the output of "df -BG" (note the capitals), like this:

```
sander@flappie:~$ df -BG
Filesystem           1G-blocks      Used Available Use% Mounted on
/dev/sda5                  29G       22G        7G  77% /
varrun                      1G        1G        1G   1% /var/run
varlock                     1G        0G        1G   0% /var/lock
udev                        1G        1G        1G   1% /dev
devshm                      1G        1G        1G   1% /dev/shm
lrm                         1G        1G        1G   8% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon           29G       22G        7G  77% /home/sander/.gvfs
/dev/mmcblk0p1              2G        2G        1G  93% /media/disk
sander@flappie:~
```

---

### Post by halovivek on 2009-02-16
You will not get virus in Linux since it is one of the  safe system created ever. 
check your trash in your computer to delete all.
clear all the cache all.

---

### Post by shaolinchamp on 2009-02-16
yea, i uninstalled firefox and reinstalled, now it wont start.  and now everytime i click the shutdown button on the system tray, the tray disappears, and ctrl+alt+del will not work!! so i have no idea whats wrong.


pwner@sha-desktop:~$ sudo df -BG
Filesystem           1G-blocks      Used Available Use% Mounted on
/dev/sda1                 107G      102G        0G 100% /
varrun                      1G        1G        1G   1% /var/run
varlock                     1G        0G        1G   0% /var/lock
udev                        1G        1G        1G   1% /dev
devshm                      1G        1G        1G   1% /dev/shm
lrm                         1G        1G        1G   5
/lib/modules/2.6.24-23-generic/volatile
overflow                    1G        1G        1G   5% /tmp

---

### Post by jocko on 2009-02-17
> **shaolinchamp said:**
> yea, i uninstalled firefox and reinstalled, now it wont start.  and now everytime i click the shutdown button on the system tray, the tray disappears, and ctrl+alt+del will not work!! so i have no idea whats wrong.


pwner@sha-desktop:~$ sudo df -BG
Filesystem           1G-blocks      Used Available Use% Mounted on
[COLOR=Red]/dev/sda1                 107G      102G        0G 100% /[/COLOR]
varrun                      1G        1G        1G   1% /var/run
varlock                     1G        0G        1G   0% /var/lock
udev                        1G        1G        1G   1% /dev
devshm                      1G        1G        1G   1% /dev/shm
lrm                         1G        1G        1G   5
/lib/modules/2.6.24-23-generic/volatile
overflow                    1G        1G        1G   5% /tmp
Your hard drive *is* full, so every application that needs to be able to write some data to the hard drive will fail.
To get a *little* bit space back, run this in a terminal (it deletes downloaded .deb files):
```
sudo apt-get clean
```Also empty your trash. Other than that, you probably need to start deleting (or moving to another drive) files that you store in your home dir.

---

### Post by Insane_Homer on 2009-02-17
> **shaolinchamp said:**
> yea, i uninstalled firefox and reinstalled, now it wont start.  and now everytime i click the shutdown button on the system tray, the tray disappears, and ctrl+alt+del will not work!! so i have no idea whats wrong.


pwner@sha-desktop:~$ sudo df -BG
Filesystem           1G-blocks      Used Available Use% Mounted on
**[COLOR="Red"]/dev/sda1                 107G      102G        0G 100% /[/COLOR]**
varrun                      1G        1G        1G   1% /var/run
varlock                     1G        0G        1G   0% /var/lock
udev                        1G        1G        1G   1% /dev
devshm                      1G        1G        1G   1% /dev/shm
lrm                         1G        1G        1G   5
/lib/modules/2.6.24-23-generic/volatile
overflow                    1G        1G        1G   5% /tmp

delete some Pr0n mate, you're using 100% of 107 GB the disk is full...

---

### Post by alfrz on 2009-02-17
Try removing the .mozilla from your home directory, this will reset the settings on your browser.

```

$cd
$rm -r .mozilla

```

---

### Post by sanderj on 2009-02-17
You have 107 GB in use. That's quite impressive. A normal Ubuntu installation will only use a few GBs.

You could look for big files like this:

sudo find / -size +100M


BTW: is your Linux a normal installation on it's own partition? You're using not Wubi or something like that?

---

### Post by shaolinchamp on 2009-02-17
yeah im cleainrg out files now.  for some reason ctrl+alt+delele still doesnt work. and clicking on the shutdown button at the top right corner of the screen still makes my system tray disappear.

---

### Post by yther on 2009-02-17
> **shaolinchamp said:**
> yeah im cleainrg out files now.  for some reason ctrl+alt+delele still doesnt work. and clicking on the shutdown button at the top right corner of the screen still makes my system tray disappear.

Ugly things can happen on a full drive.  What probably happened (it has happened to me) is something like this:

[LIST]
[*]Drive filled up, 0 bytes free
[*]Some app tried to write to its config file
[*]There was no space left so the file got truncated to 0 bytes
[*]Therefore all settings got lost and the app now does flaky stuff
[/LIST]

With Firefox, deleting the .mozilla folder or just the profile in there will make it think you're starting it for the first time, and everything will start fresh.  However, you might want to check in there for bookmarks or whatever in case you want to keep them.

I don't know what to do about your system tray, though.  :(

---

### Post by shaolinchamp on 2009-02-17
ok i finally got into my trash dir and figured out there were alot of files in there, ones i that were there for weeks.  and i realized that i was using the wrong command to delete the trash ever since i installed ubuntu...so i cleared it out.  hopefully it will fix all the issues, but i would like to thank all of you for helping, i really appreciate it.

---

