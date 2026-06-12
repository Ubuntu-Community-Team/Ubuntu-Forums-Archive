---
title: "Play On Linux Will Not Start"
date: 2012-08-12
forum: Wine
---

### Post by plzdontkillme11 on 2012-08-12
Hello,

The title explains all. Play on Linux will not start; not even a dialogue box or an error comes up. When I run it through the terminal, this is what happens:

```

Traceback (most recent call last):
  File "mainwindow.py", line 745, in <module>
    app = PlayOnLinuxApp(redirect=False)
  File "/usr/lib/python2.7/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.7/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "mainwindow.py", line 689, in OnInit
    self.frame = MainWindow(None, -1, os.environ["APPLICATION_TITLE"])
  File "mainwindow.py", line 274, in __init__
    self.jauge_update.Pulse()
AttributeError: 'Gauge' object has no attribute 'Pulse'
Exception TypeError: 'join() takes exactly 2 arguments (1 given)' in <module 'threading' from '/usr/lib/python2.7/threading.pyc'> ignored
[install_plugins] Message: Checking plugin: Offline PlayOnLinux...
[install_plugins] Message: Checking plugin: Capture...
[install_plugins] Message: Checking plugin: Transgaming Cedega...
[install_plugins] Message: Checking plugin: Wine Import...
/usr/share/playonlinux/playonlinux: line 96: python2.6: command not found
vignesh@VigneshUbuntu:~$ [install_plugins] Message: Checking plugin: Wine Look...
[install_plugins] Message: Checking plugin: Screen Capture...
[install_plugins] Message: Checking plugin: PlayOnLinux Vault...

```

It gets stuck at "Checking plugin: PlayOnLinux Vault..."

I am running Ubuntu 12.04 using Gnome3. I have an Acer Aspire 3820T-6480. 

Thanks in advance.

---

### Post by plzdontkillme11 on 2012-08-12
Well, thanks anyway. I've been working on finding a solution for a while now and I'm frankly sick of it. I'll just go back to windows.

---

### Post by Marric on 2012-08-13
Please check that you have the latest version of PlayOnLinux (4.1.6)

Paste those lines in your Terminal
```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get upgrade
```I read about some python related issues, so if the above is not working then try it with the latest development version```
git clone https://github.com/PlayOnLinux/POL-POM-4

```To use it
```
cd ~/POL-POM-4/
playonlinux
```
Alternatively use Wine.

PS:  Seriously dude, don't go back to winblows

---

### Post by plzdontkillme11 on 2012-08-13
Hey,

Thanks for the reply; it's a good thing I checked back on this, haha. I'll try out your idea sometime tomorrow.

---

### Post by plzdontkillme11 on 2012-08-13
Wow, apparently updating it worked. I actually manually uninstalled and installed the newest version, but I must have missed something. I really appreciate the help; have a good day!

---

