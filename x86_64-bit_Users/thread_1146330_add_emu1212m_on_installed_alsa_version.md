---
title: "add emu1212m on installed alsa version"
date: 2009-05-02
forum: x86 64-bit Users
---

### Post by sunhunter on 2009-05-02
I was using ubuntu hardy heron but switched to ubuntu studio amd and now my emu 1212m audio card is not working.

Ubuntu studio installed alsa and all related software with it .

To get the emu working, it has to be configured as a creative 10k1.

I could uninstall alsa again , re-install it and then add the emu with ./configure etc but I wonder if there's no faster approach to add the emu on a existing alsa version.

---

### Post by sunhunter on 2009-05-03
A bit more info.

Linux version : 2.6.28-3.rt
RT cause latency problems under the generic kernel

Ubuntu SMP Preempt RT

Ubuntu studio installs alsa by default and detects the on-board audio and the ati audio support. But the on-board has been desibled in the BIOS , still Ubuntu finds the realtec audio chip.

but: it did not detect the emu 1212m which is reasonable cause it has to be configured as 10k1 or 1010

If alsa is installed from build then ./configure can be used but How is it done when alsa has been installed default by the distribution, in  this case Ubuntu studio amd 64

ps. If there are other ways to get low latency numbers which work under the generic kernel then I'll test this.

---

