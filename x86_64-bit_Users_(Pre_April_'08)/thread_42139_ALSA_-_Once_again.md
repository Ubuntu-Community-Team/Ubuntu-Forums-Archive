---
title: "ALSA - Once again"
date: 2005-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ::DoGG:: on 2005-06-16
Hey guys, i just wanted to get alsa plugin working so i can get rid of the problem with audio desync in video files.
When i set xmms to use alsa output plugin only on adress hw0,2 it`s not spitting out and working (spectrum analyzer is working) but i can`t hear anything, i tried a various configurations with alsamixer, also set alsa to default sound system in ubuntu.
the lspci tells me this about my sound card:
```
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 1400 [size=256]
	I/O ports at 1c00 [size=128]
	Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>
```

And my asound file (i believe that`s the one that`s responsible for alsa config:

```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}
```

Is there any simple command to set from shell adress and irq for the sound card ? or can it be done in asound.conf ??

---

