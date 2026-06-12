---
title: "Installing Blender"
date: 2005-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Irony on 2005-07-06
I've downloaded Blender from [http://blender3d.com/cms/Blender.31.0.html](http://blender3d.com/cms/Blender.31.0.html) but on putting the following in the terminal;

*name@ubuntu:~$ /home/name/BlenderFoundation/blender/blender * 

I get the following; 

*/home/name/BlenderFoundation/blender/blender: error while loading shared libraries: libSDL- 1.2.so.0: cannot open shared object file: No such file or directory*

Is this libSDL file in synaptic because I can't find the exact same name there.

My second question is how do I actually sign in as root. I should point out that I've only just installed ubuntu 64 as a dual boot with XP on my computer so linux stuff is very new to me.

---

### Post by FluffyElmo on 2005-07-06
I installed Blender with Synaptic, you may have to enable the Universe/Multiverse repoitories in Synaptic before you see it. That might be the easiest way, but libsdl is in package 'sdl' I think if that's all you need.

By default, Ubuntu doesn't have a root login for security reasons and you use *sudo* to run individual commands as root. If you really want to login as root you can find instructions at [http://amd64.ubuntuguide.org/](http://amd64.ubuntuguide.org/) 

Hope this is of some help...Welcome to Ubuntu!

---

### Post by Irony on 2005-07-07
How do you install Blender with Synaptic - I can't see it in Synaptic.

Also there is a libsdl1.2-dev package in Synaptic is this the one to install?

---

### Post by FluffyElmo on 2005-07-07
First, my best attempt at detailed install instructions...

To install blender via Synaptic open the *Settings->Repositories* dialog from the menu. In the dialog click the *Add* button, check the '*Community Maintained (Universe)*' box and the '*Non-free (Multiverse)*' one as well. Click *OK*. Click *OK* again to exit the repositories dialog box. 

Now, in the main Synaptic click the *Reload* button and wait until it finishes. When it's done, click the *Search* button and search for '*blender*'. Right click on '*blender*' and select *'Mark for Installation*'. You'll usually want to select any '*Mark Recommended for Installation*' and '*Mark Suggested for Installation*' packages on the right click menu as well. 

Click the *Apply* button to install. I think Blender will appear under the *Applications->Graphics *menu, for some other packages you may have to run them from the command line. 

Second, what the preceeding does is give you access to two new program repositories. The '*Universe*' repository contains programs which are not guaranteed to be stable with Ubuntu. The '*Multiverse*' repository contains software not guaranteed to be stable, which is also not 100% open source due to patent or copyright (for instance freeware/shareware) issues. 

Third, my bad...the package I have installed for sdl is '*libsdl1.2-debian*', the version number might vary on your install, choose what is available. Generally, packages ending in '-dev' are needed for compiling software, the non-'-dev' version is for running precompiled software that require a library. 

Whew, I rambled more than usual here...hope something I've said helps. Let me know how things go...

---

### Post by Irony on 2005-07-08
Thanks FluffyElmo, its taken me about a week but your answer has allowed me to successfully download and install Blender 2.36.

I also now have an idea of how Synaptic works. I'm guessing that Synaptic downloads from an ubuntu 'repository' - rather than the Blender site itself.

Blender somewhat strangely when it is running cannot be resized to allow access to other programs, in other words it fills the screen so that the ubuntu menu bars aren't visible - this means to get to them I have to quit out of it, is that what happens in your version?

Also where is Blender actually installed, is it in the filesystem?

---

### Post by FluffyElmo on 2005-07-08
Glad I could help!

You're correct about Syanptic, it downloads software from servers maintained by the Ubuntu community and installs it on your local machine. It also does it's best to grab any dependencies and resolve conflicts at the same time, it's a very handy tool. 

Sometimes you'll need to go outside the repositories to get a program that isn't there, or the most up to date version, but if you browse around you'll find a pretty extensive collection of software is just a few clicks away. And you can find out where the files for an installed program are (among other things) by right clicking on it in Synaptic and selecting '*Properties*'.

I remember Blender had it's own custom interface. But I think you can still switch between your vurtual desktops using the keyboard. *<Ctrl><Alt>Right Arrow Key *and *<Ctrl><Alt>Left Arrow Key* should cycle between them. And like in Windows, *<Alt><Tab>* will switch between running programs on your current desktop.

Next, if you have a recent video card you might want to install the latest drivers for it to boost performance (especially 3D performance). Just search the forums for instructions...though you may want to enjoy what you've accomplished so far and try that later :)

Have Fun!

---

### Post by Irony on 2005-07-10
Thanks again FluffyElmo, those key strokes do the trick. I think I may look at the drivers for my card as it quite new and fast (ATI Technologies, Inc. Radeon X800 Pro (R420 JI)).

---

### Post by ubuntp on 2005-07-14
I tried to install blender today, but all i get is that blender depends on libglu1 or libglu1-mesa, which cannot be installed. Manually trying to install them tells me that they conflict with libglu1-xorg  :-k

---

### Post by FluffyElmo on 2005-07-14
Are you using Breezy by any chance?

[http://ubuntuforums.org/showthread.php?t=36799&highlight=libglu](http://ubuntuforums.org/showthread.php?t=36799&highlight=libglu)
[http://ubuntuforums.org/showthread.php?t=39675&highlight=libglu](http://ubuntuforums.org/showthread.php?t=39675&highlight=libglu)

---

### Post by ubuntp on 2005-07-14
I am, so is there no way? :(

---

### Post by FluffyElmo on 2005-07-14
Not that I'm aware of, I'm using Breezy myself and couldn't re-install Blender. Breezy being Breezy though, it may be fixed in an update in the near future. 

In fact, there is a bug report for this problem which has more info and status...
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11187](https://bugzilla.ubuntu.com/show_bug.cgi?id=11187)

Of course you could always try installing it into a chroot. I was forced to install a 32bit Hoary chroot in my Breezy install for just this sort of problem.
[http://ubuntuforums.org/showpost.php?p=119679&postcount=1](http://ubuntuforums.org/showpost.php?p=119679&postcount=1)

---

