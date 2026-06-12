---
title: "Wine saps processor and eventually crashes laptop"
date: 2008-04-28
forum: Wine
---

### Post by tobydeemer on 2008-04-28
Hi all-

I need IE for some apps for work (Connect-Wise and Outlook Web Access) so I have installed IEs4Linux/IE-6 and Wine. It works well, except that the Wine daemons almost immediately start to use 95-100% processor. It doesn't cause any noticeable performance cut (at first), other than making the fan run like crazy. 

When I close IE, it zombies out, and I have to open System Monitor to kill the process (or CLI, whichever mood I'm in) "IEXPLORE.EXE", and I have to kill a zombie Wine process to release the processor from the consumption. If I run IE in Wine for too long, it eventually (after 1/2 hour to 1 hour or so of use) causes a hard system freeze where none of the reset keycuts register.

I ran IE from the terminal, and it didn't throw up any errors, or any real feedback at all. Where should I start? I've looked at a lot of Wine threads dealing with game performance, but I'm not really getting anywhere. Any ideas?

Any help at all is greatly appreciated. Thanks.

---

### Post by tobydeemer on 2008-04-29
Update- sometimes when I use IE and then close it before anything really locks up, I can still use the desktop and apps, but when I try to shutdown or log out, it then locks up, and hitting ctrl+alt+backspace initiates the shutdown. Obviously because it's resetting gnome... but that's not the point.

Any ideas from a Wine guru out there?

---

### Post by Oaty on 2008-04-29
toby,
The same has been happening to me. I installed Hardy/Wine/ie4Linux last friday and get the same cpu consumption. I've uninstalled/reinstalled a couple of times. Finally I used wine to install MS Office 2003. 

When I started Word I waited for the cpu's to spike but everything stayed cool.

I've been Googling all day and have only found one other post where the user was using Edgy and they had no reply.

I'm a new Ubuntu user and have been wondering if it's a wine, ies4linux or hardy problem.

---

### Post by yipperzz on 2008-06-19
I have this same problem.  Has anybody resolved it?  I'm thinking of upgrading to 1.0 since I'm still on 0.9.59 from the ubuntu repo.  Any suggestions?  Thanks.

---

### Post by Coldfirex on 2008-06-29
Any updates on this issue?  I just recently was thinking about using ConnectWise under Wine and have seen cpu usage issues.

Can't get the PSA client to fully load though :/

---

### Post by invenit on 2008-06-29
I occasionally use IEs4Linux/IE-6 on Hardy and ran into the same problem until the update two days ago from winehq. Now IE mostly works OK until I surf to a website with a lot of flash. Then the problem returns. Still, it's a huge improvement.

---

### Post by Sourceminer on 2008-12-29
Did a search on ConnectWise and your post came up. I have been using Ubuntu now for about 2 months, first installed on my Dell Mini, now my desktop however the core tools I use are not working :-( I installed ConnectWise using Wine. However am not able to get it to launch correctly. Really trying to give Ubuntu/Linux a try here... but keep running into brick walls with all the apps we use. (Shoretel, ConnectWise, Kaseya, Evolution/Ex2k7). Seems everything is heavly tied to Winblows. Wine seems to be the only bridge but cant get it to work with these apps. Please let me know if you get it working.

---

### Post by OrbJinzo on 2008-12-30
> **tobydeemer said:**
> Hi all-

I need IE for some apps for work (Connect-Wise and Outlook Web Access) so I have installed IEs4Linux/IE-6 and Wine. It works well, except that the Wine daemons almost immediately start to use 95-100% processor. It doesn't cause any noticeable performance cut (at first), other than making the fan run like crazy. 

When I close IE, it zombies out, and I have to open System Monitor to kill the process (or CLI, whichever mood I'm in) "IEXPLORE.EXE", and I have to kill a zombie Wine process to release the processor from the consumption. If I run IE in Wine for too long, it eventually (after 1/2 hour to 1 hour or so of use) causes a hard system freeze where none of the reset keycuts register.

I ran IE from the terminal, and it didn't throw up any errors, or any real feedback at all. Where should I start? I've looked at a lot of Wine threads dealing with game performance, but I'm not really getting anywhere. Any ideas?

Any help at all is greatly appreciated. Thanks.

IE and Outlook have been known to cause wine and your PC to crash. Might I suggest you try thunderbird or some other email client?

---

