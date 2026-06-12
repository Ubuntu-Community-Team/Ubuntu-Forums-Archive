---
title: "The Sims 2 Deluxe"
date: 2011-09-18
forum: Wine
---

### Post by Yamipirogoeth on 2011-09-18
I managed to install the game (there's only one total game disc) into Wine 1.2.2 but then I get the following error when I try to run the game

```
No disc inserted.

Please insert the original "The Sims™ 2 Deluxe" CD/DVD.
```

And I'm given the option to "Retry" or "Cancel". Clicking on retry just bring up the same dialogue box with no change.

In the wine configuration menu, under the drives tab, I have drive D: set to be a CD-ROM type under the advanced settings with the path set to just "/"

Any ideas on how to correct this?

---

### Post by Toz on 2011-09-18
Looks like the CD Rom issue is going to be the least of your problems ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942")).

However, to directly answer your question:
1. Put the cd drive in your drive and wait for it to mount.
2. In a terminal window, type in:
```
cat /etc/mtab
```
3. Look for an entry for your cd mount. It will look something like:
> /dev/sr0 [COLOR="Red"]/media/something[/COLOR] iso9660 ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 0 0 (I've highlighted the mount point in red)

4. Back in the terminal window, link the mount point to a wine drive letter:
```
ln -s /media/something ~/.wine/dosdevices/e:
```
(or whatever drive letter you want - I used e: for this example)

5. You can check in winecfg, on the Drives tab, that the mount point exists.
```
wine eject
```
should also eject the cd - as a test.

6. Try with the game now, but as I mentioned earlier, good luck.

---

### Post by Yamipirogoeth on 2011-09-18
Thanks Toz, the media is linked and I can see the drive in Wine as well as ejecting it using terminal...however, I'm running into a new issue...each time I run the program, I can see it starting up but then it freezes...the system meets the minimum requirements...but I can't figure out why it freezes...any suggestion on where to start looking?

---

### Post by Toz on 2011-09-18
Click on this link: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942") and you will notice that the game is rated as "Garbage". If you read the comments posted for the individual versions of the games, you will see that it does not currently run in wine.

As an option, you can try running it on Windows in Virtualbox.

---

### Post by Yamipirogoeth on 2011-09-19
...well, if it doesn't run in Wine...I'm not gonna try to fix something that broke...but thanks for the suggestion of VirtualBox...just need to get a version of Windows to install on it

---

