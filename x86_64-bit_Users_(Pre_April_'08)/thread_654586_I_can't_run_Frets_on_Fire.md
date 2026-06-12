---
title: "I can't run Frets on Fire"
date: 2007-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by pedro.leite on 2007-12-31
After a fine install of Frets on Fire, I tried to run it and the following error occurred:

```
pedro@moesko:~$ fretsonfire 
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 166, in __init__
    self.svg = SvgContext(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 78, in __init__
    self.setGeometry(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 91, in setGeometry
    geometry[2], geometry[3])
  File "/usr/share/games/fretsonfire/game/DummyAmanith.py", line 42, in SetViewport
    glViewport(x, y, w, h)
ctypes.ArgumentError: argument 3: <type 'exceptions.TypeError'>: wrong type
```

I think maybe the glViewport receives 2 integers and then 2 floats, but only integer are supplied...
Can someone help me on this?

---

### Post by DaveRM on 2007-12-31
pedro-

This is a known problem with 64bit.
See:
[https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/136844]("https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/136844")

Get the current verision at the web site.
[http://fretsonfire.sourceforge.net/]("http://fretsonfire.sourceforge.net/")

It works but does not play well with compiz-fusion.

DaveRM

---

