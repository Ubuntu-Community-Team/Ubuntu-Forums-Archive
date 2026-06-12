---
title: "Boot Problems After Partial Uprgrade"
date: 2006-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bruce3000 on 2006-03-05
Well, I'll have to re-establish my status as a noob by posting this, but oh well.

The Background:
Got impatient with synaptic not intalling packages when smart-upgrading to breezy. Decided to do something rash: using dpkg to install *.deb in my cache (of packages downloaded by apt/synaptic.) Got half way through and things hit the fan :evil: 

Broke my dependency tree somewhat. But after removing some things with dpkg and some apt-get -f install, a few times over, apt-get seems to be behaving now. A problem or two reamins; Xorg isn't happy and I'm shunted into the command line with output. This isn't the first of my concerns, and it's something I'm not sure I need help with at this point.

My imediate concern is this:
"SED: unsupported command I" (repeated over and over during boot)
and
"udev is already active on /dev/" mentioned as a fatal error.

Now, I've got a sneaking suspicion that my 32-bit chroot isn't helping any of this but I'd like to pluck your brains for some possible causes, remedies and suggested diagnostics. There is some scale for butchery ;-)

Cheers

Bruce

P.S. I should really apt-get a command line irc client and get onto freenode. Any suggestions?

---

