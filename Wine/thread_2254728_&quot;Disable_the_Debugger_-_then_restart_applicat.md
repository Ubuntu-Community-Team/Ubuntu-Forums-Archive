---
title: "&quot;Disable the Debugger - then restart application&quot; ??"
date: 2014-11-29
forum: Wine
---

### Post by chris36 on 2014-11-29
Hi - I'm running Mint 17, with Mate enviroment and Wine 1.6.2 - problem is as above. Trying to run a Sheet Cutting Optimisation program called "Optimik v3.28" however cant get passed the debugger.

I have no other need of any other Windows programs. Can you help?
I've tried to find info on the Wine site but no hits on this or other "Optimisation cutting" programs.

Thanks in Advance.

---

### Post by Mark Phelps on 2014-11-30
Wine is not a Windows Emulator: an interface that would allow everything that runs in Windows to run in Linux.  Instead, it is a "hack" in which some Windows runtime libraries were rewritten to replace Windows OS kernel calls with Linux OS kernel calls.

To the degree that a Windows apps relies entirely on these calls for its operation, to the same degree, it will run well in Wine.

But recent apps tend to use other Windows middleware (like .net and Silverlight), which don't work well in Wine, and specialized apps (like the one you're trying to use) can even come with their own runtime libraries.  In such cases, these apps are NOT going to work in Wine.

If you really need such apps to work, you need a true Windows environment.

---

