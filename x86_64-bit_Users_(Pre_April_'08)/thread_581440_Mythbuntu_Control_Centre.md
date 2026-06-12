---
title: "Mythbuntu Control Centre"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by UKCamaroSS on 2007-10-19
Hi,

I've tried to install Mythbuntu on Ubuntu 7.10 onto my AMD 64, however when I click on "Systems, Administration, Mythbuntu Control Center" nothing happens.

I ran:

 sudo /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre

and this is what I got back:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre", line 46, in <module>
    script = ControlCentre()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 173, in __init__
    self.revert_gui()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 1075, in revert_gui
    self.query_system_state()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 758, in query_system_state
    result = self.query_installed(item)
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 585, in query_installed
    return self.cache[package].CurrentVer
KeyError: 'w64codecs'

I'm very new to Linux, so what does all this mean? Is this a bug in the 64 version of 7.10?
Thanks,

---

### Post by DSK on 2007-10-19
u dont have the codecs you need.

Enable either to your sources list and update 

[http://ubuntuforums.org/showthread.php?t=579782](http://ubuntuforums.org/showthread.php?t=579782)  

here is the official site how too:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

