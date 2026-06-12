---
title: "bluefish crash"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-11-05
i recently had a need to make a simple webpage, i searched the repos and found bluefish so i tried it out. It seemed cool, but when I went to save my file, it crashed with bug buddy giving me this info:

> Memory status: size: 183242752 vsize: 183242752 resident: 20996096 share: 12881920 rss: 20996096 rss_rlim: -1
CPU usage: start_time: 1162778593 rtime: 53 utime: 50 stime: 3 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100

Backtrace was generated from '/usr/bin/bluefish'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47143571896112 (LWP 18404)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00002ae075a63eef in waitpid () from /lib/libpthread.so.0
#0  0x00002ae075a63eef in waitpid () from /lib/libpthread.so.0
#1  0x00002ae074601a07 in gnome_gtk_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#2  <signal handler called>
#3  0x000000000042bd62 in ?? ()
#4  0x00000000fffffffd in ?? ()
#5  0x0000000000000000 in ?? ()

Thread 1 (Thread 47143571896112 (LWP 18404)):
#0  0x00002ae075a63eef in waitpid () from /lib/libpthread.so.0
No symbol table info available.
#1  0x00002ae074601a07 in gnome_gtk_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0x000000000042bd62 in ?? ()
No symbol table info available.
#4  0x00000000fffffffd in ?? ()
No symbol table info available.
#5  0x0000000000000000 in ?? ()
No symbol table info available.
#0  0x00002ae075a63eef in waitpid () from /lib/libpthread.so.0


can anyone help? ty

---

### Post by xstaticxgpx on 2006-11-06
common... dont make me bump every thread i make :(

---

### Post by kuja on 2006-11-06
First off, I recommend raising a bug in launchpad. Secondly, I don't think that backtrace is of much use anyhow. You likely need to install a seperate debugging symbols package, but I'm not sure which would be appropriate for bluefish. 

What were you doing when it crashed?

---

### Post by xstaticxgpx on 2006-11-06
i was simply trying to save a test document in bluefish, and it crashed with a bug buddy report shown above. I did post a launchpad bug and am waiting for a response. Is this a personal issue? a dependency problem? why am i the only one seeming to have this problem here on the ubuntuforums, launchpad, and google...

I also tried making a bt using gdb using [this guide]("http://bfwiki.tellefsen.net/index.php?pagename=DebuggingBluefish") but bluefish failed to load a gui, therefor I couldnt recreate the crash.

---

### Post by kuja on 2006-11-06
I've no idea. I personally use Quanta for my web development purposes, though I did play with bluefish a long time ago, and it looked okay... not as good as quant though IMO.

---

### Post by kuja on 2006-11-06
> **xstaticxgpx said:**
> common... dont make me bump every thread i make :(
I know how you feel. I have asked a handful of questions here myself. Probably less than ten. More then half of the questions I asked never got a reply.

---

### Post by xstaticxgpx on 2006-11-06
Quanta, eh? I'll look into that. I appreciate your help and understanding of my frustration of "teh bump", kuja. Ty

---

### Post by senda on 2006-11-08
I'm having the same issue so it's not something local. I hope it gets fixed soon

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-04
same issues here... The crash occurs anytime that I attempt to save my content, irregardless of what content is actually being saved. (e.g. 1 line of code | 1000 lines of code) Bluefish simply crashes... I've used Bluefish on my home computer and really never experienced too many problems -- Although, that was back when I was running Dapper... I'm on Edgy here at work! 

I'm at work using an HP/Compaq dc7100 system (stock)

-- 3.0Ghz P4 
-- 512MB RAM (Samsung PC3200)
-- Intel 82915G/GV/910GL Express Chip Set (Integrated Graphics)
-- Broadcom NetXtreme BCM5751 Gigabit Ethernet

I'll give Quanta a spin and see how it works! 

tHANKS!

---

### Post by Flensburger on 2007-01-12
Same problem here, but see:

[http://www.ubuntuforums.org/showthread.php?t=315921](http://www.ubuntuforums.org/showthread.php?t=315921)

Using the workaround described there, I can now save documents in Bluefish.

---

### Post by angryfirelord on 2007-01-13
Same problem here, apparently something is wrong with the edgy build.

I installed the dapper package instead (the official version (1.0.4), not the backported one (1.0.5)).

On the right hand side, you will see the different architectures listed. I use 32-bit Ubuntu, but the 64-bit package should work fine as well. Download the binary package, do a sudo dpkg -i & you should be all set (I can now save files).

[https://launchpad.net/ubuntu/dapper/+package/bluefish]("https://launchpad.net/ubuntu/dapper/+package/bluefish")

Edit: One thing I forgot to mention is that apt will still try to upgrade to the edgy version. Go to Synaptic, search for bluefish, highlight it, go to the menu & click package-->Force version. Select the earlier version & it won't bother you anymore.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-13
[https://bugs.launchpad.net/ubuntu/+source/bluefish/+bug/64016](https://bugs.launchpad.net/ubuntu/+source/bluefish/+bug/64016)

This sounds like it might be related...There appears to be a possible workaround for this issue...Please read through said link!  

Regards,

---

