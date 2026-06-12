---
title: "Warcraft3 refresh rate"
date: 2007-12-07
forum: Wine
---

### Post by cazimir on 2007-12-07
i use ubuntu 7.10 as main OS on Intel E2140,2gb ram,7300gt ddr3,and i have a little problem when i play warcraft3 with wine.When i play in dr3d mode the refresh rate is ok i mean 85hz but when i play in opengl mode the refresh rate drops to 60hz.How can i make to put the refresh rate on 85hz?
LE:I have a CRT monitor and the desktop resolution is 1024x768@85hz.
Please help me.

---

### Post by karth on 2007-12-11
Did you try to force that setting in the registry?

---

### Post by ossguy on 2008-04-02
> **cazimir said:**
> i use ubuntu 7.10 as main OS on Intel E2140,2gb ram,7300gt ddr3,and i have a little problem when i play warcraft3 with wine.When i play in dr3d mode the refresh rate is ok i mean 85hz but when i play in opengl mode the refresh rate drops to 60hz.How can i make to put the refresh rate on 85hz?

Although you couldn't override the refresh rate in the Wine registry at the time karth suggested it, you now can with Wine 0.9.58.  I added a feature to Wine that lets you do this which is described in my blog post (see [http://ossguy.com/?p=29]("http://ossguy.com/?p=29")).  The third paragraph of that post tells you how to use the fix.  Adding the WineHQ repositories for Ubuntu 7.10 and then updating is the easiest way to get Wine 0.9.58.  After that, you just need to set the ForceRefreshRate registry entry as described in the post and you should be able to correct that resolution setting problem.  Let me know if you have any questions about it.

---

