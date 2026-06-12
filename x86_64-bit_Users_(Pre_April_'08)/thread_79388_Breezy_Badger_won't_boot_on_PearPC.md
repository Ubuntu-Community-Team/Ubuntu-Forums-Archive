---
title: "Breezy Badger won't boot on PearPC"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by reub2000 on 2005-10-20
PearPC is a free PPC emulator that I'm trying to use to try the PPC version of breezy badger. I downloaded the livecd, and now I'm trying to boot it up, but it just hangs at a black screen. (See attached screen shot for the black screen.) PearPC has absoultly no problem booting up Mac OSX 10.3. I'm running PearPC from CVS on Gentoo i686.

Output to console:
```
reub2000@reub2000 ~ $ ppc livecd.ppc
This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License version 2 as published by
the Free Software Foundation.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111 USA

[PPC/VEC] Vector Address: 0810aff0
AuthenticAMD
 CMOV MMX 3DNOW 3DNOW+ SSE SSE2
[CPU/MMU] new pagetable: sdr1 = 0x00300003
[CPU/MMU] new pagetable: sdr1 accepted
[CPU/MMU] number of pages: 2^15 pagetable_start: 0x00300000 size: 2^18
start: 512
[CPU/CPU] execution started at 00200000
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[CPU/MMU] new pagetable: sdr1 = 0x00340003
[CPU/MMU] new pagetable: sdr1 accepted
[CPU/MMU] number of pages: 2^15 pagetable_start: 0x00340000 size: 2^18
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.
[IO/CUDA] <Warning> Event processing timed out. Event dropped.

```

---

### Post by ssam on 2005-10-20
i'd talk to the pearpc people.

can qemu emulate a ppc on x86?

why are you trying to do this, it seems crazy. development work?

my first try of linux was using virtualpc on an imac. it was hard to get hold of powerpc distros back then, and i hand no broadband. i think it was mandrake. it was the slowest thing ever. the mouse could not even keep up.

---

