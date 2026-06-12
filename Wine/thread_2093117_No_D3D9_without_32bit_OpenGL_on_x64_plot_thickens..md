---
title: "No D3D9 without 32bit OpenGL on x64 plot thickens. Mirrors don't have gnome-keyring??"
date: 2012-12-09
forum: Wine
---

### Post by NoCyberDom on 2012-12-09
This thread is an offshoot of another (ongoing) one and the issue has become a more general one of a missing lib package that can't be found online. For the specifics you can see my original thread but what it all boils down to is the info in this thread. I have put a link to the thread with all the details at the bottom of this post but I believe this one has all the info needed to understand the issue.

Short version:

If you are aware of the issues trying to run games in wine that use 32 bit OpenGL with a 64 bit version of Ubuntu then you have probably seen or read about this result in the terminal window:

[I][COLOR=DarkOrange]p11-kit: couldn't load module:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open  shared object file:[/COLOR] [COLOR=Red]No such file or directory[/COLOR]
Direct3D9 is not available without OpenGL.
Direct3D9 is not available without OpenGL.
Direct3D9 is not available without OpenGL.[/I]

The trail of breadcrumbs I followed all day caused me to again go back to this post:
[http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so](http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so)

When I get to step 2, which is *"*[COLOR=SeaGreen][COLOR=Black]*sudo getlibs -p gnome-keyring:i386",* everything went sideways. I color coded  the terminal OP here to make it easy to see what happened:[/COLOR][/COLOR]

me@mymachine:~$ [COLOR=SeaGreen]sudo getlibs -p gnome-keyring:i386[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=SeaGreen]ia32-libs is already the newest version.[/COLOR]
The following packages were automatically installed and are no longer required:
  wine-mono0.0.4 wine-gecko1.7 wine-gecko1.7:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
[COLOR=SeaGreen]The following i386 packages will be installed: gnome-keyring:i386
Continue [Y/n]? y[/COLOR]
Downloading ...
[COLOR=Red]Failed to download file [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb)[/COLOR]
The mirrors do not have the requested file or there is no internet connection
No packages to install

Le Sigh...

 My original thread, with details, is at ubuntuforums.org/showthread.php?t=2092956

As always, any constructive help is appreciated.

---

### Post by NoCyberDom on 2012-12-21
This remains unsolved but I found a workaround... I installed 12.04 32 bit in another partition and ran the program off that.

---

