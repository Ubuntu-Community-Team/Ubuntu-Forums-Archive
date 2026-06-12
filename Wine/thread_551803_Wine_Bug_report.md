---
title: "Wine Bug report?"
date: 2007-09-15
forum: Wine
---

### Post by Dark Aspect on 2007-09-15
I am some what new at wine and I have only starting installing and relying on applications though it for about 6 months.I did use a dual boot system but I don't use that any more,I just use compatibility layers like wine and crossover.

The only problem is I don't know how to report a bug report for wine.I had splinter cell working playable with a few bugs on wine 0.9.44 and now with 0.9.45 it gives a general protection error.I tried a NO-CD crack and I got the same error,can some one give me a link to where I might report bugs for wine.

A side from that the new version is awesome I have less texture bugs with Star wars Republic commando.

Just to be a little off topic I can't get Quake 2 to run on any version and every one says that works though wine.

---

### Post by splintercellguy on 2007-09-15
The full terminal output would help us determine if it's actually a bug or some other issue. Bugs are filed at [http://bugs.winehq.org](http://bugs.winehq.org), and you need to register a Bugzilla account to file one. This Wine Wiki article discusses how to appropriately write a bug report: [http://wiki.winehq.org/Bugs](http://wiki.winehq.org/Bugs)

---

### Post by Dark Aspect on 2007-09-15
> **splintercellguy said:**
> The full terminal output would help us determine if it's actually a bug or some other issue. Bugs are filed at [http://bugs.winehq.org](http://bugs.winehq.org), and you need to register a Bugzilla account to file one. This Wine Wiki article discusses how to appropriately write a bug report: [http://wiki.winehq.org/Bugs](http://wiki.winehq.org/Bugs)
Thanks a lot,I'll boot the game under command line to get a terminal output.

---

### Post by Dark Aspect on 2007-09-15
After I use the wine splintercell.exe the game crashes with this error:

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x33e00c,0x33e004): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33c8ac,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x145928) : stub, simulating 256MB for now, returning 256MB left
fixme:keyboard:RegisterHotKey (0x30028,49252,0x00000001,27): stub
fixme:keyboard:RegisterHotKey (0x30028,49253,0x00000001,9): stub
fixme:keyboard:RegisterHotKey (0x30028,49254,0x00000002,27): stub
fixme:keyboard:RegisterHotKey (0x30028,49255,0x00000002,9): stub

I created [this page]("http://appdb.winehq.org/appview.php?iVersionId=9083") on wine DB and I played it earlier today before I updated so I think its the new version. I guess it could be some thing other then a bug but I had it working so maybe some one will look and say some thing about the older version worked better.I am going to test Halo now.

---

### Post by cogadh on 2007-09-15
None of those are actually errors. The "fixme" messages are just developer notes on what still needs to be finished/fixed in Wine's coding. Are there any other errors produced or is that the full output in the terminal?

---

### Post by Dark Aspect on 2007-09-15
> **cogadh said:**
> None of those are actually errors. The "fixme" messages are just developer notes on what still needs to be finished/fixed in Wine's coding. Are there any other errors produced or is that the full output in the terminal?
well theres the line I typed that I left out that has my username and computer name but other then that yeah its the whole output....strange.The error I got was actually a dialog box form splinter cell not wine.....blast I am out of luck again,this is why I like Cedega better for games.This has happen to me like 3 times.....Is there a why to install more then one version of wine???because I would be a lot happier if there was.

---

### Post by hikaricore on 2007-09-16
Cedega is not better for games.  Stop spreading the FUD.

---

### Post by Dark Aspect on 2007-09-16
> **hikaricore said:**
> Cedega is not better for games.  Stop spreading the FUD.
I am merely saying that when some thing works on wine it breaks on later version (it has with me 3 times).With cedega you can install more then one version so if a game ran better with an older version you can select it from the settings.In that respect and only in that respect is cedega better then wine.Besides they both do different things so one can't really be better then the other.I play games on both,if wine would make it were you can install two different version than wine would far out do cedega.

---

### Post by hikaricore on 2007-09-16
> **Dark Aspect said:**
> I am merely saying that when some thing works on wine it breaks on later version (it has with me 3 times).With cedega you can install more then one version so if a game ran better with an older version you can select it from the settings.In that respect and only in that respect is cedega better then wine.Besides they both do different things so one can't really be better then the other.I play games on both,if wine would make it were you can install two different version than wine would far out do cedega.

You CAN install two different versions of WINE.
It's just not something a monkey with a package can do.

Seriously if WINE upgrades are breaking your games, stop updating or just downgrade when there is a problem.
This doesn't justify recommending a "program" *cough* that completely retards the concept of customer support, and outright steals code from WINE while still including bad flaky hacks. 

If this is "better" I'll pass.

---

### Post by Dark Aspect on 2007-09-16
> **hikaricore said:**
> You CAN install two different versions of WINE.
It's just not something a monkey with a package can do.

Seriously if WINE upgrades are breaking your games, stop updating or just downgrade when there is a problem.
This doesn't justify recommending a "program" *cough* that completely retards the concept of customer support, and outright steals code from WINE while still including bad flaky hacks. 

If this is "better" I'll pass.
Ok you won't hear a word from me about cedega again,apparently I like things easy with bad flaky hacks:)

---

