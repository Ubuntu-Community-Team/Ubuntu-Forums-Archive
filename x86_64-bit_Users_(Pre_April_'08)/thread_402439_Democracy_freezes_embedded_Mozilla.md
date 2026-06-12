---
title: "Democracy freezes embedded Mozilla"
date: 2007-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by m0bilitee on 2007-04-05
Hi gang.  I'm wondering if anyone else has had this issue. I've been using Democracy for a while, but the embedded Mozilla is "thou shalt not touch." In the past clicking any links would freeze Democracy entirely, so I resorted to adding the RSS feeds manually and not bothering with the guide.

Now they updated the guide, the guide connects with HTTPS, and I'm left with this lovely dialog box about encrypted pages and I can shut that off in the future.  Herein lies the rub--I cannot click on this dialog without freezing Democracy, and I can't get past this to play my vidcasts.

I'm using Democracy 0.9.5.1, on AMD 64 of course.  The background daemon for Democracy runs fine, blissfully downloading things, but I'm stuck without the ability to use the thing.

Ideas?

---

### Post by moon2js on 2007-04-05
That's exactly what just happened to me tonight. And I'm using an older version, from the repos, on Edgy.

---

### Post by moon2js on 2007-04-08
Running from term, and I get his:

```
$ democracyplayer
/var/lib/python-support/python2.5/democracy/eventloop.py:17: RuntimeWarning: Python C API version mismatch for module fasttypes: This Python has API version 1013, module fasttypes has version 1012.
  import database
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 89, in <module>
    onetime.OneTime()
  File "/var/lib/python-support/python2.5/democracy/onetime.py", line 104, in __init__
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
TypeError: exceptions must be strings, classes, or instances, not type
```

So I guess this is the Python problem mentioned in many other threads.

---

### Post by Hendrixski on 2007-04-09
How did you put the RSS manually?

---

