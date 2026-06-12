---
title: "[SOLVED] Wrath of the Lich King (WoW) Install Probs."
date: 2008-11-13
forum: Wine
---

### Post by Kenza on 2008-11-13
All the other game disk i just copied to my HD and ran them with WINE there and it worked fine. Now i Can't Copy the Installer.exe which happens to be the only file (1.3GB) anywhere. Right Clicking and Opening with "Wine Windows Program Loader" does nothing at all (which i thought really unusual). The CD Icon to the left has a lock on it (same as the file system), which when i check permissions it says "I am not the owner, so i can't change these permissions".

I'm running Wine 1.1.8

In Terminal it says this:

desktop:/media/cdrom0$ dir
DirectX  Installer.exe
Blah@Blah -desktop:/media/cdrom0$ wine Installer.exe
wine: could not load L"D:\\Installer.exe": Module not found

---

### Post by FNDII on 2008-11-13
same problem for me

---

### Post by jorj82 on 2008-11-13
Take a look at this: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

---

### Post by Kenza on 2008-11-13
Tyvm =)

---

### Post by FNDII on 2008-11-13
Ok I am still having a bit of trouble. not sure how that link solved the problem, i got this from reading it.

[I]To successfully install you may do the following:
(substitute username with your username)

sudo -i # Login as root, afaik this doesn't work with sudo.
chown -R root /home/username/.wine # Change ownership of .wine folder to root
WINEPREFIX="/home/username/.wine" wine /media/cdrom/Installer.exe # Install WotLK
chown -R username /home/username/.wine # Change ownership back
logout # logout as root

Normally i hate logging in as root, but so far it's the only thing I've been able to get working.[/I]


I think that what I have to do in order to get the game to install.
But I'm not sure that i understand how to use those instructions.

---

### Post by hikaricore on 2008-11-13
I ran into this issue on my flatmate's dualboot system today.

Simplest solution we came up with was to just reboot and copy the dvd to his hd in ***dows then install it in linux.
I couldn't be bothered to figure out why the hell half of the DVD wasn't readable from nautilus.

---

### Post by Kenza on 2008-11-13
I was just going to do the same thing, install windows on other HD again and just copy it over, but now i'm having problems with getting MS to even install on it, go figure. GL guys, might make another post since i had already checked as "solved", but yet, having the same problem here! i couldn't and wouldn't wanna' mess with Wine settings to get this installed, shouldn't have to

I WOULDN't DO THIS:
sudo -i # Login as root, afaik this doesn't work with sudo.
chown -R root /home/username/.wine # Change ownership of .wine folder to root
WINEPREFIX="/home/username/.wine" wine /media/cdrom/Installer.exe # Install WotLK
chown -R username /home/username/.wine # Change ownership back
logout # logout as root

Normally i hate logging in as root, but so far it's the only thing I've been able to get working.

THERE HAS'D TO BE A BETTER WAY!

---

### Post by FNDII on 2008-11-13
worldofwarcraft.com/lichking/download

I upgraded my acount on the website and am currently using the blizzard downloader to install the game.

I'll post back if it all works

---

### Post by toupeiro on 2008-11-13
I can confirm this worked for me:

As root (sudo didn't seem to work for me, but by all means try it because I can't think of a good reason why it didn't except I'm just sleepy...) mount the DVD to a directory with the following parameters: (to get a root prompt type: sudo su -) **sudo mount -t udf -o ro,unhide,uid=1000 /dev/<your_device> /your/directory**

Now, simply : wine ./Installer.exe as your user account from the DVD...  nothing special there...

If you have your game installed into another location other than the default, then go into ~/.wine/drive_c/Program Files and then type: ln -s /path/to/your/wow/directory

this will create a link so things like expansions can find the default path, but you can still keep your game wherever you want it.

EDIT: BTW, this is not a wine issue, moreso a DVD design issue which requires special mount options...

---

### Post by jessejamesallen on 2008-11-13
Sooooo, would somebody please help me by translating the former message into something with more detail for somebody who has extremely little experience using a terminal and realizes that he should likely not be logging on as a superuser but can't help himself because he really wants to log onto wow?

---

### Post by FNDII on 2008-11-13
Yea I don't understand much on how to fix the problem, I know that I am looking at the answer but I guess I dont understand how to read the instructions.

On a side note im 85% done downloading the Lich King through the blizzard downloader, I should be playing soon - downloading it is the fix for people who don't own a dvd drive - so it should work

---

### Post by toupeiro on 2008-11-13
> **jessejamesallen said:**
> Sooooo, would somebody please help me by translating the former message into something with more detail for somebody who has extremely little experience using a terminal and realizes that he should likely not be logging on as a superuser but can't help himself because he really wants to log onto wow?

... I thought what I said was straightforward, but fair enough. :)
[I]
New CLI user TIP: for directory names with spaces, type a part of the name before the first space, then hit the <TAB> key and it will usually autocomplete the full directory name unless there is another directory name with almost the exact same naming and case sensitivity.  It will help you with directories like "Program Files" or "World of Warcraft"[/I]


If your current WOW install IS in the default .wine directory, do the following:

Step one:

Open a terminal window

Step two:
type the following commands:

> 
sudo mkdir /mnt/temp
sudo su -
mount | grep cdrom 
[I](look for something that says /dev/<something> and note it, you will need it for the next step)
[/I]
mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/temp
exit
cd /mnt/temp
wine Installer.exe

...proceed to install...



Step 3: Clean up
> 
sudo umount /mnt/temp
sudo rmdir /mnt/temp 




If your World of Warcraft Directory is NOT in /home/yourID/.wine/drive_c/program files/World of Warcraft do the following:

Step one:

Open a Terminal

Step two: 

Do the following commands:

> 
sudo mkdir /mnt/temp
sudo su -
mount | grep cdrom 
[I](look for something that says /dev/<something> and note it, you will need it for the next step)
[/I]
mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/temp
exit
cd ~/.wine/drive_c/Program Files
ln -s /where/your/WOW/is/Installed "World of Warcraft"
cd /mnt/temp
wine Installer.exe

... Proceed to install ...


Step 3: Clean up 

> 

sudo umount /mnt/temp
sudo rmdir /mnt/temp 



---

### Post by FNDII on 2008-11-13
perfect step by step for low end user like me follow everything and no error till the end


fndii@Armor:/mnt/temp$ wine Installer.exe
wine: could not load L"H:\\Installer.exe": Module not found

---

### Post by toupeiro on 2008-11-13
> **FNDII said:**
> perfect step by step for low end user like me follow everything and no error till the end


fndii@Armor:/mnt/temp$ wine Installer.exe
wine: could not load L"H:\\Installer.exe": Module not found

Interesting...  in mnt/tmp, please type: ls -al and tell me what you see?

---

### Post by weaselkeeper on 2008-11-13
Ran into the following problems attempting to install Wrath on Ubuntu 8.10

1) Some kind of mounting issue with the DVD
2) Inability to "Agree" with the EULA

For 1) I mounted the dvd with unhide as suggested upthread 

For 2) I installed ie4linux (spit) and that didn't work. So I added winehq's apt repo to my sources, and upgraded to the dev version of wine, which then allowed the install to proceed normally. There are some sound issues, and I might downgrade back to the release version of wine for the game, but the installer seems to be happy now.

---

### Post by FNDII on 2008-11-13
fndii@Armor:~$ ls -al
total 1696
drwxr-xr-x 44 fndii fndii   4096 2008-11-13 05:05 .
drwxr-xr-x  3 root  root    4096 2008-09-27 07:54 ..
drwx------  3 fndii fndii   4096 2008-09-27 10:10 .adobe
-rw-------  1 fndii fndii    871 2008-11-13 05:14 .bash_history
-rw-r--r--  1 fndii fndii    220 2008-09-27 07:54 .bash_logout
-rw-r--r--  1 fndii fndii   2298 2008-09-27 07:54 .bashrc
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 08:00 .cache
drwx------  3 fndii fndii   4096 2008-09-27 09:58 .compiz
drwxr-xr-x  7 fndii fndii   4096 2008-09-28 04:13 .config
drwxr-xr-x  5 fndii fndii   4096 2008-11-13 05:00 Desktop
-rw-------  1 fndii fndii     28 2008-11-13 01:28 .dmrc
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:00 Documents
drwxr-x---  2 fndii fndii   4096 2008-09-28 07:05 .easytag
-rw-------  1 fndii fndii     16 2008-09-27 08:00 .esd_auth
drwxr-xr-x  7 fndii fndii   4096 2008-11-13 01:27 .evolution
lrwxrwxrwx  1 fndii fndii     26 2008-09-27 07:54 Examples -> /usr/share/example-content
-rw-r--r--  1 fndii fndii 839752 2008-10-21 08:06 Firefox_wallpaper.png
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:23 .fontconfig
drwx------  5 fndii fndii   4096 2008-11-13 01:28 .gconf
drwx------  2 fndii fndii   4096 2008-11-13 05:14 .gconfd
-rw-r-----  1 fndii fndii      0 2008-11-13 01:10 .gksu.lock
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 08:00 .gnome
drwx------ 14 fndii fndii   4096 2008-11-13 05:00 .gnome2
drwx------  2 fndii fndii   4096 2008-09-27 08:00 .gnome2_private
drwx------  2 fndii fndii   4096 2008-11-13 01:28 .gnupg
drwxr-xr-x  2 fndii fndii   4096 2008-10-30 10:47 .gstreamer-0.10
-rw-r--r--  1 fndii fndii    108 2008-11-13 03:30 .gtk-bookmarks
-rw-r--r--  1 fndii fndii     87 2008-09-27 08:00 .gtkrc-1.2-gnome2
drwx------  2 fndii fndii   4096 2008-09-27 08:55 .gvfs
-rw-------  1 fndii fndii   2634 2008-11-13 01:28 .ICEauthority
drwx------  3 fndii fndii   4096 2008-09-28 06:48 .kde
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 08:00 .local
drwx------  3 fndii fndii   4096 2008-09-27 10:10 .macromedia
drwxr-xr-x  3 fndii fndii   4096 2008-09-28 06:51 .mcop
-rw-------  1 fndii fndii     31 2008-09-28 06:51 .mcoprc
drwx------  3 fndii fndii   4096 2008-09-27 08:00 .metacity
drwx------  4 fndii fndii   4096 2008-09-27 09:08 .mozilla
drwxr-xr-x  7 fndii fndii   4096 2008-10-26 21:23 Music
drwxr-xr-x  3 fndii fndii   4096 2008-11-13 01:27 .nautilus
drwxr-xr-x  2 fndii fndii   4096 2008-11-13 01:21 Pictures
-rw-r--r--  1 fndii fndii    566 2008-09-27 07:54 .profile
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:00 Public
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 09:06 .pulse
-rw-------  1 fndii fndii    256 2008-09-27 08:55 .pulse-cookie
drwx------  5 fndii fndii   4096 2008-11-08 13:22 .purple
drwxr-xr-x  2 fndii fndii   4096 2008-11-05 15:41 .qt
-rw-r--r--  1 fndii fndii 447809 2008-11-13 05:05 .recently-used.xbel
drwx------  2 fndii fndii   4096 2008-09-27 08:55 .ssh
-rw-r--r--  1 fndii fndii      0 2008-09-27 08:05 .sudo_as_admin_successful
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:00 Templates
drwx------  4 fndii fndii   4096 2008-09-27 16:35 .thumbnails
drwxr-xr-x  5 fndii fndii   4096 2008-09-28 03:40 .transmission
drwxr-xr-x  2 fndii fndii   4096 2008-10-07 18:37 .update-manager-core
drwx------  2 fndii fndii   4096 2008-09-27 08:00 .update-notifier
drwxr-xr-x  4 fndii fndii   4096 2008-11-11 08:01 Videos
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 16:36 .vlc
drwx------  2 fndii fndii   4096 2008-10-02 07:30 .w3m
drwxr-xr-x  2 fndii fndii   4096 2008-11-13 01:29 .wapi
drwxr-xr-x  4 fndii fndii   4096 2008-11-13 05:05 .wine
-rw-------  1 fndii fndii    116 2008-11-13 01:28 .Xauthority
drwxr-xr-x  2 fndii fndii   4096 2008-09-28 06:49 .xine
-rw-r--r--  1 fndii fndii 200043 2008-11-13 03:42 .xsession-errors

---

### Post by toupeiro on 2008-11-13
> **FNDII said:**
> fndii@Armor:~$ ls -al
total 1696
drwxr-xr-x 44 fndii fndii   4096 2008-11-13 05:05 .
drwxr-xr-x  3 root  root    4096 2008-09-27 07:54 ..
drwx------  3 fndii fndii   4096 2008-09-27 10:10 .adobe
-rw-------  1 fndii fndii    871 2008-11-13 05:14 .bash_history
-rw-r--r--  1 fndii fndii    220 2008-09-27 07:54 .bash_logout
-rw-r--r--  1 fndii fndii   2298 2008-09-27 07:54 .bashrc
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 08:00 .cache
drwx------  3 fndii fndii   4096 2008-09-27 09:58 .compiz
drwxr-xr-x  7 fndii fndii   4096 2008-09-28 04:13 .config
drwxr-xr-x  5 fndii fndii   4096 2008-11-13 05:00 Desktop
-rw-------  1 fndii fndii     28 2008-11-13 01:28 .dmrc
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:00 Documents
drwxr-x---  2 fndii fndii   4096 2008-09-28 07:05 .easytag
-rw-------  1 fndii fndii     16 2008-09-27 08:00 .esd_auth
drwxr-xr-x  7 fndii fndii   4096 2008-11-13 01:27 .evolution
lrwxrwxrwx  1 fndii fndii     26 2008-09-27 07:54 Examples -> /usr/share/example-content
-rw-r--r--  1 fndii fndii 839752 2008-10-21 08:06 Firefox_wallpaper.png
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:23 .fontconfig
drwx------  5 fndii fndii   4096 2008-11-13 01:28 .gconf
drwx------  2 fndii fndii   4096 2008-11-13 05:14 .gconfd
-rw-r-----  1 fndii fndii      0 2008-11-13 01:10 .gksu.lock
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 08:00 .gnome
drwx------ 14 fndii fndii   4096 2008-11-13 05:00 .gnome2
drwx------  2 fndii fndii   4096 2008-09-27 08:00 .gnome2_private
drwx------  2 fndii fndii   4096 2008-11-13 01:28 .gnupg
drwxr-xr-x  2 fndii fndii   4096 2008-10-30 10:47 .gstreamer-0.10
-rw-r--r--  1 fndii fndii    108 2008-11-13 03:30 .gtk-bookmarks
-rw-r--r--  1 fndii fndii     87 2008-09-27 08:00 .gtkrc-1.2-gnome2
drwx------  2 fndii fndii   4096 2008-09-27 08:55 .gvfs
-rw-------  1 fndii fndii   2634 2008-11-13 01:28 .ICEauthority
drwx------  3 fndii fndii   4096 2008-09-28 06:48 .kde
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 08:00 .local
drwx------  3 fndii fndii   4096 2008-09-27 10:10 .macromedia
drwxr-xr-x  3 fndii fndii   4096 2008-09-28 06:51 .mcop
-rw-------  1 fndii fndii     31 2008-09-28 06:51 .mcoprc
drwx------  3 fndii fndii   4096 2008-09-27 08:00 .metacity
drwx------  4 fndii fndii   4096 2008-09-27 09:08 .mozilla
drwxr-xr-x  7 fndii fndii   4096 2008-10-26 21:23 Music
drwxr-xr-x  3 fndii fndii   4096 2008-11-13 01:27 .nautilus
drwxr-xr-x  2 fndii fndii   4096 2008-11-13 01:21 Pictures
-rw-r--r--  1 fndii fndii    566 2008-09-27 07:54 .profile
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:00 Public
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 09:06 .pulse
-rw-------  1 fndii fndii    256 2008-09-27 08:55 .pulse-cookie
drwx------  5 fndii fndii   4096 2008-11-08 13:22 .purple
drwxr-xr-x  2 fndii fndii   4096 2008-11-05 15:41 .qt
-rw-r--r--  1 fndii fndii 447809 2008-11-13 05:05 .recently-used.xbel
drwx------  2 fndii fndii   4096 2008-09-27 08:55 .ssh
-rw-r--r--  1 fndii fndii      0 2008-09-27 08:05 .sudo_as_admin_successful
drwxr-xr-x  2 fndii fndii   4096 2008-09-27 08:00 Templates
drwx------  4 fndii fndii   4096 2008-09-27 16:35 .thumbnails
drwxr-xr-x  5 fndii fndii   4096 2008-09-28 03:40 .transmission
drwxr-xr-x  2 fndii fndii   4096 2008-10-07 18:37 .update-manager-core
drwx------  2 fndii fndii   4096 2008-09-27 08:00 .update-notifier
drwxr-xr-x  4 fndii fndii   4096 2008-11-11 08:01 Videos
drwxr-xr-x  3 fndii fndii   4096 2008-09-27 16:36 .vlc
drwx------  2 fndii fndii   4096 2008-10-02 07:30 .w3m
drwxr-xr-x  2 fndii fndii   4096 2008-11-13 01:29 .wapi
drwxr-xr-x  4 fndii fndii   4096 2008-11-13 05:05 .wine
-rw-------  1 fndii fndii    116 2008-11-13 01:28 .Xauthority
drwxr-xr-x  2 fndii fndii   4096 2008-09-28 06:49 .xine
-rw-r--r--  1 fndii fndii 200043 2008-11-13 03:42 .xsession-errors

this looks like your home directory.  

type:

cd /mnt/tmp
ls -al

and paste those results here please?

---

### Post by jessejamesallen on 2008-11-13
> **FNDII said:**
> perfect step by step for low end user like me follow everything and no error till the end


fndii@Armor:/mnt/temp$ wine Installer.exe
wine: could not load L"H:\\Installer.exe": Module not found

Exactly the same for me.

---

### Post by illepic on 2008-11-13
I had to copy the contents of the Wrath DVD to a windows drive and then transfer the folder across my network to my Ubuntu box.  Then I just double clicked the Installer.exe file.  Installed incredibly fast and painlessly at that point

---

### Post by jessejamesallen on 2008-11-13
> **illepic said:**
> I had to copy the contents of the Wrath DVD to a windows drive and then transfer the folder across my network to my Ubuntu box.  Then I just double clicked the Installer.exe file.  Installed incredibly fast and painlessly at that point

Would be nice, but my buddy that set me up w/ Ubuntu didn't partition my drive.  :(

---

### Post by toupeiro on 2008-11-13
> **jessejamesallen said:**
> Exactly the same for me.

It seems I may have missed a step in my translation that I suppose I didn't think important.  I unmounted /media/cdrom before I mounted /mnt/tmp.  Shouldn't have made a diffference but ..  maybe it did.


so if you have done everything in one of the two examples above, lets go a little further down the rabbit hole:

> 
sudo umount /mnt/tmp
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/tmp
cd /mnt/tmp
wine Installer.exe



---

### Post by toupeiro on 2008-11-13
> **jessejamesallen said:**
> Exactly the same for me.

It seems I may have missed a step in my translation that I suppose I didn't think important.  I unmounted /media/cdrom before I mounted /mnt/tmp.  Shouldn't have made a diffference but ..  maybe it did.


so if you have done everything in one of the two examples above, lets go a little further down the rabbit hole:

> 
sudo umount /mnt/tmp
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/tmp
cd /mnt/tmp
wine Installer.exe



Step three would then become:

> 
sudo umount /mnt/temp
sudo rmdir /mnt/temp 
sudo mount /media/cdrom


---

### Post by jessejamesallen on 2008-11-13
drwxr-xr-x 3  503 dialout        592 2008-08-28 23:28 .

drwxr-xr-x 3 root root          4096 2008-11-13 03:07 ..

-rw-r--r-- 1  503 dialout         48 2008-08-28 23:28 autorun.inf

drwx------ 2  503 dialout        492 2008-08-28 23:28 DirectX

-rw-r--r-- 1  503 dialout     109638 2008-08-28 23:28 disc.ico

-rwx------ 1  503 dialout    1407832 2008-08-28 23:28 Installer.exe

-rwx------ 1  503 dialout 1627861562 2008-08-28 23:22 Installer Tome 2.mpq

-rwx------ 1  503 dialout 2488952542 2008-08-28 23:24 Installer Tome 3.mpq

-rwx------ 1  503 dialout 2375920098 2008-08-28 23:26 Installer Tome 4.mpq

-rwx------ 1  503 dialout 1197605083 2008-08-28 23:27 Installer Tome 5.mpq

-rwx------ 1  503 dialout  124584980 2008-08-28 23:27 Installer Tome.mpq

-rwx------ 1  503 dialout  435111965 2008-08-28 23:28 Movies.mpq

 

This is what I get for the ls -al command in the /mnt/temp directory.

---

### Post by FNDII on 2008-11-13
fndii@Armor:/mnt/temp$ ls -al
total 1384
drwxr-xr-x 3  503 dialout     592 2008-08-29 01:28 .
drwxr-xr-x 3 root root       4096 2008-11-13 05:02 ..
drwx------ 2  503 dialout     492 2008-08-29 01:28 DirectX
-rwx------ 1  503 dialout 1407832 2008-08-29 01:28 Installer.exe
fndii@Armor:/mnt/temp$

---

### Post by toupeiro on 2008-11-13
> **jessejamesallen said:**
> drwxr-xr-x 3  503 dialout        592 2008-08-28 23:28 .

drwxr-xr-x 3 root root          4096 2008-11-13 03:07 ..

-rw-r--r-- 1  503 dialout         48 2008-08-28 23:28 autorun.inf

drwx------ 2  503 dialout        492 2008-08-28 23:28 DirectX

-rw-r--r-- 1  503 dialout     109638 2008-08-28 23:28 disc.ico

-rwx------ 1  503 dialout    1407832 2008-08-28 23:28 Installer.exe

-rwx------ 1  503 dialout 1627861562 2008-08-28 23:22 Installer Tome 2.mpq

-rwx------ 1  503 dialout 2488952542 2008-08-28 23:24 Installer Tome 3.mpq

-rwx------ 1  503 dialout 2375920098 2008-08-28 23:26 Installer Tome 4.mpq

-rwx------ 1  503 dialout 1197605083 2008-08-28 23:27 Installer Tome 5.mpq

-rwx------ 1  503 dialout  124584980 2008-08-28 23:27 Installer Tome.mpq

-rwx------ 1  503 dialout  435111965 2008-08-28 23:28 Movies.mpq

 

This is what I get for the ls -al command in the /mnt/temp directory.

mmmm  your permissions...  503:dialout...  I think thats your problem, but I can't rightfully explain why they are like that.  here are mine:

> 
drwxr-xr-x 3 toupeiro dialout        592 2008-08-28 22:28 .
drwxr-xr-x 3 root     root          4096 2008-11-13 02:29 ..
-rw-r--r-- 1 toupeiro dialout         48 2008-08-28 22:28 autorun.inf
drwx------ 2 toupeiro dialout        492 2008-08-28 22:28 DirectX
-rw-r--r-- 1 toupeiro dialout     109638 2008-08-28 22:28 disc.ico
-rwx------ 1 toupeiro dialout    1407832 2008-08-28 22:28 Installer.exe
-rwx------ 1 toupeiro dialout 1627861562 2008-08-28 22:22 Installer Tome 2.mpq
-rwx------ 1 toupeiro dialout 2488952542 2008-08-28 22:24 Installer Tome 3.mpq
-rwx------ 1 toupeiro dialout 2375920098 2008-08-28 22:26 Installer Tome 4.mpq
-rwx------ 1 toupeiro dialout 1197605083 2008-08-28 22:27 Installer Tome 5.mpq
-rwx------ 1 toupeiro dialout  124584980 2008-08-28 22:27 Installer Tome.mpq
-rwx------ 1 toupeiro dialout  435111965 2008-08-28 22:28 Movies.mpq
toupeiro@utileyez:/mnt/tmp$

Note that I am set as the owner, and my permissions are rwx (read/write/execute)...


 We need to get those user bits set to you...  in the mount command, try changing "uid=1000" to user=<yourlogonID> whatever that happens to be, when you mount it.  I am really not sure why you are getting the strange rights, but I am 100% sure thats why you are getting your error.

---

### Post by toupeiro on 2008-11-13
> **FNDII said:**
> fndii@Armor:/mnt/temp$ ls -al
total 1384
drwxr-xr-x 3  503 dialout     592 2008-08-29 01:28 .
drwxr-xr-x 3 root root       4096 2008-11-13 05:02 ..
drwx------ 2  503 dialout     492 2008-08-29 01:28 DirectX
-rwx------ 1  503 dialout 1407832 2008-08-29 01:28 Installer.exe
fndii@Armor:/mnt/temp$

It looks here like your unhide switch did not get set for some reason, whereas when JesseJames did it, his did get set..  Try my alternate method that unmounts your cdrom before it mounts your /mnt/tmp directory to your cdrom.  Hopefully that will get you better mileage.

Are you both running an 8.10 version of Ubuntu or Kubuntu or Something=untu?

Jesse: since you got the directory mounted, and if you have ample free hard drive space, you can probably make a directory in /tmp and then type:

 sudo cp -R * /tmp/yourdirectory.
 <wait about 10-20 minutes>
 sudo chown -R <youruserID> /tmp/yourdirectory
 wine /tmp/yourdirectory/Installer.exe

---

### Post by jessejamesallen on 2008-11-13
As far as the version of Ubuntu, I'm running hardy heron, the version is 8.0.4, and hadn't had any issues installing BC in Wine.  As far as my recent progress using your help, the installer window opened this time, and I was able to read the EULA, but the "Agree" button didn't pop up.  :(

---

### Post by jessejamesallen on 2008-11-13
hehe, I realize that I think that I made a directory when you had me make the /mnt/temp one, but I'm a little afraid of slaughtering my computer not knowing exactly what I should enter as a command when I'm in superuser mode.  I hate to bug you so much when you've already helped tons, but do ya think you could be more specific?  (I'm very, very inexperienced w/ this.)

---

### Post by jessejamesallen on 2008-11-13
Oh, and I've got 37G available, should be plenty for w/e is necessary.  Also, when you type /tmp/yourdirectory 
what do you mean me to type in the place of "yourdirectory"?

---

### Post by toupeiro on 2008-11-13
> **jessejamesallen said:**
> As far as the version of Ubuntu, I'm running hardy heron, the version is 8.0.4, and hadn't had any issues installing BC in Wine.  As far as my recent progress using your help, the installer window opened this time, and I was able to read the EULA, but the "Agree" button didn't pop up.  :(

Excellent!   you are well on your way!  And for being new to CLI, you both are doing a fine job!  I encourage you to practice and familiarize yourself with it.  it can seem intimidating, but repeating practices like we are doing will get you comfortable with it in no time, and it will become very efficient for you.

The reason you are getting this was determined on other threads I've read to be the version of wine you are using.  I don't think I encountered this myself because I am using the latest wine version available.

To correct this, follow the instructions on the URL below to get your version of wine updated to the latest version.  Then, your problem should be resolved, and you can continue the installation.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

when I say "yourdirectory" I mean a name which you choose like "test" or "wotlk" :)  It can be anything.  so for example

If you created a directory in /tmp called wotlk using the following command:
mkdir /tmp/wotlk

then the copy command from /mnt/tmp would look like this:

yourID@/mnt/tmp$ **sudo cp -R * /tmp/wotlk**

---

### Post by hikaricore on 2008-11-13
I'm wondering if this is the result of some strange disc protection or just a batch of bad dvd mastering.
I've never seen a video or data dvd with such whacked out file permissions when mounted.

Anyone got any thoughts on these possibilities?

---

### Post by jessejamesallen on 2008-11-13
Ok, thanks tons, and I'll do that immediately.  I'll post again w/ an update when I find out if this works.

---

### Post by toupeiro on 2008-11-13
> **hikaricore said:**
> I'm wondering if this is the result of some strange disc protection or just a batch of bad dvd mastering.
I've never seen a video or data dvd with such whacked out file permissions when mounted.

Anyone got any thoughts on these possibilities?

Its a new one on me!  It could be strange disc protection .. but to what advantage, I really don't know.  Its not exactly like you can use it without an account. :)  Not to mention, you need to upgrade your existing account with a CD-Key even if you have installed it to be able to see the content.

Its definitely annoying.  I'll probably do a 'dd' of it now that I've got it mounted with the unhide switch and burn my own un-blizzard'ed copy. :P

---

### Post by toupeiro on 2008-11-13
> **jessejamesallen said:**
> Ok, thanks tons, and I'll do that immediately.  I'll post again w/ an update when I find out if this works.

My pleasure.  I think this will be enough to get you installed and working. :)


FNDII: it probably got buried by posts, but here is the link to the step I wanted you to take to see if it fixes the problem for you.  If you follow these steps, and can see the files that Jesse and myself are seeing as listed in the posts on this thread, then you can use the copy commands I've shared to copy from the CD to your hard drive if you still cannot do installs from the CD like Jesse. (still no real explanation there as to why my permissions were ok)

[http://ubuntuforums.org/showpost.php?p=6166801&postcount=21](http://ubuntuforums.org/showpost.php?p=6166801&postcount=21)

I will probably be going to bed soon, but I will check in on this thread tomorrow morning.  I hope there is enough info here to get you two going!

Cheers!

 -T.

---

### Post by jessejamesallen on 2008-11-13
> **toupeiro said:**
> My pleasure.  I think this will be enough to get you installed and working. :)


FNDII: it probably got buried by posts, but here is the link to the step I wanted you to take to see if it fixes the problem for you.  If you follow these steps, and can see the files that Jesse and myself are seeing as listed in the posts on this thread, then you can use the copy commands I've shared to copy from the CD to your hard drive if you still cannot do installs from the CD like Jesse. (still no real explanation there as to why my permissions were ok)

[http://ubuntuforums.org/showpost.php?p=6166801&postcount=21](http://ubuntuforums.org/showpost.php?p=6166801&postcount=21)

I will probably be going to bed soon, but I will check in on this thread tomorrow morning.  I hope there is enough info here to get you two going!

Cheers!

 -T.

You beautiful beautiful man, I've no idea if wow will work now, but it's sure installing!!  Couldn't have been more helpful, and I was lucky to find ya.  G'night and sweet dreams.

---

### Post by toupeiro on 2008-11-13
> **jessejamesallen said:**
> You beautiful beautiful man, I've no idea if wow will work now, but it's sure installing!!  Couldn't have been more helpful, and I was lucky to find ya.  G'night and sweet dreams.

Awesome!  Very happy to hear it, and to have been able to help! :)  And congrats at braving the CLI!

---

### Post by Bahb on 2008-11-13
I was referred to this thread by tcoffeep from [http://ubuntuforums.org/showthread.php?p=6166220](http://ubuntuforums.org/showthread.php?p=6166220) I am attempting to install wrath on cxgames, and tcoffeep said that this worked for him, however I too am stuck on the EULA, I just double checked and I am using the latest release of CX to no avail, can I install this in wine and it still work for CX, or is there perhaps an actual solution as yet?

Edit: im gonna do it and hope it doesn't break anything

---

### Post by oodledoodle on 2008-11-13
Ok guys, I have a way of installing without changing root permissions, copying from windows etc. You will however need a networked windows computer that you can access via samba. 

Put your wotlk dvd into your windows pc and share the drive on the network. follow the windows prompts if needed. You should be able to see it in your Network folder in ubuntu, provided that they are both on your home network. 

Opening the file "installer.exe" in the shared folder should now work as it should, and should be a little quicker and less risky than other methods described. 

Hope this helps someone else, it worked for me.

This, by the way, is using wine 1.1.8

---

### Post by laffys on 2008-11-13
mike@mike-desktop:/mnt/tmp$ ls -al
total 8058178
drwxr-xr-x 3  503 dialout        592 2008-08-29 00:28 .
drwxr-xr-x 4 root root          4096 2008-11-13 08:25 ..
-rw-r--r-- 1  503 dialout         48 2008-08-29 00:28 autorun.inf
drwx------ 2  503 dialout        492 2008-08-29 00:28 DirectX
-rw-r--r-- 1  503 dialout     109638 2008-08-29 00:28 disc.ico
-rwx------ 1  503 dialout    1407832 2008-08-29 00:28 Installer.exe
-rwx------ 1  503 dialout 1627861562 2008-08-29 00:22 Installer Tome 2.mpq
-rwx------ 1  503 dialout 2488952542 2008-08-29 00:24 Installer Tome 3.mpq
-rwx------ 1  503 dialout 2375920098 2008-08-29 00:26 Installer Tome 4.mpq
-rwx------ 1  503 dialout 1197605083 2008-08-29 00:27 Installer Tome 5.mpq
-rwx------ 1  503 dialout  124584980 2008-08-29 00:27 Installer Tome.mpq
-rwx------ 1  503 dialout  435111965 2008-08-29 00:28 Movies.mpq


OK I still get this message, after switching the uid=1000 to uid=mike any other suggestions as of why?

---

### Post by toupeiro on 2008-11-13
> 
I was referred to this thread by tcoffeep from [http://ubuntuforums.org/showthread.php?p=6166220](http://ubuntuforums.org/showthread.php?p=6166220) I am attempting to install wrath on cxgames, and tcoffeep said that this worked for him, however I too am stuck on the EULA, I just double checked and I am using the latest release of CX to no avail, can I install this in wine and it still work for CX, or is there perhaps an actual solution as yet?

Edit: im gonna do it and hope it doesn't break anything

I used to be a Cedega user, and I was able to upgrade wine and not have it break anything.  I'd say give it a shot.


> **laffys said:**
> mike@mike-desktop:/mnt/tmp$ ls -al
total 8058178
drwxr-xr-x 3  503 dialout        592 2008-08-29 00:28 .
drwxr-xr-x 4 root root          4096 2008-11-13 08:25 ..
-rw-r--r-- 1  503 dialout         48 2008-08-29 00:28 autorun.inf
drwx------ 2  503 dialout        492 2008-08-29 00:28 DirectX
-rw-r--r-- 1  503 dialout     109638 2008-08-29 00:28 disc.ico
-rwx------ 1  503 dialout    1407832 2008-08-29 00:28 Installer.exe
-rwx------ 1  503 dialout 1627861562 2008-08-29 00:22 Installer Tome 2.mpq
-rwx------ 1  503 dialout 2488952542 2008-08-29 00:24 Installer Tome 3.mpq
-rwx------ 1  503 dialout 2375920098 2008-08-29 00:26 Installer Tome 4.mpq
-rwx------ 1  503 dialout 1197605083 2008-08-29 00:27 Installer Tome 5.mpq
-rwx------ 1  503 dialout  124584980 2008-08-29 00:27 Installer Tome.mpq
-rwx------ 1  503 dialout  435111965 2008-08-29 00:28 Movies.mpq


OK I still get this message, after switching the uid=1000 to uid=mike any other suggestions as of why?

It seems mileage is varying on my first fix.  If you tried the previous steps to no avail, this should work for you, but I have a very important Disclaimer to this version of installing WOTLK:

ONCE YOU DO THIS, MAKE SURE YOU DO THE CLEANUP STEP AT THE END!!! 



-------------------

The ***"Damnit Blizzard why'd you make this so hard"*** Method:

*I'm going to assume you have followed instructions defined earlier in this thread, including upgrading to the latest version of wine.*

From a terminal window:

Step 1:  Determine the Device ID of your CDROM.  look for /dev/<deviceID> and note it. (if you followed my directions previously, you already know this)
> mount | grep cdrom

If you already unmounted your CDROM in one of the previous steps without doing cleanup, you will likely get nothing in return.  Should that be the case type this:

sudo mount /media/cdrom
mount | grep cdrom



Step 2:  Note the current OWNER of your /dev/<DeviceID>

> ls -al /dev/<DeviceID> | awk '{print $3}'

Step 3: Change the OWNER of your CD-ROM to YOU.

> sudo chown <yourusername> /dev/<DeviceID>

Step 4:  Unmount All instances of your CD-ROM you mounted in previous instruction on this thread.

> 
sudo umount /media/cdrom
sudo umount /mnt/tmp



Step 5: Change the owner of /mnt/tmp to YOU.

> sudo chown <yourusername> /mnt/tmp

Step 6:remount using my previous mount command:

> sudo mount -t udf -o ro,unhide,user=<yourusername> /dev/<something> /mnt/tmp

Step 7: Verify the OWNER of all the files on the CD are owned by YOU.

> ls -al /mnt/tmp

you should get output that has your username in the place of mine:
total 8058178
drwxr-xr-x 3 toupeiro dialout        592 2008-08-28 22:28 .
drwxr-xr-x 3 root     root          4096 2008-11-13 02:29 ..
-rw-r--r-- 1 toupeiro dialout         48 2008-08-28 22:28 autorun.inf
drwx------ 2 toupeiro dialout        492 2008-08-28 22:28 DirectX
-rw-r--r-- 1 toupeiro dialout     109638 2008-08-28 22:28 disc.ico
-rwx------ 1 toupeiro dialout    1407832 2008-08-28 22:28 Installer.exe
-rwx------ 1 toupeiro dialout 1627861562 2008-08-28 22:22 Installer Tome 2.mpq
-rwx------ 1 toupeiro dialout 2488952542 2008-08-28 22:24 Installer Tome 3.mpq
-rwx------ 1 toupeiro dialout 2375920098 2008-08-28 22:26 Installer Tome 4.mpq
-rwx------ 1 toupeiro dialout 1197605083 2008-08-28 22:27 Installer Tome 5.mpq
-rwx------ 1 toupeiro dialout  124584980 2008-08-28 22:27 Installer Tome.mpq
-rwx------ 1 toupeiro dialout  435111965 2008-08-28 22:28 Movies.mpq




If you DO NOT have your username set here, skip the next step, and go to CLEANUP, because this fix, for whatever reason, did not work for you.

Step 7: Proceed to install, now that you have verified your USERNAME has read/write/execute permissions on the CD-ROM files, and the unhide switch is truly showing you all the files.

> cd /mnt/tmp
wine Installer.exe

Step 8: Upgrade your account.  Do not use the blizzard account updater in the installation, it does not work.  Instead, go to [www.worldofwarcraft.com](www.worldofwarcraft.com) and do it from the main screen there.

CLEANUP:  Once you have upgraded your account and verified your install, we need to change your CD-ROM permissions back to the way they were, or it will cause problems for other users of your system...


> 
sudo umount /mnt/tmp
***sudo chown <original_ID_you_recorded_from_step_2> /dev/<DeviceID>***   <---- Very important
sudo mount /media/cdrom
sudo rmdir /mnt/tmp




Be sure to tell Blizzard Entertainment your feelings about their new DVD-burning methods. :-D

I hope this gets my fellow linux wowers a bit further!

Cheers!


-T.

---

### Post by benjick on 2008-11-13
> **toupeiro said:**
> sudo umount /mnt/tmp
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/tmp
exit
cd /mnt/tmp
wine Installer.exe

Confirmed, works. Thanks ALOT! :)

---

### Post by toupeiro on 2008-11-13
To make searching easier, I thought I would combine all the different guides into one post so you don't have to piecemeal them together:

TIPS:

*  Use <tab> to complete directory names with spaces when typing them.
*  If you do not wish to use <tab> you can use the full file or directory name, with spaces, keeping case sensitivity in mind as long as you put it in quotes (example: /media/"Lich King")
*  DO NOT cut and paste these commands before reviewing them.  There are portions of them, identified with <something_here> that you need to fill in with your systems unique information.  The steps should explain to you how to acquire this information.

PRE-INSTALL:

*  Follow [this guide]("http://www.winehq.org/site/download-deb") and download the latest version of wine if you have not already done so.


**_Guide 1: Worked for me, not for everybody._**
This guide has a part I and a part II, but you only need to do one or the other, please read the description of each part to see which applies to you.

[B]
I[/B].  If your current WOW install IS in the default .wine directory, do the following:

Step 1: 
Open a Terminal Window

Step 2:  Perform the following commands:

> 
sudo mkdir /mnt/tmp
mount | grep cdrom
(look for something that says /dev/<something> and note it, you will need it for the next steps)
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/tmp

cd /mnt/tmp
wine Installer.exe

...proceed to install...


Step 3:

CLEAN-UP:
> 
sudo umount /mnt/tmp
sudo rmdir /mnt/tmp 
sudo mount /media/cdrom


**II.** If your World of Warcraft Directory is NOT in /home/yourID/.wine/drive_c/program files/World of Warcraft do the following:

Step 1:
Open a Termnal Windows

Step 2: 
Run the following commands:
> 
mount | grep cdrom
(look for something that says /dev/<something> and note it, you will need it for the next steps)
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/temp
cd ~/.wine/drive_c/Program Files
ln -s /where/your/WOW/is/Installed "World of Warcraft"
cd /mnt/tmp
wine Installer.exe

... Proceed to install ... 

Step 3:  CLEANUP
> 
sudo umount /mnt/tmp
sudo rmdir /mnt/tmp 
sudo mount /media/cdrom



[B][U]Guide 2:  Copy / Install (This will almost undoubtably work for everybody, but its more time intensive and hard drive space intensive.  Not ideal for all people.)
[/U][/B]
 Step 1: 
Open a Terminal Window

Step 2: Run the following commands
> 
sudo mkdir /mnt/tmp
mount | grep cdrom
(look for something that says /dev/<something> and note it, you will need it for the next steps)
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/tmp
sudo mkdir /tmp/wotlk
cd /mnt/tmp
sudo cp -R * /tmp/wotlk
<wait about 10-20 minutes>
sudo chown -R <youruserID> /tmp/wotlk
wine /tmp/wotlk/Installer.exe


Step 3: CLEAN-UP (after install completes)

> sudo rm -rf /tmp/wotlk

[B][U]Guide 3: The "Damnit Blizzard why'd you make this so hard" Method:
[/U][/B]

From a terminal window:

Step 1: Determine the Device ID of your CDROM. look for /dev/<deviceID> and note it. (if you followed my directions previously, you already know this)
> Quote:
mount | grep cdrom
If you already unmounted your CDROM in one of the previous steps without doing cleanup, you will likely get nothing in return. Should that be the case type this:

sudo mount /media/cdrom
mount | grep cdrom

Step 2: Note the current OWNER of your /dev/<DeviceID>

> Quote:
ls -al /dev/<DeviceID> | awk '{print $3}'
Step 3: Change the OWNER of your CD-ROM to YOU.

> Quote:
sudo chown <yourusername> /dev/<DeviceID>
Step 4: Unmount All instances of your CD-ROM you mounted in previous instruction on this thread.

> Quote:
sudo umount /media/cdrom
sudo umount /mnt/tmp

Step 5: Change the owner of /mnt/tmp to YOU.

> Quote:
sudo chown <yourusername> /mnt/tmp
Step 6:remount using my previous mount command:

> Quote:
sudo mount -t udf -o ro,unhide,user=<yourusername> /dev/<something> /mnt/tmp
Step 7: Verify the OWNER of all the files on the CD are owned by YOU.

> Quote:
ls -al /mnt/tmp

you should get output that has your username in the place of mine:
total 8058178
drwxr-xr-x 3 toupeiro dialout 592 2008-08-28 22:28 .
drwxr-xr-x 3 root root 4096 2008-11-13 02:29 ..
-rw-r--r-- 1 toupeiro dialout 48 2008-08-28 22:28 autorun.inf
drwx------ 2 toupeiro dialout 492 2008-08-28 22:28 DirectX
-rw-r--r-- 1 toupeiro dialout 109638 2008-08-28 22:28 disc.ico
-rwx------ 1 toupeiro dialout 1407832 2008-08-28 22:28 Installer.exe
-rwx------ 1 toupeiro dialout 1627861562 2008-08-28 22:22 Installer Tome 2.mpq
-rwx------ 1 toupeiro dialout 2488952542 2008-08-28 22:24 Installer Tome 3.mpq
-rwx------ 1 toupeiro dialout 2375920098 2008-08-28 22:26 Installer Tome 4.mpq
-rwx------ 1 toupeiro dialout 1197605083 2008-08-28 22:27 Installer Tome 5.mpq
-rwx------ 1 toupeiro dialout 124584980 2008-08-28 22:27 Installer Tome.mpq
-rwx------ 1 toupeiro dialout 435111965 2008-08-28 22:28 Movies.mpq

If you DO NOT have your username set here, skip the next step, and go to CLEANUP, because this fix, for whatever reason, did not work for you.

Step 7: Proceed to install, now that you have verified your USERNAME has read/write/execute permissions on the CD-ROM files, and the unhide switch is truly showing you all the files.

> Quote:
cd /mnt/tmp
wine Installer.exe
Step 8: Upgrade your account. Do not use the blizzard account updater in the installation, it does not work. Instead, go to [www.worldofwarcraft.com](www.worldofwarcraft.com) and do it from the main screen there.

CLEANUP: Once you have upgraded your account and verified your install, we need to change your CD-ROM permissions back to the way they were, or it will cause problems for other users of your system...


> Quote:
sudo umount /mnt/tmp
sudo chown <original_ID_you_recorded_from_step_2> /dev/<DeviceID> <---- Very important
sudo mount /media/cdrom
sudo rmdir /mnt/tmp



Cheers.  

-T.

---

### Post by skylarke on 2008-11-13
Hi there

I found this link on the WOW site forums and it worked for me. 

[http://www.wow-europe.com/shared/downloads/protected/InstallWoW_enGB/InstallWoW.exe](http://www.wow-europe.com/shared/downloads/protected/InstallWoW_enGB/InstallWoW.exe) 

I clicked on it and something downloaded in 5 seconds, then my pc restarted itself. I then noticed I had a WoW installer icon on my desk top and clicked on it. I took the WOTLK option offered to download and everything kicked off from there. 

I had my disk in the drive all the time just incase it helped. 

Any hoo, WOTLK is now downloading on my pc and I am a happy bunny. I hope it works for you too. 

See you in game.

Skylarke (hellscream)

---

### Post by ticopelp on 2008-11-13
Skylarke's post reported. It's a WoW password farmer.

---

### Post by ticopelp on 2008-11-13
toupeiro, just as a note, you may want to clean up your uses of /temp/ and /tmp, which you seem to be using interchangeably throughout this guide...

---

### Post by toupeiro on 2008-11-13
> **ticopelp said:**
> toupeiro, just as a note, you may want to clean up your uses of /temp/ and /tmp, which you seem to be using interchangeably throughout this guide...

Thank you for pointing this out!  I think I caught them all.

---

### Post by Alexblack on 2008-11-13
I really hope someone can help me...
I've tried all of these methods, several times over in fact, and none of them are working. 
I can get to the EULA but am having the greyed out "accept" problem. 
I've tried changing the wine thing as suggested earlier in the post but it didn't work, so I tried downloading the latest dev version of wine but that didn't do anything either. 
Please forgive me, I'm very new to all of this and I'm having a really hard time with this OS!

---

### Post by lckeeper1 on 2008-11-13
Hey, thanks for all the great info, but I seem to have a different problem. Everytime I place my DVD into my drive, it mounts under /dev/scd1, which shows up as "Lich King."

```
dan@dan-desktop:~$ mount | grep Lich\ King
/dev/scd1 on /media/Lich King type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)
```


Basically, I can't get to mount the drives under /media, as they all show up, and when I place my DVD in the drive, a new directory pops up known as Lich King. I am quite stuck.


What this does is not allow me to do all the /dev commands in the terminal to get everything mounted, so I'm not quite sure how to work around this problem. If anyone could clue me in, I'd be in your debt.

-Dan

---

### Post by Mrmilim on 2008-11-13
Was ok up to the point of trying to unmount the drive and my system cam back saying it didn't know the command, Was using hardy heron.
Updated system to latest version and whilst I can use unmount, now my DVD drive won't accept DVD's only cds :-S

Tried sudo mount /media/cdrom and came back with 
special device /dev/hdb does not exist, what did I do wrong? pmsl

Sorry if this seems off topic but I was trying to load WotLK (and like an idiot I've already upgraded my account so am stuck with no wow at all as states need to install expansion):(

Any ideas or should I just take a hammer to it? lol

---

### Post by PMCPJ on 2008-11-13
Howdy.  Everything worked great to get the installer running, I used the directions, and I also dl'd the installer from Blizz, but I also keep running into the accept button problem.  Is there any kind og solution to this?

---

### Post by Bahb on 2008-11-13
> **toupeiro said:**
> 
[B][U]Guide 2:  Copy / Install (This will almost undoubtably work for everybody, but its more time intensive and hard drive space intensive.  Not ideal for all people.)
[/U][/B]
 Step 1: 
Open a Terminal Window

Step 2: Run the following commands
```
sudo mkdir /mnt/tmp
mount | grep cdrom
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/temp
sudo mkdir /tmp/wotlk
sudo cp -R * /tmp/wotlk
<wait about 10-20 minutes>
sudo chown -R <youruserID> /tmp/wotlk
wine /tmp/wotlk/Installer.exe 
```

Step 3: CLEAN-UP (after install completes)
```
sudo rm -rf /tmp/wotlk 
```

Should step two have:
```
cd /mnt/temp
```

after

```

sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/temp

```

as it keeps just copying my home folder...

---

### Post by toupeiro on 2008-11-13
> **Mrmilim said:**
> Was ok up to the point of trying to unmount the drive and my system cam back saying it didn't know the command, Was using hardy heron.
Updated system to latest version and whilst I can use unmount, now my DVD drive won't accept DVD's only cds :-S

Tried sudo mount /media/cdrom and came back with 
special device /dev/hdb does not exist, what did I do wrong? pmsl

Sorry if this seems off topic but I was trying to load WotLK (and like an idiot I've already upgraded my account so am stuck with no wow at all as states need to install expansion):(

Any ideas or should I just take a hammer to it? lol

Which guide were you using?  In any case, nothing done in these steps should have done anything to alter what types of media your DVD-ROM could read.  When you say you upgraded your system to the latest version, are you referring to Interpid?  If so, then is it safe to assume you have done all the necessary reboots pending to get up to date?  Its possible that some of the kernel updates in doing a system upgrade will require a system restart.

> 
Hey, thanks for all the great info, but I seem to have a different problem. Everytime I place my DVD into my drive, it mounts under /dev/scd1, which shows up as "Lich King."


Code:
dan@dan-desktop:~$ mount | grep Lich\ King
/dev/scd1 on /media/Lich King type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)
Basically, I can't get to mount the drives under /media, as they all show up, and when I place my DVD in the drive, a new directory pops up known as Lich King. I am quite stuck.


What this does is not allow me to do all the /dev commands in the terminal to get everything mounted, so I'm not quite sure how to work around this problem. If anyone could clue me in, I'd be in your debt.

-Dan 


Thats a new one.  So, rather than making the disk presentable as /media/cdrom by default, it is making it available by another name..

In the steps where you are instructed to unmount /media/cdrom, change the word "cdrom" to "Lich King" with " " around the words, and make sure you pay attention to case sensitivity.  /dev/scd1 being your dev device shouldn't be a show-stopper.  once you have unmounted /media/Lich King, you will want to mount /dev/scd1 to /mnt/tmp

---

### Post by toupeiro on 2008-11-13
> **Alexblack said:**
> I really hope someone can help me...
I've tried all of these methods, several times over in fact, and none of them are working. 
I can get to the EULA but am having the greyed out "accept" problem. 
I've tried changing the wine thing as suggested earlier in the post but it didn't work, so I tried downloading the latest dev version of wine but that didn't do anything either. 
Please forgive me, I'm very new to all of this and I'm having a really hard time with this OS!

I understand your frustration.  This expansion, specifically, was much more difficult than the last..  With a bit of patience, we'll get there. :)

If you have updated to the latest version of wine as described in this guide, please make sure you have your windows version set to "Windows XP" in winecfg. (type: winecfg to open this configuration tool)

Short of that, there are a few other treads in this forum relating to the EULA if this is not fixing it for you.  I would suggest trying one of them.  Here is one that may be promising for you.

[http://ubuntuforums.org/showthread.php?t=980685](http://ubuntuforums.org/showthread.php?t=980685)

---

### Post by ticopelp on 2008-11-13
Thanks for all your hard work in this thread, toupeiro. 

Unfortunately, I could not get any of these solutions to work for me. For whatever reason, I would get claims from my machine that there is "no media in the drive" or that the Lich King disk was empty. Finally, I had my wife copy the contents of her Lich King disc onto a backup drive, copy it onto my machine, and THAT got the installer working. 

Sadly, I ran smack into the EULA problem. The fix on [this thread](http://ubuntuforums.org/showthread.php?t=980685) did not work for me; there was too little explanation and I couldn't make it happen. I'm decent with the command line, but I'm not a whiz. 

Finally, since I was running Gutsy, updating to the latest version of wine was not an option. So I went ahead and updated to Intrepid, which suffice it to say has had its own problems (trying to get sound working again in Wine now). 

So I'm slowly getting there... updating Intrepid now and hoping to fix the sound issue, which is my last hurdle to actually playing this game. I've never had to work this hard to get a game working before...really wish they would have made it as easy as they did with Burning Crusade.

---

### Post by toupeiro on 2008-11-13
> **ticopelp said:**
> Thanks for all your hard work in this thread, toupeiro. 

Unfortunately, I could not get any of these solutions to work for me. For whatever reason, I would get claims from my machine that there is "no media in the drive" or that the Lich King disk was empty. Finally, I had my wife copy the contents of her Lich King disc onto a backup drive, copy it onto my machine, and THAT got the installer working. 

Sadly, I ran smack into the EULA problem. The fix on [this thread](http://ubuntuforums.org/showthread.php?t=980685) did not work for me; there was too little explanation and I couldn't make it happen. I'm decent with the command line, but I'm not a whiz. 

Finally, since I was running Gutsy, updating to the latest version of wine was not an option. So I went ahead and updated to Intrepid, which suffice it to say has had its own problems (trying to get sound working again in Wine now). 

So I'm slowly getting there... updating Intrepid now and hoping to fix the sound issue, which is my last hurdle to actually playing this game. I've never had to work this hard to get a game working before...really wish they would have made it as easy as they did with Burning Crusade.


Me too!  They (Blizzard) really went through some great lengths to make this painful.  I know the guides I posted were pretty tedious, as in not really user friendly, but I tried to keep them as straightforward as possible for a not-so-straightforward installation..


I went poking around the winehq forums and found some workaround information regarding a beta of WoTLK and the EULA.  hopefully some of this can apply to the problems you are having.  I'd also happily compare wine configuration settings when I get home.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13187&iTestingId=29332](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13187&iTestingId=29332)

---

### Post by louisgag on 2008-11-13
thx toupeiro your first post was simple and straight to the point.

happy leveling!

---

### Post by lckeeper1 on 2008-11-13
Toup, thanks for the help thus far. I tried doing what you suggested. I am still having difficulty though with mounting the disk. After I use the umount command with "Lich King", it unmounts with no problems, but I can't remount it at all using /dev/sdc1

```
dan@dan-desktop:~$ sudo umount /media/"Lich King" 
dan@dan-desktop:~$ sudo mount -t udf -o ro,unhide,uid=1000 /dev/sdc1 /mnt/temp
mount: special device /dev/sdc1 does not exist
```

So it's telling me that the DVD is under /dev/sdc1, but once I unmount the volume, I can remount it using that command? Something seems fishy.

If there's anymore info I can give ya, just lemme know.

-Dan

---

### Post by slingshot2hell on 2008-11-13
so I tried the first step, but when I do:
mount | grep cdrom

i don't see anything. this is true whether the disk is mounted or unmounted. how do i find out what my <something> is supposed to be??

---

### Post by slingshot2hell on 2008-11-13
Never mind, i found it by typing:
mount | grep cd

i'm using ubuntu 8.04. my device name was scd0

---

### Post by butler pirate on 2008-11-13
Thank you soooo much for this tutorial, I didn't want to have to copy it to my hdd and I didn't have to.  I did run in a couple of problems one of which was my own stupid fault.  Like when you type the sudo ... /dev/sd1 /mnt/temp
I didn't realize there was a space after something.  Also I noticed you didn't have quotes when you type Program Files and I had to do that to get it working on your 3rd step.  Other than my own faullies your guide was a life saver!

---

### Post by toupeiro on 2008-11-14
> **lckeeper1 said:**
> Toup, thanks for the help thus far. I tried doing what you suggested. I am still having difficulty though with mounting the disk. After I use the umount command with "Lich King", it unmounts with no problems, but I can't remount it at all using /dev/sdc1

```
dan@dan-desktop:~$ sudo umount /media/"Lich King" 
dan@dan-desktop:~$ sudo mount -t udf -o ro,unhide,uid=1000 /dev/sdc1 /mnt/temp
mount: special device /dev/sdc1 does not exist
```

So it's telling me that the DVD is under /dev/sdc1, but once I unmount the volume, I can remount it using that command? Something seems fishy.

If there's anymore info I can give ya, just lemme know.

-Dan

@ Dan, I would use the /dev/scd1 path which /media/"Lich King" automatically mounted when you are trying to mount /mnt/tmp.  (if you were cut and pasting from your terminal when you posted that, and it wasn't a typo)

@ Butler, you bring up a good point about " " in some of my examples.  I've noted it in the TIPS: section of the tutorial.  Like many things at the command line, there are several ways to do the same task.  some people will be more comfortable typing everything out, and others will prefer the <tab> shortcut. :)  Im really happy I was able to help!

---

### Post by Mrmilim on 2008-11-14
[QUOTE=toupeiro;6172004]Which guide were you using?  In any case, nothing done in these steps should have done anything to alter what types of media your DVD-ROM could read.  When you say you upgraded your system to the latest version, are you referring to Interpid?  If so, then is it safe to assume you have done all the necessary reboots pending to get up to date?  Its possible that some of the kernel updates in doing a system upgrade will require a system restart.




Yeah, it's not the guide thats at fault, was my new operating system I think, and yes did upgrade to intrepid (8.10?).
Ran Update Manager last night and again this morning and did a system reboot again. No joy as yet. I must be missing something, either file wise or me personally. Started a thread specifically about the DVD ROM drive issue and am hoping somebody will be able to shed some light on it.
Atleast I'm not new to command prompt usage, but that was with dos, wish I'd learned unix now, might have been easier to get to grips with the command codes. :)

Will keep an eye on this thread too incase, you can suggest anything

---

### Post by Lord Erik on 2008-11-14
Thanks to all the people with the answers so far.

I have got past the DVD reading and accept issue.  Now it comes up with a dialog box "Please insert the CD labeled "Wrath of the Lich King disc 1." with Ok and Cancel buttons.  In the background I can see another screen about account upgrade.

I can't figure out why it is asking for a disc.  I have copies all the .exe, .mpq files and DirectX dir to ~.wine/drive_c/temp and ran wine Installer.exe from there.  All the files are rwx for my user.

Any help would be appreciated.

---

### Post by Mrmilim on 2008-11-14
Well!
On a plus note Blizzard have entually allowed downloads of WotLK for the EU realms. I found the link by trying to log onto the game (I had already signed up with my authorisation code, and got an error screen which gives the download link) 

This is the link I found from my history
[www.wow-europe.com/en/downloads/client/](www.wow-europe.com/en/downloads/client/)

Had to right click the installer (which dropped onto my desktop) and choose to open it with wine. It's downloading as we speak, and will post back with feedback.

Hopefully it's now just the souncard issues to deal with due to upgrade of ubuntu, I can live without the DVD for now lol

---

### Post by Mrmilim on 2008-11-14
Yep the download way works, I now have wow back!!

Takes forever to download, but no probs with the eula, just scrolled down the windows as per all the other updates and accepted.

BTW Shattrath is deserted, fps is fantastic there now lol

Happy leveling guys, and thanks for the thread

---

### Post by sooperspook on 2008-11-14
> mine@mine-desktop:/mnt/tmp$ cd /mnt/tmp
mine@mine-desktop:/mnt/tmp$ wine Installer.exe
wine: could not load L"c:\\windows\\system32\\Installer.exe": Module not found


I get to this point and this happens.

I am a complete noob when it comes to linux btw :)

---

### Post by Mad-Halfling on 2008-11-14
On my system the command was

sudo mount -t udf -o ro,unhide,uid=1000 /dev/scd0 /media/cdrom0

the only thing that may be different on yours is the /dev/scd0 - to find out what cd drive device name yours is, type

ls -l /dev | grep cd

this will list out something like

lrwxrwxrwx  1 root   root           4 2008-11-14 13:24 cdrom -> scd0
lrwxrwxrwx  1 root   root           4 2008-11-14 13:24 cdrw -> scd0
lrwxrwxrwx  1 root   root           4 2008-11-14 13:24 dvd -> scd0
lrwxrwxrwx  1 root   root           4 2008-11-14 13:24 dvdrw -> scd0
crw-rw-rw-  1 root   tty       2, 221 2008-11-14 13:24 ptycd
brw-rw----+ 1 root   cdrom    11,   0 2008-11-14 13:24 scd0
crw-rw----  1 root   cdrom    21,   1 2008-11-14 13:24 sg1
lrwxrwxrwx  1 root   root           4 2008-11-14 13:24 sr0 -> scd0
crw-rw-rw-  1 root   tty       3, 221 2008-11-14 13:24 ttycd

you can probably use /dev/cdrom or /dev/dvd if it's there, if that doesnt work, look for what the cdrom or dvd point to.  If you have multiple drives then try a setting with each drive.

---

### Post by Starmartyr on 2008-11-14
You could try this solution: [http://ubuntuforums.org/showthread.php?t=981489]("http://ubuntuforums.org/showthread.php?t=981489")

Hope it works for ya

---

### Post by edWAR6 on 2008-11-14
To fix the eula button problem, go here and install the new wine

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by edWAR6 on 2008-11-14
to fix the eula button problem install the new beta wine
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by sooperspook on 2008-11-15
Ok, I just downloaded it from the website and it installed no problems. 

Pain in the **** waiting for it all to dl but it's running which is the important bit. :)

Only problem now is I've noticed a significant drop in fps.

---

### Post by cjclark on 2008-11-15
I had problems with the first group of instructions so I tried the second.  When I tried the second group of instructions I got the following:

Application tried to create a window, but no driver could be loaded.

Make sure that your X server is running and that $DISPLAY is set correctly.

Application tried to create a window, but no driver could be loaded.

Make sure that your X server is running and that $DISPLAY is set correctly.

err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB

fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

root@clarkmobile:/mnt/temp# fixme:powrprof:DllMain (0x7e090000, 1, (nil)) not fully implemented

fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities

fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11

fixme:powrprof:DllMain (0x7e090000, 0, (nil)) not fully implemented


Any help would be greatly appreciated.

Thanks.

---

### Post by hotballz87 on 2008-11-16
there has been a extremely large issue with certain people not being able to read the disk, not only in linux, but other operating systems.

there is a large forum post in the wow forums about it here:
[http://forums.worldofwarcraft.com/thread.html?topicId=12661296899&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=12661296899&sid=1)

so it might not be problems with wine, or linux, it could be the disk/drive read problems also

---

### Post by FLCL on 2008-11-16
Well i have a huge problem now, i've managed to fully install and get all the updates BUT when i go to log in, it says i dont have it installed. My hard drive space disagrees with that message as it is down 9 gigs from earlier last night. 
Could i get some help?

---

### Post by xang on 2008-11-17
> **FLCL said:**
> Well i have a huge problem now, i've managed to fully install and get all the updates BUT when i go to log in, it says i dont have it installed. My hard drive space disagrees with that message as it is down 9 gigs from earlier last night. 
Could i get some help?

I am having the same issue. I can access vanilla Wow and BC content, but when I sail out of StormWind harbor it kicks me back saying I must have the xpac installed. 
When I launch from the DVD, it has a play button and uninstall, so it recognizes the content. 
I didn't get much of a chance to troubleshoot. Will do more poking around once I get home tonight. 
If anyone else is seeing this issue and figured out a solution, please post. Thanks!

---

### Post by laffys on 2008-11-18
Well I managed to download the "installer" from blizzard. That worked so beautifully and flawless, since the issue was actually with the disk itself. I tried it on a windows system and came back as the disk itself is unreadable !@!@! Thanks to all with this little issue.

---

### Post by PAT_ on 2008-11-19
Hi,my issues are a little different, 
Using Crossover:
My first issue is that if I am using the download able .exe from blizzard I can not click the agreement Button at the bottom of the EULA.[http://img503.imageshack.us/my.php?image=error2kb5.jpg]("http://img503.imageshack.us/my.php?image=error2kb5.jpg")

Using Wine:
Using the downloaded .exe I get this error: Unable to install
Wrath of the linch king requires a newer operating system to run.
Windows 2000, XP or newer is required.
[http://img508.imageshack.us/my.php?image=error3wc0.jpg]("http://img508.imageshack.us/my.php?image=error3wc0.jpg")
I have tried changing the windows version 2000, xp, vista, 2003, and 2008. and still same thing.

Using Both:
I was able to get a copy of the game off a windows install, but my issue there was once I had tried to log in it game an error:says This [http://img508.imageshack.us/my.php?image=error1lm5.jpg]("http://img508.imageshack.us/my.php?image=error1lm5.jpg")





If these have already been answered sorry for the re-post.

---

### Post by PAT_ on 2008-11-19
Fixed: Had to change the application setting inside of winecfg to windows vista or xp on my "default settings". That fixed everything. For the using the downloader at least. You can not just add installwow.exe,

---

### Post by Ixonal on 2008-11-19
hmmmm, I mounted the disc exactly as was said, but I'm not getting all the files, just the install.exe and directx folder show up and they're both unreadable still. 

am I missing something here?

---

### Post by Punakuono on 2008-11-20
Hi,

I had the problem with not founding that dvd right and the solution here worked, and then I had the problem with the accept thing and again the solution in this thread helped, updating wine helped. I got the game started and watched the demo in the beginning, but then the game crashed to an access violation cause somehow it could not write to right memoryspace, or that is what the errormessage complains about. Would someone happen to know what would fix this problem cause that is what stops me from playing the game. 

Thank you.

---

### Post by snareguydave on 2008-11-22
> **benjick said:**
> Confirmed, works. Thanks ALOT! :)

Yes, definitely works... just had to change "tmp" to "temp", "media" to "dev" and "cdrom" to "cdrom1"!!! 

But, I wouldn't have even know where to start if it hadn't been for toup, so thanks!

---

### Post by gerowen on 2008-11-22
I have the patch installed, but I cannot log into my DeathKnight.  I get an error telling me that my "flybydeathknight.m2" file is corrupt.  I've ran the Blizzard Repair agent and it re-downloaded some files, but I still get the error when trying to log into my DeathKnight.  I can play my old characters though with no problem.

---

### Post by JohnParker on 2008-11-22
I have the installer running fine, but when i get to the EULA I scroll down but The I AGREE doesnt highlight so I can click it, Sad face
 

Still doesnt work after upgrading Wine

---

### Post by habelman on 2008-11-23
iv tried to follow steps iv seen here and on the winehq page. i cant get my wotlk to instal period. And i have the cd copied to my hd but i cant do anything with it. when i click nothing happend. i put more info in a thread i made if anyone can please take a look!?

---

### Post by sjones72751 on 2008-12-23
I ended up having to set up a Windows XP virtual machine using virtualbox and copy the files to linux via a shared folder.  I think the problem stems from the fact that by default on the disc you can only "see" the DirectX folder and the Installer.  You need all the tome's as well.  I know i'm responding to an old post here, but hopefully this helps someone.

---

### Post by v1nsai on 2009-03-16
I was having problems getting the installer to come up and being able to click the agree button, I was able to get the installer to come up by entering 'pkill wine' in command line to close down wine completely, then the installer came up first time I clicked on it.

My issue with clicking the agree button was fixed by going [here]("http://www.winehq.org/download/deb") and following the instructions, then going to System > Administration > Update Manager > Check for Updates.  Wine was then updated, and the agree button became clickable after restarting wine.

I hope others' problems are as easy to fix as mine.

Edit:
Would it be possible to install everything in virtualbox and then just move all the folders into the wine C:\ drive?

Editx2:  Yes, yes it is possible.  If your having wine problems, try just moving the contents of C:\Program Files\World of Warcraft onto the same location on the wine c:\ drive.  Surprisingly, it works.  I had problems with graphics at first, but I went to Applications > Wine > Configure wine and under graphics I emulated a virtual desktop (this made playing in a window possible at least, made the resolution smaller to compensate for my gnome-panels and am now playing :)

---

### Post by 1BigBore on 2009-03-31
I just wanted you folks to know that it is possible to install WoW using various methods within these forums.  I did it, and it works at least as good as my winn version, and looks better!  
Attached is my Linux unit and am using a GeForce 8400gs.
works like it should!

Thanks one and all!:D

---

### Post by ResumeMan on 2009-04-01
> **JohnParker said:**
> I have the installer running fine, but when i get to the EULA I scroll down but The I AGREE doesnt highlight so I can click it, Sad face
 

Still doesnt work after upgrading Wine

Ack! I'm having the same trouble!!

Anyone figure out a way to fix this...?

---

### Post by darcstarr on 2009-04-01
So I've been able to install Vanilla and BC no problem, my trouble lies with WOTLK. I can't even get an install to initialize. I've gone to many different places to check out methods or executing the install but nothing seems to work. I usually find myself getting to the point where it says:

wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I've also gotten(through another method in this topic):

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114

I need major help with this, I'd really like to play this game on Ubuntu any help would be appreciated. Thanks.

---

### Post by 1BigBore on 2009-04-01
While I cannot address those last items, I wanted to post my Config.wtf, because it works (for me at least), and it helped me when someone else posted theirs that worked.
```

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1360x768"
SET gxRefresh "59"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET Sound_OutputDriverName "System Default"
SET farclip "397"
SET specular "1"
SET particleDensity "1.000000"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET installType "Retail"
SET patchlist "us.version.worldofwarcraft.com"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET gxWindow "1"
SET accountName "<<your account>>"
SET mouseSpeed "1"
SET lastCharacterIndex "5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET baseMip "1"
SET spellEffectLevel "6"
SET environmentDetail "0.75"
SET weatherDensity "1"
SET realmName "<<your realm>>"
SET gameTip "3"
SET VoiceActivationSensitivity "0.39999997615814"
```

the thing that helped me so much, was removing the "runOnce.wtf" (there were 2 files. I do not remember the real names.)files in the WTF dirrectory... the movie messed up my video real bad. 
I hope this helps someone.  This has the game in a window.

---

### Post by rabaal on 2009-04-09
I've gone through multiple of these faqs to get it working, finally got it working and now when i try to eject the Wrath CD out of my CD drive it tells me

You are not privileged to unmount the volume 'Lich King'.

Details
unmount: only root can unmount /dev/scd0 from /media/cdrom0

when i tried going into terminal and doing the sudo unmount command it tells me that unmount is not a valid command....

any help please....i would really enjoy being able to use my cd drive





***Edit***

Sudo eject works much better than unmount command =-)

---

### Post by aoanla on 2009-04-11
> **rabaal said:**
> 
when i tried going into terminal and doing the sudo unmount command it tells me that unmount is not a valid command....


umount, on the other hand, is. (Yes, I know it's counterintuitive.)

---

### Post by c/Kr3t on 2009-05-08
[http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04](http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04)

cheers :)

---

### Post by roargg on 2009-05-28
Hello!

 I have all necessary files in a folder, I am able to mount/umount blabla, but I keep facing text that says "**Module not found**" when trying to get the Installer.exe working by terminal. I noticed that they have been installed as a root and I face the "**Permission denied**" time to time. Do I just need to change the owner to myself as a user in order to get this installation done quickly, if so, how do I do that?
 I went through this whole topic but I keep facing errors. I think I will try upgrading with CD-key, as *starmartyr* suggested but before that I really would like to know what's the deal with this because this is really frustrating!

 I would really appreciate if you could help me! Help me Jebus, Chuck Norris, anybody!

---

### Post by windowsareslow on 2009-06-13
I confirmed that the wine update referred to here gets past the EULA problem ("I Agree" button is greyed out)

---

### Post by Eion on 2009-07-30
Toupeiro, I owe you one!  Your guide helped me get past the crazy crap that Blizz did to their Wrath dvd!  It's installing happily right now, if the "thank" feature was still around (or maybe I just cant find it. . .) I'd give ya one.

---

### Post by Rrasyrogenees on 2009-08-14
what i found to what was written on the first and second pages on this thread are good...

   #12 post seems to say it the best for this, however i did have to put quotes on "Program Files" for it to work properly... other than that i did all that was written and i did use the long form to make sure i was in the right folder for placement and it worked very well that way.  i had no problems whatsoever once i put those quotes on... and i made sure i knew that /dev/<name of cdrom> was... mine is sr0... if you need to find it go into the  dev folder in your mount folder (/dev/cdrom)  and right click on cdrom link file and it will give what it is called (link target)... simple once you know what to look for.

   (at least this is what i did to make it download)  i was able to click on the eula and let me download with out problem... just takes a long time... there is a lot on that one disk.

let me show what i mean to the #12 post...

Quote:
If your World of Warcraft Directory is NOT in /home/yourID/.wine/drive_c/program files/World of Warcraft do the following:

Step one:

Open a Terminal

Step two:

Do the following commands:

sudo mkdir /mnt/temp
sudo su -
mount | grep cdrom
(look for something that says /dev/<something> and note it, you will need it for the next step) <<<(i found that it was in /dev/cdrom (link) and that is what i found in properties the name)

mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/temp
exit
cd ~/.wine/drive_c/"Program Files"  <<<(this is where i added the quotes to show it is one file and not two)
ln -s /where/your/WOW/is/Installed "World of Warcraft"  <<<(oh yeah... i did not use this line at all as well)
cd /mnt/temp
wine Installer.exe

... Proceed to install ...

Step 3: Clean up

sudo umount /mnt/temp
sudo rmdir /mnt/temp

---

### Post by Rrasyrogenees on 2009-08-14
by the way... i am doing this on amd 64 jaunty with creative x-fi and nvidia 9800gt with asusm3a78-em and 8gb ram... on windows i was seeing about 40+fps and maybe 70 lat or less
 i will post what this will give me when i get it done

---

### Post by Nextgeneration on 2009-10-20
> **toupeiro said:**
> It looks here like your unhide switch did not get set for some reason, whereas when JesseJames did it, his did get set..  Try my alternate method that unmounts your cdrom before it mounts your /mnt/tmp directory to your cdrom.  Hopefully that will get you better mileage.

Are you both running an 8.10 version of Ubuntu or Kubuntu or Something=untu?

Jesse: since you got the directory mounted, and if you have ample free hard drive space, you can probably make a directory in /tmp and then type:

 sudo cp -R * /tmp/yourdirectory.
 <wait about 10-20 minutes>
 sudo chown -R <youruserID> /tmp/yourdirectory
 wine /tmp/yourdirectory/Installer.exe


As i do this the terminal says:
root@tons-desktop:~# cp -r * /tmp/wotlk
cp: cannot stat `*': No such file or directory

---

### Post by Nextgeneration on 2009-10-20
Well if someone could help me out that would be great, I don't think Wilson will be helping me on this.

---

### Post by pedro_orange on 2009-10-21
> **Nextgeneration said:**
> As i do this the terminal says:
root@tons-desktop:~# cp -r * /tmp/wotlk
cp: cannot stat `*': No such file or directory

For a start you're not sudo and Linux is case sensitive (R is different from r - but not in the eyes of CP so that's not too bad)

Second, does /tmp/wotlk actually exist? If you don't have a final / at the end (/tmp/wotlk/) surely cp treats it as a file? I'm not sure on that one, I'm at work and can't test.

You may find it easier to stay away from the command line. If you do this in terminal:

```
gksudo nautilus
```

You will get a file manager GUI with su rights. Just copy whatever you need in this way, and then you won't have to worry about the command line.

---

### Post by Nextgeneration on 2009-10-21
> **pedro_orange said:**
> For a start you're not sudo and Linux is case sensitive (R is different from r - but not in the eyes of CP so that's not too bad)

Second, does /tmp/wotlk actually exist? If you don't have a final / at the end (/tmp/wotlk/) surely cp treats it as a file? I'm not sure on that one, I'm at work and can't test.

You may find it easier to stay away from the command line. If you do this in terminal:

```
gksudo nautilus
```You will get a file manager GUI with su rights. Just copy whatever you need in this way, and then you won't have to worry about the command line.

I got it to work thanks :D the problem i now face though is that when i go to run it this message pops up
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

I don't know if I should go into wine or my vid. card:confused:

---

### Post by pedro_orange on 2009-10-22
You get this problem when you run:

```
gksudo nautilus
```

??

What graphics card do you have? And have you installed the necessary drivers (& how) ?

Also, are you simply trying to copy the DVD to your local drive?
Why don't you just do it graphically (drag & drop)? 

You know, if you install WoW on a Windows machine, then copy the C:\Program Files\World of Warcraft folder onto an external media, then from that media to your Linux box, you can just run the exe under wine without having to install it on Linux.

Btw; You really need to explain what you're doing much more clearly and what you're trying to achieve.

---

### Post by Nextgeneration on 2009-10-22
[B][U]Guide 2: Copy / Install (This will almost undoubtably work for everybody, but its more time intensive and hard drive space intensive. Not ideal for all people.)
[/U][/B]
 Step 1: 
Open a Terminal Window

Step 2: Run the following commands
 	Quote:
 	 	 		 			 				sudo mkdir /mnt/tmp
mount | grep cdrom
(look for something that says /dev/<something> and note it, you will need it for the next steps)
sudo umount /media/cdrom
sudo mount -t udf -o ro,unhide,uid=1000 /dev/<something> /mnt/tmp
sudo mkdir /tmp/wotlk
cd /mnt/tmp
sudo cp -R * /tmp/wotlk
<wait about 10-20 minutes>
sudo chown -R <youruserID> /tmp/wotlk
wine /tmp/wotlk/Installer.exe 			 		 	 	 
I did all this and got no errors Untill the x server display.
it worked fine When i try to copy the files to a folder it says i don't have permition. So the problem I had was the same of the first person on this thread. I followed it all and got to this point everything works i can get it to run but I get that error. I have a GeForce 7300 SE/7200 GS (nividia) When i switched from windows ubuntu handled the installation.I have used crossovergames in the past so i know its installed properly.I can get other games to work such as the sims3 and linux fps.

This is what i get when i run gksudo nautilus:** (nautilus:4169): WARNING **: Unable to add monitor: Operation not supported
e' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory

---

### Post by Astonix on 2009-12-10
> **illepic said:**
> I had to copy the contents of the Wrath DVD to a windows drive and then transfer the folder across my network to my Ubuntu box.  Then I just double clicked the Installer.exe file.  Installed incredibly fast and painlessly at that point

For those of you who still have access to any Microsoft computer, this method does work flawlessly.

---

### Post by JamesScottSomers on 2010-05-17
This is what I did after fiddling with it a bit.

cd /media/cdrom
sudo cp -R /home/user/WOWAGE/
cd /home/user/WOWAGE
sudo chmod 755 -R *

Install with Wine etc.  I actually use Gnome to install Wine apps, Right-Click->Run with Wine

Worked like a charm.  I mean it is my (root's) computer even if the disc itself is read-only.  Better than waiting 24 hours for a download although the music is catchy.

The other thing I was going to do was give user the group dialout or else create a user named dialout not sure how that would have worked or not I don't see why not.

---

### Post by Shadowkath on 2010-05-28
Hey, I went through, and after 4 hours or so of trial and error with installing Wrath on Ubuntu, I finally got it.. Now, on the other hand, I have a slightly different issue.. When I try to run WoW, its incredibly laggy at the beginning, and the mail load up screen is broken, it doesn't work. No matter what I do.. Anyone have a solution for that? or have any info to help me resolve it?

---

### Post by sdrobinson on 2010-08-17
You know...  I have Ubuntu 10.04 installed and I used bits of the information on the 9.04 system here in the forums...

This is the command I used to access the Lich King install DVD:
**sudo mount -o remount,unhide /media/Lich\ King**

I then double clicked the install exe file and away it went...

---

### Post by Arpagiator on 2010-09-11
> **sdrobinson said:**
> You know...  I have Ubuntu 10.04 installed and I used bits of the information on the 9.04 system here in the forums...

This is the command I used to access the Lich King install DVD:
**sudo mount -o remount,unhide /media/Lich\ King**

I then double clicked the install exe file and away it went...

Thanks for this post, it helped enormously. I can confirm it also works on 10.04_86x64 and UbuntuStudio10.04(_86x64). 

Cheers:guitar:

---

### Post by Dlambert on 2010-12-31
Thanks

---

