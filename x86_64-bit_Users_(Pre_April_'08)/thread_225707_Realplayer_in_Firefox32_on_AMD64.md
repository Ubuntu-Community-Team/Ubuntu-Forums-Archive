---
title: "Realplayer in Firefox32 on AMD64"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by bbfuller on 2006-07-30
I've followed the excellent Howto by Kilz to get 32 bit firefox with plugins working on my AMD64 system.

MSI K8N Neo4 motherboard, NX6600LE PCI Express nvidia graphics.

I've also got a native 32bit system to compare it against.

On the 32 bit system RealPlayer video and sound works perfectly.

I use it to access video on [http://news.bbc.co.uk](http://news.bbc.co.uk)

On the 64 bit system I get perfect sound but the video plays about 2 frames, freezes for 10 or more frames and then plays 2 frames again, repeating this sort of sequence repeatedly with just a few bursts where video works for a couple of seconds.

The questions I'm asking myself are:

Is this a general thing for 32 bit realplayer in a 64 bit environment?

Is it just a 64 bit Ubuntu thing?

Or is it something specific to my particular hardware setup.

Obviously, with 32 bit machines it's usually easy to find a spare to compare against, much more difficult with 64 bit, so I'd appreciate hearing other peoples experiences.

Thanks in anticipation.

---

### Post by jamesford on 2006-07-30
i read somewhere that video playback for certain formats including real is broken in forefox 1.5.0.5, wait for 1.5.0.6, it should be out shortly

---

### Post by McMarley on 2006-07-30
I havent been able to get much working
on firfox ( 64bit ) I believe that It
wil all work I a few months. Your problem
is just a little BUG in the system. Dapper
is just so new that it still has problems...

Happy coffee to all

---

### Post by Kilz on 2006-07-30
I cant get it working in 1.5.0.5 , and I wrote the howto, I put 1.5.0.4 back in and video wont play at all.

---

### Post by bbfuller on 2006-07-30
Now that's a surprise to hear you all saying that.

My realplayer is behaving exactly the same in firefox 1.5.0.5 as it did in 1.5.0.4, and that is how I described in the first post of this thread.

---

### Post by jamesford on 2006-08-03
there, new version out, not sure if its in the repos yet. the video playback has supposedly been fixed

---

### Post by bbfuller on 2006-08-04
I've done the upgrade to 1.5.0.6 and I can't say that I see any real difference. Flash works as well as it ever does - it's just realplayer that stutters.

Incidentally, since the general updates yesterday, the text in the firefox32 (not the 64 bit version) "Save" dialogues has been replaced by series of squares. That's when asking to save a copy of a page or when saving file download.

I wonder if anyone else is seeing this.

---

### Post by Kilz on 2006-08-04
> **bbfuller said:**
> I've done the upgrade to 1.5.0.6 and I can't say that I see any real difference. Flash works as well as it ever does - it's just realplayer that stutters.

Incidentally, since the general updates yesterday, the text in the firefox32 (not the 64 bit version) "Save" dialogues has been replaced by series of squares. That's when asking to save a copy of a page or when saving file download.

I wonder if anyone else is seeing this.

There is a problem with one of the packages in the upgrade. [There is a post on the subject with a fix.]("http://www.ubuntuforums.org/showthread.php?t=228179")

---

### Post by bbfuller on 2006-08-04
Thanks Kilz, I'd seen the thread but was hoping against hope that it would be fixed before long with an update rather than having to apply a patch.

I can exist hopping between 64bit and 32bit until then.

---

