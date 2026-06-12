---
title: "Trying to run i386 binary on x86_64 system? (no such file or directory)"
date: 2006-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by enigma_0Z on 2006-11-17
Perhaps I can't do this, but

When I try to run a binary compiled for an i386 (32-bit?) architechure (sp?), I get the following:

```
$ ./linux_client
bash: ./linux_client: No such file or directory

```

Information about the binary:
```
$ ls -l linux_client
-rwxrwxrwx 1 root games 664304 2006-09-12 18:34 linux_client
$ file linux_client
linux_client: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), for GNU/Linux 2.4.1, stripped

```

---

### Post by Kilz on 2006-11-17
> **enigma_0Z said:**
> Perhaps I can't do this, but

When I try to run a binary compiled for an i386 (32-bit?) architechure (sp?), I get the following:

```
$ ./linux_client
bash: ./linux_client: No such file or directory

```

Information about the binary:
```
$ ls -l linux_client
-rwxrwxrwx 1 root games 664304 2006-09-12 18:34 linux_client
$ file linux_client
linux_client: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), for GNU/Linux 2.4.1, stripped

```

What is the name of this application?

---

### Post by enigma_0Z on 2006-11-17
Sauerbraten, you can get it at sauerbraten.org

It's a game.

--edit--

Recompiled it, x86_64 binary runs.

Just curious why this one doesn't. If this isn't the place, I can ask there.

---

### Post by Kilz on 2006-11-17
> **enigma_0Z said:**
> Sauerbraten, you can get it at sauerbraten.org

It's a game.

--edit--

Recompiled it, x86_64 binary runs.

Just curious why this one doesn't. If this isn't the place, I can ask there.

Are you running Edgy? If so you may have to install the [linux32]("http://packages.ubuntu.com/edgy/utils/linux32") and the [ia32 packages]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ia32&searchon=names&subword=1&version=edgy&release=all") to get 32bit applications to run.

---

### Post by enigma_0Z on 2006-11-17
> **Kilz said:**
> Are you running Edgy? If so you may have to install the [linux32]("http://packages.ubuntu.com/edgy/utils/linux32") and the [ia32 packages]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ia32&searchon=names&subword=1&version=edgy&release=all") to get 32bit applications to run.

yes I am. I installed linux32 as part of the firefox32 installation. Thanks.

---

### Post by xstaticxgpx on 2006-11-17
when I downloaded the i686 build of firefox from the main site, it used to give me a error "./firefox-bin: No such file found" even though it was obviously there, I think installing build-essentials fixed the issue for me

---

### Post by kleeman on 2006-11-17
That game worked for me using linux32 on an amd64 system but I had to klutz around with the script in the top directory I recall. I have attached said script

---

### Post by enigma_0Z on 2006-11-18
> **kleeman said:**
> That game worked for me using linux32 on an amd64 system but I had to klutz around with the script in the top directory I recall. I have attached said script

Yeah, I've made an x86_64 build, I've contactd aard, but I'm not sure if he'll accept it.

---

### Post by Kilz on 2006-11-18
I just got the game working. There are a few packages that need to be installed for running it in 32bit mode. At least I had to add them to Dapper. They need to be extracted from the deb and the libraries that are in /usr/lib in the .deb file copied to /usr/lib32.

libsmpeg0_0.4.5+cvs20030824-1.7_i386.deb
libvorbisfile3_1.1.2-0ubuntu2_i386.deb
libsdl-image1.2_1.2.4-1_i386.deb

Then run it with 

linux32 ./sauerbraten_unix

---

### Post by kleeman on 2006-11-18
> **enigma_0Z said:**
> Yeah, I've made an x86_64 build, I've contactd aard, but I'm not sure if he'll accept it.
Why are you trying to use the 32 bit version if you have a 64 bit version? Mind making it available if it works well? I like that game!

---

### Post by Kilz on 2006-11-18
I like it as well, and I tried the latest version(sauerbraten_2006_09_12_water_edition_linux). It reminds me of quake (that I cant get to run on linux). But there were no monsters in single player. I had to get an older version.

---

### Post by enigma_0Z on 2006-11-18
> **kleeman said:**
> Why are you trying to use the 32 bit version if you have a 64 bit version? Mind making it available if it works well? I like that game!

Ask and you shall receive: [http://sledgehammer.ath.cx/files/sauer_64.tgz](http://sledgehammer.ath.cx/files/sauer_64.tgz)

Just cd to the dir where you've got sauer installed and run "tar xvzf /path/to/download/sauer_64.tgz"



Basically, the question was why does it say "no such file or directory".

---

### Post by enigma_0Z on 2006-11-18
Ask and you shall receive...

[http://sledgehammer.ath.cx/files/sauer_64.tgz](http://sledgehammer.ath.cx/files/sauer_64.tgz)

Just "cd" to the directory that you extracted sauerbraten, and run "tar xvzf /path/to/download/sauer_64.tgz". Run sauerbraten_unix and enjoy.

-- sorry about the double post, 2nd page got me screwed up --

---

### Post by kleeman on 2006-11-18
Thanks works great.

---

### Post by enigma_0Z on 2006-11-20
> **Kilz said:**
> I like it as well, and I tried the latest version(sauerbraten_2006_09_12_water_edition_linux). It reminds me of quake (that I cant get to run on linux). But there were no monsters in single player. I had to get an older version.

The SP Episodes are WIP. Try dmsp.

---

### Post by wall0159 on 2006-11-27
> **enigma_0Z said:**
> ... Run sauerbraten_unix and enjoy.


I don't think I'm being stupid, but... ;-)

I've done all that and it doesn't work..

Running Edgy on AMD64. I have this file
/usr/lib/libSDL-1.2.so.0
yet, when trying to run sauerbraten_unix, I get this message:

./bin_unix/x86_64_linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

I checked, and I've patched it correctly - it's calling x86_64_linux_client properly...

Do I need to install 32-bit libs? I wouldn't think so, because it sounds like you've recompiled the app for 64-bit Linux... but maybe I'm wrong..?

Anyway, thanks for your efforts!
-Gus

---

### Post by wall0159 on 2006-11-27
> **wall0159 said:**
> I don't think I'm being stupid, but... ;-)


err.. I spoke to soon. ](*,) 

I just read my post, and realised that libSDL_image-1.2.so.0 is not the same as libSDL-1.2.so.0..

Feel like a bit of a dork!


anyway I created a symbolic link to libSDL-1.2.so.0.... and now I'm getting this message:
(I also modified the sauerbraten_unix file so that the resolution is 1024x768 )

Renderer: GeForce 6100/PCI/SSE2 (NVIDIA Corporation)
Driver: 2.0.2 NVIDIA 87.76
Using GL_ARB_vertex_buffer_object extension.
Rendering using the OpenGL 1.5 assembly shader path.
Using GL_ARB_occlusion_query extension.
Using GL_EXT_framebuffer_object extension.
Using GL_ARB_texture_rectangle extension.
./bin_unix/x86_64_linux_client: symbol lookup error: ./bin_unix/x86_64_linux_client: undefined symbol: IMG_Load


Any suggestions? I'm not terribly familiar with this sort of thing...

---

### Post by enigma_0Z on 2006-12-04
> **wall0159 said:**
> ...
anyway I created a symbolic link to libSDL-1.2.so.0....
...

OK, first of all, delete the symbolic link that you created, manual linking should not be required...

Here is the list of packages that I have installed (I've removed the dev ones, unless you want to build software, then append -dev to the names...)

```

libsdl-image1.2
libsdl-mixer1.2
libsdl1.2debian
libsdl1.2debian-alsa

```

Be sure that every one of those packages is installed, and you should be good to go (also get rid of any manually-created symlinks, copies, etc that you may have created before installing these packages).

---

### Post by wall0159 on 2006-12-04
Excellent - thanks for your assistance enigma_0Z! That did the trick! :-)

Cheers..

---

### Post by Smitje on 2007-01-24
Hi all Im trying to install sauerbraten, but Im Having no luck

when I do 
/src/make install
I get a long list of errors that all look the same. Here is the last bit:
```
ETERIVEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6478: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6479: error: typedef ‘PFNGLGENERATEMIPMAPEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6479: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6487: error: typedef ‘PFNGLSTRINGMARKERGREMEDYPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6487: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6487: error: expected primary-expression before ‘const’
make: *** [shared/tools.o] Error 1
~/install/sauerbraten/src$ 

```

Anyone got a clue what Im doing wrong?

Cheers Smitje


PS I tried to download your binaries but I thingk they are not there annymore

---

### Post by Kilz on 2007-01-24
> **Smitje said:**
> Hi all Im trying to install sauerbraten, but Im Having no luck

when I do 
/src/make install
I get a long list of errors that all look the same. Here is the last bit:
```
ETERIVEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6478: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6478: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6479: error: typedef ‘PFNGLGENERATEMIPMAPEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6479: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6487: error: typedef ‘PFNGLSTRINGMARKERGREMEDYPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6487: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6487: error: expected primary-expression before ‘const’
make: *** [shared/tools.o] Error 1
~/install/sauerbraten/src$ 

```

Anyone got a clue what Im doing wrong?

Cheers Smitje


PS I tried to download your binaries but I thingk they are not there annymore

By any chance have you installed the proprietary drivers for your video card?

---

### Post by Smitje on 2007-01-25
hi Kilz

afaik my videocard works fine. (Enemy territory, worked straight out of the box)
glxinfo | grep rendering => direct rendering: Yes
If you are refering to something else, where should I look?

Cheers,
Smitje

---

### Post by kleeman on 2007-01-25
> **Smitje said:**
> hi Kilz

afaik my videocard works fine. (Enemy territory, worked straight out of the box)
glxinfo | grep rendering => direct rendering: Yes
If you are refering to something else, where should I look?

Cheers,
Smitje
Sounds as if some graphics libraries or headers are missing. Try 
sudo apt-get install libglu1-mesa libglu1-mesa-dev

and redo your make.

---

### Post by Smitje on 2007-01-25
Thanks Kleeman for your input.

```
~$ sudo apt-get install libglu1-mesa libglu1-mesa-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglu1-mesa is already the newest version.
libglu1-mesa-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

so they were still fresh. I tried make install annyway, but no joy.

Cheers Smitje

---

### Post by kleeman on 2007-01-25
What is your video card and which driver is it using?

---

### Post by Smitje on 2007-01-28
Hi Kleeman
Sorry for the gap in the communication, I appreciate your help but have been bussy.

Im not sure where to look for the driver, in synaptic I found:
nidia-glx   1.0.8776+2.6.17.7-10.1

my catd is an EVGA GeForce 7600GT

Cheers Smitje

---

### Post by kleeman on 2007-01-28
Sounds like you are running nvidia. To check do this:

lsmod | grep nvid

If it lists nvidia in the first column you are. Assuming it does check in synaptic whether you have the package nvidia-glx-dev  installed or not......

---

### Post by Smitje on 2007-01-28
Hi Kleeman

I did the test and it is indeed nvidia,
so I checked synaptic and installed nvidia-glx-dev.

but ... I still get the same error :(

Cheers, 
Smitje

---

### Post by kleeman on 2007-01-29
You are still missing some dev files. I compiled the latest version of this yesterday (with the server crash patch). My system is amd64 so if yours is too grab the binaries from here

[http://www.math.nyu.edu/faculty/kleeman/amd64/native_client](http://www.math.nyu.edu/faculty/kleeman/amd64/native_client)
[http://www.math.nyu.edu/faculty/kleeman/amd64/native_server](http://www.math.nyu.edu/faculty/kleeman/amd64/native_server)

put them in the bin_unix subdirectory and launch

sauerbraten_unix from the main sauerbraten directory.

---

