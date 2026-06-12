---
title: "Problems installing Makehuman 0.9"
date: 2007-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Smitje on 2007-01-07
Hi all

I have found a lot of helpfull stuff here so manny thanks for that!

Sorry for the long post but I'm trying to make the picture as clear as I can, so I included all the steps. I have run into some trouble trying to install Makehuman 0.9. on my core 2 system, under ubuntu edgy eft AMD 64. 

I downloaded the files from sourceforge:
[http://sourceforge.net/project/showfiles.php?group_id=150931&package_id=211091&release_id=463093](http://sourceforge.net/project/showfiles.php?group_id=150931&package_id=211091&release_id=463093)
took the 3 regular ones (those without -dev-)

On my first attempt to install i ran into an error saying something to the effect:
 package architecture (i386) does not match system (amd64)

as suggested by  Hendrik van den Boogaard in the sticky at the top of this forum I used:

```
~/install$ sudo dpkg -i --force-architecture makehuman_0.9-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package makehuman.
(Reading database ... 89613 files and directories currently installed.)
Unpacking makehuman (from makehuman_0.9-1_i386.deb) ...
dpkg: dependency problems prevent configuration of makehuman:
 makehuman depends on mhgui1 (>= 0.1); however:
  Package mhgui1 is not installed.
dpkg: error processing makehuman (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 makehuman
```

so I installed mhgui1 only to find a simmilar problem:

```
~/install/makehuman$ sudo dpkg -i --force-architecture mhgui1_0.1-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mhgui1.
(Reading database ... 97191 files and directories currently installed.)
Unpacking mhgui1 (from mhgui1_0.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of mhgui1:
 mhgui1 depends on animorph1 (>= 0.2); however:
  Package animorph1 is not installed.
dpkg: error processing mhgui1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mhgui1
```

so I installed animorph1
and then it all goes smoothly for a while:

```
:~/install/makehuman$ sudo dpkg -i --force-architecture animorph1_0.2-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package animorph1.
(Reading database ... 97197 files and directories currently installed.)
Unpacking animorph1 (from animorph1_0.2-1_i386.deb) ...
Setting up animorph1 (0.2-1) ...

~/install/makehuman$ sudo dpkg -i --force-architecture mhgui1_0.1-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 97203 files and directories currently installed.)
Preparing to replace mhgui1 0.1-1 (using mhgui1_0.1-1_i386.deb) ...
Unpacking replacement mhgui1 ...
Setting up mhgui1 (0.1-1) ...

~/install/makehuman$ sudo dpkg -i --force-architecture makehuman_0.9-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 97203 files and directories currently installed.)
Preparing to replace makehuman 0.9-1 (using makehuman_0.9-1_i386.deb) ...
Unpacking replacement makehuman ...
Setting up makehuman (0.9-1) ...
```

That all sounded good, but when I try to execute I get :

```
~makehuman
makehuman: error while loading shared libraries: libmhgui.so.0: cannot open shared object file: No such file or directory
```

after a search I found the file in the regular usr/lib
So I copyed it to usr/lib32
and now I get:

```
~makehuman
makehuman: error while loading shared libraries: libanimorph.so.0: cannot open shared object file: No such file or directory
```

So I copy that too
and then:

```
~makehuman
makehuman: error while loading shared libraries: libglut.so.3: cannot open shared object file: No such file or directory
```

So I copy that too.
But that doesn't help:

```
~makehuman
makehuman: error while loading shared libraries: libglut.so.3: wrong ELF class: ELFCLASS64
```

 this last librarry apearantly is not a part of makehuman but of a "64 part" of something else.
does annyone see a way around this?
I'm dead stuck, and already a bit out of my league as it is, so any ideas are welcome. 
(exept 'recompile it' I just started on ubuntu and that would be a big step too far for me atm. To attemt that I would need step by step instructions)

Manny thanks,
Smitje

---

### Post by Unterseeboot_234 on 2007-01-08
Thanks for your post! I was totally unaware about an approximation for Poser. I was able to build the software. I had to Synaptic one library onto my machine. I do have deb of the three packages built for 64-bit architecture. The program ran. I have yet to play with it. I'm in the middle of a java project. There is already a Ubuntu deb for the i386 crowd, ready to download.

If you want to build...

I downloaded the source (any platform it says).

1. I have a fast internet connection. That helps.
2. I have **build essential** and several libraries already in my machine including **checkinstall**, which makes the debs.
3. At first I tried to build MakeHuman, that's when it wanted either a link to or the installed animorph. MakeHuman also wanted GLUT or FREEGLUT.
4. I Add/Remove Packages .. Advanced search for GLUT, because my ubuntu already has the lib freeglut3, and for no other reason than I like the name, I installed the freeglut3-dev instead of glut3-dev. That was the only dependancy.
5. Closed Synaptic, so the debs could install later on.
6. sudo ./configure inside the folder for animorph, then sudo make, then sudo checkinstall
7. same for mhgui
8. same for makehuman
9. ALT-F2 .. typed in makeHuman, it RUNS!!!!

If I can build it, so can you. If you have AMD64, I've got the debs.

=======
Played with the software a little bit. Loads fast. Deceptive simple interface.
makeHuman does a quick humanoid model. I look forward to when they can add clothes, hair and animate -- especially the face. I have an add-on for Poser that reads the wav file and moves the lips, eyes and face muscles on a Poser model. To render out in makeHuman takes a package called AQSIS. I tried to build that, no go, their source code build is based upon the Intel duo core running WIN C libraries. Ubuntu already has the binaries to download in Synaptic for this rendering package. Installed it and makeHuman will render out a .tif. You are better off, however IMHO, exporting the model out and using Blender, or equivalent. makeHuman, using AQSIS as a plug-in, only has one camera and one light. You get a tiny little figure in a huge black window.

---

### Post by Smitje on 2007-01-08
Thanks so much for your reply! 
ATM I keep switching to W#nd##s for makehuman and then to ubuntu for Blender and it is a pain.

If you are willing to drag me through the process I will try the build, but I warned you I am a total NOOB at this. so I have some questions below

> **Unterseeboot_234 said:**
> 
If you want to build...

I downloaded the source (any platform it says).

1. I have a fast internet connection. That helps.
2. I have **build essential** and several libraries already in my machine including **checkinstall**, which makes the debs.
3. At first I tried to build MakeHuman, that's when it wanted either a link to or the installed animorph. MakeHuman also wanted GLUT or FREEGLUT.
4. I Add/Remove Packages .. Advanced search for GLUT, because my ubuntu already has the lib freeglut3, and for no other reason than I like the name, I installed the freeglut3-dev instead of glut3-dev. That was the only dependancy.
5. Closed Synaptic, so the debs could install later on.
6. sudo ./configure inside the folder for animorph, then sudo make, then sudo checkinstall
7. same for mhgui
8. same for makehuman
9. ALT-F2 .. typed in makeHuman, it RUNS!!!!

If I can build it, so can you. If you have AMD64, I've got the debs.


1. I have an ok internet connection, no problem, I have the 3 tar.gz files in a directory
2. Installed **build essential** and **checkinstall** using synaptic, no problem.
? do I need anything else?
3. 4. I think this is related to **libglut.so.3** When I tried to execute makehuman I got:
```
~makehuman
makehuman: error while loading shared libraries: libglut.so.3: cannot open shared object file: No such file or
``` 

I found **libglut.so.3** in the usr/lib directory and copyed to the usr/lib32 directory. but then I got:

```
directory~makehuman
makehuman: error while loading shared libraries: libglut.so.3: wrong ELF class: ELFCLASS64
```

So my guess is glut is alleady on my machine in the AMD64 version, and that should be ok for what were doing right?

5. Why what did it do wrong ;)
6. 7. 8. I need a bit more help here, 
should the files be in a specific place?
what exact commands should I unleach on which files? (and do I need any extra optiona etc.?)
I tried some variations but none that did anything.
9. sounds straightforward enough.

Ill need to learn how to do this annyway, so I realy apreciate any help.
Otherwise is there a way I could use your debs?

Cheers
Smitje

---

### Post by Azakus on 2007-01-08
Try installing linux32. It will fool makehuman into thinking it is running on a 32 bit platform
then run the command with linux32 in front of it.
```
sudo aptitude install linux32
```

---

### Post by Smitje on 2007-01-08
Thanks Azakus for the hint.

Unfortunately no joy:

```
~sudo aptitude install linux32
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

~ linux32 makehuman
makehuman: error while loading shared libraries: libglut.so.3: cannot open shared object file: No such file or directory
```

Cheers, Smitje

---

### Post by Unterseeboot_234 on 2007-01-09
So, when you make your own software you use the libraries that have **-dev **on the end. When I did my Advanced search in Synaptic, I saw I did already have the library libglut BUT to build software the -dev libraries have to be there. It seems they have much more code. Makes sense, the libraries without the -dev have been optimized. I encourage you to keep trying. 

I'm trying to keep my machine all 64-bit and thus far, it has happened (except for 32-bit swiftfox and the java plug-in). Blender renders so-o-o-o much faster in 64 bit.

Also, I found I can Export makeHuman work as a .wavefront object and Blender has no problem importing the humanoid object with the materials (the skin).

AFTER you get your makeHuman going...

If you use Blender in ubuntu Drake, make a note. Start Blender from a terminal by typing **blender**. Look back in the terminal after Blender loads. If you have the an error "could not find library libtiff" then you need to install from Synaptic that library, libtiff and not the libtiff-dev. Opening Blender in the Terminal is how you code Blender with Python and find runtime execution errors. Also, without the libtiff, models with tiff textures applied will not import into Blender.

It is possible to start ubuntu Blender from the menus or from the terminal. Blender needs the terminal which comes up "automatically" in Windoze. Switch between the Terminal and Blender with the buttons along the bottom toolbar.

---

### Post by Smitje on 2007-01-09
Hi Unterseeboot_234, thanks for sticking with me.

I am however still stuck. 

it took me a while to figure out the tar bit but eventually everything ended up "untared" into its own directory.
**6. sudo ./configure inside the folder for animorph, then sudo make, then sudo checkinstall**
this all whent fine, so I go on to mhgui

But on ./configute I get:
```
...a lot of checking...
checking for FreeGLUT library... no
checking for GLUT library... no

***************************************************
* Abort!                                          *
* You need support for FREEGLUT or GLUT in mhgui! *
***************************************************
~/install/makehuman/mhgui-0.1$ 
```

I had allready installed the libglut-dev package plus dependancies with synaptic, do I need something else?

cheers,
Smitje

---

### Post by Unterseeboot_234 on 2007-01-09
The GLUTs are OpenGL libraries. I assume you have OpenGL graphics on your video. I went into my Synaptic. This is what I think...

libglut is something else. I think it is the library to connect custom software to OpenGL. (Mind you, I'm as much a Noob as you are).

freeglut3 was already installed when I started this build project.
freeglut3-dev was what I checked to install.

From there I got past the GUI module. Incidentially, each successfull checkinstall installs the module, thus when we get to MakeHuman it finds the module.

At this poiint, I forget if we need QT. If so, that would be the libqt3-mt. (But DON'T install it yet, until after the GUI and if MakeHuman fails to build). None of my qt libraries-dev is selected as installed into my system. QT is a C++ development to program widgets or to use the library to connect widgets to libraries. Widgets are the buttons, menus, etc. that sort of thing. I can't remember if MakeHuman is GTK (gNome) or not, you already have GNOME, from your ubuntu install).

Please try that, the freeglut and freeglut-dev. Let me know. MakeHuman is one of the easiest, cleanest builds I ever did. If you pull this one off, then, you'll really feel like a 5-bean ubuntu user!

Me? I can make sound with 9 different packages but I cannot get the one package I want to make one single peep???

And, hey, I don't mind helping your one bit. We're teaching others and that's how I installed Xara, by reading these posts.

---

### Post by Smitje on 2007-01-09
Thanks Unterseeboot_234

I reinstalled freeglut3 and freeglut3-dev, and added freeglut3-dev-deb just to be sure but I still get the same error:

```
~ ./configure
...
...a lot of checking...
...
checking for FreeGLUT library... no
checking for GLUT library... no

***************************************************
* Abort!                                          *
* You need support for FREEGLUT or GLUT in mhgui! *
***************************************************
```

Is there a way to tell ./configure where to look?
or maybe to check where freeglut is myself?

I'm enjoying this in a funny masochistic kind of way... its annoying and thrilling at the same time.
I guess I'm hooked 

Cheers,
Smitje

---

### Post by Azakus on 2007-01-09
Maybe you should have Unterseeboot_234 post his .debs for you. It might be worth a try to see if they work on your system.

---

### Post by Unterseeboot_234 on 2007-01-10
HMMMMM. Well I don't see how you installed freeglut3-dev.deb. Maybe you put it into the folder you're trying to build?

Let's try this. Attached is the 2nd module you build as a .deb. The GUI. 

Download, put it into the folder for mhgui-0.1. Using the mouse, go into that folder and double-click the deb. Should install.

IF you still have problems with the next module, I will gladly post the other two. MakeHuman is 36-meg as a deb. Not sure what ubuntu forums attachment size limit is. (I just saw a deb has to stay under 97 meg, this GUI deb is 61 :-k ). MakeHuman.deb is 36meg.

But, this is where I think the problem lies. I had a similar situation with installing Xara. You CAN double click the icon that makes a .tar.gz. It upacks the archive alright, but less obvious it sets all the file permissions rr-ww-ww stuff in the wrong configurations. When it comes to source code, we have to think like Mr. RedHat and Mrs. Suse. From a terminal, we type:

```
user@user-desktop~$ tar -xvvjf xaralx0.7_rev1764.tar.bz2
```
or
even better, you made a folder at the User and you cd to point Terminal inside it
```
user@user-desktop/media/ieee1394disk/linux_softwareDnload/makeHuman$  **tar -xvvf mhgui-0.1.tar.gz**
```

the -x is "extract", -v is for "verbose", -j is for "bzip2" (my guess is they ran out of letters) and -f is for "file". Having two v's just makes tar more verbose. If you want even more options, type **tar --help** at the Terminal.

Then, of course, after unpacking, you would cd into the newly created folder to point Terminal and start off ./configure.
=============
Good luck. By hook or crook, we'll have you making naked, *(why didn't they include the genitillia? MakeHuman IS Itallian. Michelangelo would be appalled at his countrymen)* bald-headed people with plastic looking skin. I would like to see the MakeHuman team finish their muscle modules, hair, clothes and offer a face animation window. Skin-blotch palletes for 3D brushes would help, but only over in the Blender side.

========== edited
I did have a similar experience on this. If I didn't **sudo** ./configure, **sudo** make, **sudo** checkinstall, then the Python script would tell me I needed support for xxxlib. And, from other goings on in Linux, I've learned it is best to have Terminal pointed with cd. I've learned to be very cautious when I commandeer Linux as "Mr. Overlord, the super root user" sudo -s -H <password>. Stay in Root mode and start banging around in your files will royally trash your system. Close any Terminal with Root going as soon as you're done. sudo is useful in more ways than one.

-----
I hope you tried all this from a folder inside your User Window. DON'T go into the File System with this stuff. Usually, the .DEB knows what to do. Sometimes, and I haven't done it yet, we have to set a variable in the ./configure command. Using my .deb should work. If it does, you only lose the ability to delete it gracefully with Synaptic should that occasion occur.

---

### Post by Smitje on 2007-01-10
Hi Unterseeboot_234

thanks for the deb it seems to install without any problems.

I tried to ./configure in the makehuman-0.9 dir but I get the same error again.
If you could post the deb that would be lovely

btw, I have been using makehuman0.9 in windows and there the genitalia are not only included but you can ajust them as well. As for the hair there is a script for that on thier website, but I'm not sure how it works. The plans show hair/clothes/expresions in the future, lets hope the future comes soon.

Cheers,
Smitje

---

### Post by DarkN00b on 2007-01-10
I installed the .deb packages with no problems. They _must_ be installed in this order:

1.  animorph1_0.2-1_i386.deb
2.  mhgui1_0.1-1_i386.deb
3.  makehuman_0.9-1_i386.deb

This is for the i386, 32bit version of Edgy.

Going to test now...

EDIT: It installed just fine, starts up quickly and runs smoothly. Now to install blender for rendering. :) The controls are very intuitive and it runs quite well on my i810 graphics chipset. I only have 256 megs of memory in this machine but still this program works just great.

[IMG]http://img.photobucket.com/albums/v191/DarkN00b/Caps/Makehuman1.png[/IMG]

---

### Post by Unterseeboot_234 on 2007-01-10
Cool, love your desktop, DarkNoob. We were doing this in 64-bit. I'd upload the remaining .debs for AMD64 but Europe seems offline to the www at the moment. I can only upload/download to America???? That is a new one on me :confused:

---

### Post by Smitje on 2007-01-13
Hi Again 

:( 

After installing your files makehuman runs ok, exept when I try to export a .obj file I get:

```
makehuman
ObjExporter::exportFile() : Trying to save file '/makehuman/myobjs/tst6'
terminate called after throwing an instance of 'std::out_of_range'
  what():  basic_string::erase
Aborted (core dumped)

```

:( that's no good.

What would you advise, should I remove everything and try again, there may still be parts of the 32 version on my system somewhere? or is there something I'm missing. I used dpkg -i ..... to install your deb files (I tried installing all three)

Cheers Smitje

---

### Post by Unterseeboot_234 on 2007-01-13
Found a online file storage to upload. If anyone is running AMD-64, you are welcome to download and try these debs. If you are into 3D modeling, I would recommend this software. MakeHuman has an equivalent in the Windows world called Poser.

There are three modules. You have to make MakeHuman in three installs...
1. The libraries
2. The GUI
3. The application

**1. ** [makeHumanLibs.deb]("http://www.divshare.com/download/44208-96")
>or copy and past this following text into your browswer navigator
>
> [http://www.divshare.com/download/44208-961](http://www.divshare.com/download/44208-961)
+++++++++++++++++++++++++++++++++

**2. ** [makeHumanGui.deb]("http://www.divshare.com/download/44211-9f7")
>or copy and paste this followinig text into your browser navigator
>
> [http://www.divshare.com/download/44211-9f7](http://www.divshare.com/download/44211-9f7)
+++++++++++++++++++++++++++++++++

**3.**  [makeHuman.deb]("http://www.divshare.com/download/44248-40d")
>or copy and paste this following text into your browser navigator
>
> [http://www.divshare.com/download/44248-40d](http://www.divshare.com/download/44248-40d)
====================================

Wished it was a FTP (http is s-l-o-w to upload, anyway, real slow). You might post on this thread if you got MakeHuman with these debs to work for you.

Regards to all the Forum.

---

### Post by Azakus on 2007-01-13
You know, you can attach .deb files into the forum. It's that option labeled "Attach Files" underneath the area where you create a post.

---

### Post by Unterseeboot_234 on 2007-01-14
Believe me, I tried. There is a size limit to what files will attach to a forum post. A file of type .deb is limited to .97 meg. MakeHuman, part 3, is 36 meg. I could wish there was a central repository for these little-known builds so that ubuntu users could upload with FTP so others could try the software. I wish there was a wiki with program descriptions with a "star" rating for all the software that is available. But, we have the forums and that works. I see 3 people have tried downloading the .debs for makeHuman 0.9. I don't know how long I'll leave them posted. [www.divshare.com](www.divshare.com) has a storage limit of 10gig.

---

### Post by Azakus on 2007-01-14
Oh wow, I didn't realize those files were so big.

---

### Post by Unterseeboot_234 on 2007-01-14
Smitje, sorry you're having so much trouble. This is the only thing I can think of. Dapper is the ubuntu build that they forgot to include either a symlink or the library for libtiff. When I first started Blender, I was firing it up with the menu. Blender worked fine but then it would only import some mesh models and not others. I couldn't figure out why. I searched around in the Blender forums. They were mostly Win users. They asked me what my terminal said. I told them I didn't have a terminal. They were puzzled. Then, I discovered the best way to run Blender is from a Linux terminal. That's when I got the error message no libtiff-library. I did a Synaptic to install the libtiff-dev. The Synaptic put sym-links inside ubuntu where they are needed to let other software find libtiff.

Blender worked fine after that. I discovered some of my models had tiff textures and others had jpeg textures. MakeHuman uses .tiff for the skin texture. You do not see the skin unless you render the humanoid inside MakeHuman and look at the jpeg result, AND MakeHuman uses remarkable textures. Really awesome skin patches in fact.

Maybe there is an option in MakeHuman to export without the skin??? I know I do not have the uv mapping in Blender applying the texture when I do get the model into Blender. Look at my first woman pic posted earlier in this thread and she is plastic. I would post a later, human-looking trial-render I did, but this is a family-oriented forum.

The files I uploaded are .deb files. They double-click from the desktop icon. There might be an apt-get something that installs them. Double-click works because I did checkinstall instead of make install.

In short, you're missing something on your basic ubuntu and I believe it could be libtiff-dev. If it's not (the libtiff is there) look for qt-x11-free-config and qt4-dev-tools. Mind you, I'm a NOOB, I can only guess. That's why build from source on the local machine is important, it finds those dependecies. Other times the build includes those dependencies. The included parts would be from the QT c++ widgets but not the libtiff.

FOR EXAMPLE ONLY:
Other debs or binaries I've downloaded from SourceForge did not work because it was missing a sym-link. It's a trial and effort type of thing. I usually try to build from source. If that doesn't work, then I try their binaries. One time a program couldn't find sym-link -- something like lib.so.3. I looked around in my File System and I did have a sym-link lib.so. I did a sudo cp lib.so lib.so.3. The software worked after that. I saw I didn't want it and I deleted it and the symlink.

---

### Post by webmadman on 2007-06-10
Your post is from quite a while ago, so I don't know if you resolved this, but I seem to have managed :-)
I actually got the compile from the OP to work- thank you so much **Unterseeboot_234**- that checkinstall thing rocks! Having an AMD64 based laptop has forced me to compile a few things, this will simplify the uninstall process in a major way :-D
But then ran into the 'std::out_of_range' issue when I tried to export- all was not lost however- I went into Adept (I run kubuntu so I use Adept rather than Synaptic) and searched for libtiff and installed libtiff-opengl and libtiff-tools, I don't know which one did the trick, but all is good now :-D
I am curious though, a post earlier mentioned genitalia, is there an answer to that, would like to be anatomically correct ;-)

BTW, thanks to the wonders of checkinstall, I have the debs and I also have a webhost so I can upload them if someone wants them, let me know if you want that and I'll oblige...

---

### Post by Smitje on 2007-06-11
hi webmadman

I'm still a noob in linux world yesterday i did my 1st successfull compile and that one has a letter by letter how to. But when I run into trouble I just don't know where to start. Sometimes I have trouble just finding files om my machine, so manny dirs :confused:

how cool to hear you worked it out. I havn't spent much time on it since untersee's last post, I changed the plan a bit and made a makehuman mesh in windows and then used that as a reference model in Blender. I would still like to play with MH more so If you can put up the binaries that would be lovely. u b a :KS

cheers Smitje

---

### Post by snifi on 2007-08-10
(This problem seems be a bit old, but if you don't mind I'll comment it anyway...)

I had yesterday exactly the same problem as Smitje describes here:

```

~ ./configure
...
...a lot of checking...
...
checking for FreeGLUT library... no
checking for GLUT library... no

***************************************************
* Abort!                                          *
* You need support for FREEGLUT or GLUT in mhgui! *
***************************************************
```

I also checked that freeglut3 and freeglut3-dev were already installed (as Synaptic says), so that was not the answer to problem. But...

I yesterday installed quite a lot different packages. (I have a new AMD64-computer, so there is almost nothing installed...) I have no idea, which package solved the problem, in fact I was installing just some basic opengl-routines for other purposes, but i got the problem solved, and here are some lines which i most suspect:

```

# Synaptic:
# Seuraavat paketit asennettiin:
# means: allready installed:
glutg3 (3.7-25)
freeglut3-dev (2.4.0-5)
---
# In Konsole:
sudo apt-get install freeglut3 freeglut3-dev
sudo apt-get install build-essential subversion
sudo apt-get install automake1.9 autoconf libtool
sudo apt-get install libgtk2.0-dev libxmu-dev libxxf86vm-dev
sudo apt-get install libglut3 libglut3-dev

cd ../mhgui-0.1
./configure
# which now outputs:
# ...
# checking for FreeGLUT library... no
# checking for GLUT library... [COLOR="Red"]yes[/COLOR]
# ...
make
sudo make install
make clean
cd ../makehuman-0.9
./configure
make
sudo make install
make clean
makehuman # it runs!!

```

Earlier yesterday i installed other packages with names "mesa" and "opengl", but that seemed not help too much.

---

### Post by Smitje on 2007-08-12
Thanks for the hint I may give it another try,
 Im curently working on something diferent however (and my hollidays are over back to work tomorrow)

cheers Smitje

---

### Post by gasaqholl on 2007-08-18
Hi everybody.
It is the libxmu-dev the one was need for ./configure.
I had libgtk2.0-dev all ready from the beginning.
No one of this was need automake1.9, autoconf, libtool.
:guitar:

---

### Post by radopenev on 2007-10-30
Hi everybody!
I'm Ubuntu/Dapperx86_64-bit user and all is OK for me!!!:lolflag:
According to Unterseeboot_234s advices from the beganing of this post,
I was download the .debs and install with  GDebi Packege Installer.
Step by step and :guitar:!
Best regards!
Sorry for my English!:)

---

### Post by Ru$$i@N on 2007-12-10
Hi, 
Thanks to Unterseeboot_234, i have installed the software.
But when i try to actually work with it, it does almost nothing. I mean, i can rotate the model, but i can't do any changes to it!!! :confused:
I don't know what to do. The "buttons" do light up, but the numbers under them remain unchanged.

HELP!

---

### Post by chingchong on 2008-03-04
I was having the same issues as others:

> makehuman: error while loading shared libraries: libmhgui.so.0: cannot open shared object file: No such file or directory

I'm running 64bit Gutsy FYI... so I looked around and the libmhgui.so.0 file was in /usr/local/lib but not in /usr/lib after creating a sym link 

 sudo ln -s  /usr/local/lib/libmhgui.so.0 /usr/lib/libmhgui.so.0

makehuman ran no problem

Thanks for the checkinstall suggestion I love how that creates new debs thats awesome!

If anyone knows why my lib went to /usr/local/lib instead of /usr/lib i.e. I accidently ran ./configure instead of sudo ./configure I would be interested to know.

Thanks

---

### Post by Robynsveil on 2008-03-04
Well, this thread has been helpful in that a number of people made the same mistakes I made, like not issuing a sudo in front of a ./configure, make and make install. The packages I downloaded (.tar.gz files) I was able to un-archive with the archive manager. Finally got it all built, but then had to:
```

sudo ln -s /usr/local/lib/libmhgui.so.0 /usr/lib/libmhgui.so.0
sudo ln -s /usr/local/lib/libanimorph.so.0 /usr/lib/libanimorph.so.0

```

because of, well, those "error while loading shared libraries: libanimorph.so.0: cannot open shared object file: No such file or directory" issues.

I've got it running, but it seems to be stuck, somehow. Maybe I'm doing something wrong, but the thing seems to freeze, and then spastic-ly jumps and does something and then freezes again. For those suspecting OpenGL or other issues, I am running GG Linux 2.6.22, NVidia GeForce 6600GT with restricted drivers manager, and The GIMP and Blender run smoothly.
Any ideas or thoughts?

BTW, this was my first-ever, full-on BUILD_FROM_SOURCE!! Wow, did that make me feel like a tech wienie or WHAT? WooHOO!!!

---

### Post by ShelJ on 2008-05-20
> **snifi said:**
> (This problem seems be a bit old, but if you don't mind I'll comment it anyway...)

I had yesterday exactly the same problem as Smitje describes here:

```

~ ./configure
...
...a lot of checking...
...
checking for FreeGLUT library... no
checking for GLUT library... no

***************************************************
* Abort!                                          *
* You need support for FREEGLUT or GLUT in mhgui! *
***************************************************
```

I also checked that freeglut3 and freeglut3-dev were already installed (as Synaptic says), so that was not the answer to problem. But...

I yesterday installed quite a lot different packages. (I have a new AMD64-computer, so there is almost nothing installed...) I have no idea, which package solved the problem, in fact I was installing just some basic opengl-routines for other purposes, but i got the problem solved, and here are some lines which i most suspect:

```

# Synaptic:
# Seuraavat paketit asennettiin:
# means: allready installed:
glutg3 (3.7-25)
freeglut3-dev (2.4.0-5)
---
# In Konsole:
sudo apt-get install freeglut3 freeglut3-dev
sudo apt-get install build-essential subversion
sudo apt-get install automake1.9 autoconf libtool
sudo apt-get install libgtk2.0-dev libxmu-dev libxxf86vm-dev
sudo apt-get install libglut3 libglut3-dev

cd ../mhgui-0.1
./configure
# which now outputs:
# ...
# checking for FreeGLUT library... no
# checking for GLUT library... [COLOR="Red"]yes[/COLOR]
# ...
make
sudo make install
make clean
cd ../makehuman-0.9
./configure
make
sudo make install
make clean
makehuman # it runs!!

```

Earlier yesterday i installed other packages with names "mesa" and "opengl", but that seemed not help too much.
Thanks for this, it worked great!!

---

### Post by jblackthorne on 2008-06-04
The instructions provided do in fact nearly work.  Though, the program will install into a non-standard installation directory.  Furthermore, additional changes are required for a x64 installation.  Library linking as mentioned in a previous post is not necessary (nor a good idea).

Instead of "./configure" run 

"sudo auto-apt run ./configure --sysconfdir=/etc --libdir=/usr/lib64 --prefix=/usr"

the above instructs the proper directory for a 64bit platform, the proper program directory, and the proper config directory

Also, as of version 0.9.1-rc1a at least, "checkconfig" will not work normally because the make script includes chmod commands.  However, there is a trick to get around this:

NOTE: With instructions below use 

* --libdir=/usr/lib64 (for 64 bit)
* --libdir=/usr/lib (for 32 bit)

* run these commands for each of the three program directories

1. open a terminal
2. sudo -s (to become root)
3. auto-apt run ./configure --sysconfdir=/etc --libdir=/usr/lib64 --prefix=/usr
2. make
3. make install
4. and then one of the following:

checkinstall -D --pkgname="animorph" --pkgversion=0.3 --maintainer="makehuman group" --requires="libxmu, libxmuu1, freeglut3" --install=yes

checkinstall -D --pkgname="mhgui" --pkgversion=0.2 --maintainer="makehuman group" --requires="animorph" --install=yes

checkinstall -D --pkgname="makehuman" --pkgversion=0.9.1 --pkgrelease=rc1a --maintainer="makehuman group" --requires="animorph, mhgui" --install=yes

The advantage of using the above checkinstall method is that the program will be listed as a package in Synaptic Package manager.  Hence, it can be removed, upgraded, etc.


Edited to add:
I attempted to attach the x64 debs to this post for those who have problems or do not wish to compile code.  However, the main makehuman program is 28mb and exceeds the max size allowed for this forum.


Hope this helps.

---

### Post by menschtx on 2008-06-09
I found out on the website that Make Human isn't for linux, not at this time, at least not now and that they would be working on it. But the suggestion is to archive your downloads for when a release is set.

---

### Post by jblackthorne on 2008-06-09
> **menschtx said:**
> I found out on the website that Make Human isn't for linux, not at this time, at least not now and that they would be working on it. But the suggestion is to archive your downloads for when a release is set.

I am not sure what you read menschtx.  Though, I am running 0.9.1 RC1a on Ubuntu Hardy x64 perfectly.  Plus, here is the Linux source:

[http://sourceforge.net/project/showfiles.php?group_id=150931&package_id=168385&release_id=560648](http://sourceforge.net/project/showfiles.php?group_id=150931&package_id=168385&release_id=560648)

Again, my post above details how to properly compile that linux source.  In fact, I attached two of the three compiled deb files to the post itself. If you run into problems compiling, please attach details here.  Otherwise, if there is a strong request, I will post the 3rd deb on a file share somewhere.

Regards

Edited to add:
Here is the 3rd Deb for those who do not wish to compile:
[http://rapidshare.com/files/121223336/makehuman_0.9.1-rc1a_amd64.deb.html](http://rapidshare.com/files/121223336/makehuman_0.9.1-rc1a_amd64.deb.html)

Install animorph, mhgui, and then makehuman deb files in that order.

Since this post is a bit out of date and in an archive forum, I am going to make a new and up to date HowTo soon.

---

