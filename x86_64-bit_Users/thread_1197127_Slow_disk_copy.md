---
title: "Slow disk copy"
date: 2009-06-25
forum: x86 64-bit Users
---

### Post by BugBuster on 2009-06-25
On Windows Vista i get 44MB/s while copying from to ntfs, while on ubuntu 9.04 its 15-20MB/s max on the same machine.

Any suggestions?

---

### Post by foxmulder881 on 2009-06-25
Off the top of my head, I can only think that your available disk space could be small. Have you got much free hard drive space available?

---

### Post by BugBuster on 2009-06-25
> **foxmulder881 said:**
> Off the top of my head, I can only think that your available disk space could be small. Have you got much free hard drive space available?

Well its a 160GB partition on a 250 GB SATA II and I performed the test with both the OS'es on this very same partition.So I think the space limit is same for both.

Here is the output from df -h;

/dev/sda7             9.9G  3.2G  6.2G  34% /
tmpfs                 868M     0  868M   0% /lib/init/rw
varrun                868M  296K  868M   1% /var/run
varlock               868M     0  868M   0% /var/lock
udev                  868M  148K  868M   1% /dev
tmpfs                 868M  684K  868M   1% /dev/shm
lrm                   868M  2.5M  866M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda1              21G  4.6G   16G  23% /media/Windows
/dev/sda5             161G   89G   72G  56% /media/Data
/dev/sda6              43G   23G   19G  55% /media/VBox

And the partition that we are speaking about is sda5

---

### Post by sebastianabate on 2009-06-26
Are you testing the speed on the ntfs partition from Windows and Linux? If this is the case is normal the diference in performance (the Linux ntfs driver is the culprit). To make a reliable test you must do it over a native Linux filesystem in Linux (ext2/3/4, reiserfs, etc) , and over a native Windows filesystem in Windows (fat32 or ntfs).

In my system I get 30/35 MBs from Windows on ntfs, 40/42 MBs from Linux on ext4, and 18/20 MBs from Linux on ntfs.

Other variable in the tests is the disk controller driver; if you have a device poor supported in Linux the performance may be impacted.

PD: sorry for my english, I'm from Argentina.

---

