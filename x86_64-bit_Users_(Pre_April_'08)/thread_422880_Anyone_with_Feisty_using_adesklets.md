---
title: "Anyone with Feisty using adesklets?"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Posh on 2007-04-25
I am having trouble with adesklets since upgrading to Feisty.  After the upgrade weatherforecast wasn't showing up anymore (it's the only one i use).  So I eventually tried to delete my .adesklets file and re-register weatherforecast when I was met with this error.
```

posh@posh:~/weatherforecast-0.2.0$ ./weatherforecast.py
Traceback (most recent call last):
  File "./weatherforecast.py", line 41, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'
```

using update-alternatives I switched my default python to 2.4 and then my weatherforecast worked.  Unfortunately that breaks other things (beryl-settings for example).  I was wondering if anyone has successfully gotten adesklets to work on Feisty amd64. 

Thanks!

---

### Post by Posh on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942](https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				For those interested I posted a bug about this on [[COLOR="Blue"]launchpad[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942")  and there is a discussion of the problem on the [[COLOR="Blue"]adesklets forum[/COLOR]]("http://adesklets.sourceforge.net/forum/viewtopic.php?p=2299#2299").

---

