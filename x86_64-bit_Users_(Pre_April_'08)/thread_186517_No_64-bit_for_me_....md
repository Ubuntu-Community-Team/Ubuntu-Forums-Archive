---
title: "No 64-bit for me ..."
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yoeri on 2006-06-02
Downloaded the 64-bit edition yesterday. When booting from the live cd there was a Kernel-Panic :( . I can't get it up and running with the 64-bit edition.

SPECS:
ASUS A4K Laptop AMD 3200+ Athlon64 Mobile. 1GB RAM 80GB HD ATI Radeon Mobility 9700 128MB




I downloaded the i386 afterwards and everything works like a charm. I was really surprised with the improved hardware support. My ATI Mobility works great out of the box and so does my WIFI-card. Keep up the good work !!

---

### Post by Patsoe on 2006-06-02
How unfortunate! 

Did you check if there were errors in the 64bit iso after downloading? (you can use the MD5SUMS file on the download pages for that)

If the iso was good, then please file a bug report.

---

### Post by henriquemaia on 2006-06-02
[quote=Yoeri]Downloaded the 64-bit edition yesterday. When booting from the live cd there was a Kernel-Panic :( . I can't get it up and running with the 64-bit edition.

SPECS:
ASUS A4K Laptop AMD 3200+ Athlon64 Mobile. 1GB RAM 80GB HD ATI Radeon Mobility 9700 128MB




I downloaded the i386 afterwards and everything works like a charm. I was really surprised with the improved hardware support. My ATI Mobility works great out of the box and so does my WIFI-card. Keep up the good work !![/quote]

Check if the .iso is correct (checksum it with md5sum, like suggested by Patsoe). If it is alright, record it using the lowest speed possible of your cd recorder. I have had that experience before. My installation was hanging somewhere near the end and the problem was with the burning of the iso. Try that.

---

### Post by Yoeri on 2006-06-02
I had it before when I tried Dapper Flight 3. I always download the iso and burn it to a cd-rw at 10x. I'll check tonight to post the exact Kernel Panic message.

I think i'll stick with the !386 version ... it works great.

---

### Post by henriquemaia on 2006-06-02
[quote=Yoeri]I had it before when I tried Dapper Flight 3. I always download the iso and burn it to a cd-rw at 10x. I'll check tonight to post the exact Kernel Panic message.

I think i'll stick with the !386 version ... it works great.[/quote]

I have to record at 4x. At 10x the cd does not work. But maybe this is due to some issue on my recorder, don't know. 

Apart from this, if i386 is working, that's also nice.

---

### Post by miggl on 2006-06-02
[QUOTE=henriquemaia]I have to record at 4x. At 10x the cd does not work. But maybe this is due to some issue on my recorder, don't know. 

Apart from this, if i386 is working, that's also nice.[/QUOTE]
This can also be due to older/cheap media you are trying to burn on. I have found that the limitation is imposed by the speed advertised on the blanks, rather than the CD-RW drive itself (when corrupting ISO burns). Perhaps your media is only rated at 4x or 6x?
In my case I have a whole stack of 16x blanks, eventhough my burner suppoerts 40x. I have to burn at 16x, otherwise the burn will fail or corrupt the files it is burning.

---

### Post by henriquemaia on 2006-06-03
[quote=miggl]This can also be due to older/cheap media you are trying to burn on. I have found that the limitation is imposed by the speed advertised on the blanks, rather than the CD-RW drive itself (when corrupting ISO burns). Perhaps your media is only rated at 4x or 6x?
In my case I have a whole stack of 16x blanks, eventhough my burner suppoerts 40x. I have to burn at 16x, otherwise the burn will fail or corrupt the files it is burning.[/quote]

Thanks for the tips. I'm using a faily good (in my opinion) media from tdk, a 12x RW. I think the problem can be the recorder, because it is a bit old. Its maximum speed is 20x. Like yours, if I burn full speed, the files get corrupted.

---

### Post by zluka on 2006-06-03
i had a more interesting problem. i burned the iso on my plextor cd-rw, and (as the disk is it's own and else) i booted from it. nothing. the startup sound tried to play for half a second, and i'm looking at the default background image, and i've got the cursor, that's all ;)

i downloaded and burned the 32-bit version (anyhow i would need it), and booted again from plextor. i got the desktop, all right, but everything is too slow, and too many programs do not work.. just "starting ..." and nothing. as i had flight 6 installed, i knew it'd work, so just tried my chance with the pioneer dvd-rw, works like a charm, and while i'm surfing and checking my files, it installed itself in 20 min (the 64-bit version).

so, not only md5sum or writing errors, but reading can also be a pain in the a..

just wanted to share. winxp 64 never worked for me, suse 10 also.. i was waiting for a 64-bit os for a long time, and ubuntu did not dissapoint me, as always ;)

i got no problems with video and audio (had some in breezy 64), and swiftfox just installed the flash player ;)

happy as a kid, and i suggest Yoeri and other suspicious 64-bit users to try the dapper 64. quite fast and effective, and had no problems (yet :mrgreen: )

ps: i mean no offence about trademarks, it was my situation, my plextor is old, and i played rough with him, so maybe i should have guessed..

---

### Post by henriquemaia on 2006-06-03
[quote=zluka]i had a more interesting problem. i burned the iso on my plextor cd-rw, and (as the disk is it's own and else) i booted from it. nothing. the startup sound tried to play for half a second, and i'm looking at the default background image, and i've got the cursor, that's all ;)

i downloaded and burned the 32-bit version (anyhow i would need it), and booted again from plextor. i got the desktop, all right, but everything is too slow, and too many programs do not work.. just "starting ..." and nothing. as i had flight 6 installed, i knew it'd work, so just tried my chance with the pioneer dvd-rw, works like a charm, and while i'm surfing and checking my files, it installed itself in 20 min (the 64-bit version).

so, not only md5sum or writing errors, but reading can also be a pain in the a..

just wanted to share. winxp 64 never worked for me, suse 10 also.. i was waiting for a 64-bit os for a long time, and ubuntu did not dissapoint me, as always ;)

i got no problems with video and audio (had some in breezy 64), and swiftfox just installed the flash player ;)

happy as a kid, and i suggest Yoeri and other suspicious 64-bit users to try the dapper 64. quite fast and effective, and had no problems (yet :mrgreen: )

ps: i mean no offence about trademarks, it was my situation, my plextor is old, and i played rough with him, so maybe i should have guessed..[/quote]

I second your suggestion. I never had such a stable OS as this one.

---

