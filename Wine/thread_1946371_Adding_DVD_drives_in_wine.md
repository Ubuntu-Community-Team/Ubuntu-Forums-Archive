---
title: "Adding DVD drives in wine"
date: 2012-03-24
forum: Wine
---

### Post by DGINSD on 2012-03-24
I'm tring to get DVDshrink and DVDfab to work in wine but neither of them are seeing discs when inserted, I used these instructions in the community documentation to add the drive, found here [https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")

> 
Adding CD and DVD drives to Wine

Go to the drives tab in winecfg. 

Hit the Autodetect button.

If you find that this does not work correctly for you, then follow these instructions:

Run  winecfg

Navigate to the drives tab

Click on Add In the path bar, type:  /media/cdrom

Click Show Advanced button below the Browse button and set the Type to: CD-ROM


What am I doing wrong?

---

### Post by howefield on 2012-03-24
Thread moved to the "*Wine*" forum.

---

### Post by DGINSD on 2012-03-25
So I've experimented a bit with changing the path to the CD/DVD drive. If I put the path as /media/"name" "name" being the name of the disc in the drive, the DVD shrink program can read the disc and all works well. 

So obviously it seems silly to have to edit the path line every time I want to use a new disc, so there must be some script that can be run so this process happens automatically how to write and have executed said script is well beyond by abilities.

I also tried to use the path /dev/dvd that didn't work. I also tried /dev/sr0 same result.

Whats the purpose of the cdrom directory in the files system there's nothing contained in it, even when a disc is inserted?

---

### Post by DGINSD on 2012-03-25
From a bunch of searching and piecing together bits and pieces from here and there, I found out that because of some new security feature added in Ubuntu the regular fstab entry for a cdrom drive is no longer there by default.

So someone with a relatively new Ubuntu install and wine install following the community documentation will run into the same issue; DVD and CD programs won't recognise the cdrom. My issue was solved by adding to the fstab file in /etc this file can be edited by running in the terminal. 

```
gksudo gedit /etc/fstab
```

I added "/dev/cdrom /media/cdrom auto ro,noauto,user,exec 0 0" minus the quotes.

```
/dev/cdrom /media/cdrom auto ro,noauto,user,exec 0 0
``` 

Then I ran in the terminal

```
sudo mkdir /media/cdrom
```

These will only work in a standard system with only one cdrom if you have more than one you will want to add two fstab lines changing cdrom to cdrom0 in the first and cdrom1 in the second. Same applies to the mkdir command,run twice changing the output to cdrom0 and cdrom1. Reboot and all should be well.

Hope this helps someone else. If someone more experienced than myself can make sure my commands are done correctly I'd appreciate it. The command line is still a bit foriegn to me so use them at your own risk.

---

