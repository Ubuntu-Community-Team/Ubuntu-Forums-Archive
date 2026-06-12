---
title: "OpenOffice.org drag and drop broke after upgrading to Edgy"
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-01-25
I recently upgraded my Dapper amd64 to Edgy amd64, which automatically upgraded OpenOffice.org 2.02 to 2.04. Suddenly I can no longer drag and drop text. Drag and drop still works in other apps (e.g., AbiWord), so I don't think it is a Gnome issue or an Edgy issue per se. But it would be awesome cool if someone would say they had the same problem, and even awesomer cooler if they had a solution.

---

### Post by crazedgremlin on 2007-02-12
I started on this computer with a clean install of edgy (amd64) and haven't been able to drag and drop text in openoffice.
It's really annoying.
I've got no clue how to fix it....wish I did.:(

---

### Post by John Jason Jordan on 2007-02-13
> **crazedgremlin said:**
> I started on this computer with a clean install of edgy (amd64) and haven't been able to drag and drop text in openoffice.
It's really annoying.
I've got no clue how to fix it....wish I did.:(
I've been fiddling with various things on and off ever since upgrading Dapper amd64 with OOo 2.02 to Edgy amd64 with OOo 2.0.4. Just now I did a complete removal and reinstall of OOo 2.04 and drag and drop of text still isn't working. :(

There is another thread where this has been discussed. There are about five of us that I know of. None of the others have found a solution either.

I might add that I have one additional bug. With Writer open I can go into Tools > Options > Writer > General and set a default tab stop. (The default is set to 2 cm.) The default tab stop for the document will then be the new setting. But if I close and reopen the document it is back to 2 cm. I can also change the default and save it to my default template and it does not "take." The next time I open a new, blank document the default tab settings are back to 2 cm.

It would be interesting to find out if you have the default tab stop problem as well.

There are two normal approaches to troubleshoot these problems. One is that we could all compare notes about all programs we have installed to see if we have a package in common that might be causing a conflict. The other approach is the opposite -- find users who do not have the problem and get lists of all the packages they have installed to see if there is something we are missing.

Another option would be to query the developers and find out which libraries or modules the drag and drop of text uses. That might give us a more direct answer to what is wrong.

I should also add that I can drag and drop text in AbiWord, so the problem is within OOo or some package it depends on.

---

### Post by crazedgremlin on 2007-02-17
I'm sorry I won't be too much help now.
Next week I'll be switching over to the 32-bit version: I've had enough of no flash player, messed up OOo, and recompiling.  :/

---

### Post by John Jason Jordan on 2007-02-17
> **crazedgremlin said:**
> I'm sorry I won't be too much help now.
Next week I'll be switching over to the 32-bit version: I've had enough of no flash player, messed up OOo, and recompiling.  :/
I understand your frustration. I do have Flash 9 running in 64-bit Firefox now, although it took some work to get it going. As for the OOo drag and drop problem, I have determined that the problem is with Edgy, not OOo. Therefore, I filed a bug report with Ubuntu:

[https://launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/85248](https://launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/85248)

Hopefully, someone from Ubuntu will eventually see it and do something about it.

---

