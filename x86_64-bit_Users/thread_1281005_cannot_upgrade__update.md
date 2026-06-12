---
title: "cannot upgrade / update"
date: 2009-10-02
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2009-10-02
Hi guys,

When I want to update I get the following bug report / message

Traceback (most recent call last): File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run threading.Thread.run(self) File "/usr/lib/python2.6/threading.py", line 477, in run self.__target(*self.__args, **self.__kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 168, in wrapper func(*args, **kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 859, in doUpdateSystem if not self._commit_changes(): return False File "/usr/lib/packagekit/aptDBUSBackend.py", line 1704, in _commit_changes PackageKitInstallProgress(self, install_range)) File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 277, in commit res = self.installArchives(pm, installProgress) File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 252, in installArchives res = installProgress.run(pm) File "/usr/lib/python2.6/dist-packages/apt/progress.py", line 281, in run res = pm.DoInstall(self.writefd) SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2) 

I have tried to file a bug report but doesnt work for me

can someone help

Kind regards

Bloem

---

### Post by Bloemetjesgordijn on 2009-10-02
Solved it

In console when I entered sudo apt-get upgrade....I got weird errors referencing to a "statoverride file" 

Some googling found me: 

[http://ubuntuforums.org/showthread.php?t=329560](http://ubuntuforums.org/showthread.php?t=329560)

Which worked

* No to set my own thread as solved :P

---

