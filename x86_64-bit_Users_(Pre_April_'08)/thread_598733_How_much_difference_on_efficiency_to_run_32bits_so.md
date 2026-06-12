---
title: "How much difference on efficiency to run 32bits softwares on i386 ubuntu and 64bit?"
date: 2007-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by fansico on 2007-10-31
Now I am using a laptop with CPU Core 2 T5600, Memory 1G,

I just switched from WinXP to Ubuntu 7.10 i386 last week and found it really great, with high speed and friendly interface and abundant softwares!

After I read some threads here, I know AMD64 version is not only for AMD64 but also for Intel Core 2. So I'm considering to switch to the 64bit version Ubuntu.

But if I just use some softwares on Multimedia, Web Browser, Openoffice and some science software like Octave, Abinit, PWscf, is there much difference on efficiency?

And are most of the 32bit softwares compatible with the 64bits Ubuntu?

Thank you!

---

### Post by sph on 2007-10-31
Good questions!
I believe you will find most of your answers here:

[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)


Have fun,
sph

---

### Post by elanthis on 2007-10-31
The difference in performance varies, but in general, things are much faster in 64-bit.  This is due to the architectural improvements of the amd64/x86-64 design over regular i386/x86.

Pretty much all software that Ubuntu ships is available on the amd64 version of the distribution.  There is no need to run 32-bit versions of most open source applications like Firefox or Open Office, as they all run just fine in native 64-bit mode.

64-bit Linux is capable of running all 32-bit applications.  The only problem is that Ubuntu only has a small handful of 32-bit libraries in the amd64 edition; unlike RPM-based systems, you can't just install both the 32-bit and 64-bit versions of a library.  Most of the libraries you'll need for proprietary 32-bit applications exist (including gtk, SDL, and various system libraries), but I have run into situations where some popular 32-bit app will not run on Ubuntu due to the lack of some necessary 32-bit library that Ubuntu only ships in 64-bits.  You can remedy this yourself by manually installing the missing library.  The number of applications that you'll run into this problem with are very very small, however, and you can always file a bug requesting the addition of the necessary library to the 32-bit compat packages.

---

### Post by Yellow Pasque on 2007-10-31
A 32-bit program isn't going to run significantly faster with a 64-bit OS. Use 64-bit apps wherever possible.

---

