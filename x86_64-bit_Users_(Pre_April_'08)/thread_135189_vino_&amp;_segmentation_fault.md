---
title: "vino &amp; segmentation fault"
date: 2006-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by thomasleveil on 2006-02-23
Hi, I can't vnc to my breezy. I tried to find some howto on ubuntu forums and wiki with no luck.

Here is what I've tried:
- checked that I can ping my breezy (I can ssh as well)
- reinstalled vino from synaptic
- run vino-server with: ```
/usr/lib/vino/vino-server
``` I got a segmentation fault

- I also tried to build from sources (not sure if it can help but I did it anyway :-k ):
```
sudo apt-get remove vino
sudo apt-get build-dep vino
sudo apt-get --build source vino
sudo make install
# /usr/lib/vino/vino-server
``` I got a segmentation fault again
- I run ```
# gdb /usr/lib/vino/vino-server
``` and the bt shows:


```
root@bidule-ubuntu:/home/thomas/vino-2.12.0# gdb /usr/lib/vino/vino-server
GNU gdb 6.3-debian
Copyright 2004 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...Using host libthread_db library "/lib/libthread_db.so.1".

(gdb) run
Starting program: /usr/lib/vino/vino-server
[Thread debugging using libthread_db enabled]
[New Thread 46912582065328 (LWP 7488)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 46912582065328 (LWP 7488)]
vino_input_init (display=Variable "display" is not available.
) at vino-input.c:128
128                   if (global_input_data.keycodes [keysym] != 0)
(gdb) bt
#0  vino_input_init (display=Variable "display" is not available.
) at vino-input.c:128
#1  0x000000000040b7f8 in main (argc=1, argv=0x7fffffc4b2f8) at vino-main.c:76
(gdb) quit
The program is running.  Exit anyway? (y or n) y
```

My DISPLAY env. variable is "*:0.0*" which seems fine to me....

Can any one help ? :-?

---

### Post by pixelbeat on 2007-06-25
Me too. Just tried to turn on desktop sharing on my breezy desktop.
When I couldn't connect I tried to start vino-server manually with the same reaults you had.

I'm also in Ireland. A coincidence?

$ echo $LANG
en_IE.UTF-8

cheers,
Pádraig.

---

