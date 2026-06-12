---
title: "Running Anjuta after installation?"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by _TK_ on 2006-07-30
Hi,

this is going to sound like a complete newbie question (well I suppose it is!) I recently installed Anjuta. I had a few problems compiling the download so I downloaded a pre compiled .deb of Anjuta. I installed this with no problems (at least it said it was installed).

This is all well and good but how do I actually run the program?!? Im sure I'm just being stupid about this all but it dosn't have a shortcut in the applications menu and theres nothing like a .exe I can use !

Thanks

_TK_

---

### Post by cocteau on 2006-07-30
Hi

In Accessories start the Alacarta Menu Editor and see if the anjuta shortcut has been disabled. It should install itself by default into programming/anjuta in the ubuntu menu. Otherwise you can create it. The command to start it is 'anjuta'.

You can always open a terminal and try and type the name of the program you wish to start to see if the command does what it is supposed to do. If you are unsure of the name of a command run:

sudo updatedb
...and wait as that may take a while, but when it us done type 'locate' followed by whatever you are looking for.

Hope that solves your problem.

---

### Post by _TK_ on 2006-07-30
Ok... So Ive gone into the Alacate menu editor, and theres no mention of Anjuta. So i create a new entry and just use the command "anjuta" when I click on the link nothing happens. When I hange the command to "Anjuta" the message says 'Failed to execute child process no suce file or folder'.

Then I try to locate the program by the above method and get a whole list of files and folders so something is installed!

I was just wondering whether or not the fact that I am running the 64 version of ubuntu or the fact that I didnt install the program correctly in the first place!

Thanks 

_TK_

---

### Post by Kilz on 2006-07-30
> **_TK_ said:**
> Ok... So Ive gone into the Alacate menu editor, and theres no mention of Anjuta. So i create a new entry and just use the command "anjuta" when I click on the link nothing happens. When I hange the command to "Anjuta" the message says 'Failed to execute child process no suce file or folder'.

Then I try to locate the program by the above method and get a whole list of files and folders so something is installed!

I was just wondering whether or not the fact that I am running the 64 version of ubuntu or the fact that I didnt install the program correctly in the first place!

Thanks 

_TK_

Open a terminal type in
```
anjuta
```
hit enter, what happens? copy/paste any errors in a post here.

---

### Post by _TK_ on 2006-07-30
When I type 'ajunta' this is what I get:

anjuta: error while loading shared libraries: libgnomeui-2.so.0: cannot open shared object file: No such file or directory

---

### Post by _TK_ on 2006-07-30
I guess I then have to get and install libgnomeui 2?!? is so does anyone know the easiest way to do that?!?

Thanks

_TK_

---

### Post by Kilz on 2006-07-30
> **_TK_ said:**
> When I type 'ajunta' this is what I get:

anjuta: error while loading shared libraries: libgnomeui-2.so.0: cannot open shared object file: No such file or directory

That file is part of the gnome interface. Are you running Kubuntu or Xubuntu by any chance? If you are running Ubuntu, where did you get the ajunta.deb file?

---

### Post by _TK_ on 2006-07-30
I am running Ubuntu and I got the deb files from : 
[http://www.ubuntuforums.org/showthread.php?t=203382](http://www.ubuntuforums.org/showthread.php?t=203382)

The deb that I managed to install was the :
anjuta-common_2.0.2-3ubuntu1_all.deb

---

### Post by kaamos on 2006-07-30
That is a unstable/developement version of anjuta. If you really want that, you should install all the debs created in that process. If not, just remove the packages you installed (you can find them in synaptic under state->installed (local or obsolete) (1)), apply the changes and use synaptic to install the package "anjuta".

(1) or something like that, my dapper is in finnish

---

### Post by _TK_ on 2006-07-30
The trouble with the debs that were created within the process is that they will only work under the i386 architecture and not the 64 bit version of ubuntu that Im using. OK they might but I dont know how to get them to sucessfully install or if they actually do work with ubuntu 64.

So i have now uninstalled the anjuta packages, does anyone know how I can install them and use them ?!?

Thanks

_TK_

---

### Post by Kilz on 2006-07-30
> **_TK_ said:**
> The trouble with the debs that were created within the process is that they will only work under the i386 architecture and not the 64 bit version of ubuntu that Im using. OK they might but I dont know how to get them to sucessfully install or if they actually do work with ubuntu 64.

So i have now uninstalled the anjuta packages, does anyone know how I can install them and use them ?!?

Thanks

_TK_

Well that makes a diffrence. I thought you were trying to install amd64 packages. You may be better off trying to compile the application as 64 bit. 
But if you would rather try and force the 32bit package you can [go here and search for libs]("http://packages.ubuntu.com/"), search the contents of a package for the mi9ssing libs. Download the i386 versionof the packages. Open a terminal and install this package
```
sudo apt-get install dpkg-dev
```to enable you to open the .deb files with the archive program. Inside of the extracted files you will find a data.tar.gz. Extract that. Inside you will find a usr folder, and a lib folder inside that. Copy the contents of the lib folder to /usr/lib32 on your computer. Then try the application again. You may have quite a few libs to install this way. But eventualy it will work.

---

### Post by cocteau on 2006-07-30
instead of installing from .deb package using synaptic manager and search for anjuta instead. It will take care of installing all your dependencies for you if it needs anything else.

If you can't find anjuta in synaptic change the repositories so you have both the universe and multiverse repositories enabled.

---

### Post by Kilz on 2006-07-30
> **cocteau said:**
> instead of installing from .deb package using synaptic manager and search for anjuta instead. It will take care of installing all your dependencies for you if it needs anything else.

If you can't find anjuta in synaptic change the repositories so you have both the universe and multiverse repositories enabled.

I dont know why I didnt look before. ](*,)  I just asumed he already did.

---

### Post by cocteau on 2006-07-30
and on another note to what you said previously. As far as I understand it anyway, linux doesn't use file name suffixes to identify executables. Executable is a file property instead, so there is no way to tell from a file name wether you may execute it or not. You can type 'ls -l' to see if it is, though.

Convention in linux also has it that most system binary files will be located in /usr/bin or /usr/local/bin, so when you do your locate command, files in one of those folders is a good guess for what to type to start your program.

---

### Post by _TK_ on 2006-07-31
Thanks for all your help!

To be honest with you ... I didnt know that I could do that :D ... well I do now!!!

Im happy to say that Unjuta is now installed and running and the next problem is learning how to use it!

Thanks again

_TK_

---

