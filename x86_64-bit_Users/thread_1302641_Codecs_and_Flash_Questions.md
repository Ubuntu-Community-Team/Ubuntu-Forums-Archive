---
title: "Codecs and Flash Questions"
date: 2009-10-27
forum: x86 64-bit Users
---

### Post by BarfBag on 2009-10-27
Howdy, all!  9.10's release will be the same day my new PC arrives!  How awesome is that?

I'll be using 64 bit for the first time, and have some questions.  Does installing ubuntu-restricted-extras still work?  Will that install all the codecs commonly used?  Also, what about libdvdcss?  I know that has to be installed separately, but is that compatible with 64 bit?

My second question involves flash.  Is it still able to be installed through apt-get, or do the instructions for downloading it from Adobe have to be followed?

Thanks in advance!

---

### Post by fancypiper on 2009-10-27
Question 1 yes, yes, yes.
Question 2 yes, no.

---

### Post by oldos2er on 2009-10-27
> **BarfBag said:**
> I'll be using 64 bit for the first time, and have some questions.  Does installing ubuntu-restricted-extras still work?  Will that install all the codecs commonly used?  Also, what about libdvdcss?  I know that has to be installed separately, but is that compatible with 64 bit?

My second question involves flash.  Is it still able to be installed through apt-get, or do the instructions for downloading it from Adobe have to be followed?


 Installing ubuntu-restricted-extras gives you 32-bit flash run with nspluginwrapper. In my opinion 64-bit flash is a better option for someone running 64-bit Ubuntu.

 You'll need to enable the Medibuntu repository to install libdvdcss2; and yes, it's 64-bit.

---

### Post by dabl on 2009-10-27
Just follow this (using "karmic", of course) and it all should work correctly:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

