---
title: "Wine In Ubuntu [The following file did not self registered issue]"
date: 2013-11-06
forum: Wine
---

### Post by dipti.kothari on 2013-11-06
Hi,

I am using [http://www.howtogeek.com/105271/](http://www.howtogeek.com/105271/) link to install wine on ubuntu machine.Wine installed successfully.After that i tried to install one of the exe file.I am getting message "The following file did not self registered.*****.dll Module Not Found"

What is reason behind same?
How can i resolve this issue?

Thanks,

---

### Post by howefield on 2013-11-06
Thread moved to the "*Wine*" forum.

---

### Post by Toz on 2013-11-06
> **dipti.kothari said:**
> Hi,
After that i tried to install one of the exe file.I am getting message "The following file did not self registered.*****.dll Module Not Found"

Which file/program are you trying to install?

---

### Post by Mark Phelps on 2013-11-06
Wine works by substituting some DLL files (dynamic linked library) that were written for MS Windows with files written for Linux. In most cases, these are all that are needed.

But some Windows apps come with their own DLL files, and in that case, they will most likely NOT work in Wine.

You should go to the WineHQ website and do a search for the app you're trying to use:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

If the app is not listed, or if its rating is lower than Gold, you're basically wasting your time with Wine.

---

### Post by dipti.kothari on 2013-11-07
I am trying to install [https://www.dropbox.com/sh/nvqe3n0asz63q8a/gMguNdjJ3Z/NOW%20Setup.zip](https://www.dropbox.com/sh/nvqe3n0asz63q8a/gMguNdjJ3Z/NOW%20Setup.zip)

---

### Post by dipti.kothari on 2013-11-07
I am not able to find out my app name in [COLOR=#000000] [/COLOR][http://appdb.winehq.org/objectManage...Ascending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by Toz on 2013-11-07
Is [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=27638") it? Note its rating, Garbage means it won't work.

For those that don't want to download the zip file to find out what the application is, it is an online stock trading app called "NOW".

---

