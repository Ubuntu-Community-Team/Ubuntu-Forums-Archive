---
title: "Powernowd causes crashes for Athlon 64?"
date: 2006-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by phibxr on 2006-11-09
I'm running an Athlon 64, and I've been trying various distros for both x86 and 64 with random crashes in ALL of them, but none in Windows.

I've tried everything I could think of, ran checks on my RAM for eternities, tried running with vesa and NV-drivers, and all possible versions of official NVIDIA-drivers - until I disabled powernowd on a clean installation.

Now my system has been running without one single crash for almost five days with some heavy use, including playing DVDs and running OpenGL-games.

Is there any known problem with powernowd and AMD Athlon 64-processors?

---

### Post by kuja on 2006-11-09
I never had any troubles with it before, the problem must be much more narrow.

---

### Post by eurgain on 2006-11-09
> **phibxr said:**
> I'm running an Athlon 64, and I've been trying various distros for both x86 and 64 with random crashes in ALL of them, but none in Windows.

I've tried everything I could think of, ran checks on my RAM for eternities, tried running with vesa and NV-drivers, and all possible versions of official NVIDIA-drivers - until I disabled powernowd on a clean installation.

Now my system has been running without one single crash for almost five days with some heavy use, including playing DVDs and running OpenGL-games.

Is there any known problem with powernowd and AMD Athlon 64-processors?

This is a bit of a "don't do that then" problem.  AFAIK, many Athlon 64 desktop processors don't do frequency scaling (mine does not) so there is no reason to run powernowd.  If you have a laptop, that is another matter...

I have certainly experienced this in the past with my Athlon 3000+ machine.  However, I have not had any problem recently.  (I think that it was around the time of SUSE10.0 that the problem was rife.)  I had to kill powernowd to keep the system running for more than a few minutes.  Now, it does not cause me problems, but I do not run it because it is just a wast of processor cycles and RAM bytes.

Are you using Edgy or an older release? What processor do you have?

Regards
A

---

### Post by Ric95 on 2007-05-01
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/94739](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/94739) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There are several bugs reported on this. It seems like some 3d function doesn't like the cpu scaling that Powernowd does, especially with 64 bit versions.  
Xfce desktop helps. Disabling powernowd helps more.

---

