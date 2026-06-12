---
title: "Secure Digital (SD) Media 4 GB"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by jkzubu on 2008-06-22
Hi All -

I have noticed that my 4 GB SD card (Lexar 4 GB 133x) is not mounted/recognized by Ubuntu from my USB 2.0 built-in card reader.  I use this card in my camera (Nikon D80) and my OS is Gutsy 64 on an AMDx2.  I can use either of my 1 GB or 2 GB SD cards in my card reader (same camera) and both mount/become readable with no problems.  

FYI I have the same card reader on my XP machine and it performs flawlessly.

For what reason might the 4 GB SD card not mount/recognize in Ubuntu? And, how can this problem be solved?


Thanks

J Kaz

---

### Post by roderick on 2008-06-22
You need a newer card reader with support for >= 4GB SDHC (which yours does not appear to have.

Try purchasing a SDHC with a USB card reader, that's what I had to do.

---

### Post by jkzubu on 2008-06-22
Hi Roderick -

I did think of that, but what would explain the exact same card reader to run the same 4 GB SD card on my XP machine?

Thanks

J Kaz

---

### Post by roderick on 2008-06-23
Hmm.. strange. 

Can you look at your dmesg and syslog and see what shows up there? Should be some hint.

---

