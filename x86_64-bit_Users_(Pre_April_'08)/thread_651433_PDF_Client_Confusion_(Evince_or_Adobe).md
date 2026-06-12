---
title: "PDF Client Confusion (Evince or Adobe?)"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by vgrisham on 2007-12-27
Hi,

I'm really confused about which PDF client works best in 64-bit gutsy. I have 32 bit firefox installed as well as 64 bit. 

When I open a PDF from the internet, Evince opens the document but won't print it. I have to right click, save it, open it and then print it. Conversely, I understand that Adobe Reader 8 doesn't work well in the 64 bit environment.

What PDF reader should I be using? 

Thanks,
Vaughn

---

### Post by bford16 on 2007-12-28
> **vgrisham said:**
> Hi,

I'm really confused about which PDF client works best in 64-bit gutsy. I have 32 bit firefox installed as well as 64 bit. 

When I open a PDF from the internet, Evince opens the document but won't print it. I have to right click, save it, open it and then print it. Conversely, I understand that Adobe Reader 8 doesn't work well in the 64 bit environment.

What PDF reader should I be using? 

Thanks,
Vaughn
Adobe Reader works fine in the 64-bit environment.  It is available from the Medibuntu repositories.  However, there is no Mozilla plugin for it at this time.

---

### Post by shane2peru on 2008-02-08
I prefer it not to open in the browser, that is always an annoyance to me. I have this wonderful little extension for Firefox, it is called:  PDF Download, it  is great, you can view the pdf as html, or download it or open it.  the best.

Shane

---

### Post by sawjew on 2008-02-11
You can actually use acrobat reader with the firefox plugin on amd64 using nspluginwrapper, the same wrapper used for flash.

if you go [here]("http://plugindoc.mozdev.org/linux-amd64.html") you will find out how to do it.
You will need to remove the adobe reader from the repositories and go to adobe's web site and get their 32 bit version.

I have it working perfectly on my 64 bit Gutsy with the latest adobe reader.

you can go [here ]("http://ubuntuforums.org/showthread.php?t=679824&highlight=acroread+nspluginwrapper")for some more information.

---

