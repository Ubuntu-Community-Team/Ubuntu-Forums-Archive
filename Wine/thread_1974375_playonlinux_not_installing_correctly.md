---
title: "playonlinux not installing correctly?"
date: 2012-05-06
forum: Wine
---

### Post by gandalf3 on 2012-05-06
i installed playonlinux from the software center,
but when i tried to open it, nothing happened.
result of the command 'playonlinux' in the terminal:

```
playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 30, in <module>
    import wx
ImportError: No module named wx
/usr/share/playonlinux/playonlinux: line 97: python2.6: command not found
```
i then tried to install it from they'er website, and as far as i can tell i was successful, but the same thing still happens..
:confused: anyone know why this is happening and how to fix it?
any help appreciated..

---

### Post by gandalf3 on 2012-05-29
hmm... 
i did it again ```
playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 31, in <module>
    import wxversion
ImportError: No module named wxversion
/usr/share/playonlinux/playonlinux: line 97: python2.6: command not found

```now its "wxversion", not just "wx"... odd.
anyway, BUMP.
can't think of anymore relevant information right now...:confused:

---

### Post by sffvba[e0rt on 2012-05-29
Seems to be a Python related problem (see [this]("http://ubuntuforums.org/showthread.php?t=1658489)")).


404

---

### Post by gandalf3 on 2012-06-01
hmm thanks..
but i have more than two "python" files in there.. (python, python2, and the config files, AND python2.7 with the 2.7 config)

```
/usr/local/bin$ ls
2to3  OgreMeshUpgrader  pydoc   python2    python2.7-config  python-config
idle  OgreXMLConverter  python  python2.7  python2-config    smtpd.py

```
how should i proceed? 
also, will this affect any python projects im working on?

---

### Post by forrestcupp on 2012-06-03
Did you try installing this?
```
sudo apt-get install python-wxversion
```

---

### Post by gandalf3 on 2012-06-03
i don't remember installing it, but it seems i did at some point..
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-wxversion is already the newest version.
python-wxversion set to manually installed.
The following package was automatically installed and is no longer required:
  simgear2.0.0
Use 'apt-get autoremove' to remove them.

```
but...
```
 playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 31, in <module>
    import wxversion
ImportError: No module named wxversion
/usr/share/playonlinux/playonlinux: line 97: python2.6: command not found

```
still the same..
thanks anyway

---

### Post by forrestcupp on 2012-06-03
What version of Ubuntu are you using? Are you using an unsupported version of Ubuntu?

Maybe try installing
```
sudo apt-get install python-wxgtk2.6
```
It seems like it's wanting python 2.6, and it looks like you only have 2.7 installed. I don't get it, though, because I never had it ask for 2.6, and I only have 2.8 installed.

---

### Post by gandalf3 on 2012-06-03
> **gandalf3 said:**
> hmm thanks..
but i have more than two "python" files in there.. (python, python2, and the config files, AND python2.7 with the 2.7 config)

```
/usr/local/bin$ ls
2to3  OgreMeshUpgrader  pydoc   python2    python2.7-config  python-config
idle  OgreXMLConverter  python  python2.7  python2-config    smtpd.py

```how should i proceed? 
also, will this affect any python projects im working on?

im not sure..
i don't see any "python 2.6" files there..
but i'm using Ubuntu 11.10

---

