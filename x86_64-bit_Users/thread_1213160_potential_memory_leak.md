---
title: "potential memory leak?"
date: 2009-07-14
forum: x86 64-bit Users
---

### Post by osakechan on 2009-07-14
Hey gang, I'm brand new to this forum and fairly new to ubuntu/any linux flavor so please be patient with me.  I have been running 9.04 x64 (kernel version is 2.6.28-11) for a while on my machine and have been experiencing painfull slowdowns after uptimes exceeding 24 hours or so.  Occasionally (often during these slowdowns), I have experienced weird redraw errors as though my video memory is corrupt or being screwed with somehow.

After a fresh boot, this little memory panel applet i have displays something like 10% in use by programs and 10% in use as cache.  By the end of this 24 hour period, it looks more like 10% in use by programs and 90% in use as cache.  A quick look at system manager shows the top memory users something like this:

Opera ~ 200M
Transmission ~ 200M
Rhythmbox ~ 50M
Nautilus ~ 50M

The rest is mostly daemons and whatnot with pretty small memory usages.  I havent made an effort to tally the total usage, but I'm pretty sure it falls WAY short of my system's 8gb of ram.

Is such a high cache usage typical?

In an effort to pin down what I assume is some sort of memory leak, I have moved from Firefox to Opera (some improvement), utorrent+wine to transmission (again, slight improvement), and from banshee to rhythmbox (more minor improvement).  None of these changes, however, have had a signifigant impact on my problem.

If anybody has any insight into my problem, or could perhaps give me some idea how to troubleshoot this, I would be most gracious.  Thanks for your time!

~M

---

### Post by philinux on 2009-07-14
For slowdowns use this command in the terminal to see whats eating cpu. Also free -m is good to see what memory is up to. Linux use memory more efficiently than windows. Dont worry about cache.

```
top


free -m
```

---

### Post by khelben1979 on 2009-07-14
With the top command: use shift M to sort all processes based upon memory usage.

---

### Post by philinux on 2009-07-14
Goog idea, and press the 1 key to see both cpu's.

---

### Post by renkinjutsu on 2009-07-14
there is no problem.. at the end of 24 hours, still only 10% is used for programs.

the linux kernel aggressively caches data that is used often and fully utilizes the RAM, otherwise the RAM's just sitting there not doing anything, and you would have wasted your money buying the modules. Everytime you open an application for file and close it again, that data is stored in cache, but the cache has a lower priority than buffers, so the RAM used in cache is truly still available for you to use for your own purposes since it'll be flushed out or pushed into swap if you need to work with RAM.
You probably open a LOT of different apps.

---

### Post by osakechan on 2009-07-14
Thanks for the quick reply!  I took a look at both commands and heres the gist:

> **free -m]Pretty much the same picture as I was getting with system manager: nearly 100% of my 8gb of ram is in use.

~6G under the buffers column
~800M under cached column
~0 of my 15gb swap partition in use[/quote]

[quote=top]This is showing gnome-system-mo utilizing the most cpu on average with ~15% in use.  Occasionally there are spikes of opera or transmission using ~40%.

As for memory, I can now see that there are about 30 processes utilizing in the range of 100M-400M of ram each under the VIRT column.  One of the largest users of VIRT is evolution-alarm, weighing in at over 400M.  Why an alarm would need 400M of cache is completely beyond me....[/quote]

[QUOTE=renkinjutsu said:**
> there is no problem.. at the end of 24 hours, still only 10% is used for programs.

the linux kernel aggressively caches data that is used often and fully utilizes the RAM, otherwise the RAM's just sitting there not doing anything, and you would have wasted your money buying the modules. Everytime you open an application for file and close it again, that data is stored in cache, but the cache has a lower priority than buffers, so the RAM used in cache is truly still available for you to use for your own purposes since it'll be flushed out or pushed into swap if you need to work with RAM.
You probably open a LOT of different apps.

Thanks for this reply, this helps clear up some of the mystery of the kernels cache management for me.  Still, beyond whatever system proccesses are running, I am only ever running about a half dozen applications concurrently (opera, transmission, rhythmbox, dropbox, and mebbe terminal here or there)...

Further thoughts?

---

### Post by bedtime_with_the_bear on 2009-07-14
As others have stated, having 100% of your memory in use is no bad thing, and since you are showing no swap file usage, I'd say there's probably nothing to worry about with your memory usage.

During one of the slowdowns, run uptime in a terminal and post the output - I'm interested in the load average as that is an indication of how many processes are runnable, but are waiting on some other event. This usually means processes are blocked waiting for I/O. For example, during a backup, my load averages have been known to creep up into double figures since there is so much disk I/O going on, the system is spending more time waiting for the physical disk than it is actually running processes. For a responsive system, you will probably want your load averages to remain below 1 multiplied by the number of cores or physical CPUs you have. My system right now, running Kubuntu 9.04 and fully patched up to today and idle except for a dolphin window, a konsole window, and firefox with 38 open tabs I currently have a load average of 0.05, which means that over the last five minutes, my system was active for 1.25% of the time (since I have a quad core CPU).

Finally, you point at graphical issues - what video card and driver are you using?

---

