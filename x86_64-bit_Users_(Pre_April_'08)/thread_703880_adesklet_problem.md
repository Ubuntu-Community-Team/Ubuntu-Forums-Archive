---
title: "adesklet problem"
date: 2008-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by spdaniel91 on 2008-02-21
I'm sure this is a 64 bit issue.

I installed adesklets on KDE, but when I try to register/install a desklet, i get this error:

```
xxx@xxx:~/weather-0.0.4$ ./weather.py
Traceback (most recent call last):
  File "./weather.py", line 52, in <module>
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

---

### Post by prince_niceguy on 2008-02-24
not sure why you are using adesklets in kde.. as it is gtk app. have you tried super karamba?

---

