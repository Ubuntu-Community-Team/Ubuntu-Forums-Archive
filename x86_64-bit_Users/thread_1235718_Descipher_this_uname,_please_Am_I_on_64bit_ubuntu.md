---
title: "Descipher this uname, please: Am I on 64bit ubuntu?"
date: 2009-08-09
forum: x86 64-bit Users
---

### Post by Poddster on 2009-08-09
Hi,

I installed Ubuntu a few weeks ago and I was fairly confident I installed the 64bit version. I've been believing that this was true untik today, when I noticed I had only 3.2gb of RAM available, which is a sure sign that I only have the 32bit version.

$ uname
Linux emma 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

i686 is given my -m, but which part tells me if I've a 64bit linux running? I'm guessing instead of generic it should say 64bit or something similiar? If it's correct that I'm running 32 bit, well:

 a) that sucks. I've spent ages installing all the things I need and messing about with graphics drivers and asound.confs in order to get things working how I want them
b) is it possible to just upgrade without doing a free install, or have my past few weeks been a waste of time?

---

### Post by snowpine on 2009-08-09
You are running 32 bit, but if it works ok for you, it hasn`t been a waste of time... lots of people run 32 bit on their 64 bit hardware.

---

### Post by Sef on 2009-08-09
If you had installed 64-bit it would look like this:

> Linux jokat0 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 **x86_64** GNU/Linux
  (I bolded the part that says it is 64-bit.)

---

### Post by Barafu Albino Cheetah on 2009-08-10
There is a way to convert 32bit ubuntu to 64. Search for a good howto.

---

### Post by Yellow Pasque on 2009-08-10
I would not recommend re-doing your install just to move to 64-bit unless you actually use more than 3.2GB of RAM or you run apps (on a regualr basis) that actually take advantage of 64-bit.

The next time you have to install fresh, you can then use 64-bit.

---

