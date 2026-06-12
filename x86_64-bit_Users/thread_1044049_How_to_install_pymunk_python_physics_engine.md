---
title: "How to install pymunk python physics engine"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by ibbuntu on 2009-01-19
Hi, I followed the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=911966](http://ubuntuforums.org/showthread.php?t=911966)

and I get this error message when trying to run the demo_basic_test.py:

Loading chipmunk for Linux (64bit) [/usr/lib/python2.5/site-packages/pymunk-0.8.1-py2.5.egg/pymunk/libchipmunk.so]
Traceback (most recent call last):
  File "demo_basic_test.py", line 1, in <module>
    import pymunk as pm
  File "/usr/lib/python2.5/site-packages/pymunk-0.8.1-py2.5.egg/pymunk/__init__.py", line 14, in <module>
    import _chipmunk as cp
  File "/usr/lib/python2.5/site-packages/pymunk-0.8.1-py2.5.egg/pymunk/_chipmunk.py", line 8, in <module>
    chipmunk_lib = load_library("chipmunk", print_path=_lib_debug)
  File "/usr/lib/python2.5/site-packages/pymunk-0.8.1-py2.5.egg/pymunk/libload.py", line 39, in load_library
    lib = ctypes.cdll.LoadLibrary(libfn)
  File "/usr/lib/python2.5/ctypes/__init__.py", line 431, in LoadLibrary
    return self._dlltype(name)
  File "/usr/lib/python2.5/ctypes/__init__.py", line 348, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: /usr/lib/python2.5/site-packages/pymunk-0.8.1-py2.5.egg/pymunk/libchipmunk.so: wrong ELF class: ELFCLASS32

I imagine this is a problem due to the fact I am running 64-bit, hence why I am posting here.

Any ideas?

---

### Post by ibbuntu on 2009-01-19
Solved by following the instructions here:

[http://code.google.com/p/pymunk/issues/detail?id=12](http://code.google.com/p/pymunk/issues/detail?id=12)

Should have checked there first, sorry for the spam.

---

