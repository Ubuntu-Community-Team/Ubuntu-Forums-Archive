---
title: "64-bit processors and 32-bit stuff"
date: 2006-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by celsofaf on 2006-12-11
Hello. I don't know whether this is the best place to ask about it. :confused: 

I'm intending to buy a laptop in a few months, and I'm still to decide if the processor will be a 64-bit one (AMD64, most likely) or a "normal" one. This is the only question for me right now, as the following:

OK, yes, there are specialy-done 64-bit versions for Ubuntu and several other distros, but... OK, suppose I install a 64-bit Ubuntu. Will 32-bit software (pre-compiled) run normaly? Will I have problems if I compile myself a 32-bit source? Or, better asked: is backwards compatibility ensured?

](*,)

---

### Post by ispmarin on 2006-12-11
I think that this question belongs to the 64bits forum. The Cafe is just for general discussions...
The amd64 processors can run 32bits apps, just depending on all the application being 32bits (like libraries, etc). As far as I know, it does not exist a `mix mode (32bits and 64bits in the _same_ application)`. But a 64bits kernel (like in Ubuntu 64bits) can run 32bits application. 
Moderator, can you please move this thread?

Hope it helps.

Ivan

---

### Post by Kindred on 2006-12-11
Yeah you can still just install the 32 bit version of Ubuntu or whatever distro, I think most do, though I like my 64 bit install.  Most 32 bit only junk can be made to work with some effort on 64 bit without resorting to chroot though.

---

### Post by o_fortuna on 2006-12-11
32-bit software sometimes (but not always) runs normally since many 32-bit programs require 32-bit libraries. At this time, I would recommend using 32-bit Ubuntu on a 64-bit processor.

That said, you shouldn't buy an x86 processor today that doesn't support 64-bit. At least Intel Core 2 and _all_ AMD processors from the past two years are 64-bit enabled. A "normal" processor is now pretty much a 64-bit processor, as far as buying a new computer.

---

### Post by argie on 2006-12-11
You'll have lots of problems with flash and the like or so I notice from these forums.

---

### Post by lyceum on 2006-12-11
I would skip the 64 and go with a Dual Core. The 64 bit will be a waist, as you can go with the 32 Ubuntu, and not use the full 64 bit processor or you can go with the 64 Ubuntu and not use all the programs Ubuntu offers. That is why I think it is a waist, well if you want to stick with Ubuntu that is. I guess there are other distros out there that were made for a 64 bit processor.

---

### Post by kuja on 2006-12-11
All current processors are 64-bit anyway, not much to discuss :)
That is, these processors, I consider them to be current anyway: Intel Core2 Duo(but not Intel Core Duo, only the Core2 Duo, officially anyway)), Intel Pentium D (At least some of them, I believe), Intel Xeon(At least some of them), AMD Athlon64/Turion64/Sempron/Opteron(sockets 754, 939, 940, S1, and AM2) 

There are three modes with regards to 64-bit processors:

A pure 64-bit setup - self describing

"Mixed mode" - a 64-bit kernel with 32-bit apps (and not the other way around, ever) It works well enough, but you need to have the 32-bit libraries. Compiling said 32-bit is very, very hairy, find packages rather than doing it yourself if possible.

"Legacy mode" - 32-bit kernel with 32-bit apps. This usually works, but sometimes ACPI problems prevent you from having a system working as it should, for example, you might not be able to use all cores in a multi-core processor.

---

### Post by ispmarin on 2006-12-11
Nowadays the pure 64bits approach is working very well (including flash, if you use a 32bits static compiled browser), and yes, most of the new processors out in the market are 64bits. And I will (risking start a flame war here) stick to the amd64 with a 64bits kernel, 'cause some improvements made in processor arch, memory bandwidth, prefetching, the cost and the temperature is still favoring the AMD processors (the Athlon64 X2 is very good at cost/benefit, althougt the Core Duo is faster in some tasks), and the problems with some 32bits apps on a 64bits arch are smoothed (search in this forum and compares the messages from, say, one year ago with newer messages). The problems are being solved or workarouds are provided, and the future _is_ 64bits computing. If you want to stay in 32bits and are searching for a fine processor (_very_ cheap and not so bad at horse power), try the AMD Sempron line. (I've warned about the flame war! :mrgreen: )

Hope it helps.

---

### Post by celsofaf on 2006-12-11
Very informative of you all... This is a great community. :) And you're making me decide for a 64-bit one, yes. I don't know how to thank you all for the support and help. :D

---

