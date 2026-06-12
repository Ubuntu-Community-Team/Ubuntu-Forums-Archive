---
title: "S3 Graphics Unichrome Pro IGP"
date: 2005-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by arjaybe on 2005-11-05
Has anyone found a way to use this integrated graphics chipset?  I just got an Athlon 64 on an ASRock motherboard which has integrated graphics.  It's called Integrated Unichrome Pro 3D Graphics in VIA K8M800 and a web search indicates that it's the S3 mentioned in the Subject.

Ubuntu 64 (and many others) defaults to VESA, which gives me an acceptable picture, but I'd like to make proper use of my graphics.

---

### Post by poptones on 2005-11-05
You know, I had an S3 board and I got rid of it thinking this nvidia would be so much better. At the time the s3 linux driver was "unofficial" because the fellow who wrote it had obtained the information he used to write it under an NDA and so it was technically "illegal."

Anyway, you may be happily surprised to learn S3 (and via) have become very open source friendly....

[here ya go....](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109) and not an object module in the package (ie it's *really* open source).

I'm not running a 64 bit system or breezy so I can't help you with the compiling, but since you wanted that 64 bit system there's no time like the present to learn to use it :)

Anyone wanna buy a dualhead matx nforce2 motherboard?

---

### Post by poptones on 2005-11-05
Oh yeah... the 3D (not exactly "free") stuff:

[http://sourceforge.net/docman/display_doc.php?docid=26963&group_id=102048](http://sourceforge.net/docman/display_doc.php?docid=26963&group_id=102048)

---

### Post by jvictor on 2005-11-05
[http://ubuntuforums.org/showthread.php?t=76037](http://ubuntuforums.org/showthread.php?t=76037)

this is a 64 bit driver built for haory and works for me on breezy seamlessly ! wish u all luck

---

### Post by arjaybe on 2005-11-05
Thank you.  I followed your instructions in that thread and am now using the Via driver.  Much nicer than VESA.

---

### Post by poptones on 2005-11-05
Does the 3d work pretty well?

I am **seriously** considering replacing this nvidia motherboard with a via s3.

---

### Post by arjaybe on 2005-11-05
I don't know.  What would be aq good test of 3D?

---

### Post by poptones on 2005-11-05
I don't care about benchmarks. For example, do 3d screensavers seem fluid?

I don't even use 3d that much, I just want a system that is more "open" than the one I have now. My s3 system never gave me any trouble and it was easy to install everything even if I did have to install my own xf86 drivers.

---

### Post by arjaybe on 2005-11-06
I previewed a few 3D screensavers and they seem pretty smooth.  Maybe I should try out Project Looking Glass.-)

---

### Post by jvictor on 2005-11-06
From what ive seen VIA is more of pain than NVIDIA... so dont be hasty to jump onto VIA. We're with via bcoz of fate ;) ..

I put in my old systems NVIDIA RIVA TNT2 card, just coz i dont like the card eating 64 MB of my RAM, when i dont play games or do any 3d stuff.

There are the sources of VIA available, but when i built it , the module refused to load..

---

### Post by arjaybe on 2005-11-06
You could be writing my script.  I'm happy to get my integrated graphics off VESA, but there's an AGP slot on the board begging to be filled.

---

### Post by docshawnc on 2007-02-23
Have a look here: [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109)

you may find something that will work for you

---

