---
title: "Clock Drift Problems"
date: 2006-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by guy-in-corner on 2006-03-07
The clock on my box is drifting. The rate of drift varies. Over the last week, it had drifted by about 12 hours. This is about 5 minutes per hour.

I turned off Cool-n-Quiet in the BIOS settings last night, and it's still drifting by about 1 minute per hour, so this doesn't appear to fix it completely.

It's an AMD X2 3800+, on an Asys A8V-E SE motherboard. I've not overclocked it.

I did some searching around, and people have suggested booting with various different kernel options.

Does anyone have a definitive answer to the problem, or does it vary by machine? Does anyone have a list of different options for different machines?

Or should I be trying the various different switches myself, and publishing my results?

---

### Post by Sutekh on 2006-03-07
[QUOTE=guy-in-corner]The clock on my box is drifting. The rate of drift varies. Over the last week, it had drifted by about 12 hours. This is about 5 minutes per hour.

I turned off Cool-n-Quiet in the BIOS settings last night, and it's still drifting by about 1 minute per hour, so this doesn't appear to fix it completely.

It's an AMD X2 3800+, on an Asys A8V-E SE motherboard. I've not overclocked it.

I did some searching around, and people have suggested booting with various different kernel options.[/QUOTE]Did you come across this [thread?](http://www.ubuntuforums.org/showthread.php?t=75281)

[QUOTE=guy-in-corner]
Does anyone have a definitive answer to the problem, or does it vary by machine? Does anyone have a list of different options for different machines?

Or should I be trying the various different switches myself, and publishing my results?[/QUOTE]
By the looks of the thread (apologies if you've seen it already) you probably have to try the many different methods.  Apparently the A8V doesn't have this problem, but no news about the A8V-E SE or what methods work for it.

---

### Post by guy-in-corner on 2006-03-07
[QUOTE=Sutekh]Did you come across this [thread?](http://www.ubuntuforums.org/showthread.php?t=75281)
[/QUOTE]

No. I didn't find that. Good pointer. Thanks.

As it happens, I don't have any problems with video or MP3 playback, although I may not have tried it (I don't recall) since I replaced the -i386 default kernel, so I'll check again before I try any other kernel options.

I was just thinking that it'd be nice to have a list of chipsets that were affected, and the switches required, because what's listed strikes me as 3 pages of voodoo chicken incantation. I'm not saying that to knock the Ubuntu forums, because the pages I found on LKML weren't any better.

I'll update here once I've had a chance to check the effects of the various options available.

---

### Post by guy-in-corner on 2006-03-08
[QUOTE=guy-in-corner]I'll update here once I've had a chance to check the effects of the various options available.[/QUOTE]

Update: With this particular PC (AMD X2 3800+, Asus A8V-E SE), the "notsc clock=pmtmr" kernel options appear to fix the problem.

---

### Post by Sutekh on 2006-03-08
[QUOTE=guy-in-corner]Update: With this particular PC (AMD X2 3800+, Asus A8V-E SE), the "notsc clock=pmtmr" kernel options appear to fix the problem.[/QUOTE]
That's good to know!  You should your problem and solution on that HOWTO thread for future reference.

---

