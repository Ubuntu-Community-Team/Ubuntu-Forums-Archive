---
title: "Install 32bit Intel compiler on gutsy x86-64"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by pguo on 2008-01-07
After some attempts, I finally managed to install and run Intel compiler 10.1.011 (both 32-bit and 64-bit) on Ubuntu 7.10 (gutsy) x86_64.  Here are my approache, for the people who need it.

1. Install ICC as normal.  ICC 10.1.011 already has installation support for Ubuntu.  Maybe you need to skip some warnings.  But the installation process is rather smooth, and don't need extra hacking.  It will install 32-bit compiler under /opt/intel/cc/10.1.011 and 64-bit compiler under /opt/intel/cce/10.1.011.  The 64-bit compiler works fine without extra modification.  But if you want to run 32-bit compiler and produce 32-bit code, it will reporting some errors during linking. E.g.
  ld: skipping incompatible /usr/lib/libm.so when searching for -lm
  ...
  ld: i386:x86-64 architecture of input file `/usr/lib/crt1.o' is incompatible with i386 output
 ...
My approache will fix these link errors.

2. Make an directory like /opt/intel/build32, and make some symbolic links:
  # mkdir /opt/intel/build32
  # ln -s /usr/bin /opt/intel/build32/bin
  # ln -s /usr/include /opt/intel/build32/include
  # ln -s /usr/lib32 /opt/intel/build32/lib

3. Set environment GCCROOT to point to that directory:
  $ export GCCROOT=/opt/intel/build32

4. Run 32-bit icc as normal, it should compile and link successfully.  Or you can patch /opt/intel/cc/10.1.011/bin/icc and /opt/intel/cc/10.1.011/bin/icpc, set the GCCROOT before actually run iccbin or icpcbin.

Although I didn't test it on Debian, but I think Debian may also use similar approach.

---

### Post by leohart on 2008-04-27
Thanks for the great first post, I cannot even get the 64-bit compiler to work. I use the Eclipse extension from Intel.

I notice that it resides in the cc directory (so it might not work with 32-bit). Do you use Eclipse at all?

---

