---
title: "Does the KXStudio Respository No Longer Exist? &quot;Or Failed to load DLL wineaiso.dll&quot;"
date: 2016-10-15
forum: Wine
---

### Post by muddpup64 on 2016-10-15
Hello all!

 I'm in the middle of cobbling together Amplitude 4 through wine but first I need to (or so I've read) install something called WineASIO. When I first looked into trying to install it, the easiest way appeared to be using the kxStudio repository. But for some reason, even after following these handy dandy instructions: [http://kxstudio.linuxaudio.org/Repositories](http://kxstudio.linuxaudio.org/Repositories), I always run into this problem```
 E: Unable to locate package kxstudio-repos 
```.

So that's when I decided to try a different route. After all, KXStudio may not support 16.04.

That's when I came across this: [http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_WineASIO](http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_WineASIO). Again, however, I ran into another hitch. I can not seem to get the damn thing to register. I get this message ```
 Failed to load DLL wineasio.dll 
``` when I run [B]regsvr32 wineasio.dll.

Note:[/B] The cockos tutorial is missing some steps for 64bit. I found a better set of instructions from the README file attached with WineASIO download.

README.txt

```
 ONTENTS
========
1. Installation
2. General Information
3. Change Log
4. Legal Stuff

1. INSTALLATION
---------------

Copy the file asio.h from Steinberg's ASIO SDK to the wineasio source
directory.

Wineasio by default uses 32 bit float as sample format (the native format used
by Jack), if this causes a problem for an ASIO host, wineasio can be built to
use 32 bit integer by defining the ASIOST32INT variable.  Do this by defining
ASIOST32INT in the source code or by passing it as an argument to the compiler.

Do the following to build for 32 bit Wine.
# make clean
# make

To install (substite with the path to the 32 bit wine libs for your distro).
# sudo cp wineasio.dll.so /usr/lib32/wine/wineasio.dll.so 

To build for 64bit Wine a shellscript has been added to modify asio.h and make
it compatible with both 32 and 64bit Wine/Linux.  A separate Makefile has also
been added for 64bit.

Do the following to build for 64bit Wine.
# ./prepare_64bit_asio
# make clean
# make -f Makefile64

To install (substite with the path to the 64 bit wine libs for your distro).
# sudo cp wineasio.dll.so /usr/lib/wine/wineasio.dll.so 

Finally the dll must be registered in the wineprefix.
For both 32 and 64 bit wine do:
# regsvr32 wineasio.dll

On a 64 bit system with wine supporting both 32 and 64 applications, regsrv32
will register the 32 bit driver in a 64 bit prefix, use the following command
to register the 64 bit driver in a 64 bit wineprefix:

# wine64 regsvr32 wineaiso.dll

regsvr32 registers the ASIO COM object in the default prefix "~/.wine".
To use another prefix specify it explicitly, like:
# env WINEPREFIX=~/asioapp regsvr32 wineasio.dll

2. GENERAL INFORMATION
----------------------

The wineasio driver has been almost completely refactored, so the changes are
far too many to explain in detail. These are some of the more obvious changes:

Wineasio takes advantage of a new function in the jack api, which lets jack
create the wine callback thread.  This results in a much cleaner callback
without having to wait on semaphores, requires jack1 (0.117.0) or jack2 (1.9.4)
or later.

The default sample type has been changed to use ASIOSTFloat32LSB, which is the
native format of jack, and allows the removal of the sample rate conversion
from the processing callback.

Wineasio can now slave to the jack transport.

Support has been added for jack's bufsize_callback(), meaning that asio apps
get notified if the jack buffersize changes.

CreateBuffers() can now change jack's buffersize if so desired.  Must be
enabled in the registry, see below.

The old configuration file has been removed and been replaced by a registry key
(HKEY_CURRENT_USER\Software\Wine\WineASIO).  All these options can be overriden
by an environment variable.  The key is automatically created with default
values if it doesn't exist when the driver initializes. It contains the
following values:

[Number of inputs] & [Number of outputs]
These two settings control the number of jack ports that wineasio will try to
open.  Defaults are 16 in and 16 out.  Environment variables are
WINEASIO_NUMBER_INPUTS and WINEASIO_NUMBER_OUTPUTS

[Autostart server]
Defaults to off (0), setting it to 1 enables wineasio to launch the jack
server.  See the jack documentation for further details. The environment
variable is WINEASIO_AUTOSTART_SERVER, and it can be set to on or off.

[Connect to hardware]
Defaults to on (1), makes wineasio try to connect the asio channels to the
physical I/O ports on your hardware.  Setting it to 0 disables it. The
environment variable is WINEASIO_CONNECT_TO_HARDWARE, and it can be set to on
or off.

[Fixed buffersize]
Defaults to on (1) and is the old behaviour where the buffer size is controlled
by jack and wineasio has no say in the matter.  When set to 0, an asio app will
be able to change the jack buffer size when calling CreateBuffers(). The
environment variable is WINEASIO_FIXED_BUFFERSIZE and it can be set to on or
off.

[Preferred buffersize]
Defaults to 1024, and is one of the sizes returned by GetBufferSize(), see the
ASIO documentation for details.  Must be a power of 2. The other values
returned by the driver are hardcoded in the source, see ASIO_MINIMUM_BUFFERSIZE
which is set at 16, and ASIO_MAXIMUM_BUFFERSIZE which is set to 8192. The
environment variable is WINEASIO_PREFERRED_BUFFERSIZE.  Be careful, if you set
a size that isn't supported by the backend, the jack server will most likely
shut down, might be a good idea to change ASIO_MINIMUM_BUFFERSIZE and
ASIO_MAXIMUM_BUFFERSIZE to values you know work on your system before building.

In addition there is a WINEASIO_CLIENT_NAME environment variable, that
overrides the JACK client name derrived from the program name.

3. CHANGE LOG
-------------

0.9.2
28-OCT-2013: Add 64bit support and some small fixes

0.9.1
15-OCT-2013: Various bug fixes (JH)

0.9.0
19-FEB-2011: Nearly complete refactoring of the wineasio codebase (asio.c) (JH)

0.8.1:
05-OCT-2010: Code from Win32 callback thread moved to JACK process callback, except for bufferSwitch() call.
05-OCT-2010: Switch from int to float for samples.

0.8.0:
08-AUG-2010: Forward port JackWASIO changes... needs testing hard. (PLJ)

0.7.6:
27-DEC-2009: Fixes for compilation on 64bit platform. (PLJ)

0.7.5:
29-Oct-2009: Added fork with call to qjackctl from ASIOControlPanel(). (JH)
29-Oct-2009: Changed the SCHED_FIFO priority of the win32 callback thread. (JH)
28-Oct-2009: Fixed wrongly reported output latency. (JH)

0.7.4:
08-APR-2008: Updates to the README.TXT (PLJ)
02-APR-2008: Move update to "toggle" to hopefully better place (PLJ)
24-MCH-2008: Don't trace in win32_callback.  Set patch-level to 4. (PLJ)
09-JAN-2008: Nedko Arnaudov supplied a fix for Nuendo under WINE.

0.7.3:
27-DEC-2007: Make slaving to jack transport work, correct port allocation bug. (RB)

0.7:
01-DEC-2007: In a fit of insanity, I merged JackLab and Robert Reif code bases. (PLJ)

0.6:
21-NOV-2007: add dynamic client naming (PLJ)

0.0.3:
17-NOV-2007: Unique port name code (RR)

0.5:
03-SEP-2007: port mapping and config file (PLJ)

0.3:
30-APR-2007: corrected connection of in/outputs (RB)

0.1:
???????????: Initial RB release (RB)

0.0.2:
12-SEP-2006: Fix thread bug, tidy up code (RR)

0.0.1:
31-AUG-2006: Initial version (RR)

4. LEGAL STUFF
--------------

Copyright (C) 2006 Robert Reif
Portions copyright (C) 2007 Ralf Beck
Portions copyright (C) 2007 Johnny Petrantoni
Portions copyright (C) 2007 Stephane Letz
Portions copyright (C) 2008 William Steidtmann
Portions copyright (C) 2010 Peter L Jones
Portions copyright (C) 2010 Torben Hohn
Portions copyright (C) 2010 Nedko Arnaudov
Portions copyright (C) 2011 Christian Schoenebeck
Portions copyright (C) 2013 Joakim Hernberg

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA
 
```  

I may have forgot to mention some things. If there is a problem just let me know. And thank you guys!

---

### Post by CrocoDuck on 2016-10-15
KXStudio still exists and it is very well active. After you modify the software sources you have to refresh the local package database. Did you run this?

```
sudo apt-get update
```

It will pull info from all the repos and allow you to search packages on the newly added ones. Try to install the package after the update command.

As for registering wineasio I am afraid I cannot help. The last time I installed it was something like 8 years ago... god I am getting old...

---

### Post by muddpup64 on 2016-10-15
>  KXStudio still exists and it is very well active. After you modify the  software sources you have to refresh the local package database. Did you  run this?

     Code:
     sudo apt-get update 
It will pull info from all the repos and allow you to search  packages on the newly added ones. Try to install the package after the  update command.

As for registering wineasio I am afraid I cannot help. The last time I  installed it was something like 8 years ago... god I am getting old...                  

I did indeed try that. No beuno.


To be honest with you, I believe it would be much easier to figure out why I can't register. I already have it installed just need to register. If we go the other route, vie KXSudio, I'll have to reinstall the whole thing again. And if that does work we can fall back on the other idea. I've done some much hard work to get to this point. Lol, why let it go to waste?

---

### Post by howefield on 2016-10-16
Thread moved to the "*Wine*" forum.

---

### Post by CrocoDuck on 2016-10-16
> **muddpup64 said:**
> 
To be honest with you, I believe it would be much easier to figure out why I can't register. I already have it installed just need to register.


Yeah, indeed. But I think I need to point out that probably you are just querying the repos in a wrong way. This error:

```

 E: Unable to locate package kxstudio-repos

```

makes me think you entered this command:
```

sudo apt-get install kx-studio-repos

```

which makes no sense. Once the repos are added, just do
```

sudo apt-get install wineasio

```

or whatever package in the repos you need.

Perhaps, you got confused by the [kx-studio-repos.deb package here]("http://kxstudio.linuxaudio.org/Repositories"). That is supposed to be downloaded and installed with dpkg or gdebi and its function is to add the repos in your system. You can either do that OR follow the manual instructions below. Once that is done, just query the repos directly.

Apparently, wineasio.dll will not register if you did not properly installed wineasio for your distribution. Parhaps [this]("https://www.linuxmusicians.com/viewtopic.php?t=10450") will help.

Also, the Reaper page you linked is very outdated (2011). It still lists RemixOS, which died something like around 2013...

---

### Post by muddpup64 on 2016-10-16
> **CrocoDuck said:**
> Yeah, indeed. But I think I need to point out that probably you are just querying the repos in a wrong way. This error:

```

 E: Unable to locate package kxstudio-repos

```

makes me think you entered this command:
```

sudo apt-get install kx-studio-repos

```

which makes no sense. Once the repos are added, just do
```

sudo apt-get install wineasio

```

or whatever package in the repos you need.

Perhaps, you got confused by the [kx-studio-repos.deb package here]("http://kxstudio.linuxaudio.org/Repositories"). That is supposed to be downloaded and installed with dpkg or gdebi and its function is to add the repos in your system. You can either do that OR follow the manual instructions below. Once that is done, just query the repos directly.

Apparently, wineasio.dll will not register if you did not properly installed wineasio for your distribution. Parhaps [this]("https://www.linuxmusicians.com/viewtopic.php?t=10450") will help.

Also, the Reaper page you linked is very outdated (2011). It still lists RemixOS, which died something like around 2013...

I don't recalled posting a reaper link. Do you need both Reaper and WineASIO to function?

This post "[this"]("https://www.linuxmusicians.com/viewtopic.php?t=10450") doesn't really help much seeing as how I'm 16.04 64 bit. The README.txt file already gives me step by step instructions on how to install it. Unless they are wrong, there has to be another issue

And yes, I did use this command: 
sudo apt-get install kxstudio-repos

I'm sure I used another command at some point that was supposed to do the same thing for me, I don't remember what it was, however. If I'm doing this wrong, please let me know.


Or perhaps I haven't explained myself well. It's not that I can't install WineASIO but rather I can't gain access to the kxstudio repository to then install WineASIO.

---

### Post by CrocoDuck on 2016-10-16
> **muddpup64 said:**
> I don't recalled posting a reaper link. Do you need both Reaper and WineASIO to function?
> **muddpup64 said:**
> That's when I came across this: [http://wiki.cockos.com/wiki/index.ph...uring_WineASIO]("http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_WineASIO").
That link is from Reaper wiki and no, you don't need Reaper.

> **muddpup64 said:**
> This post "[this"]("https://www.linuxmusicians.com/viewtopic.php?t=10450") doesn't really help much seeing as how I'm 16.04 64 bit
Did you see that after a few posts FalkTX explains how to install WineASIO on regular Ubuntu using KXStudio repos? If you have Ubuntu 64 bit perhaps you just have to make sure you install the appropriate wineasio version. I cannot remember very well how it is done, but I think that for some reason you still need to install (whatever the software source is) the 32 version or else regsvr32 will not work. Not sure if this makes sense, but try to run
```

regsvr64 windeasio.dll

```
and see what happens.

> **muddpup64 said:**
> I'm sure I used another command at some point that was supposed to do  the same thing for me, I don't remember what it was, however. If I'm  doing this wrong, please let me know.
It does not works like that. A repository is a place in the internet where you can download packages. When you add a repo to your system you are telling to the system to look up in this place in the internet every time you want to install a package. I get you already added the KXStudio repos, so that is fine. sudo apt-get install <package name> will search into each repo you added (which are places in the internet) for <package name> and it will install it for you. sudo apt-get install kxstudio-repos is nonsense as a package called kxstudio-repos is not stored in the repos. It is just there, [in that page]("http://kxstudio.linuxaudio.org/Repositories"), to be manually downloaded and manually installed if you want to add the repo easily. I think the instructions are pretty clear.

Sorry if this seems out of topic, but I want to make it clear for you:
Adding a repos does not install anything, it just add an internet location into a list. Your package manager will search for software you want to install among the locations in this list.

To check whether you have access to KXStudio repos copy and paste the output of sudo apt-get update here.

---

### Post by muddpup64 on 2016-10-16
> **CrocoDuck said:**
> That link is from Reaper wiki and no, you don't need Reaper.


Did you see that after a few posts FalkTX explains how to install WineASIO on regular Ubuntu using KXStudio repos? If you have Ubuntu 64 bit perhaps you just have to make sure you install the appropriate wineasio version. I cannot remember very well how it is done, but I think that for some reason you still need to install (whatever the software source is) the 32 version or else regsvr32 will not work. Not sure if this makes sense, but try to run
```

regsvr64 windeasio.dll

```
and see what happens.


It does not works like that. A repository is a place in the internet where you can download packages. When you add a repo to your system you are telling to the system to look up in this place in the internet every time you want to install a package. I get you already added the KXStudio repos, so that is fine. sudo apt-get install <package name> will search into each repo you added (which are places in the internet) for <package name> and it will install it for you. sudo apt-get install kxstudio-repos is nonsense as a package called kxstudio-repos is not stored in the repos. It is just there, [in that page]("http://kxstudio.linuxaudio.org/Repositories"), to be manually downloaded and manually installed if you want to add the repo easily. I think the instructions are pretty clear.

Sorry if this seems out of topic, but I want to make it clear for you:
Adding a repos does not install anything, it just add an internet location into a list. Your package manager will search for software you want to install among the locations in this list.

To check whether you have access to KXStudio repos copy and paste the output of sudo apt-get update here. I believe the very bottom is where you'll be interested.

I believe the very bottom it where you'll find the most interest.

```
 Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]   
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:4 http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu xenial InRelease
Ign:5 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial InRelease  
Ign:6 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial Release    
Hit:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Ign:8 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en_US
Hit:12 https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu xenial InRelease
Ign:13 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main DEP-11 64x64 Icons
Err:8 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:9 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial/main DEP-11 64x64 Icons
Fetched 190 kB in 6s (28.2 kB/s)                                               
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/kxstudio-team/kxstudio/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
 
```

I'm still learning a lot of the linux commands. I had a feeling that sudo apt-get install kxstudio-repos was a little sketchy. I don't remember what the exact command needed to add repositories so that they are visable to my box, (is it wget, cp, or dpkg? IDK) but either way I KNOW I can't accesss them. I've done a lot of research I it's hard to keep track of what all I've read but at some point I attempted to add the repo with the return of an error message. Perhaps I need to be sat down like a child and taught how.

regsvr64 windeasio.dll returns:
```
 regsvr64: command not found 
```

sudo apt-get install regsvr64 returns:
```
 E: Unable to locate package regsvr64 
```

This is what the README.txt file suggests:
```
 Finally the dll must be registered in the wineprefix.
For both 32 and 64 bit wine do:
# regsvr32 wineasio.dll

On a 64 bit system with wine supporting both 32 and 64 applications, regsrv32
will register the 32 bit driver in a 64 bit prefix, use the following command
to register the 64 bit driver in a 64 bit wineprefix:

# wine64 regsvr32 wineaiso.dll 
```

---

### Post by deadflowr on 2016-10-16
Remove the kxstudio-team ppa.
As it won't work on 16.04.
The kxstudio-debian ppa is functional on 16.04, though.

Typically when one repo is dead and gone and the return is a 404, as the kxstudio-team ppa is doing, the system ignores updates from every other repo, since it cannot determine whether or not packages from the dead repo were critical.
disabling that ppa should allow the package listings to update properly, and thus allow package upgrades to work, and then allow the proper installation of the proper repo for kxstudio.
if that make sense.

---

### Post by muddpup64 on 2016-10-16
Removing kxstudio-team solved it!! 
After I ran sudo apt-get update:
```
 it:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease          
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:3 http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu xenial InRelease
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]   
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:6 https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu xenial InRelease
Fetched 190 kB in 4s (42.9 kB/s)
Reading package lists... Done
 
```

But! I still am unable to install WineASIO. :(
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wineasio 
```




EDIT: I have no idea what happened...

```
 muddpup@Foghorn:/$ wine64 regsvr32 wineasio
Successfully registered DLL wineasio 
```



*SIGH* I'm sorry. I still can not get the amp programs I'm running to see WineASIO or Jackd (which is what I though the purpose of WineASIO was).
I tried this to no luck: [https://www.youtube.com/watch?v=gjbSaOAdm2Y](https://www.youtube.com/watch?v=gjbSaOAdm2Y)

---

### Post by deadflowr on 2016-10-16
Well now that the kxstudio-team ppa is gone, you should have no problem running the commands from here, 
[http://kxstudio.linuxaudio.org/Repositories]("http://kxstudio.linuxaudio.org/Repositories")
right?
Which is where the wineasio package seems to be.

A quick look at the kxstudio-debian ppa while functuional for xenial, is rather light on packages (it only contains the kxstudio-artwork package; whereas the the packages in the ppa for older releases like 14.04/trusty have several other packages like kxstudio-meta and kxstudio-repos.

For reference, what the trusty and xenial ppa pages look like for the kxstudio-debian ppa:
Trusty[https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=trusty]("https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=trusty")
Xenial[https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=xenial]("https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=xenial")

Not sure if that make sense.

---

### Post by muddpup64 on 2016-10-16
> **deadflowr said:**
> Well now that the kxstudio-team ppa is gone, you should have no problem running the commands from here, 
[http://kxstudio.linuxaudio.org/Repositories](http://kxstudio.linuxaudio.org/Repositories)
right?
Which is where the wineasio package seems to be.

A quick look at the kxstudio-debian ppa while functuional for xenial, is rather light on packages (it only contains the kxstudio-artwork package; whereas the the packages in the ppa for older releases like 14.04/trusty have several other packages like kxstudio-meta and kxstudio-repos.

For reference, what the trusty and xenial ppa pages look like for the kxstudio-debian ppa:
Trusty[https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=trusty](https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=trusty)
Xenial[https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=xenial](https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio?field.series_filter=xenial)

Not sure if that make sense.

I followed this: [http://kxstudio.linuxaudio.org/Repositories](http://kxstudio.linuxaudio.org/Repositories) and still get this:
```
 muddpup@Foghorn:~$ sudo apt-get install wineasioReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wineasio
 
```

---

### Post by crashedthecar on 2016-11-03
If you are willing to try

I just found installing those 2 deb packages, then in synaptic search kxstudio meta, install the wine meta package.

then register the dll

Does the trick for me

---

