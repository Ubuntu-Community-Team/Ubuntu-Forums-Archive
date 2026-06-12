---
title: "Severe CPU hogging on certain program installs"
date: 2017-06-18
forum: Wine
---

### Post by arkostin01 on 2017-06-18
Hiya!

Anytime I attempt to install anything using PlayOnLinux, the installer gets stuck at the spinny wheel stage and a process pops up in the 'top' window either under the name 'kworker/x: x' (Which is apparently a kernel process for one of the four CPU cores I have) or 'fglrx'. Their CPU usage instantly shoots up to 100%, making me not able to start any new programs, open new browser tabs, or hunt down the actual problem using perf. I can't stop the process, xkilling the PlayOnLinux windows does nothing, and there's nothing on the forums with any mention of a fix. I've purged and reinstalled POL, wine, and winetricks several times to no avail.

Does anybody have any clue as to what's happening/a probable fix? 

Thanks ahead of time :)

---

### Post by SeijiSensei on 2017-06-18
Can you revert to the open-source video driver and not use fglrx during this task?

Open a terminal and run "top" then try running PlayOnLinux in another window and watch what happens.

---

