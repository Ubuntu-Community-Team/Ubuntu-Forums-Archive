---
title: "CPU AMD X2 4600 is used like hell under hardy"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by xieu90 on 2008-05-11
hi everyone
I have newly installed hardy on my computer which has AMD X2 4600 as its CPU
and when I don't do any my cpu usage will always be around 30%-like in pictures

what would the cause of this crazy cpu usage?
before in gutsy I found out that tracker would be the cause when my cpu suddenly jump up. in system monitor it showed that it only use 3% of my cpu but it fact it used up around 80%, after i shoot it down like a duck my cpu usage would be 5% or 0%

would there be some kind of other program like that tracker in hardy ?

---

### Post by Kilz on 2008-05-11
Tracker is installed in Hardy. You may want to disable it in sessions. Also it looks like you have a lot of swap being used, how much memory (ram) do you have?

---

### Post by xieu90 on 2008-05-11
I have 1,5 Gb ram, and 489 mb Swap
I think my computer has never touched swap yet.

---

### Post by soxs on 2008-05-11
Swap does never get touched. tracker is the only possible answer to your problems. But you can check yourself which process is consuming most of your mem/cpu/porcesstime in the second right tab.

---

### Post by xieu90 on 2008-05-11
well I always checked it
but as you can see in pictures
they are always 4, 5 % but in reality my cpu usage is around 30%
and I chose show all process
and tracker use max 3% and in truth it make my cpu run with 50% or 80%
so I'm a bit confused

---

### Post by lamborghiniwang on 2008-05-12
What about the CPU usage if you turn off the System Monitor? I always thought that part of the CPU was occupied if you turn on System monitor and switch to the "Resources" tab.

---

### Post by philinux on 2008-05-12
Use TOP instead of system monitor. The graphical tab has a high cpu usage. It's been reported.

If you shrink it's window horizontally the usage goes down.

---

### Post by HornedBeast on 2008-05-12
```
sudo apt-get install htop
htop
```

Type that into a terminal. It will give you some nice stats about your box without using a tonne of resource.

Hope that helps!

P.S. If you ever get trouble with network bandwidth, you can also try using "bwm-ng". Similar to "htop" but for network monitoring!

---

### Post by Tomatz on 2008-05-12
System, preferences, sessions, startup

Disable "tracker"

Reboot




The problem is probably caused by tracker indexing the content of large files.

I.e .iso 

;)

---

### Post by philinux on 2008-05-12
It could be the firefox sql database bug for attack site or forgery. I have both disabled under the pref security tab until RC1 appears late May.

---

### Post by olivierp on 2008-05-12
> **philinux said:**
> It could be the firefox sql database bug for attack site or forgery. I have both disabled under the pref security tab until RC1 appears late May.

You can re-enable them, and install firefox from the hardy-proposed repo. It contains a firefox build with the proposed workaround. I haven't had the high CPU/disk thrashing issue since it has been installed (roughly a week of uptime, ff3 always running)

---

### Post by philinux on 2008-05-12
> **olivierp said:**
> You can re-enable them, and install firefox from the hardy-proposed repo. It contains a firefox build with the proposed workaround. I haven't had the high CPU/disk thrashing issue since it has been installed (roughly a week of uptime, ff3 always running)

Are there any other bugs to report. :)

---

### Post by olivierp on 2008-05-12
> **philinux said:**
> Are there any other bugs to report. :)

It still runs on Windows :) ...

---

### Post by xieu90 on 2008-05-13
under top my cpu1 was max 7%
and other was around 2%
so together it was around 5%, still acceptable 
and sometimes they go down 3% + 0% 
htop is cool !

I'm writing in Firefox , listening to music chatting and downloading with ktorrent, and my cpu usage would be around 14 + 16%
and when they jump, they would be 29 and 21%

I thought that I had to go back to gutsy ^^

thank you everyone. :lolflag:

---

