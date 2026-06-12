---
title: "How do I Clean Up /boot partition?"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-08-25
Hi,

I've updated the kernel headers a few times and my /boot partition has all of the previous versions contained in it and it's up to 98% capacity.

What's the best way to remove old versions and to clean up /boot?

Thanks.

---

### Post by a-musing amazon on 2006-08-25
I would imagine it would be safest to use Synaptic to remove them, if that is how you updated in the first place - or if you had just updated when notified. Especially since then Synaptic also knows that you have done so.

Though I've never quite understood the difference between Remove and Completely Remove - anyone know? - I've always just use Remove.

---

### Post by a-musing amazon on 2006-08-25
To add to that, most of the /boot partition on my PC (and I expect yours) was taken up with multiple updates of the kernel, initrd, etc. (which is a packaged version of the kernel for lading into memory).

In my case I had the original, June, Dapper -2-6-15-23- kernel set through -25- and then current -26- version.

You can remove the older versions by

changing to the boot partition:
 cd /boot

check what there:
 ls -al

lets assume you have the -23- kernel set /and/ a later set  of kernel files e.g. the current -26- kernel set:

check the removal syntax, so you are sure you aren't removing your current kernels:
 ls -al *-23-*

you should see something like this:
drwxr-xr-x  4 root root    2048 2006-08-25 21:34 .
drwxr-xr-x 23 root root    4096 2006-08-07 21:24 ..
-rw-r--r--  1 root root  260570 2006-08-03 05:22 abi-2.6.15-23-amd64-generic
-rw-r--r--  1 root root  260570 2006-08-03 05:24 abi-2.6.15-23-amd64-k8
-rw-r--r--  1 root root   62892 2006-08-03 03:49 config-2.6.15-23-amd64-generic
-rw-r--r--  1 root root   62870 2006-08-03 04:09 config-2.6.15-23-amd64-k8
drwxr-xr-x  2 root root    1024 2006-08-07 21:24 grub
-rw-r--r--  1 root root 7267575 2006-08-03 22:30 initrd.img-2.6.15-23-amd64-generic
-rw-r--r--  1 root root 7264827 2006-08-03 22:31 initrd.img-2.6.15-23-amd64-k8
drwxr-xr-x  2 root root   12288 2006-06-03 23:13 lost+found
-rw-r--r--  1 root root   94760 2005-10-25 11:36 memtest86+.bin
-rw-r--r--  1 root root  890639 2006-08-03 05:22 System.map-2.6.15-23-amd64-generic
-rw-r--r--  1 root root  890639 2006-08-03 05:24 System.map-2.6.15-23-amd64-k8
-rw-r--r--  1 root root 1491706 2006-08-03 05:22 vmlinuz-2.6.15-23-amd64-generic
-rw-r--r--  1 root root 1491786 2006-08-03 05:24 vmlinuz-2.6.15-23-amd64-k8

(the filesize you see here are slightly wrong, since I removed my -23- before i wrote this and have produced this listing by editing the -26- listing).

then actually remove the redundant kernel stuff:
 sudo rm *-23-*

repeat this with all the other, older, kernel sets e.g.:
 sudo rm *-25-*

In my case removing additional kernel headers got me down from 98% to 85% utilisation on /boot, removing the redundant kernels reduced this again to 35%!

FWIW I've since rebooted and the system does still work.

---

### Post by hajk on 2006-08-26
....mmm, I can't recommend doing it the way "amusing amazon" suggests. Better use Synaptic to get rid of an old kernel, because that also fixes the GRUB boot menu and removes the associated kernel modules from the /lib/modules tree. Besides, there is less danger of making a typing error.

But if you must use the "rm" command, then at least first use the "ls" command with the same arguments -- a typing error there will show up immediately without doing any harm. Don't think you'll never make typing errors with "rm", you will!

Signed: "been there".

---

### Post by a-musing amazon on 2006-08-26
Yes, you are quite right - having recommended using Synaptic for the headers and then finding I had all this other redundant stuff in the /boot directory I was then just a bit frustrated last evening not finding where the relevant packages were in Synaptic - I should really know how to search better.

In fact what you need to search for is 'linux-image': this will then list all the kernel images sets you have, and you can then safely Remove the older ones (making sure you do keep at least one!).

Doing this will also clean out redundant stuff in the /usr/share/doc/, /usr/lib/modules/ and /usr/lib/firmware directories.

As we are getting these kernel updates automatically it seems an omission that there isn't some more automated clean-up process - especially as you are recommended to create a relatively small /boot partition. Mine is 60Mb. I would expect it filling up is now likely to become an increasingly common occurence.

---

### Post by bper on 2006-08-26
Thanks for the suggestions. I used Synaptic and was able to clean things up. Will double check to see if there isn't anything left over.

Thanks again.

---

### Post by tmetro on 2006-11-19
See wiki entries:

[PurgeOldKernels]("https://wiki.ubuntu.com/PurgeOldKernels?highlight=%28%2Fboot%29")
[SystemCleanUpTool]("https://wiki.ubuntu.com/SystemCleanUpTool?highlight=%28%2Fboot%29")

for related information. Those are proposals for tools that would perform the cleanup of /boot, but the proposals may contain useful suggestions on what steps should be taken, which coukd be applied manually.

 -Tom

---

