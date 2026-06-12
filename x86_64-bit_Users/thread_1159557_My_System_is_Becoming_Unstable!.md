---
title: "My System is Becoming Unstable!"
date: 2009-05-14
forum: x86 64-bit Users
---

### Post by Thelasko on 2009-05-14
I'm running Hardy Heron 8.04, because I like a stable system.  Over the past two days I have had Gnome crash twice!  This has never happened on this install of Ubuntu.

Yesterday's crash occurred while I was uploading a file to a website from my desktop.  Firefox crashed right after I selected the file to upload.  Upon forcing Firefox to quit, Gnome froze.

Today, I've noticed I've been having audio issues.  As a matter of fact, this was happening yesterday too.  Pidgin was no longer making sounds when I IM people, and Rhythmbox refused to play.  However, Flash audio worked perfectly in Firefox.

I've restarted Ubunutu and things appear to be working fine at the moment, but I feel I should post this.  Perhaps someone has some insight about what is going on.

---

### Post by Yellow Pasque on 2009-05-14
If those things happen again, investigate them (i.e. start programs from the terminal to figure out exactly why they don't have sound).

On the hardware side, make sure nothing's overheating and run memtest.

---

### Post by Thelasko on 2009-05-15
I ran rhythembox from the terminal when it happened. It said:```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/x-rar decoder|decoder-application/x-rar
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
```

Apparently this is a known bug (I already filed a bug report).

Right now I'm combating [some connection issues.]("https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/376981")

---

### Post by Thelasko on 2009-05-15
The audio issue appears to be a conflict with Firefox.  I do have the 64-bit alpha version of Flash installed, perhaps that is the culprit.

---

### Post by Thelasko on 2009-05-18
So, a random window pops up on my machine today, and I couldn't close it.  Turns out GNOME had frozen again!  I restarted my machine and now Thunderbird is receiving emails again.

THIS IS CRAZY!

---

### Post by RoboNuggie on 2009-05-18
It may not be this, but could you have a stick or two of bad ram?

---

### Post by Yellow Pasque on 2009-05-18
> So, a random window pops up on my machine today, and I couldn't close it.
What did the window look like?

> THIS IS CRAZY!
Embrace the madness.

---

### Post by Thelasko on 2009-05-30
> **Temüjin said:**
> What did the window look like?


Embrace the madness.

It was just a titlebar and nothing else.

---

### Post by Thelasko on 2009-05-30
My connection issues have been solved (they were due to moblock running in the background).

It appears that my system instability issues may be due to pulseaudio.  Funny, since I never experienced any of the pulseaudio issues everyone was complaining about until now.

---

