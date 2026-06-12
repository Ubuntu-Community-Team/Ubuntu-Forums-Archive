---
title: "remove wine, for fresh start.. how?"
date: 2008-05-01
forum: Wine
---

### Post by studo77 on 2008-05-01
I had a successful install of wine and a few apps. Nothing important. 

But i installed Oblivion, and could use the extra umpf from not having any desktop effects running.

The easy, and best way, in my oppinion is to have a gameruser.

So i made one. Logged in and found none programs installed, as expected.

So tried a quick fix, found on this forum. Give rights to all, and point the c_drive the right place. It did not work out, as expected.

(On my user, the Wine menus was lost a long time ago, without me deleting them. At least not deleting while wine was installed.)

So i now want a fresh wine, for use mostly in my gameruser. But after a purged uninstall, deleting .wine and reinstall results in a missing c_drive. which means there is no basic files for wine. 



**In short** Where do wine keep configuration files, or all files for that matter.

---

### Post by ajackson on 2008-05-01
> **studo77 said:**
> **In short** Where do wine keep configuration files, or all files for that matter.
The default for wine is a directory called .wine in your home directory.

---

### Post by cogadh on 2008-05-01
If you are creating a new user just for Wine, then all you need to do is log in as that user, open a terminal, then run winecfg. That will create a new .wine directory for that user and you can then install any apps you need.

Its not a good idea to try and set up that user to use an existing .wine directory in another user's home directory. You will have all kinds of permission problems and that is really not how Wine is intended to work.

---

### Post by studo77 on 2008-05-01
Well, it is not only for wine. I do like the occasional Sauerbraten or Nexuiz. They are fast, even with compiz running.

But hey, a login for gaming purposes is what i need. And also i can have a user with basic settings, that have not been tampered with, if (_when_) i get in trouble.

I will not share anything across the two users. Yeah, those permissions will give trouble. I just read on another post, where it was mentioned, with a warning. I say, do not go there.


But then to the menu-question. I removed everything wine, ie. purged wine, deleted .wine-folder a few scattered wine files. And installed again, but still i get no menuitems on my user. They are there for the new user. Not majorly important. as i do wine from terminal anyway.

---

