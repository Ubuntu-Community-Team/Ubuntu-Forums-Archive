---
title: "Failed to find memory iBook G3"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by My Lego on 2005-10-14
I installed Breezy on an iBook after a complete system crash. It ran OS 9 when it crashed so i thought why not install Ubuntu. 

The problem is that only 61 MB of ram is found o the system even though it should have 256 MB. This of results in a *very* sluggish system with very (in the 90'ish %) cpu wa process. Opening or doing anything on the system takes at least minutes.

If anyone has any ideas I would be very grateful. :( 


Thanks :D 

Marcus / My Lego

---

### Post by Rxke on 2005-10-15
Have you any idea why it crashed under 9? Macs can become quite unstable when there are problems with the RAM... So maybe it's a hardware problem. Did you try to gently reseat the extra memory?

Oh, what's the size of your RAM-disk (swap in linux-speak) You can find that under the menu Applications (the leftmost-one, I'm not 100% sure that's the right name, running this in Dutch...) then go to 'systemtools (again, same remark, it's the one with the computer-icon) and select 'processmanager' (the monitor-icon) then select 'graphs' there your memory-usage is listed. If the swap is around 96Mb, the installer didn't find the extra RAM, if it's around 256, it recognized it initially, but not presently... Pretty unlikely, but who knows if this would be the case,  this might give someone else a clue.

---

