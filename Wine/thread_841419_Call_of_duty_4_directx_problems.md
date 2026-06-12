---
title: "Call of duty 4 directx problems"
date: 2008-06-26
forum: Wine
---

### Post by satipera on 2008-06-26
I have installed steam and attempted to run call of duty 4. I get an error that says video card or driver does not support enough textures for the directx code path I am using 7950g2x card and the propriety 3d drivers. All help gratefully received    I am using wine 1.0

---

### Post by piratesmack on 2008-06-26
To run Call of Duty 4, you have to apply a patch and recompile Wine. Otherwise you get that error

I'll write a quick howto Just copy and paste the following in a terminal:

*Note: This is assuming you're using Ubuntu 32bit

```
sudo apt-get remove --purge wine
```


```

sudo apt-get build-dep wine

```

```

wget http://internap.dl.sourceforge.net/sourceforge/wine/wine-1.0.tar.bz2

```

```

tar -xvjf wine-1.0.tar.bz2 && cd wine-1.0

```

```

wget http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch

```

```

patch -p1 < wine-0.9.59-3dmark.patch

```

```

./configure

```

```

make depend && make

```

```

sudo make install

```


After that, the game should run

---

### Post by satipera on 2008-06-26
Thanks for reply but I am running 64 bit I should have included this info

---

### Post by cereal killer on 2008-06-26
Thanks for the info. I did it all and it worked, but I'm not really satisfied with the performance and want to remove COD4.

How do I remove it? The changes made through the process don't really allow me to casually uninstall it.

---

### Post by piratesmack on 2008-06-27
> **cereal killer said:**
> Thanks for the info. I did it all and it worked, but I'm not really satisfied with the performance and want to remove COD4.

How do I remove it? The changes made through the process don't really allow me to casually uninstall it.

yeah you have to lower the settings quite a bit to get it running smoothly. There is also a registry tweak in the wine appdb that improves performance a bit. I'm pretty happy with how smooth I've got it running on my 7600GT

To uninstall:

```

cd wine-1.0

```

```

sudo make uninstall

```

```

rm -rf ~/wine-1.0

```

```

rm -rf ~/.wine

```



To remove menu entries:
-Right-click applications menu
-choose edit menus
-Right-click and delete the "wine" menu entry

---

### Post by piratesmack on 2008-06-27
> **satipera said:**
> Thanks for reply but I am running 64 bit I should have included this info

OK I'll write instructions for 64bit too, then:

```
sudo apt-get remove --purge wine
```


```

sudo apt-get build-dep wine

```

```

wget http://internap.dl.sourceforge.net/sourceforge/wine/wine-1.0.tar.bz2

```

```

tar -xvjf wine-1.0.tar.bz2 && cd wine-1.0

```

```

wget http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch

```

```

patch -p1 < wine-0.9.59-3dmark.patch

```

Then follow the instructions here to compile (skipping the "sudo apt-get build-dep wine" step since we did it already):
[http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873](http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873)

---

### Post by satipera on 2008-06-27
I followed the instructions and got this part way through 

ian@ian-desktop:~$ sudo apt-get remove --purge wine
[sudo] password for ian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  wine*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 54.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152559 files and directories currently installed.)
Removing wine ...
Purging configuration files for wine ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ian@ian-desktop:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for wine could not be satisfied.
ian@ian-desktop:~$

---

### Post by piratesmack on 2008-06-27
> **satipera said:**
> I followed the instructions and got this part way through 

ian@ian-desktop:~$ sudo apt-get remove --purge wine
[sudo] password for ian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  wine*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 54.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152559 files and directories currently installed.)
Removing wine ...
Purging configuration files for wine ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ian@ian-desktop:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for wine could not be satisfied.
ian@ian-desktop:~$


Hm try running:
```

sudo apt-get update

```

And try again


If that doesn't work, try adding the Winehq repositories:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list

```

-Then go to System>Administration>Synaptic Package Manager
-Click Settings>Repositories
-Enable:
```

deb-src http://www.wine.budgetdedicated.com/apt hardy

```

Then run:
```

sudo apt-get update

```

Then try "sudo apt-get build-dep wine" again

---

### Post by Zaiden on 2008-06-27
I've also followed your instructions for the 64Bit setup, but I get the same error, even with the instructions posted before this reply.

---

### Post by thefishki345 on 2008-06-27
thanks for ripping ahaslams and my guide piratesmack.

[http://ubuntuforums.org/showthread.php?t=641987&page=24](http://ubuntuforums.org/showthread.php?t=641987&page=24)

you will find all the information and help you ever need about call of duty 4 in that thread, and if you keep it in the one thread people can help you quicker.

---

### Post by piratesmack on 2008-06-28
> **thefishki345 said:**
> thanks for ripping ahaslams and my guide piratesmack.

[http://ubuntuforums.org/showthread.php?t=641987&page=24](http://ubuntuforums.org/showthread.php?t=641987&page=24)

you will find all the information and help you ever need about call of duty 4 in that thread, and if you keep it in the one thread people can help you quicker.



Ripping your  guide?

I just gave them the same instructions I got from the AppDB:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429)

---

### Post by piratesmack on 2008-06-28
> **Zaiden said:**
> I've also followed your instructions for the 64Bit setup, but I get the same error, even with the instructions posted before this reply.

hm not sure what's going on with Ubuntu 64bit.


check that thread the other guy posted, someone posted a patched 64bit debian package you could use

---

### Post by starcannon on 2008-06-28
Thanks piratesmack, much appreciated.

---

### Post by thefishki345 on 2008-06-28
ok sorry lol.
although there is my guide aswell on the link I gave you guys :p

---

### Post by piratesmack on 2008-06-29
> **thefishki345 said:**
> ok sorry lol.
although there is my guide aswell on the link I gave you guys :p

yes, very helpful thread

---

### Post by eschatologicalhumor on 2008-10-10
Alright, I have gone through this guide (and the other that's linked), with Hardy-AMD64, and it is patched and installed, so good job on the info.

I have a few issues though.

1. First and foremost, my old WINE dir under Applications is still there, not replaced by a new one, and none of my previously installed WINEdows programs work.

2. There is no winecfg installed. Why? I might need that, yes?

3. Synaptic does not show that wine is installed, but I understand why that is. Only problem is, I cannot install playonlinux because it requests that wine should be installed from the repo's. It's not a serious issue, but it's restrictive. Am I going to have other issues like that in the future?

I'm sure there's something else...

I'll try to install something and report back.

---

### Post by eschatologicalhumor on 2008-10-10
> **eschatologicalhumor said:**
> Alright, I have gone through this guide (and the other that's linked), with Hardy-AMD64, and it is patched and installed, so good job on the info.

I have a few issues though.

1. First and foremost, my old WINE dir under Applications is still there, not replaced by a new one, and none of my previously installed WINEdows programs work.

2. There is no winecfg installed. Why? I might need that, yes?

3. Synaptic does not show that wine is installed, but I understand why that is. Only problem is, I cannot install playonlinux because it requests that wine should be installed from the repo's. It's not a serious issue, but it's restrictive. Am I going to have other issues like that in the future?

I'm sure there's something else...

I'll try to install something and report back.

Yes, I knew there was something else!
This is what I get when I run 'winecfg':

sotec@sotec-desktop:~$ winecfg
wine client error:1c: version mismatch 342/339.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

---

### Post by eschatologicalhumor on 2008-10-10
Ok, I figured out the wineserver error. I just killed all wine processes and ran 'winecfg'.

Also, apparently that fixed the issue of my previously installed programs not running as well.

I guess I just solved my own issues. Jesus, it's been a long day...

---

