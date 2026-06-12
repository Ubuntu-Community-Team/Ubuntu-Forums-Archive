---
title: "Wine no longer run in rootless mode"
date: 2011-11-13
forum: Wine
---

### Post by goofrider on 2011-11-13
Hi all,

I've been using wine on Ubuntu for years without issues. Each win32 app will launch in a rootless window as if it's a native X11 app. 

Suddenly, since a week or so ago, all win32 apps now appear inside a single emulated  Windows desktop X11 window. How can I make Wine to use rootless mode again?

---

### Post by BillyBoa on 2011-11-13
Are you sure you didn't change something to the folder .wine?

You could try to change the permissions of the folder.

I have a similar issue with 11.10 on the folder Downloads changing permissions by itself.

---

### Post by goofrider on 2011-11-14
Thanks Billy.

Just checked. Permission is fine.

Any other ideas?

---

### Post by BillyBoa on 2011-11-14
I don't have many solutions but you could rename the .wine folder, to see when Wine creates a new one if the problem insists.

---

