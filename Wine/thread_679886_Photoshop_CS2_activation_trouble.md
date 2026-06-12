---
title: "Photoshop CS2 activation trouble"
date: 2008-01-27
forum: Wine
---

### Post by JaggedOne on 2008-01-27
I acquired CS2 after Wine just became compatible with it. When I try to run the phone activation it complains that it does not have enough disk space to start the application. How do I fix that?

---

### Post by SyCo123 on 2008-01-29
Check you version of wine and update if necessary you need 0.9.54. I had a problem that apt-get update said it was the latest version when it was 0.9.49 so i had to add the budgetdedicated repos to my sources which sorted it.

If you want the latest and greatest version of wine, add these lines to /etc/apt/sources.list:
## WineHQ APT Repository
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

Run 
sudo apt-get update

and a minute after I had a software update to the latest version which apparently should fix your bug. I cant uninstall PS right now so am about to start a thread on that if you have the same problem with missing serial numbers.

---

### Post by Kokesh on 2008-01-31
The same problem here, mine Wine is the 0.9.54 from the source you've mentioned.

---

### Post by SyCo123 on 2008-02-04
Double check you have the right version with

```
aptitude show wine | grep 'Version:'
```

If you get 0.9.54 then you definately good.

I removed wine and reinstalled to be sure it wasn't going to cause an issue.
```

sudo apt-get remove --purge wine

sudo apt-get install wine

```

re installed the required times font
[http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)

Renamed the existing Adobe folder to adobe_old and re installed CS2

That worked for me, I hope it does for you too!

---

### Post by Kokesh on 2008-02-04
I had activation problem also. What helped me? 
I deleted **~/.wine/drive_c** and installed CS2 again.....

The only thing is, that I had to install my under-wine applications again, but it wasn't big deal, since it was just few of them.

 I was able to register. Annoying Free space warning didn't show up and now I can finally work in Photoshop CS2 without booting Virtualbox.

:guitar:

---

### Post by SyCo123 on 2008-02-05
Sweet. 
I only had CS2 and Utorrent in Wine so it was no big deal for me either but having to re-install is a bit of a hassle. Not bad for pre-release software though :)

---

### Post by kyutums on 2008-02-10
What finally allowed me to install Photoshp CS2 was 0.9.54 AND NOT installing winetricks.  :)

---

### Post by volksman on 2008-02-20
Since this comes up as a top hit with Google when searching for this problem here is how I overcame it:

Using the SCSI ATA PASSTHRU method:

Make your primary harddisk block device (/dev/hda or /dev/sda .. whatever,
owned by root) raw accessible to the wine user.
At least: chmod g+rw /dev/hda (sda), if you are in "disk" group.
If not: chmod a+rw /dev/hda (sda).
+r is not enough because the block device is unfortunately opened with default
READ_WRITE permissions requested.
Don't be scared .. "write" isn't used at all.

Make the following symlink in .wine/dosdevices: "ln -s /dev/hda c::"

Start Photoshop CS2 and wait for activation dialog. It should now show
activation code. Fill in required authorization code to activate your copy.

If successful you can remove the symlink and revoke permissions to hda/sda.

Found here: [http://bugs.winehq.org/show_bug.cgi?id=10018#c16](http://bugs.winehq.org/show_bug.cgi?id=10018#c16)

---

### Post by rcatman on 2008-03-04
I had the "disk out of space" problem when trying to active by phone aswell. The new version of wine fixed the problem. I now have Photoshop CS2 up and running on my amd64 gutsy laptop!

---

### Post by RRosset on 2008-03-23
YOU ROCK VOLKSMAN. I've been stuck with photoshop for a couple of days since I found this post. WHOOOOOOOOOOOOOOOAAAAAAAAAAAAAAAAAAA man... you make my day dude. I'm more than happy now. Really, thanks!!!

---

