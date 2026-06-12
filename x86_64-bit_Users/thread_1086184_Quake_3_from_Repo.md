---
title: "Quake 3 from Repo"
date: 2009-03-03
forum: x86 64-bit Users
---

### Post by Scott O'Nanski on 2009-03-03
Has anyone had any success installing, and running, Quake3-Data from the repository?

I've searched all over the place trying to get Quake 3 arena to run on my machine but to no avail.

I'm not looking to emulate, I want use the Linux version.

I want to stay clear of ioquake as well. The documentation for installing it is horrible, if not non-existent.

Thanks.

---

### Post by nzadLithium on 2009-03-04
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

That guide explains how to install Q3. If you use the icculus version on that page, I reckon you probably won't have a problem with sound. However if your using the id version of quake3 then you might want to try this 'hack' [http://nullkey.ath.cx/et-sdl-sound/quake3-sdl-sound.gz](http://nullkey.ath.cx/et-sdl-sound/quake3-sdl-sound.gz) which makes your sound work nicely with alsa :D

(page about the hack is here [http://nullkey.ath.cx/et-sdl-sound/](http://nullkey.ath.cx/et-sdl-sound/))

---

### Post by Scott O'Nanski on 2009-03-04
> **nzadLithium said:**
> [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

That guide explains how to install Q3. If you use the icculus version on that page, I reckon you probably won't have a problem with sound. However if your using the id version of quake3 then you might want to try this 'hack' [http://nullkey.ath.cx/et-sdl-sound/quake3-sdl-sound.gz](http://nullkey.ath.cx/et-sdl-sound/quake3-sdl-sound.gz) which makes your sound work nicely with alsa :D

(page about the hack is here [http://nullkey.ath.cx/et-sdl-sound/](http://nullkey.ath.cx/et-sdl-sound/))

Thanks, nzad. I'll check it out and report back with how everything went.

---

### Post by Scott O'Nanski on 2009-03-04
Here's the problem I'm running into...

```
Uncompressing Quake III Arena Point Release 1.32b............................................
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com
The setup program seems to have failed on unknown/glibc-2.0

Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com

```

Any ideas?

---

### Post by marcelkoopman on 2009-03-04
> **Scott O'Nanski said:**
> Here's the problem I'm running into...

```
Uncompressing Quake III Arena Point Release 1.32b............................................
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com
The setup program seems to have failed on unknown/glibc-2.0

Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com

```

Any ideas?

Quake 3 is a bit outdated. Why not have a PS3? I've got that and it's great, my home pc is for development and internet.

---

### Post by stchman on 2009-03-04
I can run Quake III very well using WINE.  Since QIII is an openGL game all you need WINE for is to run the executables.  The video card handles all the openGL stuff.

---

### Post by nzadLithium on 2009-03-05
This problem occurs cause your running 64bit, the installer does not understand how to install quake3 on your pc. Basically what you need to do is get this file:
[ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run](ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run)

make sure you have permissions to execute the file
chmod a+x linuxq3apoint-1.32b-3.x86.run

One possibility that may work and would be the easiest way to go about it is to run that file from a terminal like this:

```
su
linux32 sh linuxq3apoint-1.32b-3.x86.run
```

That may cause the installer to run. 
Failing that you can make it just unpack the files in the installer to a directory, although you will then have to put quake3 in the right place yourself. (I think the suggested path is /usr/local/games/quake3?).
You can do that like this:
linuxq3apoint-1.32b-3.x86.run --keep

You can then follow these instructions provided by ID to copy the remaining needed files from your quake3 arena/quake 3 team arena cd.
[http://zerowing.idsoftware.com/linux/q3a/INSTALL](http://zerowing.idsoftware.com/linux/q3a/INSTALL)

Once this is done, if you have not already, you will need to install the 32bit library's required by the game. I'm not sure which libraries you actually need, but I think this may be all you need:

```
sudo apt-get install ia32-libs
```

This will install id's official version of quake3. You should still look at step 3 on that other tutorial so you can setup punkbuster.

---

### Post by nzadLithium on 2009-03-05
Ah theres also a further update to the client and server. You can get it here:
[ftp://ftp.idsoftware.com/idstuff/quake3/quake3-1.32c.zip](ftp://ftp.idsoftware.com/idstuff/quake3/quake3-1.32c.zip)

you will need to get the binaries from in the linux folder in that zip and copy and paste them over the top of your existing binaries from the previous installation.

---

### Post by Yashiro on 2009-03-05
[http://zerowing.idsoftware.com/linux/q3a/#install](http://zerowing.idsoftware.com/linux/q3a/#install)

Just follow the instructions.

---

### Post by nzadLithium on 2009-03-07
Those instructions don't tell marcelkoopman everything thats needed to install and run quake3 on ubuntu 64bit, thats why I explained it myself.

---

### Post by Yashiro on 2009-03-08
Thing is, they do. You just need to read it all, including the notes about the expected error with missing 32bit libs.

---

### Post by rajeev1204 on 2009-03-08
> **stchman said:**
> I can run Quake III very well using WINE.  Since QIII is an openGL game all you need WINE for is to run the executables.  The video card handles all the openGL stuff.


I second that. Use it with wine and it runs flawlessly.

Dont have to try these sound hacks etc,I could never get quake3 to even install properly.ioquake3 or whatever.



regards

rajeev

---

### Post by nzadLithium on 2009-03-08
> Thing is, they do. You just need to read it all, including the notes about the expected error with missing 32bit libs. 

Correct me if i'm wrong but I don't remember it saying anything along the lines of run "sudo apt-get install ia32-libs", the closest it gets to that is saying that your distro must have support for 32bit binary's :D

> Use it with wine and it runs flawlessly. Except punkbuster. Which means if you want online play your very limited in the number of servers you can play on (thats if quake 3 still has servers? I haven't played it, just games based on same engine :p).

---

