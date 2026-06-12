---
title: "Thunderbird 2.0"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by StratosL on 2007-04-22
Any chance of seeing tb2.0 64bit in Feisty? 

I tried compiling from source and also building according to [http://ubuntuforums.org/showthread.php?t=160226](http://ubuntuforums.org/showthread.php?t=160226) (regarding tb1.5) but I had no luck yet.

---

### Post by Tanker Bob on 2007-04-22
I'd like to add my voice to the 64-bit Thunderbird 2.0 request.  This was the current release version of Thunderbird a month before Feisty was released, so technically it should be supported in the repositories.

---

### Post by ronocdh on 2007-04-22
> **Tanker Bob said:**
> I'd like to add my voice to the 64-bit Thunderbird 2.0 request.  This was the current release version of Thunderbird a month before Feisty was released, so technically it should be supported in the repositories.
[This page]("http://www.mozilla.com/en-US/thunderbird/all.html") purports to offer i686 (i.e. friendly to 64-bit) packages. Is that the version OP used and failed to install?

---

### Post by Tanker Bob on 2007-04-22
I believe that he was compiling from the source files.  My put would be that 64-bit friendly isn't 64-bit software.  Full 64-bit software would have better performance and stability.

---

### Post by ronocdh on 2007-04-22
> **Tanker Bob said:**
> I believe that he was compiling from the source files.  My put would be that 64-bit friendly isn't 64-bit software.  Full 64-bit software would have better performance and stability.
I may be wrong here, but I am very interesting in being corrected if that is the case.

It was my understanding that the abbreviation "i686" referred to packages which were natively geared toward 64-bit architectures, but in a way that could still accommodate old i386 systems. Isn't this the logic behind Apple's "Universal" packages, which contain separate instruction sets for PowerPC and Intel processors?

Again, please tell me whether I'm wrong. I'm currently reinstalling Feisty, but I will certainly try this TB2 package tonight and see.

---

### Post by StratosL on 2007-04-22
I'm not sure about that, I would think that i386 packages are supposed to run on all intel machines, i586 was relevant for Pentium I and i686 is for Pentium IV and later. While i686 packages run on single core 32bit systems,  64bit packages would have to have the "amd64" signature.

---

### Post by Case_f on 2007-04-22
ronocdh: OK. You're wrong :) (and StratosL is right)

BTW I'm running the default Mozilla i686 build (available at [http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/) ) without any problems in 64bit Feisty, no there's no need for i686 package, really - all you have to do is download it, unpack and off you go (if you have ia32-libs and ia32-libs-gtk installed, that is). 
Although native Feisty AMD64 build would be nice, sure. I've tried to do a 64bit compile, but it failed for some reason and I didn't have time to find out why did it fail and how to solve it.

---

### Post by Kilz on 2007-04-22
> **StratosL said:**
> I'm not sure about that, I would think that i386 packages are supposed to run on all intel machines, i586 was relevant for Pentium I and i686 is for Pentium IV and later. While i686 packages run on single core 32bit systems,  64bit packages would have to have the "amd64" signature.

the AMD64bit processor and the newer EMT64 intel chips can run it all on Ubuntu.

> **Tanker Bob said:**
> I believe that he was compiling from the source files.  My put would be that 64-bit friendly isn't 64-bit software.  Full 64-bit software would have better performance and stability.

The problem with this is that for there to be performance gains the code has to be written to take advantage of the 64bit processor. Compiling the code used to make 32bit applications on a 64bit machine will simply make it install easier. It may give it a slight , and I mean slight (not humanly noticeable) boost.

---

### Post by StratosL on 2007-04-23
I downloaded the i686 binary from mozilla and it runs fine. It also does not mess with the files of Feisty Thunderbird installation, as it extracts all its files into one single directory and you run it from there (just need to edit the profile, by "./thunderbird  -profilemanager", in order to make it use the directory where you already have all your email).

This way, you can use the official TB2.0 and if/when Feisty gets TB2.0 64bit  (through back-ports most likely), then you can install it. One should really not expect any noticeable difference in 64bit performance, as TB is not exactly a number-crunching application.

---

### Post by RawMustard on 2007-04-23
Really, I did the same and it won't run.  Say's it can't find thunderbird-bin, but it's there right next to thunderbird.  You must have the ia32-libs installed?

---

### Post by Case_f on 2007-04-23
Yes.

---

### Post by StratosL on 2007-04-23
Yes, I had installed it while installing firefox32 w/ all the plugins, following the link in Kilz's signature.

---

