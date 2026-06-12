---
title: "problems installing WoW Burning Crusade"
date: 2008-03-17
forum: Wine
---

### Post by xyZen on 2008-03-17
Im having a few issues being able to "see" the installer .exe for the WoW expansion Burning Crusde using WINE.

I've copied the files onto my desktop, as this guide suggests;

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

and as i cant see the exe file ive tried to mount the disc using the below;

sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

and it returns:

mount: /dev/scd0 already mounted or /media/cdrom0/ busy
mount: according to mtab, /dev/scd0 is mounted on /media/BC DVD


the disc does appear on my desktop, but i still cant see the exe file.

i have used this technique this morning to install the basic WoW game, but the same technique doesnt appear to work for the Burning Crusade.

Any ideas?

---

### Post by pedro_orange on 2008-03-17
Why don't you just run the installer from the CD? 
It should automatically come up with the splash TBC screen when u stick in the CD.

NB: You'll need to tell wine to release the CD draw during the installation using the command "wine eject d:" in terminal (d cause thats what it called my drive)

---

### Post by Onyxblack on 2008-03-17
How did you "copied the files onto my desktop, as this guide suggests;" 

if you copied the files from a cd then you should just try running it - mounting it is only good if you have it in a iso or a mdf file.... try just...  ```
cd /<path-to-directory>/
 wine Installer.exe
```

note that it can take wine some time to start the application up... give it a good 10-20 seconds

---

### Post by xyZen on 2008-03-17
when i enter the disc the splash screen doesnt load, nor can i see the installer.exe if i navigate to the disk's contents when the disc icon appears on my desktop...

---

### Post by ikt on 2008-03-19
> **xyZen said:**
> when i enter the disc the splash screen doesnt load, nor can i see the installer.exe if i navigate to the disk's contents when the disc icon appears on my desktop...

Confirmed :/

I can only see a folder for OSX and 4 Installer Tomes..

---

### Post by eveningsparkle on 2008-05-15
I have the same issue. I viewed hidden-- no luck. I think this is only a problem for the DVDs. Inside the OSX folder there's an InstallLauncher.pef but I am not entirely sure how to run it with wine. 

Also, I just got gutsy this morning, so I am a bit out of my league, after six hours WoW works but won't let me log in because I'm at 61. Curses! Help?

---

### Post by Faud on 2008-05-15
> **eveningsparkle said:**
> I have the same issue. I viewed hidden-- no luck. I think this is only a problem for the DVDs. Inside the OSX folder there's an InstallLauncher.pef but I am not entirely sure how to run it with wine. 

Also, I just got gutsy this morning, so I am a bit out of my league, after six hours WoW works but won't let me log in because I'm at 61. Curses! Help?

What does Im at 61 mean ?

---

### Post by sdtootle on 2008-10-16
I had the same problems running Ubuntu 8.10 with the DVD version of TBC.  I found the following information:

> 
> # umount /media/'WoW DVD'
>
> -- after the disk gets auto mounted, then remount manually:
>
> # mount -t iso9660 -o ro /dev/dvd /mnt/cdrom
>
> -- this time the 'Windows side' appears at the begining.
> -- The iso9660 is the 'new format' that needs to be specified


Found this at [Codeweavers.com]("http://www.codeweavers.com/support/tickets/browse/?ticket_id=699509;list=16;ticket_level=2")

---

