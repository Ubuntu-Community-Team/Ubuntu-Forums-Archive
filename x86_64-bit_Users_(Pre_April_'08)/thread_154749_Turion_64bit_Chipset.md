---
title: "Turion 64bit Chipset"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by franklee on 2006-04-03
Do I need the AMD64 iso of Breezy to maximise performance or will the 32 suffice?

Cheers

---

### Post by bpat1434 on 2006-04-03
[QUOTE=franklee]Do I need the AMD64 iso of Breezy to maximise performance or will the 32 suffice?

Cheers[/QUOTE]

It's been reported that the 64 bit isn't really well supported for applications, and installing certain apps (like Flash) aren't great.

Really, a 32-bit OS won't be able to take a hold of the power of the 64 bit processor, but you can still work faster with it.  I haven't seen performance problems running 32 bit OSes of Windows, Ubuntu, or SuSE.

---

### Post by RS3York on 2006-04-04
I have a Turion CPU.

I've run 32-bit Breezy, 32-bit Dapper and I'm currently using 64-bit Dapper.

The performance boost I've seen (comparing Dapper 32-bit against 64-bit) is mostly in the areas reported by others - Encryption and media encoding/decoding.  The system also *seems* to handle high load situation better, but it's not so much better you'll think you added a second core to your CPU. I've also never been able to lock up 64-bit Dapper, but seeing as how Dapper is in testing...that may be more to do with chance than anything else.

My advice is, if you *really* need wmv9 support.  Go with 32-bit.  While there are ways to get wmv9 to play (I received a recompiled VLC Media Player from another Ubuntuite) the whole experience is currently easier under 32-bit.

However if you're not completely new to linux, want to learn more, or deal a lot with programs that throw around huge numbers (scientific/complex mathematics, encryption, media work) go for the 64-bit version.  Despite the reports to the contrary, a 32-bit chroot isn't hard to set up at all.  Worst case scenario is you copy and paste into a terminal, learn nothing and have WINE & Firefox with Mplayer-plugin working.  Best case scenario is exactly the same as the worst but you learn something new.

I've only been using linux for a year so far, Desktop linux at that.  Outside of following guides...I'll rarely use the terminal except for simple tasks like updating apt because it's faster (Yakuake!).  All in all I prefer, KDE & Gnome to the terminal.  If you can read, copy & paste - you can setup a chroot environment and Firefox w/Flash & Java.

---

