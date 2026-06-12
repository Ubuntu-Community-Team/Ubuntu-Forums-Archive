---
title: "question about using apt-get to install libfftw3-dev"
date: 2008-07-11
forum: x86 64-bit Users
---

### Post by pegasusmd on 2008-07-11
Hi all, 

I 'm trying to install libfftw3-dev in my computer. gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7))

After I use ' apt-get install linfftw3-dev' , the libfftw3 files are in /usr/lib. How can I install them in /usr/lib64 ? 

The libfftw3 library I installed should be 64 bits because the file name is 
libfftw3-dev_3.1.2-3ubuntu1_amd64.deb

Thanks, 

Dan

---

### Post by Kilz on 2008-07-11
> **pegasusmd said:**
> Hi all, 

I 'm trying to install libfftw3-dev in my computer. gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7))

After I use ' apt-get install linfftw3-dev' , the libfftw3 files are in /usr/lib. How can I install them in /usr/lib64 ? 

The libfftw3 library I installed should be 64 bits because the file name is 
libfftw3-dev_3.1.2-3ubuntu1_amd64.deb

Thanks, 

Dan

/usr/lib64 in a 64bit install is a symlink to /usr/lib. Its the same directory.

---

### Post by pegasusmd on 2008-07-11
> **Kilz said:**
> /usr/lib64 in a 64bit install is a symlink to /usr/lib. Its the same directory.

I met the error when I was installing a tool named ROOT

/usr/bin/ld: /usr/local/lib/libfftw3.a(plan-dft.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libfftw3.a: could not read symbols: Bad value

it may related to the library version.

---

