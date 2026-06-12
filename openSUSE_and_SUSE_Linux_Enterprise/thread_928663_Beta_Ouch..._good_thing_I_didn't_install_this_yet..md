---
title: "Beta Ouch... good thing I didn't install this yet."
date: 2008-09-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Antman on 2008-09-24
**Serious e1000e Driver Issue in SLE 11 Beta 1 and openSUSE 11.1 Beta 1:**> We have an important announcement regarding openSUSE 11.1 beta 1 and
SUSE Linux Enterprise 11 beta 1:

The Intel e1000e driver on openSUSE 11.1 Beta 1 and SUSE Linux
Enterprise 11 Beta 1 might have a serious issue with the potential to
damage the network card in a way that it cannot be used any longer.

Intel and Novell are currently working to analyze and solve the issue.

For the time being:

Please do NOT USE:

openSUSE 11.1 Beta 1
or
SUSE Linux Enterprise 11 Beta 1

on systems with Intel e1000e hardware.

Any other hardware, including systems with Intel e1000 (without -e)
network cards, is not affected by this issue.

---

### Post by Antman on 2008-09-24
Hhhmmm.... actually it looks as though Intrepid is having the same issues.

---

### Post by PmDematagoda on 2008-09-24
> **Antman said:**
> Hhhmmm.... actually it looks as though Intrepid is having the same issues.

Yes, Intrepid has the same issue. However, this is nothing to be highly critical about since you probably aren't using the 2.6.27 kernel and you may not even be having the hardware in question. Just so this is clear, this issue only affects the e1000e Intel hardware, as mentioned in the announcement you quoted:-
> Any other hardware, including systems with Intel e1000 (without -e)
network cards, is not affected by this issue.

More information on this issue can be found [here]("http://ubuntuforums.org/showthread.php?t=927943").

---

