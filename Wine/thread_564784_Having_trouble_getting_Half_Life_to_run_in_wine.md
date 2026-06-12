---
title: "Having trouble getting Half Life to run in wine"
date: 2007-10-01
forum: Wine
---

### Post by parsonsb on 2007-10-01
I have installed wine, and Steam runs fine, I've added the tahoma.ttf file to the correct place, however when I run half life, it loads up but there isn't any text. are there more fonts I need?

---

### Post by qubodup on 2007-10-04
Google ->

[QUOTE=http://appdb.winehq.org/appview.php?iVersionId=1554&iTestingId=11438]When running from standard install no text is displayed.
There was an advice to install tahoma.ttf font but it is not freely available. So I worked around it in the following way:
1. Open .wine/system.reg in text editor.
2. Find key [Software\\Microsoft\\Windows NT\\CurrentVersion\\FontSubstitutes]
3. Add subkey:
"Tahoma"="Times New Roman" [/QUOTE]

Did you do that too?

---

