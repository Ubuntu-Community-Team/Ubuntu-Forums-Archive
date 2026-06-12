---
title: "Error setting up NFS on 10.3"
date: 2007-10-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by coldstatue on 2007-10-21
First let me state that I have a desktop and laptop - both setup to use NFS properly in Ubuntu FF. My desktop in a dual-boot w/ openSuSE 10.3 I have used all of the same paths in openSuse, in terms of path and name of the shared folder for simplicity. My IP (as well as hostname)  is the same in SuSE as it is in Ubuntu.

I am using 10.3, and I can't set up NFS. I right click on my share folder, go through all the appropriate NFS settings, and click ok. When I click ok and put in my admin password, I get this.


Command 'cp '/tmp/kde-coldstatue/kdesktopARl2Ka.tmp' '/etc/exports';exportfs -ra;' not found

Now the temp file is created, but disappears as soon as I click ok on this message. As far as I can tell, the temp file is empty. Because of my user name and the changing temp file name, I am having a really hard time finding info about this.

I tried copying my exports file from Ubuntu after messing with this for a while, but it didn't work.

Doesn't seem related, but I DO NOT have a firewall set up.

Please tell me you know the secret solution! 

Thanks

---

