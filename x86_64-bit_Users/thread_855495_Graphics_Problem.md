---
title: "Graphics Problem"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by Hyuukai on 2008-07-10
Ok i am currently running Ubuntu 64bit 8.04 on my Dell Vostro 1500 everything ran basically straight out of the box i got envy for this version of unbutu and got the most recent driver for my Nvidia 8600 M GT, I had some linux games like Warsow already install running on max nicely with no lag or fps problems. I installed Steam using wine and installed some HL2 mods like CSS and even when i turned all the setting down i was only really getting 20-30fps and thats when it was good, i decided to download the latest driver on the nvidia website instead of using the envy one it can be seen here [http://www.nvidia.com/object/linux_display_amd64_173.14.09.html](http://www.nvidia.com/object/linux_display_amd64_173.14.09.html). I installed this driver and it again is playing nice with Warsow and my other linux games but in wine i am getting really poor fps, i have a pc with an 8800gtx running the same configuration except its 7.10 and the fps on that is basically the same as it was when it was running windows. Is this a problem with 64bit 8.04 or just poor drivers for my mobile card? my friend on windows was getting double the fps i was getting at least

---

### Post by soxs on 2008-07-10
Mobile processors ar usally cut down to about 50%. the have less shaders/units etc... this may be the reason, though running games through wine is never a serious method for gaming. Every new driver may brakce acceleration (ati driver fglrx 8.6 did so...)

---

### Post by saru411 on 2008-07-11
The arch of the 8800 and 8600 are very different. the vostro 1500(which im typing from currently) had only a 64bit interface with the mother board. compare to 256bit or higher interface of 8800's

---

### Post by Hyuukai on 2008-07-11
Ok now today my laptop wont even turn on :( it goes from the bios says loading grub i believe then the screen goes blank, it did a few times come up with different kernals i wanted to use and some in recovery mode :(

---

### Post by Kilz on 2008-07-11
> **soxs said:**
> Mobile processors ar usally cut down to about 50%. the have less shaders/units etc... this may be the reason, though running games through wine is never a serious method for gaming. Every new driver may brakce acceleration (ati driver fglrx 8.6 did so...)

I dont know. Running games with wine in my experience has produced better results that running the game on windows because of all the anti (anti vuirus, anti malware, anti etc) stuff running in the background on windows.

---

### Post by Hyuukai on 2008-07-11
Ok now i got a major problem when turning on my laptop i tried to install windows xp via a disc and got this error blue screen

NO_MORE_IRP_STACK_LOCATIONS

then i got this error trying to boot into ubuntu

memory write/read failure at 00024010, read 0202ed02 expecting ed02ed02 to resolve issue try to reseat the memory

then when i ran the diagnostics i got 

test results: system error
error code 2000-0111
msg cpu 0 invalid opcode exception occurred at selector 18 physical offset 34060 map file offset 130

EAX =00100000h EBXX = 006E776FH ECX = 00000006h EDX= 00100040h EBP = 00032264h ESI= 00032294h EDI = 00100040h ESP = 00032268h
CS = 0018h DS = 0020h ES= 0020h FS = 0018h GS= 0020h CR0 = 00000011h CR2 = 00000000h CR3 = 00000000h

then i also got this error 24 attempt to access block outside partition 

 :(

---

