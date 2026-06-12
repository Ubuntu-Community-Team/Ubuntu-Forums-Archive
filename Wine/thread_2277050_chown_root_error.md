---
title: "chown root error"
date: 2015-05-06
forum: Wine
---

### Post by mike311 on 2015-05-06
ubuntu14@ubuntu14-Aspire-ES1-512:~$ sudo addgroup _system HiDownload_platinum
[sudo] password for ubuntu14: 
addgroup: The user `_system' does not exist.
ubuntu14@ubuntu14-Aspire-ES1-512:~$ sudo addgroup -system HiDownload_platinum
Adding group `HiDownload_platinum' (GID 128) ...
Done.
ubuntu14@ubuntu14-Aspire-ES1-512:~$ sudo chown root:HiDownload_platinum
chown: missing operand after ‘root:HiDownload_platinum’
Try 'chown --help' for more information.
ubuntu14@ubuntu14-Aspire-ES1-512:~$ sudo chown root:/HiDownload_platinum /usr/bin/dumpcap
chown: invalid group: ‘root:/HiDownload_platinum’
ubuntu14@ubuntu14-Aspire-ES1-512:~$ 


what does chown invalid group mean? Regards mike311

---

### Post by steeldriver on 2015-05-06
it means the name of the group is HiDownload_platinum not **/**HiDownload_platinum

---

### Post by mike311 on 2015-05-07
Thanks Steeldriver so the command would be
 
sudo chown root:HiDownload_platinum /usr/bin/dumpcap

and not

sudo chown root:/HiDownload_platinum /usr/bin/dumpcap

 
?

---

