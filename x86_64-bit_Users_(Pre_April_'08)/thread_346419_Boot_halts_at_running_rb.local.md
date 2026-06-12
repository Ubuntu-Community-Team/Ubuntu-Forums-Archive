---
title: "Boot halts at running rb.local"
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by PlancksCnst on 2007-01-25
My boot process is hanging at when it says something to the effect of "running local boot scripts (/etc/rc.local)".  I can press alt+f2 to get to a session and mess around at this point.

I had gotten beryl set up on my computer, and wanted it to start automatically.  So I searched and found the instructions [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL").  Since I already had beryl installed and working properly, I followed the instructions (for kde, nvidia) under "Configuration" except for the part about adding beryl to an existing session.  It had me make a script and a symlink in the Autostart directory to automatically start beryl.  When I restarted, it started hanging.  I have since deleted the symlink and the script I made, but still, it hangs.

---

