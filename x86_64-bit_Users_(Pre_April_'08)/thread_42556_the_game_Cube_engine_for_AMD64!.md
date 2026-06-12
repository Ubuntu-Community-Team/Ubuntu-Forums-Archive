---
title: "the game Cube engine for AMD64!?"
date: 2005-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fanskapet on 2005-06-18
Hmm anyone know how to compile this game within Ubuntu 64?
[www.cubeengine.com/](www.cubeengine.com/)

if someone succeded in this please give me a reply or two :) would be neat to have some nice games to play around with :)

Best regards Fanskapet  \\:D/

---

### Post by Pinoy915 on 2006-09-13
Any information regarding running this game on AMD64? Either Cube 1 or Cube 2 (Sauerbraten).

---

### Post by dfreer on 2007-02-22
I was able to get Cube, Action Cube, and Sauerbraten working in AMD64, although sadly I couldn't get it to compile a AMD64 client, I simply used the i686 client. Here's how to do it:

Note: You will need to install 32-bit libraries using this method. I already had a bunch installed from installing 32-bit Firefox, Mplayer, Wine, and ZSNES. So I can't tell you which ones you'll need for sure until I have a chance to install cube on a clean system. A good tip would be to try:

```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
```

That should give you some basic 32-bit libraries.

Get either Action Cube or Sauerbraten, open up a terminal. untar the *.tar.gz file, and navigate to the newly created folder. From there, 
```
cd bin_unix
./linux_client
```
More likely than not, it will complain about some lib file missing, for me I was missing libvorbisfile3, libsdl-image-dev, and maybe a few others. Go to [http://packages.ubuntu.com]("http://packages.ubuntu.com") and do a search for whatever package it is complaining about. Download the i386 package, and install it with 
```
sudo dpkg --force-architecture -i ******-i386.deb
```. Go back to the bin_unix directory and try running the linux client again. If you got the right package, either it will try to start or more than likely complain about another package that's missing. Repeat the above process until it stops complaining. It actually tried to start on me once I got all the dependencies installed, and I think I had to use <CTRL><ALT><BACKSPACE>.

So now that you have all your 32-bit libraries installed, go up one directory and edit the install script. There is a variables defined right at the beginning of the script:
```
MACHINE_NAME=`uname -m`
```
This simply says we are running x86_64, and this will cause the Startup script to fail. If you have linux32 installed, simply change the variable to this:
```
MACHINE_NAME=`linux32 uname -m`
```
I guess if you don't wanna do that, you could simple change it to say:
```
MACHINE_NAME=i686
```

For Sauerbraten only!:
Before running the sauerbraten_unix script, you will need to do these additional steps:
```
sudo apt-get install libsdl-image1.2-dev libsdl-mixer1.2-dev
cd src
./configure
make
make install
cd ../
```

The game should run now :D
Execute the startup script and you should be up and running!

---

### Post by dfreer on 2007-03-01
You will also need to install some developer packages, specifically libsdl-mixer1.2-dev and libsdl-image1.2-dev. For sauerbraten you will also need to navigate to the src folder and compile part of the game. I've edited the above how-to to reflect these changes. If anyone else has a problem installing Actioncube or Sauerbraten using these steps please let me know (and post your terminal output please).

---

### Post by s4lv1n0 on 2007-11-11
Hi people! I've successfully compiled a i386 package of this game in my Xubuntu 64bits - after downloading A LOT of libs - but the Debian package is only 5Kb! I don't know if something gone wrong but I actually was able to play the game, BUT it is really slow. Any tips on how to run it faster?

* My hardware:
-- Athlon64 3700+ (2.2Ghz)
-- 1Gb DDR1 400Mhz
-- No 3D acceleration card, just my onboard video adapter with 128Mb

---

### Post by dfreer on 2007-11-11
You'll probably need a 3D accelerated card to play a 3D game like this :p
But your onboard card most likely is capable of direct rendering/3D acceleration, unless the drivers aren't up to par. You may want to try searching for an how-to for your specific chipset, to see if you can get it working if it's not already.

As for the debian package, did you make it with checkinstall? can you upload the package, or at least a directory list of the files within?

EDIT: I haven't messed with this game for a long time... perhaps it's time for a proper howto/package?

---

### Post by Korsaire71100 on 2007-12-26
Thanks dfreer
It works perfectly after dpkg --force-architecture
and thanks for this :
AMD64 Repository with 32-bit programs now open! (May 2007)

See ya

---

### Post by Rhubarb on 2007-12-27
Actually, it's very easy to compile sauerbraten and assault cube for 64bit.
Here's how:

Install:
```
sudo aptitude install libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-mixer1.2 libsdl-image1.2 build-essential
```
Then navigate to sauerbraten/src/
Then run:
```
make
make install
```
To run the game from your sauerbraten directory:
./sauerbraten_linux -w(your width) -h(your height)

This also works for Assault Cube (which uses the cube 1 engine).

---

### Post by go_beep_yourself on 2008-03-28
Hi Rhubarb. I know you! w00p clan and I have you on msn. And dfreer, where have you been? I need to ask you a few questions. Contact me through IM.

---

### Post by dfreer on 2008-03-29
@ go_beep_yourself - Been dead to the world lately, haven't had time for any ubuntu related activities. I'll try and leave skype/MSN on, haven't used them in forever.

---

### Post by maxol on 2008-03-30
If you like FPS games a good free native 64 bit game is Urban Terror.

[http://www.urbanterror.net](http://www.urbanterror.net)

---

### Post by maxol on 2008-04-05
64 bit AssaultCube here.

[http://www.getdeb.net/app.php?name=AssaultCube](http://www.getdeb.net/app.php?name=AssaultCube)

---

