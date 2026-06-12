---
title: "Wine can't find the executable? WTF ITS THERE!"
date: 2008-08-07
forum: Wine
---

### Post by m4lmsteen on 2008-08-07
i'm having a problem no matter what i do... ive checked the .exe is in the correct folder and wine can't find it... any ideas ?

Installing Application: scrhst version 5
Warning: MD5 sum not found
Warning: Can't find executable /home/jon/.wine-doors/apppacks/scrhst-5.6/resources/WindowsXP-Windows2000-Script56-KB917344-x86-enu.exe /Q, Assuming CD drive path
Detected CD drive /media/cdrom0
Traceback (most recent call last):
  File "/usr/share/wine-doors/src/queue.py", line 145, in Execute
    app_pack = ApplicationPack( INSTALL, pack, version, repo )
  File "/usr/share/wine-doors/src/application.py", line 136, in __init__
    self.InstallApplication()
  File "/usr/share/wine-doors/src/application.py", line 289, in InstallApplication
    self.status = wine.Execute( installer, installer_args )
  File "/usr/share/wine-doors/src/wine.py", line 188, in Execute
    exec_orig = re.sub("\\\\\\\\", "/", exec_orig)
UnboundLocalError: local variable 'exec_orig' referenced before assignment

---

