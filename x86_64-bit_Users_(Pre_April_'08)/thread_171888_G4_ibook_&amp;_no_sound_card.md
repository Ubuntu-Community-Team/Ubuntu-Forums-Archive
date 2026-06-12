---
title: "G4 ibook &amp; no sound card"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bforbarry on 2006-05-07
Hello folks. I'm sure this has been posted somewhere else before, but I haven't the solution in either this Apple forum or the sound & video forum. So, I have an g4 ibook, 768mb, superdrive with a TI sound card, with Dapper 6. But the sound card does not show up any where within the system. In the upper bar by the clock, there is a red X, in the "system, preferences, sound, default sound card is blank. In Alsamixer gui, no device. I'm really green with Linux, but I'm muddling my way thru with help from these posts & forums. Got my Airport Extreme working, bluetooth mouse working, just really would like sound so I can watch videos and listen to the radio.
Anyway to fix this would be absolutely great, 
thanks, Barry

---

### Post by bforbarry on 2006-05-11
Well folks, finally after two weeks of searching, reading  posts & threads, posting questions, finally found an answer in the bugzilla. Bug # 29750 by Ben Collins, (thank you very very much). sudo modprobe snd-powermac, gives me my sound card. so now everything is working. I was getting frustrated and was thinking of trying another distro if the official Dapper release didn't fix it. Happy as clam now !!

---

### Post by oswaldkelso on 2006-05-13
Thank for posting the answer I'm soundless too :)

---

