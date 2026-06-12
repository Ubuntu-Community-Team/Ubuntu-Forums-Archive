---
title: "Counter Strike Source Error: Failed to lock index buffer in cmeshDX8::LockIndexBuffer"
date: 2007-10-04
forum: Wine
---

### Post by {NmE} on 2007-10-04
HELP!

 I am getting this error 
```
Failed to lock index buffer in cmeshDX8::LockIndexBuffer ubuntu
```

when I start up Counter Strike Source and try to join a game. 

I have it installed with wine..

My computer is more than capable of dx8.. where would I set this up to 9 or 9.1? As i think this is the issue..

anyone else having problems with this?

---

### Post by abadtooth on 2007-10-04
> **{NmE} said:**
> HELP!

 I am getting this error 
```
Failed to lock index buffer in cmeshDX8::LockIndexBuffer ubuntu
```

when I start up Counter Strike Source and try to join a game. 

I have it installed with wine..

My computer is more than capable of dx8.. where would I set this up to 9 or 9.1? As i think this is the issue..

anyone else having problems with this?

Did you follow this guide?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

---

### Post by krak on 2007-11-14
> **{NmE} said:**
> HELP!

 I am getting this error 
```
Failed to lock index buffer in cmeshDX8::LockIndexBuffer ubuntu
```

when I start up Counter Strike Source and try to join a game. 

I have it installed with wine..

My computer is more than capable of dx8.. where would I set this up to 9 or 9.1? As i think this is the issue..

anyone else having problems with this?

try this command i in steam > Counter-Strike: Source > Properties > Set lunch options. Paste that line below
```
-windowed -width 640 -height 480 - heapsize 2097152 -dxlevel 70
```
u can use any resolution but remember to keep 4:3 ratio eg
```
-windowed -width 1024 -height 768
```
[[IMG]http://img141.imageshack.us/img141/86/counterstrikeatisteamsx0.th.jpg[/IMG]](http://img141.imageshack.us/my.php?image=counterstrikeatisteamsx0.jpg)

CS:S using Wine ATI drivers 8.42.3 @ Radeon 9600Pro
[[IMG]http://img140.imageshack.us/img140/3619/csatigk4.th.jpg[/IMG]](http://img140.imageshack.us/my.php?image=csatigk4.jpg)

---

### Post by {NmE} on 2007-11-15
Yes, see but I want to be able to play at higher rez then that... and also be able to use my widescreen ratio

---

### Post by Rafadagaffer on 2007-11-15
I had the same problem.

 I had to set my video memory manually in wines registry. Open up the terminal, enter this

```
regedit
```

Navigate to HKEY_CURRENT_USER_>>>Software>>>Wine>>>Direct3D

Create a new string called "VideoMemorySize". Add the amount of your video in memory in megabytes into the data field. Eg if you have 256mbs of video ram add 256 to the data field. 

Exit regedit, restart steam. This worked for me, hopefully it will work for you too :)

---

### Post by Ber P on 2007-11-24
That did it for me! 
I'm using the 8.43 driver from ATI, and with the regedit fix, CS:S actually runs pretty nice! The colors a completly messed up, though - but that's another issue. Lets hope it is stable!

---

### Post by dvord on 2008-02-07
Using this advice I was able to get 1024X768 without crashing.  I would prefer 1440X900 but I get crashes after that.

I tried the REGEDIT advice above, but there was no Direct3D section.  I did create it and the suggested value but to no avail.

---

