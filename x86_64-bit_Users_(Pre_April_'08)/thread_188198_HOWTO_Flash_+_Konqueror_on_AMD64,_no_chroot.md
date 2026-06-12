---
title: "HOWTO: Flash + Konqueror on AMD64, no chroot"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jiilik on 2006-06-03
I have this working, here's what I did...

Instructions for using flash (32, proprietary) with konqueror on amd64.

```
sudo mv /usr/bin/nspluginscan /usr/bin/nspluginscan_64
sudo mv /usr/bin/nspluginviewer /usr/bin/nspluginviewer_64
```

get the following i386 packages from packages.ubuntu.com
konqueror-nsplugins_3.5.2-0ubuntu26_i386.deb
libxcursor1_1.1.5.2-0ubuntu4_i386.deb
libxfixes3_3.0.1.2-0ubuntu3_i386.deb
libxft2_2.1.8.2-0ubuntu2_i386.deb


One at a time for the above four packages: 

open them with ark, and look for data.tar.gz. Open this file (again using ark, it'll spawn a second window) and extract it's contents to /home/username (where username is your username)

You should now have /home/username/usr/lib and /home/username/usr/bin, etc.

Issue the following commands:
```
sudo cp -r /home/username/usr/lib/* /usr/lib32/
sudo cp /home/username/bin/* /usr/bin/
```

Now download flashplayer 7 from macromedia. Extract the archive, and issue the following commands...
```
chmod u+w flashplayer-installer
nano flashplayer-installer
```

Look for line 252 which should look like:
```
  i[3456]86)
```
and change it to:
```
  i[3456]86|x86_64)
```

Save and close the file.
Run ./flashplayer-installer and choose /home/username/.mozilla as the location to install the plugin

Rescan for netscape plugins from konq's settings, and then visit a site using flash.  Tada!

(you can now rm -rf /home/username/usr/ and delete the deb files you earlier downloaded)

The only downside to this method is that this solution works outside of the normal apt/dpkg system, so upgrading will probably not respect these changes.

---

### Post by NamShub on 2006-06-20
How do I open a .deb file with ark? I downloaded the files but they are not in tar.gz format and ark will no open them. As far as I know they are binary files, oorrect?

---

### Post by cameronsstone on 2006-06-23
Use dpkg -x konqueror-nsplugins_3.5.2-0ubuntu26_i386.deb /home/username instead.

---

### Post by Jiilik on 2006-08-23
Just an update to this information - flash stops working whenever you update the kong-nsplugins thing using the normal apt/adept/etc methods.  The only step that needs to be repeated is to replace nspluginscan and nspluginviewer with the 32bit versions again.  Enjoy.

---

### Post by eflavoie on 2006-11-13
Update for Edgy.  After upgrating to Edgy, the flash windows were very tiny in Konqueror.  I dowloaded the newer versions of the i386 packages and followed the instructions on this post and the problem was gone.

---

