---
title: "Error 2: Bad File or Directory Type"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by jafenske on 2008-04-26
When Grub loads I get this error: Error 2: Bad File or Directory Type.

I googled it amd I found some bug reports put I still don't really understand whats going on.  If some one could help me I would appreciate it

---

### Post by John.Michael.Kane on 2008-04-26
> **jafenske said:**
> When Grub loads I get this error: Error 2: Bad File or Directory Type.

I googled it amd I found some bug reports put I still don't really understand whats going on.  If some one could help me I would appreciate it

Was this system upgraded from a previous version of Ubuntu or a Clean install?

From what I can source on the error listed. the following info was returned. 

"Bad file or directory type" This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.

Which leads me to believe your install might be corrupt, and would require a clean install, however. Being that I have not experience this error personally you may want to wait until other members chime in on this problem.

---

### Post by jafenske on 2008-04-26
Yes this is a clean install... I have redone the install a couple of times and the same result.

---

### Post by jafenske on 2008-04-27
I solved my problem...  Drop me a message if you are curious

---

### Post by markymark on 2008-07-19
I also got this problem with a multiboot linux system.
The old grub was unable to boot the new linuxes (in this
case both mandriva spring and opensuse 11.0 could 
not be booted).

I'm assuming that this is the
grub vs inode problem discussed in the following
[http://www.linuxplanet.com/linuxplanet/tutorials/6480/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6480/1/)
caused by new distributions using  
ext3 filesystems with 256 byte inodes

grub is not able to access these partitions

---

