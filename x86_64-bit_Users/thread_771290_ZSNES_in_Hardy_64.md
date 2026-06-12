---
title: "ZSNES in Hardy 64"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by ASULutzy on 2008-04-27
I've found lots of threads about installing zsnes, but can't seem to get it going... It was much easier in gutsy 32, just sudo apt-get install zsnes.

I've downloaded the source and when I make it it says, 

```
/usr/bin/ld: i386 architecture of input file `video/hq2x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `video/hq3x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `video/hq3x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `video/hq4x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `video/hq4x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `video/copyvwin.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `linux/sdlintrf.o' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status
make: *** [main] Error 1
```

There's more of it that looks like that, but basically it's a 64 bit issue... Workarounds that have popped into my head are booting into my XP install through Virtualbox, or using wine to run native windows binaries.

Has anyone successfully installed zsnes in 64 bit hardy?

---

### Post by Cappy on 2008-04-27
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2ubuntu1_i386.deb
sudo dpkg --force-all -i zsnes_1.510-2ubuntu1_i386.deb
```

Install getlibs: [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

```
getlibs /usr/bin/zsnes
```

---

### Post by ASULutzy on 2008-04-27
```
ryan@ryan-desktop:~$ sudo zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: Logitech USB-PS/2 Optical Mouse
Mouse 1: Macintosh mouse button emulation
Segmentation fault
```

segfaults are bad!

edit: I can get it to run inside my VM under windows, and with Wine, but I'd really like a linux based solution :X

---

### Post by Cappy on 2008-04-27
Try
```
zsnes -ad oss

```

```
zsnes -ad alsa

```

or

> **dfreer said:**
> 
[*]***pSX, mupen64, and/or ZSNES segfault and I can't figure out why!*** - [rcsdnj]("http://ubuntuforums.org/member.php?u=135017") reports that the "Data execute prevention" on x86_64 processors may be the cause of a segmentation fault. I haven't tried this myself, so proceed with caution:
> 
Originally Posted by rcsdnj  
To stop , I first did it by going to the BIOS and disabled the "XD Technology" option. Since I didn't want to disable it globally, I looked for a way to disable and I found this:

- install prelink package ( sudo aptitude install prelink - I'm not sure about the package name, I'm not in my Ubuntu machine right now)

- run the executable you want to disable the XD technology by using:

execstack -s program_name

I'm not saying this is the solution for the problem, but it's maybe a good test.



---

### Post by ASULutzy on 2008-04-27
heh, I'll try the first one... I'm not making myself vulnerable to buffer overflow attacks just so I can play super nintendo :)

---

### Post by beartard on 2008-04-27
I wouldn't worry about trying.  It doesn't help.

I tried compiling zsnes the other day to no avail.  Tonight I tried all the tips in this thread, but still get a segfault.  You have to set the execstack using sudo, then run zsnes in sudo.  It still segfaults.

The zsnes manpage talks about deleting the ~/.zsnes directory as well.  Same result.

---

### Post by ZeroHimself on 2008-05-03
I had the same problem...

It would run however with ```
zsnes -ad null
```

since then, i made sure i got the latest ai32-libs...

and i've reinstalled all the libsdlxxxxx  and -dev packages

upon seeing your thread, I tried to reinstall zsnes....
and it just worked with sound!!!!!!!!!

so I did an ldd of it.... if you feel like hunting, you may be able to get it to work...

```
zero@atlantis:~$ ldd /usr/bin/zsnes
	linux-gate.so.1 =>  (0xffffe000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7f79000)
	libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7eea000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf7ec6000)
	libao.so.2 => /usr/lib32/libao.so.2 (0xf7ec2000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e1e000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7d2b000)
	libm.so.6 => /lib32/libm.so.6 (0xf7d06000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7cfb000)
	libc.so.6 => /lib32/libc.so.6 (0xf7bab000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7b93000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7ad0000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7acc000)
	libdirectfb-1.0.so.0 => /usr/lib32/libdirectfb-1.0.so.0 (0xf7a69000)
	libfusion-1.0.so.0 => /usr/lib32/libfusion-1.0.so.0 (0xf7a61000)
	libdirect-1.0.so.0 => /usr/lib32/libdirect-1.0.so.0 (0xf7a4d000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf6f38000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6f36000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6f28000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6e41000)
	/lib/ld-linux.so.2 (0xf7fa8000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6e3d000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf6e3b000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6e23000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6e1e000)
```

---

### Post by ASULutzy on 2008-05-03
Ooh forgot about this one, thanks I'll try it later!

---

### Post by Yellow Pasque on 2008-05-03
We used to have a pre-made zsnes package available in dfreer's repo, but I don't believe that repo has worked for a while. zsnes is a popular package that Ubuntu doesn't provide a 64-bit version of. If there's anyone out there with the know-how to make a Hardy64 .deb, please do so, as this is a difficult package for n00bs to build.

---

### Post by Banhammer on 2008-05-03
Works great for me in wine.

---

### Post by Yellow Pasque on 2008-05-03
> **Banhammer said:**
> Works great for me in wine.
Running zsnes through wine probably takes a lot of CPU/GPU horsepower and won't be a feasible option for a lot of users.

---

### Post by dfreer on 2008-05-07
ZSNES uses 32-bit assembly code, and therefore cannot be compiled as a 64-bit binary (you may be able to still compile it as a 32-bit binary on a 64-bit machine, though).

ZSNES 1.51 also uses libao with OSS (if compiled with --enable-libao), which provides the highest quality sound in previous ubuntu versions. If you are on a 64-bit machine and you try to run ZSNES with the OSS sound output (zsnes -ad oss), you will get a segfault unless you have 32-bit libao sound libraries placed in /usr/lib/ao/plugins-2/ (this probably explains why ZeroHimself was able to get zsnes working with the sound output set to null). Hardy already has ia32-libs installed with the 32-bit libao libraries placed at /usr/lib32/ao/plugins-2/, a simply system link will suffice (make sure not to overwrite the already existing 64-bit files in /usr/lib/ao/plugins-2/!)

The second highest quality sound comes from using SDL sound output (zsnes -ad sdl), after installing the libsdl1.2debian-oss package. From what I understand of it, this package takes all SDL output and pipes it through OSS instead. Note, however, that just doing a **sudo apt-get install libsdl1.2debian-oss** may not be enough; ZSNES being a 32-bit binary will most likely need the **32-bit** version of libsdl1.2debian-oss installed.

Also, running zsnes or really any program with **sudo** is a bad idea all around. Right off the bat, you will be using root's ~/.zsnes/ preferences instead of your own ~/.zsnes/, which means anything you change in zsnes while root will not show up when running zsnes normally and vice versa, making troubleshooting a nightmare.

Finally, regarding my zsnes packages for hardy, until I can figure out a way for zsnes to actually OUTPUT sound with this blasted pulseaudio, or to somehow bypass it... if someone figures that out, it would be great. I like the idea of pulseaudio, I just wish that Ubuntu got it fully working in Ubuntu before the hardy release.

---

### Post by Holonet on 2008-05-07
Got it!  I installed as Cappy originally posted, and ended up with the exact same library readout as ZeroHimself, but I still had no sound, of course.

I was testing with Chrono Trigger (with Squaresoft sound, what better test?), and I tried -ad auto, and got sound but sort of effed up sound.  I then tried this:

zsnes -dh -ad sdl

Presto.  Worked like a charm.  -dh removes rom-specific hacks, I believe.

---

### Post by dfreer on 2008-05-07
> **Holonet said:**
> Got it!  I installed as Cappy originally posted, and ended up with the exact same library readout as ZeroHimself, but I still had no sound, of course.

I was testing with Chrono Trigger (with Squaresoft sound, what better test?), and I tried -ad auto, and got sound but sort of effed up sound.  I then tried this:

zsnes -dh -ad sdl

Presto.  Worked like a charm.  -dh removes rom-specific hacks, I believe.

I'll check on what -dh does, but that solution makes absolutely no sense to me lol. Glad it works for you, though I'm willing to bet that something else you did is responsible for zsnes working.

---

### Post by Holonet on 2008-05-08
Sorry that wasn't clear, and I did screw something up.  -ad auto results in a segmentation fault...but it's the -ad sdl that makes it work at all, in conjunction with the getlibs (which I honestly don't know what that does) bit at the beginning.  However, I didn't try it without doing that...but that package was the one used.

-dh does disable ROM-specific hacks, it's in zsnes -?.  That wasn't what made it work, but it fixes the sound screw ups.  -ad sdl makes it work with sound, but the sound is skippy and messed up.  -dh fixes just that part.

---

### Post by Artemis3 on 2008-07-05
> **Holonet said:**
> I was testing with Chrono Trigger (with Squaresoft sound, what better test?)

Tales of Phantasia; playing the entire opening sequence flawless (2 times in a row). This is the hardest for emulators because of the way Enix chained vocal samples with music.

Last time i tried Zsnes in linux, it failed to reproduce this opening flawless, while on the same machine, using windows zsnes worked. Currently with my fast machine, snes9x plays it fine.

Another interesting test is Seiken Densetsu 3, as the music in the opening sequence likes to get out of sync. Its also a quick way to test hi-res mode.

As for pulseaudio, i love the ancient method: **killall pulseaudio** (fixes VLC hiccups as well) :)

Also last time i used zsnes (with sdl), make sure you have libsdl1.2debian-oss NOT alsa. You might as well test with libsdl1.2debian-pulseaudio if you don't kill it like i do. There is this ancient bug with alsa causing it to produce static like noise which does not manifest if you use alsa's oss emulation.

---

### Post by Yellow Pasque on 2008-08-09
I've built an amd64 .deb by hacking the 386 .deb. I replaced the zsnes binary with a K8-optimized build (courtesy of Nach on the zsnes forums) and you can use getlibs to install the appropriate 32-bit libraries like so:
```
cd ~/
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs -p libao2 libc6 libgcc1 libgl1-mesa-glx libpng12-0 alsa-oss libsdl1.2debian-oss libstdc++6 zlib1g
```

PM me your e-mail if you're interested in the .deb. or if you know of a good repo to put it in.

---

### Post by luridsorcerer on 2008-09-19
Woo hoo! I had so many problem running ZSNES in Wine, and now I don't have to put up with any of that anymore! The first time I read this thread it really didn't help much, but this time around I've got it working thank to you guys. For people who don't want to follow the whole thread again, here's what I did.

First, I forced the install of the 32bit .deb package.
```

wget http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2ubuntu1_i386.deb
sudo dpkg --force-all -i zsnes_1.510-2ubuntu1_i386.deb

```
I downloaded and installed getlibs (link is in a previous post), and ran it on zsnes.
```
sudo dpkg -i getlibs-all.deb
getlibs /usr/bin/zsnes
```
Now zsnes runs great as long as I run it with either of these commands:
```
zsnes -ad null
zsnes -dh -ad sdl
```
The null one runs it without sound. The sdl one uses Simple Direct Layer for sound, but it was all scratchy until I turned the sample rate up to 48000.
Next, I got rid of snes9x.
```
sudo apt-get remove snes9x-x
```
Thanks to everyone who contributed to this thread. It was a big help!

---

### Post by Vince4Amy on 2008-09-29
Excellent, works great:D

---

### Post by Artemis3 on 2008-09-29
snes9x doesn't conflict with zsnes, there is no need to uninstall it.

In the end i always use snes9x with snes9express gui.

---

### Post by Modax42 on 2008-10-12
Great Work!  For me, the sound was still scratchy and distorted, even a 48000 Hz, but under the 'lowpass' options in the sound menu, I went from 'none' to 'high quality' and now the sound is flawless.

---

