---
title: "Memory runnout issues"
date: 2007-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by crazy_fox on 2007-08-29
Hello all,

Its not too long since i updated to 7.04, from 6.06. Initially the system was running amazingly smooth and all the new feats were just great.

Later on i decided to give compiz a try. It worked fine for a great while as well, with very rarely crashing for no reason, but i didnt care. But one day this started happening alot, and memory was running out badly. When running firefox, limewire(frostwire), the used RAM started going up alot, and so was cache. The system would freeze, and i would have to wait  (not joking) 10 minutes for it to come back to me. Or i would use ctrl+alt+backspace and X would restart in about a minute. I thought compiz was causing this, so i removed it (not sure how well, might have some left over settings). This made the crashes fewer, but they still occur in the same fashion. When memory fills app by firefox (with flash) or limewire, it goes extremely slow, or X server restarts on each own.

While playing around with the services trying to fix it, i discovered that, disable DBUS (althought causing other problems) everything would run extremely smoothly, no crashes what so ever.

Any ideas?

PS: long explanation, but not the every day problem i think...

---

### Post by Jouke74 on 2007-08-29
You added some device that connects and reconnects? 
Update done before it started happening?

---

### Post by crazy_fox on 2007-08-29
What type of device that connects and reconnects? On what port?

Well i dont remember if there was an update done unfortunately.

---

### Post by John.Michael.Kane on 2007-08-29
> **crazy_fox said:**
> Hello all,

Its not too long since i updated to 7.04, from 6.06. Initially the system was running amazingly smooth and all the new feats were just great.

Later on i decided to give compiz a try. It worked fine for a great while as well, with very rarely crashing for no reason, but i didnt care. But one day this started happening alot, and memory was running out badly. When running firefox, limewire(frostwire), the used RAM started going up alot, and so was cache. The system would freeze, and i would have to wait  (not joking) 10 minutes for it to come back to me. Or i would use ctrl+alt+backspace and X would restart in about a minute. I thought compiz was causing this, so i removed it (not sure how well, might have some left over settings). This made the crashes fewer, but they still occur in the same fashion. When memory fills app by firefox (with flash) or limewire, it goes extremely slow, or X server restarts on each own.

While playing around with the services trying to fix it, i discovered that, disable DBUS (althought causing other problems) everything would run extremely smoothly, no crashes what so ever.

Any ideas?

PS: long explanation, but not the every day problem i think...

As for firefox it is a heavy browser nothing much can be done about it, and t's memory use

What you could try is  eliminating the other two programs you post about as  the reason for  you memory issues.

Step 1
Run the machine with out compiz running eg: use the standard metacity, and monitor your memory usage.

If the memory issue is still present.

Step 2 
Run the machine with out loading limewire(frostwire). note: limewire(frostwire) seem to require java which is also known to be heavy on system resources depending on the program.

Also it would help you garner more answers, if we knew your complete system specifications, and any modifications you may have made to the standard install.

---

