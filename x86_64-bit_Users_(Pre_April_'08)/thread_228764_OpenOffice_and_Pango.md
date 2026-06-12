---
title: "OpenOffice and Pango"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by drlock on 2006-08-03
After an apt-get update today, OpenOffice is having font troubles.  Primarily the Open and Save dialog boxes render all characters with a square rather than the character.

Running oowriter from the command line shows this error over and over:
(soffice.bin:5693): Pango-WARNING **: /usr/lib/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'


/usr/lib/pango/1.5.0/modules/pango-basic-fc.so does exist and is readable to the world.  I did find that /etc/pango/pango.modules had paths to 1.4.0 which was no longer valid.  I changed the paths but did not fix anything.
(I have another non-64 bit machine and can not duplicate the problem there, so I am not sure what the cause is)

Any ideas?  Thanks

---

### Post by jamesford on 2006-08-03
yes, many of us have the same prob, therse a fix towards the end here [http://www.ubuntuforums.org/showthread.php?t=228179](http://www.ubuntuforums.org/showthread.php?t=228179)

im sure ubuntu will fix it shgortly too

---

### Post by jonah1980 on 2006-08-03
yeah i did an "update manager" early on today and i have the same problem.

in open office the open dialog looks fine but when i do a save as all the text is messed up. where it would normally say "browse other folders", "save" "cancel" and all the other writing in dialog box is just squares instead of writing...

hope someone can sort this out, messy!

---

### Post by drlock on 2006-08-03
Thanks guys for the quick response.

For those who may stumble onto this thread there seems to be a problem in the 16.1 version of ia32-libs-gtk.  There is already a bug report on it here: [https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55058](https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55058)

The fix for the time being is to downgrade to version 16.0, which you can get here: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fi%2Fia32-libs-gtk%2Fia32-libs-gtk_16_amd64.deb&md5sum=af03ec867f5845ec011cd057a5b7307d&arch=amd64&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fi%2Fia32-libs-gtk%2Fia32-libs-gtk_16_amd64.deb&md5sum=af03ec867f5845ec011cd057a5b7307d&arch=amd64&type=main)

After downloading you can install it with: sudo dpkg -i ia32-libs-gtk_16_amd64.deb

Thanks again for the help.

---

### Post by jamesford on 2006-08-03
you can also install the previous version in synaptic by choosing 'force version' from the edit menu

---

### Post by jonah1980 on 2006-08-03
so do you think ubuntu devs will quickly sort this out and it'll "update manager" sort itself out?

---

### Post by Kilz on 2006-08-03
> **jonah1980 said:**
> so do you think ubuntu devs will quickly sort this out and it'll "update manager" sort itself out?

Lets hope so. Seeing how a downgrade has produced no noticeable problems it may not take long. I recommend everyone lock the version of this lib on the old one for now. That way it wont keep coming up as a upgrade and it wont accidentally be installed.

---

