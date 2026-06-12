---
title: "FIX: No Sound While Running Crossover"
date: 2008-02-11
forum: Wine
---

### Post by V0X on 2008-02-11
Hi, I recently discovered an easy fix for the no-sound woes in CrossOver. **THIS HAS ONLY BEEN TESTED ON nVidia nForce 680i SLI Motherboard.** If you have a different motherboard, continue ***at your own risk.*** I am in no way responsible for any damage caused to your system during this process.

Applications > CrossOver > Configuration > Manage Bottles (tab)

Then click your bottle. For steam users it's win2000 (default).

Press configure.

Go to the Control Panel tab, and ignore any warnings it might give you.

Click the wine glass icon to open winecfg.

Go to the Audio tab, and ignore any warnings it might give you.

There, make sure both the ALSA Driver ***and*** OSS Driver boxes are checked.

Press Apply, then OK.

There! Sound should now work outside the CrossOver environment while it's running. Hope it helps!

---

