---
title: "Fallout: New Vegas - Graphics Rendering"
date: 2012-03-30
forum: Wine
---

### Post by TDalton on 2012-03-30
Hey y'all. I've tried searching the forums but I haven't found enough help to fix the problem.

I'm using Ubuntu 11.10. 

lspci-v tells me I have this for my graphics card:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1be2
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e080 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```

I am using Wine 1.4 (stable), playonlinux.

The problem: Fallout: New Vegas doesn't load character textures (minor problem) or parts of 3D textures in the world (big problem). The result is that I am running in empty space where I can't see any items. A screenshot is attached.

Thanks

---

### Post by lite1979 on 2012-03-31
Looks like your video card isn't powerful enough. According to [this site](http://www.game-debate.com/games/index.php?g_id=589&game=Fallout:%20New%20Vegas), a GeForce GT 140 (a.k.a. 9600 GT) is the minumum card required, and it has 1GB of VRAM, whereas you only have 256M on your integrated graphics card. I hate to tell you this, but it looks like it's time to upgrade.

---

### Post by TDalton on 2012-03-31
The problem with that response is that, before switching to Ubuntu, I ran New Vegas off Windows 7 with the same laptop. It ran very smoothly, hardly laggy at all. I had no problems with it. 

So the idea that my graphics card isn't enough doesn't cut it. I think its a problem with drivers.

---

### Post by Soulcage on 2012-04-01
Drivers is exactly the problem and you probably wont be getting any better ones on linux.

---

### Post by TDalton on 2012-04-01
That's it? Really?

---

### Post by TDalton on 2012-04-05
[IMG]http://forums.watchuseek.com/attachments/f29/539840d1319204349-new-price-omega-speedmaster-apollo-11-35th-anniversary-3569-31-limited-edtion-mariobump.jpg[/IMG]

---

