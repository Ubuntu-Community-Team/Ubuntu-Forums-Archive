---
title: "Problems installing wine 1.3.33"
date: 2011-11-21
forum: Wine
---

### Post by jbumgar on 2011-11-21
I am having problems installing wine 1.3.33.  I uninstalled the old version but I get this message when trying to do this:


jb@jb:~$ sudo apt-get build-dep wine1.3
[sudo] password for jb: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


What do I need to do?

---

### Post by azmyth on 2011-11-21
You probably have synaptic or some other package manager open. If no then reboot as it should go away.

---

### Post by jbumgar on 2011-11-21
Did a reboot and it failed!  So I rebooted in the recovery mode and that restored my my old wine version.  So now I am going to uninstall it again and see what happens. grin

---

### Post by azmyth on 2011-11-21
It shouldn't be doing this. You need to check the permission of /var/lib/dpkg/lock and you can also do a sudo lsof | grep lock to see which process has taken control of your lock file.

---

