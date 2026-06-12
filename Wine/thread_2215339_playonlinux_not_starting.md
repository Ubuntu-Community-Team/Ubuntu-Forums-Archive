---
title: "playonlinux not starting"
date: 2014-04-06
forum: Wine
---

### Post by Frank Haverkort on 2014-04-06
Hi, 
I've installed playonlinux using synaptic on Ubuntu 13.10, and the installation works fine (although I had to install the p7zip-full dependency by hand, as noted in several places around the internet). But when I try to start the application, no window appears. Trying to debug by starting playonlinux from the commandline gives this:
frank@thuis:~$ playonlinux
Looking for python... 2.7.5+ - selected
[main] Message: PlayOnLinux (4.2.2) is starting
[clean_tmp] Message: Cleaning temp directory
[Check_OpenGL] Message: 32bits direct rendering is enabled
[POL_System_CheckFS] Message: Checking filesystem for /home/frank/.PlayOnLinux/
[main] Message: Filesystem is compatible
[install_plugins] Message: Controleren plug-in: Capture...
[install_plugins] Message: Controleren plug-in: ScreenCap...
[install_plugins] Message: Controleren plug-in: PlayOnLinux Vault...
[maj_check] Message: List is up to date
[POL_SetupWindow_Init] Message: Creating new window for pid 20859

And then simply nothing happens... I've searched extensively on the internet, and have tried the reinstall solution proposed here: [http://ubuntuforums.org/showthread.php?t=2200483&highlight=playonlinux](http://ubuntuforums.org/showthread.php?t=2200483&highlight=playonlinux)

But nothing seems to help, so I'm really lost now. Hope you can help me out!

---

