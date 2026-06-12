---
title: "Why do I have to compile wine to add patches to it?"
date: 2012-05-14
forum: Wine
---

### Post by venom104 on 2012-05-14
Okay here's the thing. For SWTOR and Diablo 3, I had to compile WINE with certian patches to make the games work properly. MY (again MY) understanding of wine is that is a compatibility layer for the windows API and a synthetic kernel (winedevice.exe) that work together to run windows programs.

If someone makes a patch, why don't they just integrate it in to wine? If the entire point of wine is to make windows software work, why WOULDN'T they include a patch into newer versions of wine?

---

### Post by cogadh on 2012-05-14
Because there is an approval process that all submitted patches must go through before they are integrated into Wine. Until that approval is given, a patch cannot be integrated, but there is nothing stopping a patch creator from making that code available for those that choose to risk using an unapproved patch. Additionally, some patches make specific apps work while breaking other functionality in Wine and will never get approved, but again, those patches are still made available for those willing to risk it. This is the case with the TOR patch, which was a proof of concept hack that was never intended to be included in Wine.

---

### Post by rai4shu2 on 2012-05-14
Windows is a bit of a house of cards with all the APIs (some of which break conceptually or conflict with each other in some weird way). Ergo, you can't always expect to patch one thing without breaking ten other things in the process. This is why they have this elaborate and lengthy process for submitting and approving patches.

---

