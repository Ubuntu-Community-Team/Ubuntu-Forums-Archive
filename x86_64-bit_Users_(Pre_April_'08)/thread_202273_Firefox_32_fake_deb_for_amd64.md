---
title: "Firefox 32 fake deb for amd64"
date: 2006-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by EPOX123 on 2006-06-23
Hi, i know this is kinda stupid but is there a fake Firefox deb that will install Firefox 32 into x86_64.

I want an easy way to delete this app, if you know what i mean.

---

### Post by chrestomanci on 2006-06-23
[QUOTE=EPOX123]Hi, i know this is kinda stupid but is there a fake Firefox deb that will install Firefox 32 into x86_64.

I want an easy way to delete this app, if you know what i mean.[/QUOTE]

If you are trying to run 32 bit firefox so that you can use flash and other plugins, you need to setup a chroot environment. See:
[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=space](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=space)
You will need about 1Gb disc space.

---

### Post by EPOX123 on 2006-06-23
Intresting thanks, although that seams like alot of work LOL but ill give it a shoot :-k

---

### Post by Kilz on 2006-06-23
[QUOTE=chrestomanci]If you are trying to run 32 bit firefox so that you can use flash and other plugins, you need to setup a chroot environment. See:
[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=space](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=space)
You will need about 1Gb disc space.[/QUOTE]
You do not need to setup a chroot, Dapper will let you install the 32 bit firefox and plugins without a chroot. Someone on the Document team keeps deleting the page, He has it redirecting to the java page. I have writen the document team mailing list, but they dont answer. I guess I will have to make a howto on the forums with updated information. Here is a link for now to the diffrence page for the old howto. The directions are still folowable.
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava?action=diff](https://wiki.ubuntu.com/FirefoxAMD64FlashJava?action=diff)

---

### Post by vigleik on 2006-06-23
[QUOTE=chrestomanci]If you are trying to run 32 bit firefox so that you can use flash and other plugins, you need to setup a chroot environment. See:
[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=space](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=space)
You will need about 1Gb disc space.[/QUOTE]

You do not have to set up chroot. In fact, to run 32 bit firefox you don't even have to install it. Just download firefox or swiftfox, unpack and you can run firefox with something like /home/username/swiftfox/firefox. Navigate to a flash site, install plugin and voila. This also makes the 32 bit firefox extremely easy to delete, if you want to.

You might want to move your .mozilla directory out of the way before you do this.

Vigleik

---

### Post by EPOX123 on 2006-06-23
I want to use DEB's so i can easly install update or remove. ;-) can i use 32bit debs on x86_64?

---

### Post by Kilz on 2006-06-23
[QUOTE=EPOX123]I want to use DEB's so i can easly install update or remove. ;-) can i use 32bit debs on x86_64?[/QUOTE]
Yes you can use 32 bit .deb files with sudo dpkg --force-architecture -i <filename> But I think you may have to add -overrwrite to for something that already exists. But you wont be able to update it the normal way, a 32 bit program will be updated with a 64 bit version.
Besides, is it that hard to download the next version of firefox, untar it,and  cp it into place?

---

