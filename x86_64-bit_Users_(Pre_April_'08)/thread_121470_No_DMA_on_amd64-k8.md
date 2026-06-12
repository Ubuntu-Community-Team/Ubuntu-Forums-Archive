---
title: "No DMA on amd64-k8 ???"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by qbits on 2006-01-25
Hello peoples,

I now have a shiny new Turion based laptop and I noticed something very annoying: every now and then, my dmesg contains this:

[  553.471609] ide: failed opcode was: unknown
[  558.481309] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  558.481322] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  558.481329] ide: failed opcode was: unknown

/* repeated several times /*

[  726.900467] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  726.900475] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  726.900481] ide: failed opcode was: unknown
[  726.949946] ide0: reset: success

/me is nervous about this 'BadCRC' thingy...... 

Anyone with similar problems?

---

### Post by Bandit on 2006-01-26
Have you checked to see if DMA is turned on in /etc/hdparm.conf?
If not just enable it there and see if it helps.
Cheers,
Bandit

---

### Post by qbits on 2006-01-27
Yes, DMA is enabled and working.
What I'm unsure about is the question if DMA transfers over the ide bus are supposed to be *that* unreliable in terms of *resetting* the whole bus. Perhaps I should try with some boot parameters like noapic or just switch to 2.6.15.... with or without hotplug?

Oh, the chipset is a VIA K8T890

---

