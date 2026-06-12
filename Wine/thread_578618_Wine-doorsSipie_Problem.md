---
title: "Wine-doors/Sipie Problem"
date: 2007-10-17
forum: Wine
---

### Post by sagui on 2007-10-17
I;m running Kubuntu Gutsy and I have some issues with python calls while I'm trying to run Wine-doors and sipie.

When I'm trying to run Wine-doors it says:

> 
sagui@sagui-laptop:/usr/bin$ sudo wine-doors
Started logging session
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 21, in <module>
    from wine import wine
  File "/usr/share/wine-doors/src/wine.py", line 14, in <module>
    from utils import GetCDMountPoint
  File "/usr/share/wine-doors/src/utils.py", line 9, in <module>
    log.Debug("Can't use gconf for proxy configuration")
NameError: name 'log' is not defined


When I;m trying to run Sipie it says:

> sagui@sagui-laptop:~/apps/Sipie-0.1190648273$ python sipie.py
Traceback (most recent call last):
  File "sipie.py", line 22, in <module>
    Sipie.cliPlayer()
  File "/home/sagui/apps/Sipie-0.1190648273/Sipie/cliPlayer.py", line 69, in cliPlayer
    sipie = Player(config.items())
  File "/home/sagui/apps/Sipie-0.1190648273/Sipie/Factory.py", line 99, in __init__
    self.__setupOpener()
  File "/home/sagui/apps/Sipie-0.1190648273/Sipie/Factory.py", line 115, in __setupOpener
    opener = urllib2.build_opener(cookie_handler, proxy_handler)
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>


Since these seem to be python issues, I figured they are probably related.
Any ideas?

---

### Post by cogadh on 2007-10-17
This probably has nothing to do with the problem, but don't run Wine-Doors with sudo, it's just as bad as running Wine with sudo. Best case scenario, whatever you install with WD will have root permissions and not run for a normal user. Worst case scenario, it could really screw up Ubuntu.

---

### Post by astrotoad on 2007-10-24
I had the same problem with Sipie.  I received the TypeError you described after upgrading to Gutsy.  To fix it, I edited line 114 in Factory.py:

From:
proxy_handler = None

To:
proxy_handler = urllib2.ProxyHandler({})

This provides an appropriate BaseHandler instance required by build_opener in urllib2.

It would also be a good idea to upgrade to the most current version of Sipie (0.1190648273).  You can download it at:

[http://sourceforge.net/projects/sipie]("http://sourceforge.net/projects/sipie")

---

### Post by astrotoad on 2007-10-25
I forgot to add the following...

After editing Factory.py, I ran the local sipie.py (not the one in /usr/bin) to compile and create a new Factory.pyc.  This launched a working instance of Sipie for me, verifying that the fix worked.  Finally, I added the new Factory.py and Factory.pyc to the existing Sipie egg file.  I used file-roller:

> sudo file-roller /usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg

Cheers!

---

