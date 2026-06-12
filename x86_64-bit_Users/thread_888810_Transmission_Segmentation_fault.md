---
title: "Transmission: Segmentation fault"
date: 2008-08-13
forum: x86 64-bit Users
---

### Post by norwyn on 2008-08-13
Hi!
When I tried to open Transmission today I got a 'Segmentation fault' instead. What does it mean, and how do I fix it?
I use Hardy 64 bit.
Thank you in advance!

kern.log: 

```
Aug 13 07:44:54 robin-laptop kernel: [30224.169134] transmission[31629]: segfault at c13000 rip 44258b rsp 7ffff2cf4ca8 error 4
Aug 13 18:19:46 robin-laptop kernel: [44464.150245] npviewer.bin[19690]: segfault at ff439ffc rip ffffe402 rsp ff43a000 error 6
```

---

### Post by satellite360 on 2008-08-14
Transmission starts fine for me but if I leave it running for any length of time it closes itself down.  Started it from the terminal - again starts fine - and received the same 'Segmentation fault' message when Transmission closes.

Any ideas?

Ubuntu 8.04 32-bit

---

### Post by norwyn on 2008-08-19
No, sorry. Havn't figured this out yet. Not even found any good information about segmentation fault.
Have you had any luck?

---

### Post by satellite360 on 2008-08-20
> **norwyn said:**
> No, sorry. Havn't figured this out yet. Not even found any good information about segmentation fault.
Have you had any luck?
My problem is different to yours in that Tranmission would start up ok but stop working after a while with the 'segmentation fault' error, also I'm running 32-bit Ubuntu. I ended up turning off my screensaver and since then Transmission has worked fine.

---

### Post by norwyn on 2008-08-20
Yeah, I understand that it is a different problem. But now as I think of it, I actually activated my screensaver just around the days when Transmission stopped working. 
Will try that out as soon as I get home, thank you for mentioning it!

---

### Post by NIT006.5 on 2008-08-26
It has something to do with the transmission files stored in your home directory i.e. ~/.transmission

If you move the .transmission folder to another location and restart transmission it will probably run fine BUT without the downloads you had in progress. Haven't figured it out completely yet, so not sure how you could re-add incomplete downloads without losing what you had downloaded already... or maybe you might have to just start again :(

---

### Post by Willy13 on 2008-11-16
After the same happening to me, I renamed my .transmission folder and started Transmission to re-instate it's folder.

I then shut Transmission down and copied the folders back one at a time, restarting the program after each one and found the fault in the Torrents folder. It seems that the segmentation fault is in one of the downloading torrents (in my case, at least).

I couldn't find a way to get Transmission to recognize the torrents already part downloaded.

Hope this helps!

Update - After starting Transmission, click Edit - Preferences  and set your download preferences, in particular your download folder.

Then, 
(1) In the Torrents folder in your renamed .transmission folder, double-click each of the files and they will jump back into Transmission, and it will recognize the part torrents stored there. 

(2) The torrent causing the segmentation fault will cause Transmission to crash, so when you know which is causing the problem, delete it from your ~/.transmission/Torrents folder and restart Transmission. 

(3) Continue double-clicking the remaining files in the other torrents folder (avoiding the one causing the problem) and all should be well!

---

