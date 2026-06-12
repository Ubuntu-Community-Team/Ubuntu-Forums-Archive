---
title: "Fiesta by OutSpark"
date: 2007-11-19
forum: Wine
---

### Post by sekinto on 2007-11-19
I cannot get Fiesta (a MMORPG made by OutSpark) to run under Wine. Does anyone have a good tutorial or guide on how to do this?

---

### Post by hikaricore on 2007-11-19
This game appears to be brand new and there was no listing for in in the WINE Application Database: [http://appdb.winehq.org](http://appdb.winehq.org)

It is unlikely that it will be running under WINE any time soon.

---

### Post by spykodemon on 2007-11-21
I managed to get it running just by installing everything onto a memory stick and copying it into my virtual C: drive.

try it.

---

### Post by wortxyzzy on 2007-12-06
> **spykodemon said:**
> I managed to get it running just by installing everything onto a memory stick and copying it into my virtual C: drive.

try it.

Could you please elaborate on what you did to get Fiesta working.

I have installed under wine, and then copied a working windows copy into the /dive_c/Program Files/Outspark  folder.

however when i attempt to run with wine i still get an error.

outspark.exe.log 

Traceback (most recent call last):

  File "outspark.py", line 1085, in <module>

  File "wx\_core.pyc", line 7819, in __init__

  File "wx\_core.pyc", line 7416, in _BootstrapApp

  File "outspark.py", line 716, in OnInit

  File "outspark.py", line 515, in __init__

  File "outspark.py", line 92, in get_appdata_path

TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'




am i missing something?

---

### Post by Vadi on 2007-12-06
That's weird. If they're using Python and wxwidgets, then the game should be very easily portable...

Try installing the libwxgtk2.8-0 package and all packages that come along with it.

---

### Post by wortxyzzy on 2007-12-08
I installed the mentioned packages, and still get the same error.
It may simply not work. It is just that dude said he had it working....

---

### Post by Qinjuehang on 2007-12-17
I'm sure that dude meant that he booted to windows, installed it, and copied over:)

---

