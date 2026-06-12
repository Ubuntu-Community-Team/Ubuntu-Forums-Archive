---
title: "libasound_module_pcm_empty.so"
date: 2007-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by dozch on 2007-01-15
I have successfully installed the 32-bit applications skype and the flashplugin 9 beta, thanks to various posts on linux32 apps, but still have a problem with sound/libasound32. With both flash and skype I get the following error:

ALSA lib ../../../src/pcm/pcm.c:2109:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so

Because I had issues with sound I got the latest version of alsa (1.0.14rc1) for its hda_intel driver (I have an ASUS M2N-E mobo) and build it, so that might be related to the problem. Sound for 64-bit apps works fine. There is no library libasound_module_pcm_empty.so on my box and also does not seem to get installed with Edgy.

Does anyone know what this means? It is a bit of a worry that alsa looks for a library with 'empty' in it... 

Thanks for any help.

---

### Post by nbayiha on 2007-01-17
i actually have the same problem than you. 
i think it's because of the latest alsa.:-| 

damn i should have thought twice before installing them.

when i run firefox from the terminal i get a lot error cause of alsa.

i've follow a lot of thread but nothing help me till now.

---

### Post by theonhighgod on 2007-06-24
i had to install the new alsa libary and driver to get any sound in ubuntu, i've got the same problem as u guys, if i open  firefox and browse to a page with flash i get the following in ther terminal
```

ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint

```

This is using the nspluggin wrapper, i tryied installing 32 bit firefox and removing the plugin but i get the same message, im not certain i fully disabled the nspluggin wrapper think its time to try another flash player :( ne help would be much appreciated

---

### Post by darwinmach on 2007-06-25
had the same problem, fixed it by doing the following:

A.) manual remove of the main ALSA components
B.) recompile and reinstall ALSA from source

- - -

A.) removing ALSA:

in the terminal (i did this from a tty session, after shutting down kde with "/etc/init.d/kdm stop"):
```

user@localhost:/$ sudo su
root@localhost:/$ rm /usr/sbin/alsactl
root@localhost:/$ rm /usr/bin/amixer
root@localhost:/$ rm /usr/bin/aplay
root@localhost:/$ rm /usr/bin/arecord
root@localhost:/$ rm /usr/bin/alsamixer
root@localhost:/$ rm -r /usr/lib/libasound*
root@localhost:/$ rm -r /usr/bin/alsa-lib

```

- - -

B.) Compiling an installing the latest ALSA from [http://alsa-project.org](http://alsa-project.org)

in the following sequence:

1 - alsa-firmware
2 - alsa-driver
3 - alsa-lib
4 - alsa-utils
5 - alsa-plugins
6 - alsa-oss

then reboot system with sudo shutdown -r now

- - -

these steps didn't replace the missing library but fixed the issue of no sound in firefox32 on my AMD64 Kubuntu system...

i will add a note that i initially tried to solve this using some other references to using a gentoo package emul-linux-x86-soundlibs-2.5.tar.bz2 (untar and copy the files to the correct places) but it ended up "breaking" ALSA altogether, thus my reinstallation as documented above

---

### Post by JAmerican on 2007-06-30
This didn't work for me :( I only have music and video +  audio playing correctly but Flash only shows but there is no audio.

I keep getting that **libasound_module_pcm_empty.so** error

JAmerican

---

### Post by JAmerican on 2007-06-30
FIXED!!! NO MORE ERROR. Flash works great :popcorn:

Look here...

[http://ubuntuforums.org/showpost.php?p=2941067&postcount=32](http://ubuntuforums.org/showpost.php?p=2941067&postcount=32)

JAmerican

---

### Post by algebraist on 2007-07-02
JAmerican, your link ([http://ubuntuforums.org/showpost.php...7&postcount=32](http://ubuntuforums.org/showpost.php...7&postcount=32)) does not seem to point towards the solution -- am I missing something?

I am still having the error 
    "Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so"

when I try to run Skype 1.4 on Feisty Kubuntu. No sound. :(

---

### Post by JAmerican on 2007-07-02
> **algebraist said:**
> JAmerican, your link ([http://ubuntuforums.org/showpost.php...7&postcount=32](http://ubuntuforums.org/showpost.php...7&postcount=32)) does not seem to point towards the solution -- am I missing something?

I am still having the error 
    "Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so"

when I try to run Skype 1.4 on Feisty Kubuntu. No sound. :(

What are your hardware specs?

I basically reinstalled Ubuntu in my root partition. My sound was working just low so I increased the volume in alsamixer. Then I installed the [nspluginwrapper]("http://ubuntuforums.org/showthread.php?t=425672") and flash worked great.

JAmerican

---

### Post by woodyst on 2008-01-07
If you use 64bit GNU/Linux distribution:

I had the same problem and solved it compiling a 32bit version of alsa-lib 1.0.15. My system had different alsa lib versions intalled for 64 and 32 bit (Debian GNU/Linux).

If you want to try it you'll have to install linux32 binary and export some environment vars before compiling. linux32 changes output of uname for 32 bit cpu. This is how I did it:

I downloaded alsa-lib-1.0.15 sources, unpacked it and then cd into sources dir. Then:

$ export CFLAGS=-m32
$ export CXXFLAGS=$CFLAGS
$ linux32 ./configure --prefix=/home/edi/src/32/alsa/dist
# You have to change prefix according to your needs (I recomend a new empty directory, because you'll only need lib stuff and not the rest.
$ make -j2
$ make -j2 install

It puts all in /home/edi/src/32/alsa/dist. Then copy all files in /home/edi/src/32/alsa/dist/lib/* to /usr/lib32 or whenever your 32 lib files are in your system (You can make a backup first, but remember than a simple apt-get install --reinstall ia32-libs is sufficient to restore old libs).

I hope this will help you.

Regads.

---

