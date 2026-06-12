---
title: "Newbe Question About Installing Wine 1.0.1."
date: 2017-06-30
forum: Wine
---

### Post by cjreynolds on 2017-06-30
I am currently using Wine 1.7.1. I am trying to install e-Sword using this post:
[https://ubuntuforums.org/showthread.php?t=404042&highlight=e-sword](https://ubuntuforums.org/showthread.php?t=404042&highlight=e-sword)
The installation failed. According to the above post, newer versions of Wine have trouble with the e-Sword installer, and it recommends ver. 1.0.1. I downloaded 1.0.1, and have 2 questions:

1. Must I remove ver. 1.7.1 before installing 1.0.1?

2. The tar.gz package I downloaded doesn't seem to have an installer exe, so I'm assuming it needs to be installed from the terminal. It's been years since I used Linux - How do I direct the install command so it can find the 1.0.1 directories? I tried changing directories to Downloads/Wine 1.0.1/wine-1.0.1 (where I extracted the files to), but I still get "Unable to locate package wine-1.0.1". Is there a location I should move the build files to?

Thanks for your patience,

joe

---

### Post by monkeybrain20122 on 2017-06-30
Use Playonlinux, it  is exactly what you need, it allows you to use different versions of wine for different apps by creating separate wine prefixes. It is in the repo.

In playonlinux's main window, choose Tools > manage wine versions, pick the version of wine you want, POL will download and install it for you (may take a while) then click "Install" (under +) You can choose the program to install, if your program is not listed, click "install an unlisted program" at the bottom, then it will ask you to choose the version of wine (click "use a different version of wine" then it will show you the list of wine versions installed from the first step) and the path to your program's installer (the exe file) then just let it run.

You can leave your system's wine alone

> 
The tar.gz package I downloaded doesn't seem to have an installer exe
.exe is a Windows specific extension, you don't install things in Linux with .exe files. Wine is a compatibility layer that allows you to install and run some Windows programs on Linux (e.g ".exe installers") by creating a faked Windows environment to fool the program. But Wine itself is not a Windows program, so no .exe installer. The tar ball is the source codes that need to be compiled. If you are a novice better avoid installing from source.

---

### Post by cjreynolds on 2017-07-06
Thanks! The 1.0.1 installation worked flawlessly from PlayOnLinux. But  how do I use that version to install a program (ie: install executable  for e-Sword)? When I do > wine --version in terminal, it  still says 1.7.1 - Please excuse my ignorance - it's been a VERY long  time since I used Linux...

---

### Post by CatKiller on 2017-07-06
> **cjreynolds said:**
> Thanks! The 1.0.1 installation worked flawlessly from PlayOnLinux. But  how do I use that version to install a program (ie: install executable  for e-Sword)? When I do  in terminal, it  still says 1.7.1 - Please excuse my ignorance - it's been a VERY long  time since I used Linux...

> **monkeybrain20122 said:**
> In playonlinux's main window, choose Tools > manage wine versions, pick the version of wine you want, POL will download and install it for you (may take a while) then click "Install" (under +) You can choose the program to install, if your program is not listed, click "install an unlisted program" at the bottom, then it will ask you to choose the version of wine (click "use a different version of wine" then it will show you the list of wine versions installed from the first step) and the path to your program's installer (the exe file) then just let it run.

You can leave your system's wine alone

It's your system's wine that's at 1.7.1. You use 1.0.1 with POL as monkeybrain described.

---

### Post by sccman on 2017-07-07
> **cjreynolds said:**
> Thanks! The 1.0.1 installation worked flawlessly from PlayOnLinux. But how do I use that version to install a program (ie: install executable for e-Sword)? When I do in terminal, it still says 1.7.1 - Please excuse my ignorance - it's been a VERY long time since I used Linux...

As CatKiller says, you'll have two different versions of Wine installed. The 1.7.1 is the one you installed on the system outside of PlayOnLinux, and the 1.0.1 is the one you installed inside of PlayOnLinux.

PlayOnLinux lets you install multiple Wine versions so you can run programs like e-Sword on a Wine version that everyone knows will work. It keeps multiple versions of Wine installed and keeps your programs in the right Wine version's virtual drive.

Try CatKiller's suggestion first. If not, I know PlayOnLinux allows you to automatically detect versions of Wine that the community knows work. It may find another version for you if 1.0.1 doesn't work.

---

