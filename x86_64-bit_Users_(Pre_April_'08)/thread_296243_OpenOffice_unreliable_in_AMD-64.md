---
title: "OpenOffice unreliable in AMD-64?"
date: 2006-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by eurgain on 2006-11-09
Hi

I am experiencing crashes with OOo 2.0.4 on Edgy.  It normally happens when I select a drawing object in a text document.  The whole of OOo just vanishes.

Since OOo is the key application for my use, this is such a major problem that I am going to have to do something like:

Install OOo 32-bit; re-install dapper (with ultra-reliable 32-bit OOo already); install another distro altogether.

Is this something anyone else has experienced?

My system is AMD64 3000+ with 1GByte RAM and NVidia binary drivers.

Regards
A

---

### Post by fabertawe on 2006-11-09
Can you give some more detail as to the steps taken to invoke this? I just opened a new document and drew some shapes and tried selecting and it was fine. I don't use it very often but I have the same specs as you so I'll try it if you can give me some steps to follow.

Paul

---

### Post by eurgain on 2006-11-09
I have replied to this using "private message".

A

---

### Post by Kilz on 2006-11-09
> **eurgain said:**
> I have replied to this using "private message".

A

IMHO its better to discuss problems on the forum. You will get more people involved, its less likley that you will get duplicate information, and it may help someone else with the problem fix it.

---

### Post by eurgain on 2006-11-09
> **Kilz said:**
> IMHO its better to discuss problems on the forum. You will get more people involved, its less likley that you will get duplicate information, and it may help someone else with the problem fix it.

Yes, in general I agree.  However, in this case, I wanted to exchange some files and e-mail addresses with an individual rather than have them on the open forum. 

Anyway, we have made some progress.

My correspondent could not repeat the fault.  I have done some further investigation, and I have discovered that the fault only occurs when OOo is using a display that runs KDE.  This is irrespective of whether the display is local or remote.

If the display is in a Gnome session on the local machine running OOo does not crash; it does in a KDE session.  Executing from a remote session (from a 32-bit SUSE box using ssh -Y) there is no crash using Gnome or WindowMaker (on the SUSE machine) but a crash if the SUSE machine is running KDE.

So, it seems that 64-bit OOo does not like using a KDE display; I find this odd.

When displaying on KDE, OOo dumps lots of messages to stderr as follows:

(process:21932): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

I will test whether it is a problem with Ubuntu's 64-bit build of OOo or is more widespread when I have downloaded SUSE10.2Bets2.

Regards
A

---

### Post by xstaticxgpx on 2006-11-09
gnome imo is more reliable and less of a resource hog than kde anyway... why dont you just completely switch to gnome? I really liked the way kde was set up, but i liked gnomes reliability and resourcefulness. So I made gnome look like kde (placement wise) and installed some kde apps and all of the kde libs, base and core - i just didn't install kdm or kubuntu-desktop

---

### Post by kuja on 2006-11-09
Sounds like this bug should be reported if you haven't already.

---

