---
title: "Dpkg Issue - Amazon.com's Deb Package and  &quot;--configure -a&quot;"
date: 2008-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by CMM on 2008-03-21
Hi folks,

I know this issue has been talked about frequently, but none of the other posts seem to resolve my particular issue with this.  I was doing some video editing in Kino on my laptop running Gutsy 7.10 64-bit and needed a particular MP3.  I decided to be quick about it and just buy it from Amazon, but I needed to install their client.  However, when I tried installing the Gutsy 7.10 .deb they have I got a bunch of errors because it doesn't want to run on a 64-bit architecture.

The entry for the Amazon client still showed up in Add/Remove and on my menus, so I removed it from the menus and left it alone.  Until last night when I went to install some updates and got the error saying I needed to run "dpkg --configure -a".

The errors I'm getting are all related to the amazonmp3.deb.  I get a long list of errors all mentioning some dependency I'm missing for the client.

The final error mentions inframts, but I'm pretty sure it's all related to Amazon.  I've tried running "dpkg --configure -a && apt-get -f install", deleting cache files and a few other things other threads said worked, but I still can't open Synaptic or run any aptitude commands from the terminal.

I'll post the actual errors and maybe even my sources list as soon as I can.  I'll just have to bring up laptop and post from there in a little wuile.  For now any advice would be greatly appreciated.

Is there a way to purge the partial installation of the Amazon client?

---

### Post by CMM on 2008-03-21
I solved my issue with the Amazon client by just installing the dependencies it wanted and then using "dpkg -i --force-architecture amazonmp3.deb".  Amazon does not run, but it 'installed' without any errors.

However, now I get:

Setting up unzip (5.52-10ubuntu1.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)

After running sudo apt-get upgrade.

apt-get update now works fine.

---

### Post by CMM on 2008-03-21
For the sake of closing this topic:  I have resolved the issue.

I ran "sudo dpkg -P initramfs-tools" in the terminal and received errors stating I could not remove iniramfs because of all of its dependencies.  Which was fine, I didn't want to remove it, but this allowed me to open up Synaptic and install packages again.

I then located the util-linux package and found it was uninstalled.  After installing it getopt was back in my usr/bin directory and everything now works fine.

I'm still stuck with this Amazon MP3 client that refuses to actually launch, but at least I seem to have dodged an Ubuntu reinstall.

Hopefully someone else finds this useful.

---

### Post by Cappy on 2008-03-21
If "amazonmp3" shows a shared library error then use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
```
getlibs /usr/bin/amazonmp3
```

---

