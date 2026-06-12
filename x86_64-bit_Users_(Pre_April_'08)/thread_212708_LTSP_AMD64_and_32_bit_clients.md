---
title: "LTSP AMD64 and 32 bit clients"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by cesera on 2006-07-10
I have a kubuntu-AMD64 machine up and running and now would like to run LTSP with 32 bit thin clients, does anyone know if that is going to work out of the box, or do I have to do anything special to bridge the 64/32 bit divide?

---

### Post by Kilz on 2006-07-10
> **cesera said:**
> I have a kubuntu-AMD64 machine up and running and now would like to run LTSP with 32 bit thin clients, does anyone know if that is going to work out of the box, or do I have to do anything special to bridge the 64/32 bit divide?
You may also want to post this question in the [Server Talk]("http://www.ubuntuforums.org/forumdisplay.php?f=45") section if you get no other answers here.

---

### Post by tonym on 2006-07-13
This may not be the most helpful response ever as I have never tried this but did once look into it.

One of the scripts in LTSP that you use to create the client image calls debootstrap.  If you edit the script to add the --arch parameter I think that might work.

Regards

Tony.

---

### Post by cesera on 2006-07-14
Thank you very much. I did actually post this question to the Server Talk forum as suggested, and I got some very helpful replies. You can check it out here: [http://www.ubuntuforums.org/showthread.php?t=213043](http://www.ubuntuforums.org/showthread.php?t=213043)

---

