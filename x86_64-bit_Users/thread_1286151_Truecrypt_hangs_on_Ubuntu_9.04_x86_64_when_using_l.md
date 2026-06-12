---
title: "Truecrypt hangs on Ubuntu 9.04 x86_64 when using large container file"
date: 2009-10-08
forum: x86 64-bit Users
---

### Post by dslbrian on 2009-10-08
I've been running into a Truecrypt problem on Ubuntu 9.04 on x86_64.  Truecrypt was installed from Synaptic, and I believe it is version 6.2a (I did not compile it from scratch).  The kernel is the current generic one for 9.04.

I have a large data set, approx 350GB which I was attempting to place into an encrypted backup container file.  I created a 400GB container file on a 500GB host drive (both the container and host drive are formatted as ext3).

What happens is that when I copy the data from the original location into the container file it will get anywhere from 250GB-300GB into the copy and then hang the machine.  I've been able to do this 4 times.  Unfortunately this takes several hours to reproduce (3hrs to create the TC container and another 3hrs or so for the copy).

The source files are anywhere from a few kb (text files) to several Gb (other TC containers).  It doesn't seem to have any problems with any particular file, it simply hangs after transferring a large amount in total.

When the machine hangs there doesn't seem to be any error message (I tried monitoring dmesg, and doing a tail -f /var/log/messages, but there is no error that shows). 

Just as a check on the hardware I did the same copy to the drive without using a TC container and it worked fine.

I'm guessing there is some problem between the kernel and truecrypt, but I'm not sure what direction to go - recompile kernel, recompile TC, wait for 9.10?  If anyone has ideas I would be interested to know.  Thanks.

---

