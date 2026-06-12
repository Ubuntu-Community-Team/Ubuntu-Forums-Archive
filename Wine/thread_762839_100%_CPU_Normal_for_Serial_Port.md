---
title: "100% CPU Normal for Serial Port?"
date: 2008-04-22
forum: Wine
---

### Post by canclan on 2008-04-22
I am trying to use a small windows satellite file loading program in Wine.  When I try to upload the file, cpu load jumps to 100% (roughly 65/35 program/wineserver) with no apparent successful connection.  I can not seem to get the program to successfully upload the file, so in the course of troubleshooting, I am trying to ascertain if this is normal for serial port connections with Wine and possibly if it can/should be reduced.

I can post any log file/output if requested.  

Thanks in advance for any feedback!

---

### Post by hikaricore on 2008-04-23
You may want to watch for error messages while running this software from a terminal.

In all likelyhood with this type of behavior said software will not work properly under WINE.

---

### Post by canclan on 2008-04-23
> **hikaricore said:**
> You may want to watch for error messages while running this software from a terminal.

In all likelyhood with this type of behavior said software will not work properly under WINE.

Thanks for the reply (even if it isn't good news!)!  I will see what terminal spits out.

---

### Post by canclan on 2008-04-25
So I ran it in terminal, and here is what came out:

```
brian@brian-laptop:~/.wine/drive_c/windows$ wine pansatloader.exe
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
fixme:comm:set_queue_size insize 10000 outsize 10000 unimplemented stub
brian@brian-laptop:~/.wine/drive_c/windows$ 
```So, does anyone know how to read this output?

Thanks again in advance for any help!

---

### Post by nick_h on 2008-09-13
I'm getting a similar error to this.

It looks like Wine [bug #7526](http://bugs.winehq.org/show_bug.cgi?id=7526) and could be fixed.

It would be worth trying the latest version of Wine.

---

### Post by shahav on 2009-04-27
Guys, any solution for this problem?
I'm facing a similar problem, once a wine application opens the serial port, the cpu usage ramp to 100%, about 60% the application and the rest 40% on the wineserver.
Any suggestions?
10x

R.

---

### Post by canclan on 2009-09-13
I am sorry to say that I gave up trying.  After a whole lot of time consuming dead ends, I gave up on the problem and used a hardware workaround. 

Sorry!

---

### Post by Tigersmind on 2009-09-14
I may get smacked for this, but have you thought about running this under a virtual machine? Its not a native solution, but if you install a program called Rain for pre-XP versions of windows in the machine it drops CPU usage to 0 until something is running.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I lost my copy of Rain, but I am gonna look tomorrow so I can post a link if you want it.

---

