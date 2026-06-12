---
title: "rolling back changes in LINUX systems"
date: 2007-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by vinceZZZZ on 2007-06-05
Hello forum users again...


I wonder if any of you can offer me good advice about ROLLING BACK changes in Linux?....a method of almost putting your LINUX into a shadow session....so no matter how much mess you create you can always ROLL BACK or dump the entire user session and changes....

(is this already a feature in LINUX?....is it already possible to DUMP a session)

I have found similar software for SHADOW working in windows...and it's super....i have never had a single window problem in a long time (1 year).....since using SHADOWUSER....and shadowsessions....(it is a kind of GHOST feature on drives)

is there an actual TOOL for doing this rolling back in LINUX....a GUI windowed tool?

thanks then

---

### Post by stmiller on 2007-06-05
Hm, I don't think there is for Linux. The software on windows that does this is okay, but I would not risk critical data with something like this.

---

### Post by ©TriMoon® on 2007-06-06
You could make separate partitions to hold your "working" and "mess-out" versions.
Then just copy-over from "working" to "mess-out" after deleting all files on the "mess-out" partition.
This needs some careful-hand because of special files like those in /dev, but you get the idea :)

It should be fairly simple if both partitions are exact same size, in which case you could perhaps even use the dd command :D

Never tried either way, but these are my thoughts that came up after reading your question :)

---

### Post by vinceZZZZ on 2007-06-07
Hello,

thanks for your advice....i was kiind oh hoping there would be a proper TOOL to do this shadowing of a linux session.

You see, the thing with the windows tool i use...is it is superb...it does not affect your PC's performance...but allows you to use your computer in a totally SCARE free way.....because you are always within a SHADOW session.

If you want to keep a file for ever...you merly right click and COMMIT the file to the hard drive...

but in normal shadow MODE....nothing is ever actually commited to your HARD DRIVE...unless you athorize it...your running in a  VIRTUAL windows....so to speak

these shadow sessions stay...even if the PC is powered OFF into HIBERNATE....they last as long as you like....they prevent you messing up your windows system and you can dump them any-time you like.... you can dump a poor software INSTALL or any spyware etc...by simply dumpiing the shadow session...

a brilliant tool...SHADOWUSER.

I have personally found a proper way to rollback in LINUX...it is a few commands on the command line..but it's no-where near as HANDY as this windwos shadow tool....for ease of USE.

V

---

### Post by octoberdan on 2007-06-07
Don't give up hope. I think there is something like this out there... I don't have time at the moment, but later tonight or possibly tomorrow I'll take a look for you. Keep up the search.

---

### Post by vinceZZZZ on 2007-06-07
Hello


thanks for your reply..it would be great to find a SHADOWUSER style tool for linux...like SHadowuser for windows.

It makes me feal totally SECURE about using a computer...and doing whatever to the system...

People underestimate this ROLLING BACK.... and also they underestimate SHADOW style software...it's actually brilliant s/w...

if you look at forums and read about the condition people get their LINUX machines into....they often end up worse off by doing further messing around...

a tool like Shadowuser prevents all these problems...

it's just so simple to use Shadowuser....


and it provides even SIMPLE computer users...with that UNIQUIVICAL security...... about how they use their computer..... on a daily basis...

anyhow

V

---

### Post by Cappy on 2007-06-08
I found this today:
[http://www.getdeb.net/release.php?id=996](http://www.getdeb.net/release.php?id=996)

It seems pretty neat, It's incremental so it won't take up a lot of space!

Unfortunately, it is more for settings and personal files than anything else. It could do what you want, I think, but it would take twice your system disk space and the effort to rollback the files, if needed. Just thought I would mention it anyway.

It WOULD be pretty neat if there was a program that turned the partition to read-only and kept the files you change in memory, kind of like what the live-cd does. It sounds neat =P

---

### Post by vinceZZZZ on 2007-06-08
Hello,

thanks for that great TOOL...

i understand what you mean about doing a FULL SYSTEM restore.....you would need TWICE your disk space..

but this tool seams to offer a FULL SYSTEM restore....a bit like in winXP....now this is pretty usefull....

say for example i was installing a new Linux tool...REALbasic....and beforehand i used your tool to do a FULL BACK UP......if my install then goes wrong.....i can use your tool to RESTORE my SYSTEM...

this does not require any MANUAL intervention right?.....it is just a two clilck affair...right?

I supposse i could SEE what directories my REALbasic install is affecting....and i could LIST THOSE DIRECTORIES in the inital BACK-UP.....right?

thanks

Vince

---

### Post by vinceZZZZ on 2007-06-08
Hello,

just to add further comments here...


would it ALSO be necessary to rollback the actual install aswell.....REALbasic....using command line entries...?

as well as restoring the system... using your tool?

thanks

(i understand how to ROLLBACK...it is four command line entries for any install)

thanks

V

---

### Post by mbradlcu on 2007-06-08
having a full function tool like that would be very cool, can anyone tell me how to just roll back a particular package? I remember I had to do this once for an xorg package that was funky with one of the updates but I can't remember nor find any info on how it's done.. thanks!!

---

### Post by floke on 2007-06-08
You COULD use APORT cd for your TOOL although it won't help with YOUR use of capital LETTERS at apparently RANDOM intervals.

---

