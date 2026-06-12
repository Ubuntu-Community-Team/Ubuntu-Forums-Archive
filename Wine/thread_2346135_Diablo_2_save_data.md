---
title: "Diablo 2 save data"
date: 2016-12-11
forum: Wine
---

### Post by mr.man2 on 2016-12-11
i'm sporting a xenial xub & i was wondering where diablo 2 stores the save data, ran thru wine, for i cannot find it in the default folder (namely the "Save" one). I ran a search on the entire filesystem for the characters' names with no hits. I didn't install the game i transplanted it & it's patched to the latest 14d, but it works spick & span. The saves are reliable & work swell, but the files are nowhere to be found. It's to be noted that i'm a linux rookie. Thanks in advance, please have a nice day! :guitar:

---

### Post by DuckHook on 2016-12-11
Do you use wine-prefixes? Have you changed the default install? Did you install wine from the repos, or PPA?

If a default install and no prefix, then look under: "~/.wine/drive_c/Program Files/Diablo II/save"

For users new to Linux/Ubuntu, you can always find a file by doing:```
locate name_of_file
```The trouble with *locate* is that it can be finicky&#8213;the file name must be exact, including case and extensions&#8213;so the *find* command is more versatile, but *find* requires more command line knowledge, hence I recommend *locate* for new users. In your case, if, for example, one of your saved profiles is "Heracles", it would be:```
locate Heracles.d2s
```

---

### Post by mr.man2 on 2016-12-12
```
locate
``` worked supa swell, thank u for the help!!!!

---

### Post by DuckHook on 2016-12-12
Glad it worked out. Kindly mark thread *solved* using thread tools at top of thread for the benefit of other searchers.

---

