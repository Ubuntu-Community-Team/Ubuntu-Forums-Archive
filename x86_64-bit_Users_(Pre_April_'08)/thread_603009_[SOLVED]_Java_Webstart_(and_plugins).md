---
title: "[SOLVED] Java Webstart (and plugins)"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by mivo on 2007-11-04
For a specific Java application I apparently need Java Web Start. The problem is that it apparently does not exist in a 64-bit version (just like the plugins). The Java site says something about "please use the 32-bit version" (of Webstart). How would I go about doing this without messing up my "regular" Java (and Gutsy) installation?

Also, the IcedTea Java plugins are not sufficient for the one Java'ed site (no sound) I would need it for. Is my only choice here to install an additional 32-bit version of Firefox and use it whenever necessary? How would I do this? (The repo only offers the 64-bit version?) Ideally I would like this to be "clean" too so that nothing else gets messed up.

Sorry if these are newbie'ish questions. This is my first 64-bit machine. :)

---

### Post by Kilz on 2007-11-04
> **mivo said:**
> For a specific Java application I apparently need Java Web Start. The problem is that it apparently does not exist in a 64-bit version (just like the plugins). The Java site says something about "please use the 32-bit version" (of Webstart). How would I go about doing this without messing up my "regular" Java (and Gutsy) installation?

Also, the IcedTea Java plugins are not sufficient for the one Java'ed site (no sound) I would need it for. Is my only choice here to install an additional 32-bit version of Firefox and use it whenever necessary? How would I do this? (The repo only offers the 64-bit version?) Ideally I would like this to be "clean" too so that nothing else gets messed up.

Sorry if these are newbie'ish questions. This is my first 64-bit machine. :)

Please take a look at the stickies and the first page or two of this section of the forum.

---

### Post by mivo on 2007-11-04
Thanks! I had been thrown off by the mention of Drapper Drake in the sticky post. :) Found your Howto here and the script worked flawlessly. This also took care of the Java Web Start (I ran a search for it, but it had not come up), so everything is working now. Well, almost everything! Swiftweasel does not have an icon if you make a desktop launcher for it, but that is simple enough.

I think I might just run the 32-bit Swiftweasel for everything. Not an ideal approach, but it seems easier than having two different browsers.

How do we get Swiftweasel updates?

---

### Post by Kilz on 2007-11-04
> **mivo said:**
> Thanks! I had been thrown off by the mention of Drapper Drake in the sticky post. :) Found your Howto here and the script worked flawlessly. This also took care of the Java Web Start (I ran a search for it, but it had not come up), so everything is working now. Well, almost everything! Swiftweasel does not have an icon if you make a desktop launcher for it, but that is simple enough.

I think I might just run the 32-bit Swiftweasel for everything. Not an ideal approach, but it seems easier than having two different browsers.

How do we get Swiftweasel updates?

Swiftweasel will notify you when a new version is released, and open a little window to download the newest version. Gdebi will install it nicely, you only need to install the script once.

---

### Post by mivo on 2007-11-04
Great! I had wondered if I needed to check the project's page manually. Super that it works automatically.

Thanks again! I really appreciate the howto and the work you put into the script. :)

---

### Post by Kilz on 2007-11-04
> **mivo said:**
> Great! I had wondered if I needed to check the project's page manually. Super that it works automatically.

Thanks again! I really appreciate the howto and the work you put into the script. :)

Yep, it makes it easy, just make sure to install swiftweasel32 , there are lots of versions in a release.

---

