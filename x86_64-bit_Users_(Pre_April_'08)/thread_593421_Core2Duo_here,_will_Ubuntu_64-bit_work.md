---
title: "Core2Duo here, will Ubuntu 64-bit work?"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by volanin on 2007-10-27
I just bought a MacBook with a Core2Duo processor.
I am running Gutsy 32-bit just fine in it, just because I have always used 32-bit in my old Celeron processor.

But today, I got curious:
Will Gutsy 64-bit work in my Core2Duo?
Is it worth it to replace my current installation with a 64-bit one?
:)

---

### Post by dabl on 2007-10-27
Kubuntu 64-bit Gutsy runs fine on my Core 2 Extreme, on an Intel motherboard.  I dunno about Macs, but the processor is definitely 64-bit architecture.  :)

---

### Post by John.Michael.Kane on 2007-10-27
> **volanin said:**
> I just bought a MacBook with a Core2Duo processor.
I am running Gutsy 32-bit just fine in it, just because I have always used 32-bit in my old Celeron processor.

But today, I got curious:
Will Gutsy 64-bit work in my Core2Duo?
Is it worth it to replace my current installation with a 64-bit one?
:)

Yes Ubuntu 64 bit will work with a Core 2 duo, however. The issue is not the processor alone. The end issue will be with the machines hardware as a whole. e.g. wifi/wired network/sound/firewire/gpu etc.

---

### Post by volanin on 2007-10-27
I installed it here as a test.
Everything worked perfectly (except for wireless, but it's unsupported even in 32bit).
But, it is not worth it YET:

I realized after installing that the 64bit of the kernel does NOT have tickless (NO_HZ).
While the tickless 32bit kernel idled at 12.5W, the non-tickless 64bit kernel idled high, at 16.5W.
This took almost an entire hour off my battery.

I believe tickless is being implemented for x86_64 in the 2.6.24 kernel.
I'll probably wait to go 64bit by Hardy then!
:)

---

