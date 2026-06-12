---
title: "[SOLVED] Broken system (libc.so.6)"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by radopenev on 2007-11-09
Hi !I need any help!:confused:
I'm Ubuntu Dapper x86 64 bit user
According to post ["Howto make debian standard debs from scratch"]("http://ubuntuforums.org/showthread.php?t=51003")
with Synaptic I installed packages following 
[Debian's guide!]("http://www.debian.org/doc/maint-guide/")
But after that i can't run Ubuntu !
**error while opening shared file libc.so.6**
And loading crashed!
Using liveCD i mounted brocken filesystem:
**sudo mount -t ext3 /dev/sda3 /mnt**
And now I see somthing wrong...
 **/lib/libc.so.6** is link to **/lib/libc-2.3.6.so**
and in lib64
**/lib64/libc.so.6** is link to **/lib/**libc-2.3.6.so too
But every another link :
**/lib64/anotherlink.so.*** is link to /**lib64**/anotherlib*.so:confused:
How can i restore my Ubuntu please help!
Sorry for my English!

---

### Post by radopenev on 2007-11-09
Hi people!
I solve the problem just now,but maybe that is not right solution!
1.delete link **libc.so.6**
2. rename library **libc-2.3.6.so** to **libc.so.6**
System runing OK!:(:(:(
I knew that is wrong but ...please help me with right   solution!:confused::confused:
Sorry for my English!

---

### Post by Cappy on 2007-11-09
The libraries are supposed to be linked like that.

Maybe you should try:
```
sudo apt-get --reinstall install libc6
```

I don't see the list of packages that you installed that broke your Ubuntu. That list would probably help fix the problem.

Maybe [CODEsudo apt-get install ubuntu-minimal[/CODE] if you removed something essential.

---

### Post by radopenev on 2007-11-10
Hi ,Cappy  !
Thank you for help!
I follow step by step 
**[Programs you need for development]("http://www.debian.org/doc/maint-guide/ch-start.en.html")**
Some packages I've been installed yet.Think the problem appear  after installation **libc6-dev**
through Synaptic I've install:
cpp-3.4 (3.4.6-1ubuntu2)
g77 (4:3.4.6-1)
g77-3.4 (3.4.6-1ubuntu2)
gcc-3.4 (3.4.6-1ubuntu2)
gcc-3.4-base (3.4.6-1ubuntu2)
libg2c0 (1:3.4.6-1ubuntu2)
libg2c0-dev (1:3.4.6-1ubuntu2)
dh-make (0.40)
I skip **lintian**;** linda** ; **pbuilder** ,because Synaptic allarm me 
for problem with package identification and I was closed Synaptic.
Sorry for my English!
Best regards!

---

### Post by Cappy on 2007-11-11
I don't know why any of those packages would cause a problem. None of those packages remove anything from Ubuntu. What is also weird is that renaming the linked file would fix the problem.

The lib6-dev installs a usr/lib/libc.so but that shouldn't be conflicting.

Your ubuntu is fine for the moment  but without knowing the cause of this problem it could happen again.

---

