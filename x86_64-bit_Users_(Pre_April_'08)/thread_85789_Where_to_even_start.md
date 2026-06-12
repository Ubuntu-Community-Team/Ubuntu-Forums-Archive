---
title: "Where to even start?"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by secureboot on 2005-11-03
I've tried an PPC Ubuntu install on two different PPC machines (new Powerbook 1.67Mhz and new dual G5 w/ 20" display), and both have failed so horribly so as not to be even basically useful.  I've done 50+ linux installs on 386 machines, so I do know what I'm doing with linux in general, just not on the PPC.

The G5 has an ATI viedo card, i think, which gives me a completely garbled gdm screen, AND NO TERMINALS via ctrl-alt-f(1-6).  I picked install-powerpc64 video=ofonly.  Was that not right, or is support for this machine just so bad that you can't even get a terminal?

The Powerbook has no touchpad support, though I get terminals and can login.


The G5 install also doesn't pick out the OS X partition correctly, so trying to boot it afterwards fails, leading to a complete OS reinstall.

Oddly enough, wired networking works fine for both, thankfully.



Are there up to date howtos out there that will tell me the 101 workarounds necessary to get Ubuntu working on a PPC for either machine?  I love it for the 386, but this is ridiculous...

Of course, solutions to any of the above problems one-by-one are quite welcome as well.

---

### Post by bluerowlf on 2005-11-22
I don't have an answer for you, but your problem seems similar to mine on an x86 platform. So far the following thread is all the progress I've made: [http://ubuntuforums.org/showthread.php?t=92956](http://ubuntuforums.org/showthread.php?t=92956)
:confused:

---

### Post by ssam on 2005-11-22
maybe a vga= boot argument (search for vga modes) on the imac

i think the trackpads in the new powerbooks are on a usb interface (the old ones where adb (apple desktop bus)) this might be a useful clue.

i think that some machines run linux very well, others dont. this is true for x86 as well. the only things that dont work on my 1ghz titanium powerbook are the softmodem (i think you can get drivers from somewhere but i have never bothered.) the vga out (maybe if i play with my xorgconf i could make it work) everything else is perfect.

maybe your newer hardware is supported better by a newer kernel. the devs are testing 2.6.15 in dapper. if you know linux well maybe you could help the devs get dapper to be dapper on your imac and powerbook

---

