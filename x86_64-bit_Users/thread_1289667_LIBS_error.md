---
title: "LIBS error"
date: 2009-10-12
forum: x86 64-bit Users
---

### Post by DUCKFACE on 2009-10-12
hello friends
i have a problem when i try to apt-get somethin ... 
/sbin/ldconfig.real: /usr/lib/libjspTru64Alpha.so is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libjspAixPpc.so is not an ELF file - it has the wrong magic bytes at the start.
Ubuntu 9.04 

i have no idea from where r those files and how to remove em ... 
as you can see 
dpkg: *libjspTru64Alpha.so* not found.
dpkg: *libjspAixPpc.so* not found.

what can i do ?

---

### Post by dabl on 2009-10-12
Not a new error:

[http://bbs.archlinux.org/viewtopic.php?id=36123](http://bbs.archlinux.org/viewtopic.php?id=36123)

[http://forums.fedora-fr.org/viewtopic.php?pid=171378#p171378](http://forums.fedora-fr.org/viewtopic.php?pid=171378#p171378)

[http://ubuntuforums.org/archive/index.php/t-204974.html](http://ubuntuforums.org/archive/index.php/t-204974.html)

In that last thread, it looks like the problem is with a non-standard repository in your sources.list file.  So maybe you need to comment out the non-ubuntu source repo, and then do ```
sudo dpkg --reconfigure -a
```

---

### Post by DUCKFACE on 2009-10-13
I din't try to instll pacman .. or KDE .. 
i just made apt-get upgrade .. and the libs bet wrong ... 
my french is very ver bad .. ilke i dont have one .. 
so .. how can i see what progs support this files .. and how to remove em . ?
and btw .. on the top of this .. the apache crash every day 
*** glibc detected *** /usr/sbin/apache2: double free or corruption (!prev): 0x00007ffdff879760 ***
======= Backtrace: =========
/lib/libc.so.6[0x7ffdfd762cb8]
/lib/libc.so.6(cfree+0x76)[0x7ffdfd765276]
/usr/lib/libapr-1.so.0(apr_allocator_destroy+0x45)[0x7ffdfdc940f3]
/usr/lib/libapr-1.so.0(apr_pool_destroy+0x11a)[0x7ffdfdc94d88]
/usr/sbin/apache2[0x7ffdfe571bde]
/usr/sbin/apache2[0x7ffdfe57205c]
/usr/sbin/apache2[0x7ffdfe5722ea]
/usr/sbin/apache2(ap_mpm_run+0xaca)[0x7ffdfe572e1a]
/usr/sbin/apache2(main+0xa2d)[0x7ffdfe54860d]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7ffdfd7095a6]
/usr/sbin/apache2[0x7ffdfe5476b9]

---

