---
title: "[SOLVED] D2LOD Error"
date: 2008-01-11
forum: Wine
---

### Post by Syndacate on 2008-01-11
I'm trying to get D2 LOD installed with WINE.

I installed it fine - but it didn't ask me for any discs (cinematics 'n such) - even though I hit "full version."

It won't play because it says it can't find the CD (I'm using images).

I can't use the D2Loader because it's not patched.

It wont' update (the patch from 1.07 to 1.11b) because it says "cannot find BNClient.dll") - that's a manual file download - not b.net.

Anybody give me any help here?

And PLEASE don't post a write-up on "how to install D2 LOD on WINE" - I have like 50 of them up in firefox and none even remotely mention problems that I'm having.

I'm assuming the D2 loader will work once the patch goes through - but it can't find the damn DLL file.

---

### Post by Syndacate on 2008-01-11
*bump

Anybody??

---

### Post by hikaricore on 2008-01-11
It's been 3 hours friend.  ^_^  Ye of little patience.
Please wait 24-48 hours for a response before bumping your post, as this removed it from the Unanswered Posts section of the forums.

Best of luck.

---

### Post by Syndacate on 2008-01-12
Well I wasn't sure how it was listed - in terms of order - since I originally posted in the gaming section but an admin moved it.

So I wasn't sure where it put it in this forum (top, bottom, in correspondence with the date??) - so I bumped it - normally I wouldn't so soon.

---

### Post by Syndacate on 2008-01-13
Okay, So I finally got D2LOD installed properly.

Method:
After I installed it, I copied all the files out of the program folder on my laptop (running XP and Diablo II LOD 1.11b) and pasted them into **/.wine/drive_c/Program Files/Diablo II/** and it ALMOST ran fine.

I don't have the CD's - don't worry - before you all go up in arms about the copyright crap that I know you care so much about - **THIS IS A 100% LEGAL COPY**.  I used a CD-Key Grabber to grab the CD-Key (that came when I **BOUGHT** the game) off my laptop and used that for the installation here.  Though I haven't seen the CDs in ages, every time I go to do a format or whatever, I just yank the keys and write 'em down.

So now that that's out of the way as I don't have CD's, I had to install everything through images - which is fine - whatever.

I type **wine D2Loader-1.11b.exe** and I get the error message:

```

Couldn't load Diablo II MPQ files.  Please insert your Diablo II CD.

```

BUT

When I right click D2 Loader - open with >> and type "wine" it loads fine, works 100%.

Any suggestions?  Tomorrow I'm going to try burning the image to a CD and putting it in the drive and see if that works.  Though that kind of defeats the purpose of the loader.

And PLEASE don't give me any crap about "it's because you're using a Loader" - it's not because I'm using a loader - because there's 1000 people using the same one on 100% legit versions like mine that simply don't want to put a CD in every time (like me).

I also have no sound - I'm assuming maybe that the -ns option is enabled by default?  I have no problem with the right clicking thing to turn it on - but I'd like to run it in window mode which requires the -w option.

Almost there ;).

Any help is appreciated.

---

### Post by Syndacate on 2008-01-13
Update:

By checking "Emulate Virtual Desktop" in the "graphics" tab of WINE setup, you can get "window mode" by default - so you don't need the -w option.

I'm still curious as to why it won't read the MPQ files if you do it through the command line, but more importantly, I still have no sound.

I can't check the "audio" tab in the WINE config because it glitches and nothing happens (as I hear this is a common problem).

Anybody got any ideas??

---

### Post by Syndacate on 2008-01-14
Man, shoulda just left my post in the beginners forum.

Bump*

Anybody?

---

### Post by EGJason on 2008-01-14
The stickies at the top tell you how to configure your CDROM properly, that's the only issue I had with D2 was it recognizing the correct CD mount.

You can also rip the ISO's and mount them, I do this for all of my games that don't have DRM or some sort.

---

### Post by Syndacate on 2008-01-14
> **EGJason said:**
> The stickies at the top tell you how to configure your CDROM properly, that's the only issue I had with D2 was it recognizing the correct CD mount.

You can also rip the ISO's and mount them, I do this for all of my games that don't have DRM or some sort.

Uhh yeah, that's the way I have it and it works fine - not working through the command line - but it works fine by right clicking on the loader...

Though I wouldn't care about that - but there's no sound :(

EDIT:
I'm using mounted .iso's (with gmount-iso) and it's assigned to a letter and all - that's how I installed it - and I can click on it from there - and it'll open the thing and say that no CD is in - but if I go to diablo's run folder and run the loader it works fine.

This isn't the first time I've had problems with D2 not recognizing the CD - I recall having this problem a few times in the past - even though the original OEM CD was in the drive.

I really don't care how I start it - but the no sound part is killing me :(

---

### Post by Syndacate on 2008-01-16
Fixed - use OSS driver instead of ALSA.

---

### Post by Timelle on 2009-03-09
> **Syndacate said:**
> Update:

By checking "Emulate Virtual Desktop" in the "graphics" tab of WINE setup, you can get "window mode" by default - so you don't need the -w option.

I'm still curious as to why it won't read the MPQ files if you do it through the command line, but more importantly, I still have no sound.

I can't check the "audio" tab in the WINE config because it glitches and nothing happens (as I hear this is a common problem).

Anybody got any ideas??

I have same problems with sound but if you check WINE audio settings and wrote something like; 44100 , 8 bit, driver emulation - you can get what you want.

P.S. Sorry for my awful English:D

---

### Post by Syndacate on 2009-03-16
> **Timelle said:**
> I have same problems with sound but if you check WINE audio settings and wrote something like; 44100 , 8 bit, driver emulation - you can get what you want.

P.S. Sorry for my awful English:D

Hey,

Yeah, I switched to the OSS driver instead of ALSA - it worked after that.

Though I basically kind of gave up on WINE for everything but keygens 'n the like - I'd love to put faith into WINE, but regardless of how advanced and kick-*** WINE gets, it is now my belief that people should try to find replacement programs in Linux, not try to run all the "good ones" from Windows on Linux.  I keep a Win install handy on all my non-server computers for compatibility sake (ie, my blackberry manager when it isn't in mass storage mode, games requiring DX 9+, etc.).

---

