---
title: "vmware problem under feisty"
date: 2007-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2007-05-18
I always get the below when i try run vmware. Sometimes the config script will work and then it'll start up but then on reboot i get the same prob and have to try it again. Can anyone please help fix this?

> jonah@jonah-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

jonah@jonah-desktop:~$ sudo /usr/bin/vmware-config.plPassword:
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Workstation

Execution aborted.

jonah@jonah-desktop:~$ 


---

### Post by M$LOL on 2007-05-18
See [here]("http://ubuntuforums.org/showthread.php?t=406399").

---

