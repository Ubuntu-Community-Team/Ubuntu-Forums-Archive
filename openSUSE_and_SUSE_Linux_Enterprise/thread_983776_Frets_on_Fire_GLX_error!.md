---
title: "Frets on Fire GLX error!"
date: 2008-11-16
forum: openSUSE and SUSE Linux Enterprise
---

### Post by kelinu on 2008-11-16
Hi guys,

Problem.  Big Problem.  I'm running OpenSuse right now, and I installed Frets on Fire, but when I click its icon it does not startup.  It tried running it with terminal, here's what I got...
  >   File "/usr/games/fretsonfire", line 68, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/Video.py", line 69, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: Couldn't find matching GLX visual

And here's what I got when I ran it with sudo:
> Traceback (most recent call last):
  File "/usr/games/fretsonfire", line 68, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/Video.py", line 69, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: OpenGL not available

I have no idea what this is saying, I hope some of you Linux boffins will!

Thanks, Any help is much appreciated.

---

### Post by 67GTA on 2008-11-16
What source did you use to install it? I replied to your other thread about installing it. If you compile from source, you have to install any dependencies manually. If you installed from the repos, or one click install, then just try reinstalling. Do you have a 3D graphics card with the correct driver installed?

---

### Post by kelinu on 2008-11-17
I do have a 3d Graphics Card with proper drivers, I basically installed it from an rpm Package (did not compile it myself), and I have all the dependencies installed I check that...but doesn't the error message indicate anything at all? Is there some package I must install?

---

### Post by kelinu on 2008-11-17
bump

---

### Post by 67GTA on 2008-11-17
Did you install it from the Opensuse repos?

---

### Post by kelinu on 2008-11-17
no, it wasn't there, i found it here: [http://rpm.pbone.net/index.php3/stat/4/idpl/8338634/com/fretsonfire-1.2.512-6.1.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/8338634/com/fretsonfire-1.2.512-6.1.noarch.rpm.html)

I would be willing to compile, but I would need aa tutorial please...I also wanna know how to uninstall software that haas been copiled from source...

thanks for your interest btw mate

---

### Post by 67GTA on 2008-11-17
First I would uninstall it. Then use the instructions here to add the Opensuse Games repo [http://ubuntuforums.org/showthread.php?t=983233](http://ubuntuforums.org/showthread.php?t=983233) Then install Frets on Fire from the Opensuse Games repo. Some RPM packages(and some poorly packaged DEB packages) do not have dependency lists included. If not, the package manager won't know what else to pull in at the time of installation. Also, there are different versions of packages that may need dependencies/libs that are not the same version on your system. It is always best to install from your distros repos if possible. Un-installing something installed from source can be tricky. Look in the tarball you downloaded for a read me file, or uninstall script. If there is not one of these present, then you will have to find the files/libs that were installed and delete them manually. You might be able to search for the package name in the file system and track them down. What did you install from source?

---

### Post by RedDwarf on 2008-11-17
Frets on Fire is a python game... you don't need to compile it. But the game has lots of problems: [https://bugzilla.novell.com/show_bug.cgi?id=392750](https://bugzilla.novell.com/show_bug.cgi?id=392750). Up to where I know Debian/Ubuntu still have the same problems.
Some of the problems seem to be because of python 2.5 incompatibilities... and you don't want to downgrade to 2.4.

Even on Windows people says 1.2.512 is too buggy. And since the project looked like dead people started to use a fork: [http://code.google.com/p/fofix/](http://code.google.com/p/fofix/) (based on an older version of FoF)
Recently version 1.3.110 of the original Frets on Fire has been released. The sound problem is fixed, but there are still graphic glitches and you need to downgrade a file to see the menus.

The fork, based on an old version and more alive, is the thing that best works. But the latest stable version needs some svg vs png hacking... so I would wait to the next version that stops using svgs at all.

If the Ubuntu package works without problems add a comment to [https://bugzilla.novell.com/show_bug.cgi?id=392750](https://bugzilla.novell.com/show_bug.cgi?id=392750), but if doesn't... you will need to wait for upstream to fix the bugs.

---

### Post by kelinu on 2008-11-18
> **67GTA said:**
> First I would uninstall it. Then use the instructions here to add the Opensuse Games repo [http://ubuntuforums.org/showthread.php?t=983233](http://ubuntuforums.org/showthread.php?t=983233) Then install Frets on Fire from the Opensuse Games repo. Some RPM packages(and some poorly packaged DEB packages) do not have dependency lists included. If not, the package manager won't know what else to pull in at the time of installation. Also, there are different versions of packages that may need dependencies/libs that are not the same version on your system. It is always best to install from your distros repos if possible. Un-installing something installed from source can be tricky. Look in the tarball you downloaded for a read me file, or uninstall script. If there is not one of these present, then you will have to find the files/libs that were installed and delete them manually. You might be able to search for the package name in the file system and track them down. What did you install from source?

I did not install FoF from source, but from that package link I sent you. Hold on a bit let me add that repo...and how can I uninstall the curreeent installed FoF?

---

### Post by kelinu on 2008-11-18
> **67GTA said:**
> First I would uninstall it. Then use the instructions here to add the Opensuse Games repo [http://ubuntuforums.org/showthread.php?t=983233](http://ubuntuforums.org/showthread.php?t=983233) Then install Frets on Fire from the Opensuse Games repo. Some RPM packages(and some poorly packaged DEB packages) do not have dependency lists included. If not, the package manager won't know what else to pull in at the time of installation. Also, there are different versions of packages that may need dependencies/libs that are not the same version on your system. It is always best to install from your distros repos if possible. Un-installing something installed from source can be tricky. Look in the tarball you downloaded for a read me file, or uninstall script. If there is not one of these present, then you will have to find the files/libs that were installed and delete them manually. You might be able to search for the package name in the file system and track them down. What did you install from source?

Hey, I installed the game from repos and its still dont work...

---

### Post by 67GTA on 2008-11-18
I didn't realize there were that many problems with the package. I just assumed it was a dependency/version problem.

---

### Post by kelinu on 2008-11-19
thats ok...i can see we're kind of stuck here.  But thanks for your help anyways, I'm moving back to Ubuntu.

---

### Post by RedDwarf on 2008-11-19
> **kelinu said:**
> thats ok...i can see we're kind of stuck here.  But thanks for your help anyways, I'm moving back to Ubuntu.
You mean in Ubuntu works without a single problem?

Quoting myself
> If the Ubuntu package works without problems add a comment to [https://bugzilla.novell.com/show_bug.cgi?id=392750](https://bugzilla.novell.com/show_bug.cgi?id=392750)

---

### Post by kelinu on 2008-11-19
oh yea i didnt see that, yes in ubuntu it works except the menus lag, when playing the actual song its fine

---

### Post by RedDwarf on 2008-11-19
Well, your "Couldn't find matching GLX visual" problem to me it's clearly a graphic card driver problem. I would need your "glxinfo" output to believe otherwise.

About the game problems. The Ubuntu package seems identical to the openSUSE one, using the Ubuntu package on openSUSE I have the same graphic glitches. So... or you though the graphic glitches were "FX effects", or it's a 64 vs 32 bits problem (I'm on 64) or Ubuntu has some patch on pygame, pyopengl or something... and I'm not really so interested in the game to look in all of them.

---

### Post by kelinu on 2008-11-20
no, it cant be graphics card...it worked fine on Ubuntu!  my graphics card is a nvidea geforce 7300 LE...its good for fof

---

### Post by RedDwarf on 2008-11-20
> **kelinu said:**
> no, it cant be graphics card...it worked fine on Ubuntu!  my graphics card is a nvidea geforce 7300 LE...its good for fof
> **RedDwarf said:**
> your "Couldn't find matching GLX visual" problem to me it's clearly a graphic card **_driver_** problem.
I have a 7600GT, previously a 5200 and the game starts fine. The 1.1.324 version of the game even works without a single problem... latter versions were the ones that started giving problems (Debian/Ubuntu have heavily patched them to have something that works).

---

