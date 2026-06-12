---
title: "where it goes (wine)"
date: 2012-06-14
forum: Wine
---

### Post by herumi555 on 2012-06-14
i'm curently using 12.04 version and install wine on it,

when i tried to run windows app it works fine, but when i show desktop the app is minimized and i can't show it back. the app didn't show in quick launch.

i have no idea where it goes :confused:

---

### Post by zombifier25 on 2012-06-14
First off, is it showing up in Alt+Tab?

This is a stupid question, but did you check the Launcher carefully for a program that has an "?" icon?

---

### Post by herumi555 on 2012-06-14
> **zombifier25 said:**
> First off, is it showing up in Alt+Tab?

This is a stupid question, but did you check the Launcher carefully for a program that has an "?" icon?

i'm sorry if i was stupid, i'm just started using linux yesterday
the program didn't show up in alt+tab, or launcher, or in another desktop, 
it's an portable app, it process show in system monitor, just minimized but don't know how to show it up again,

even when i'm gonna unmount the drive where the app belongs, it said still there's process running on the drive  ( the app )

---

### Post by mastablasta on 2012-06-14
it could be that it crashed or not responding. you could try to launch it from terminal by typing 
wine nameofapp
 
it will then give any possible error messages inside the terminal. btw what applicaiton is it exactly? it could be there is a known issue with it.
 
not every applicaiton can work in wine. only some.

---

### Post by herumi555 on 2012-06-14
> **mastablasta said:**
> it could be that it crashed or not responding. you could try to launch it from terminal by typing 
wine nameofapp
 
it will then give any possible error messages inside the terminal. btw what applicaiton is it exactly? it could be there is a known issue with it.
 
not every applicaiton can work in wine. only some.

it's sai ( a painting app ) a portable one
umm, there's no problem on terminal too,
the app work perfecly, but when it minimized, i can't make it back.
because the app not showed in launcher, nor in alt+tab even when not minimized/when active, lol

---

### Post by afixane on 2012-06-14
> **herumi555 said:**
> it's sai ( a painting app ) a portable one
umm, there's no problem on terminal too,
the app work perfecly, but when it minimized, i can't make it back.
because the app not showed in launcher, nor in alt+tab even when not minimized/when active, lol

Tell me what wine version that you have. I'm runing Wine 1.4 and SAI work perfectly to me, and i can minimise and maximise it.

---

### Post by herumi555 on 2012-06-14
> **afixane said:**
> Tell me what wine version that you have. I'm runing Wine 1.4 and SAI work perfectly to me, and i can minimise and maximise it.

wine 1.3.30, i run it using gui mode,
sai 1.1.0 i'm using offline installer, since my office blocked transfer protocol :(

let's try 1.4 tomorrow.

---

### Post by zombifier25 on 2012-06-14
> **herumi555 said:**
> i'm sorry if i was stupid, i'm just started using linux yesterday
the program didn't show up in alt+tab, or launcher, or in another desktop, 
it's an portable app, it process show in system monitor, just minimized but don't know how to show it up again,

even when i'm gonna unmount the drive where the app belongs, it said still there's process running on the drive  ( the app )

I was saying MY QUESTION was stupid. Sorry if that wasn't clear.

---

### Post by eriktheblu on 2012-06-14
Does it normally (in Windows) minimize to the notification area? Of late I'm not seeing this handled well in Wine on Ubuntu.

If so, are there settings in the program to change that behavior?

---

### Post by Elfy on 2012-06-14
*Thread moved to **Wine**.*

---

### Post by ergo-proxy on 2012-06-14
How about -> winecfg -> Graphics -> check emulate desktop and set resolution. Perhaps in such away it will be easier to find it.

---

### Post by herumi555 on 2012-06-15
after i realize the one wrong is the launcher, here some examples..

[[IMG]http://s9.postimage.org/xgur6qnuz/launcher_error.png[/IMG]]("http://postimage.org/image/xgur6qnuz/")

[[IMG]http://s9.postimage.org/4fqexc3ez/Screenshot_from_2012_06_15_13_18_50.png[/IMG]]("http://postimage.org/image/4fqexc3ez/")

run the app but not show in launcher or "alt+tab"
is it my launcher problem :S

---

