---
title: "Where is my memory going ?????"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by mzruya on 2008-05-26
Hello, i recently noticed something weird with my ubuntu, after a cold boot or after some usage, i close all of the running programs, and the used ram is still more then the sum of all the running processes,
no, it's not cached memory, cause i'm using the gnome system-manager and it doesn't show cached ram, only actual used memory + i already tried flushing it :-)

here are some snapshots :
[[IMG]http://img293.imageshack.us/img293/9972/29493311sl8.th.png[/IMG]](http://img293.imageshack.us/my.php?image=29493311sl8.png)
[[IMG]http://img293.imageshack.us/img293/7607/34415443ht6.th.png[/IMG]](http://img293.imageshack.us/my.php?image=34415443ht6.png)

now 58.1+25.9+10.4+9.8+8.8+8.0+7.9+7.6+6.5+2.9+1.8+1.3+0.904+0.788+0.548+0.440+0.428+0.392+0.136+0.116+0.096+0.092 = **[SIZE="4"][COLOR="Blue"]152.94[/COLOR][/SIZE]** while the usage it shows is **[SIZE="4"][COLOR="Red"]297.9[/COLOR][/SIZE]**  **twice** as much, this problem is on a wider scale after longer use, i can get up to 500mb of ram used when no extra applications are running.

hope you can help, and if u think the answer is because of caching, hope you can show me a better way to flush everything and go back to the 152.94mb of ram, cause even if i boot into a clean system the minimum it would show is** 200 +/-**

---

### Post by ibutho on 2008-05-26
To be frank with you, there doesn't seem to be a problem here. Its just the way that linux manages memory on your system. If the "used" memory is needed by other applications, the kernel will release it. To make more sense of whats happening take a look at this [article]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management"). Obviously if the system starts swapping a lot, then there is a problem somewhere.

---

### Post by chrisccoulson on 2008-05-26
No need to worry. The memory usage figures in System Monitor are pretty inaccurate. Per-process memory usage is difficult to calculate as processes share libraries etc.

And why would you want to flush cache to free up memory? That would mean you have RAM completely wasted and doing nothing. Cache is 'free' in the sense that it can be freed up automatically if an application needs it. Cache is necessary to prevent you constantly having to re-read stuff from disk, which would slow the machine down

---

### Post by Yellow Pasque on 2008-05-26
Linux is very good at memory management (unlike another popular OS which shall remain nameless). Use the following command to determine memory usage:
```
free -m
```

---

