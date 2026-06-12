---
title: "Error after update..."
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xordan on 2006-08-02
Hi, I just updated a bunch of packages, and now I'm getting errors when trying to run a 32-bit program which I didn't have before. The most important of which seems to be:

(main.tcl:5118): Pango-WARNING **: /usr/lib/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

This file does exist however. How can I get this working?

It seems that nobody on IRC would answer any question I asked at all, so hopefully someone here will be able to help! :)

Thanks.

---

### Post by Kilz on 2006-08-02
> **Xordan said:**
> Hi, I just updated a bunch of packages, and now I'm getting errors when trying to run a 32-bit program which I didn't have before. The most important of which seems to be:

(main.tcl:5118): Pango-WARNING **: /usr/lib/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

This file does exist however. How can I get this working?

It seems that nobody on IRC would answer any question I asked at all, so hopefully someone here will be able to help! :)

Thanks.

My guess is that there was a problem with that file. But since you are saying its only with 32bit applications it may have another cause. There are 2 packages I would recommend you install to see if it goes away.
[ia32-libs-gtk_16_amd64.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fi%2Fia32-libs-gtk%2Fia32-libs-gtk_16_amd64.deb&md5sum=af03ec867f5845ec011cd057a5b7307d&arch=amd64&type=main")
[libpango1.0-0_1.12.2-0ubuntu3_amd64.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fp%2Fpango1.0%2Flibpango1.0-0_1.12.2-0ubuntu3_amd64.deb&md5sum=86e82d3b08ef93c9a7dc643570e16a1b&arch=amd64&type=main")
I would bet its the first package since we are dealing with a 32bit error. Use the ```
dpkg --force-overwrite PackageName
``` to make sure it overwrites the files in case one is corupted.

---

### Post by Xordan on 2006-08-02
Ok, I downloaded and installed ia32-libs-gtk_16_amd64.deb and everything works fine. I downloaded the latest version of it ia32-libs-gtk_16.1_amd64.deb and the error occurs. So it seems like the problem is with the newest ia32-libs-gtk package.

Where can I report this to the developers?

---

### Post by Kilz on 2006-08-02
> **Xordan said:**
> Ok, I downloaded and installed ia32-libs-gtk_16_amd64.deb and everything works fine. I downloaded the latest version of it ia32-libs-gtk_16.1_amd64.deb and the error occurs. So it seems like the problem is with the newest ia32-libs-gtk package.

Where can I report this to the developers?

I have never had to make a bug report. [The page with info on how to do it is here.]("http://www.ubuntu.com/support/bugs")But I have installed this update myself and don't get the error. Its possible you have a corrupted package in your cashe. You might want to try 
```
sudo apt-get clean
```to empty it. Then try the update process again just to make sure.

---

### Post by jamesford on 2006-08-02
i got weird fonts after the latest update. works fine with 64 bit firefox, but not with 32 bit swiftfox

---

### Post by Xordan on 2006-08-02
Yes jamesford, that's exactly the same problem.

I downloaded the file fresh and I have the same problem still.

---

### Post by Kilz on 2006-08-03
Well that's 2 people so its defiantly a problem, bug report time.

---

### Post by Lonthong on 2006-08-03
I also have similar problem with my open office.
See my thread [here]("http://ubuntuforums.org/showthread.php?p=1333162#post1333162") with picture of it.

---

### Post by Lonthong on 2006-08-03
I also have similar problem with my open office.
See my thread [here]("http://ubuntuforums.org/showthread.php?p=1333162#post1333162") with picture of it.

I noticed that during the download of update proces one of open office component was failed to be downloaded.
I reran update couple of times so I thought all updates have been downloaded & installed

---

### Post by chrisccoulson on 2006-08-03
I have exactly the same problem. I posted a separate thread [here]("http://www.ubuntuforums.org/showthread.php?t=228592") before I saw this one.

Back to Windows for me until this one is fixed unfortunately:(

---

### Post by jamesford on 2006-08-03
i would be surprised if it wasnt fixed very shortly

---

### Post by chrisccoulson on 2006-08-03
Downgrading ia32-libs-gtk works for me. Upgrading to 16.1 causes the problem again.

---

### Post by jamesford on 2006-08-03
confirmed, ia32-libs-gtk is the problem

---

### Post by azmrb on 2006-08-03
Same thing here.  The update failed on a couple of files and then found new updates but I can't get them and I can't use the check function.

Check produces this error message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)
________________________________________________________________________

Nautilus and 2 nautilus dependencies show as available but I can't download them either:
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.14.3-0ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.14.3-0ubuntu1_amd64.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.14.3-0ubuntu1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.14.3-0ubuntu1_all.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.14.3-0ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.14.3-0ubuntu1_amd64.deb)
  404 Not Found

______________________________________________________________________

Also, Real Player 10 is broken now.  It can't play .rm files anymore
and when I play an mp3 the letters in the interface are just empty
rectangles.

Something has gone terribly wrong.:mad:

---

### Post by a-musing amazon on 2006-08-03
I've also downloaded the new packages and am noticing two problems. 

In Realplayer - like you - there is no text/symbols in the player, though on my PC BBC audio files play OK.

Mplayer seems OK.

The second problem is that GoogleEarth now seg-faults after the ititial splash screen.

Neither of these happened before. Both are 32-bit programs. Not noticed any other problems yet.

---

### Post by azmrb on 2006-08-03
I just checked OpenOffice and the dialog boxes are broken there too.  Just has rectangles where letters are supposed to be.  Must be a broken common library.  I can't believe they released this without more testing.

---

### Post by a-musing amazon on 2006-08-03
Just downgraded and this fixes the problem with the text in Realplayer (presumably it will work in OoenOffcie too).

NB the systac to downgrade is
sudo dpkg --force-overwrite -i <download_path>/ia32-libs-gtk_16_amd64.deb

i.e you need -i as well as --force-overwrite

However googleearth is still seg-faulting on me (catches signal 11).

---

### Post by jakedh on 2006-08-05
I just got the ia32-libs 1.4ubuntu20 and it seems to be fixed
YAY!

---

### Post by azmrb on 2006-08-05
It looks like the 16.2 version was just released.  I am downloading it now to test.

---

### Post by a-musing amazon on 2006-08-05
I'm still seeing the v16.1 to download. 

I thought I might try again sunce there has since been updates of libpango and other libs.

However it /is/ still broken and I've had to downgrade again.

---

### Post by jamesford on 2006-08-05
fixed for me

---

### Post by a-musing amazon on 2006-08-05
At the moment the version in the Ubuntu update channel is still 16.1.

However having downloaded ia32-libs-gtk_16.2_amd64.deb from [http://archive.ubuntu.com/ubuntu/pool/main/i/ia32-libs-gtk/?C=N;O=A](http://archive.ubuntu.com/ubuntu/pool/main/i/ia32-libs-gtk/?C=N;O=A) and run  sudo dpkg -i <download_path>/ia32-libs-gtk_16.2_amd64.deb realplayer now displays OK.

---

