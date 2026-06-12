---
title: "Boot Up Manager"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by kozimodo on 2005-10-16
I noticed one other person had problems with the PPC version of BUM. The error I get is:
```
Can't locate stddef.ph in @INC (did you run h2ph?) (@INC contains: /usr/share/bum/ /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/bits/types.ph line 10.
Compilation failed in require at /usr/lib/perl/5.8/termios.ph line 9.
Compilation failed in require at /usr/lib/perl/5.8/bits/ioctl-types.ph line 8.
Compilation failed in require at /usr/lib/perl/5.8/sys/ioctl.ph line 9.
Compilation failed in require at /usr/share/bum//bumlib.pm line 29.
Compilation failed in require at /usr/bin/bum line 44.
BEGIN failed--compilation aborted at /usr/bin/bum line 44.

```
Is there some dependency that is broken? What do I need to install to fix it?

---

### Post by DJ_Max on 2005-10-16
I got the same error on my mac. I thought I was the only one. I installed it from the repository, so it looks like a bug. Someone should file a bug report.

---

### Post by kozimodo on 2006-01-01
I filed a bug report and it is apparently fixed in the Debian repository
```
wget http://http.us.debian.org/debian/pool/main/b/bum/bum_2.1.4-1_all.deb
sudo dpkg -i bum_2.1.4-1_all.deb
```

---

### Post by abqaussie on 2006-01-17
Yep that works great! However first I got...

(Reading database ... 67529 files and directories currently installed.)
Preparing to replace bum 1.3.2-1 (using bum_2.1.4-1_all.deb) ...
Unpacking replacement bum ...
dpkg: dependency problems prevent configuration of bum:
 bum depends on libgtk2-gladexml-perl; however:
  Package libgtk2-gladexml-perl is not installed.
<snip>

So I went and found the libgtk2-gladexml-perl package in Synaptic (which correctly reported I had one broken package when I opened it). 
Install the package, retry and voila - working bum.

---

