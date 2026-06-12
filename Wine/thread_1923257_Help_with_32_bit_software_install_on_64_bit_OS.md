---
title: "Help with 32 bit software install on 64 bit OS"
date: 2012-02-10
forum: Wine
---

### Post by bmachia on 2012-02-10
I’m trying to install and run a windows 32 bit program called Win500, Police Scanner programing software.   Others appear to have made it run using Wine.  While I appear to have gotten somewhere with my installation the program crashes during the initial startup.

I initially posted my question on a Win500 forum.  But, it appears my Ubuntu OS, Oneiric 64 bit has complicated matters and I have not gotten a response.

I am running Ubuntu, Oneiric Ocelot (11.10) 64 bit on an HP Pavilion G7T.  Wine has been on this machine for years and while I need it very infrequently, it has never given me a problem.  

Next, the only way others have gotten this program to run under Wine was to include dotnet11, mfc42, allfonts, fontfix from Winetricks.  I am not really familiar with Winetricks, but the instructions I followed seemed to be complete and to the point.

A little more detail on the Crash.
I open a terminal window and type ‘wine Win500’ or ‘wine Win500_COM’.  I get the same results on both programs.  I see an initial GUI window with loading information for about 1 second.  Then the program crashs.  The GUI disappears and my Terminal window automatically returns to /home/bill/Win500.  No GUI errors, no terminal information.

The Light Bulb when on for me last night - 32 bit program on a 64 bit OS.  How dumb could I be?  :o

Does anyone agree?  
If yes, how can I make a compatibility call to a 32 bit program under wine using this OS?

Can anyone offer some troubleshooting idea’s so I can gain more information on the problem?

Or can anyone recommend a true Linux program I can use on my Laptop.
Hoping to hear from someone

Bill

---

### Post by sffvba[e0rt on 2012-02-10
*Thread moved to **Wine**.*


404

---

### Post by Tweak42 on 2012-02-15
There's an [appdb entry for win500]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10772") but is rather out of date.

To answer your wine on 64bit OS question:
> Note that Wine for 64-bit actually runs in 32-bit mode. This is necessary, as virtually all Windows applications are 32-bit. Support for 64-bit Windows applications is currently experimental (see Wine64).

    Wine is currently offered in 32-bit. 16-bit and 32-bit Windows applications work with it. It runs on both 32-bit and 64-bit Linux/Unix installations.
    Wine is also experimentally offered in 64-bit. 32-bit and 64-bit Windows applications (should) work with it. It runs only on 64-bit Linux installations. 


Source:[Does Wine run on 64-bit?](http://wiki.winehq.org/FAQ#head-b89ca9d7cdf2bc2ddfb23b3e5829219df48524f8)

---

