---
title: "Nautilus slow to close"
date: 2009-01-26
forum: x86 64-bit Users
---

### Post by nrobinson on 2009-01-26
I am running Ubuntu 8.10 64 bit

Kernel 2.6.27-11-generic
GNOME 2.24.1

Since I have upgraded to 8.10 it takes ages to close any nautilus window. After closing the window it sits there for at least 5 seconds before which the wait / force dialog comes up and then then the window closes of its own accord.

Any help would be appreciated

---

### Post by Yashiro on 2009-01-27
Launch 'nautilus' from a terminal.
Close nautilus.
Read the terminal text. Possibly find the error. Profit.

---

### Post by nrobinson on 2009-01-28
Nautilus shows no errors on exiting.

---

### Post by Yashiro on 2009-01-28
You might have to debug it with strace if you want to fix it. Or hope someone notices the error here and recognizes the issue. This is how most things get fixed ;)

First though, make a new user account. Log in as this user. Does it still hang for him?

---

