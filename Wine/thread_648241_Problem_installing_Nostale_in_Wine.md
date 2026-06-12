---
title: "Problem installing Nostale in Wine"
date: 2007-12-23
forum: Wine
---

### Post by auroragb on 2007-12-23
Hi,

I've installed wine 0.9.49.  I'm trying to install Nostale, but am getting this error
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"

and a dialog box with
Access violation at address 004097b6, Write of address 00400000

I'm probably missing something.  Can someone help?

This is on an ASUS Eee xandros
Nostale apparently worked on 0.9.46 on slackware

TIA

---

### Post by cogadh on 2007-12-23
Is that the full error or was there a few more lines to it? Usually when you see that "Microsoft.Windows.Common-Controls" message it is followed by another error that specifies a particular DLL that might be missing.

---

### Post by auroragb on 2007-12-23
That was it, one error comes on the terminal and a dialog box with the access violation error

---

### Post by auroragb on 2007-12-26
Can someone suggest anything I can try?

TIA

---

### Post by auroragb on 2008-01-02
No one can help? :(

---

### Post by CodeCarpenter on 2008-06-04
You might try updating Wine to 0.9.56. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10971](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10971) Shows no problems with the latest Wine/Nostale versions together.

---

### Post by cogadh on 2008-06-04
What's with people necromancing threads lately? This thread has gone 6 months without a response. Around here, that means its a dead thread. 

Besides, the latest Wine is 1.0-rc3, not 0.9.56. That version of Wine is actually 8 revisions old now.

---

