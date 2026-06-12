---
title: "Best x86 kernel?"
date: 2006-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by dlanor78 on 2006-07-29
I have an amd 64 3200+ processor, but want to stick to 32 bit for now just cause it's easier to get everything working.  What's the best option for an optimized kernel on this processor (686, k7, something else)?

Thanks in advance for any help.

---

### Post by Kilz on 2006-07-29
i386 generic. If you are going to be just using 32bit what does it matter? All those kernels are not made for your processor, so it will not matter.

---

### Post by jamesford on 2006-07-29
k7-smp i believe, its what i used anyway

---

### Post by dlanor78 on 2006-07-29
Thanks for the replies so far guys.  The reason I'm looking for the best x86 kernel is because I do a lot of video encoding and want to get the best perfomance I can withough going 64 bit (at least until it's better supported).

---

### Post by jamesford on 2006-07-29
oops smp is for if u have a dual core one, if not i guess its plain k7

---

### Post by Kilz on 2006-07-29
> **dlanor78 said:**
> Thanks for the replies so far guys.  The reason I'm looking for the best x86 kernel is because I do a lot of video encoding and want to get the best perfomance I can withough going 64 bit (at least until it's better supported).

Better supported? Im really sick of people running 32bit saying 64bit isnt supported. Encoding is one area where there are gains.

---

### Post by dlanor78 on 2006-07-29
Maybe better supported wasn't the best choice of words.  All I meant is that wine is a pain in the butt to get working with 64-bit, and there are no win64codecs.  Flash for linux is pitiful with being stuck at version 7, but it's better than nothing (and gnash isn't ready yet, so I don't run that).

None of those things are major set backs, but they're just annoying enough for me to not run it for now.

---

### Post by Kilz on 2006-07-29
> **dlanor78 said:**
> Maybe better supported wasn't the best choice of words.  All I meant is that wine is a pain in the butt to get working with 64-bit, and there are no win64codecs.  Flash for linux is pitiful with being stuck at version 7, but it's better than nothing (and gnash isn't ready yet, so I don't run that).

None of those things are major set backs, but they're just annoying enough for me to not run it for now.

I have automated setup scripts for firefox with macromedia flash 7 and wine for the amd64 version. They should take all of 20 minutes to download, run, and setup both of them. They are in my signature.
There are no win64codecs but the sticky has a link to setting up the win32codecs on the amd64 version. The only time you will have to use them is if you are viewing or messing with wmv or wma.

---

### Post by dlanor78 on 2006-07-29
Thanks for the info Kilz, I think I may give 64-bit another try if I can get HandBrake ([http://handbrake.m0k.org/](http://handbrake.m0k.org/)) to work with it.  I know there are other encoding programs out there, but that one is my favorite so far...very easy to use and I have yet to mess up a dvd>whatever format yet with it.

I also need to find out if I can get ntfs-3g installed in 64-bit mode....maybe if I can get the deb files I can use the --force-architecture option.

---

### Post by Kilz on 2006-07-30
> **dlanor78 said:**
> Thanks for the info Kilz, I think I may give 64-bit another try if I can get HandBrake ([http://handbrake.m0k.org/](http://handbrake.m0k.org/)) to work with it.  I know there are other encoding programs out there, but that one is my favorite so far...very easy to use and I have yet to mess up a dvd>whatever format yet with it.

You may have better luck compiling, I tried on both versions, i386 (my small pentium3 file server runs ubuntu) and amd64 and couldnt get it to work.

---

### Post by dlanor78 on 2006-08-06
Thanks for your help Kilz.  I'm now running the 64-bit kernel with no major problems so far (wine even seems to run better now!!!).  For handbrake, I have a version compiled in 32-bit ubuntu, and it still runs fine in 64-bit.  I did try to compile it for 64, but it failed with "skipped HBTest for lack of libhb.a".  This happens in 32-bit sometimes too...seems very hit or miss.  That's why I kept a copy of handbrake when I finally got it to compile.

NTFS-3G worked fine using the --force-architecture option on the deb files I found.  So that's a bonus :D

---

