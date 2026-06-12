---
title: "NEED HELP: Hardy 64-bit Wireless on Compaq v6719nr"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by commonmanthemes on 2008-06-08
I need help with the wireless on my Compaq v6719nr.  It is the Atheros ar5007 wireless chipset and 64-bit Hardy.

I have been following the instructions here:

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

When I input this command:

tar xvf ndiswrapper-newest.tar.gz

I get the following error:

tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

I think I might be a total |\|008 for this one, but I've followed the instructions correctly up to this point.  I know that much for sure.  I don't know if "newest" is to be replaced with a version of the driver.  So far I've tried the following to no avail:

tar xvf ndiswrapper-ar5007eg-64-0.2.tar.gz

I'm sure the answer is somewhere on this forum but I've yet to be able to find it.  Can someone please link me to an "official" install procedure or reinterpret these directions I have to work?

I appreciate your help.

---

### Post by Anduu on 2008-06-08
Try this [http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by jblackthorne on 2008-06-08
> **commonmanthemes said:**
> 

When I input this command:

tar xvf ndiswrapper-newest.tar.gz

I get the following error:

tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now



Your problem looks to be simply that you are trying to extract files from a tar archive, but you are using the wrong name.  Try one of the following:

Option 1: right-click on the tar file and click "Extract Here".  (This allow graphical extraction through Nautilus file manager)

Option 2: type "tar xvf ndis" and then press <tab> to autocomplete the remaining letters

---

### Post by Flag on 2008-06-09
Why don't you use synaptic to install ndiswrapper, then follow one of the instructions, make sure you got the right driver.
Worked for me.
Atheros AR5007, I use the 5211 driver on an Aspire 7520.
Good luck

---

### Post by commonmanthemes on 2008-06-10
Those seemed okay until the svn command.

root@rafox-laptop:~# svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname ([http://svn.madwifi.org](http://svn.madwifi.org))

Think the website is down temporarily?

---

