---
title: "ia32-libs"
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by grossaffe on 2008-03-10
for the longest time, i've been trying to get flash installed on my 64-bit ubuntu installation, but it appears that i need "ia32-libs".  unfortunately, this fabled package doesn't seem to exist in any of the repositories.  i couldn't get any straight answers in the flash thread since someone else would always post with another problem before anyone answered mine.  so, where the heck do i find ia32-libs and how do i install it (My computer is running on an intel core2duo, if that means anything).

---

### Post by whoop on 2008-03-10
Have not tried it myself but you could try installing it using getlibs:
[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

hope this helps

---

### Post by Kilz on 2008-03-10
> **grossaffe said:**
> for the longest time, i've been trying to get flash installed on my 64-bit ubuntu installation, but it appears that i need "ia32-libs".  unfortunately, this fabled package doesn't seem to exist in any of the repositories.  i couldn't get any straight answers in the flash thread since someone else would always post with another problem before anyone answered mine.  so, where the heck do i find ia32-libs and how do i install it (My computer is running on an intel core2duo, if that means anything).

It exists and here is a [list of download locations]("http://packages.ubuntu.com/gutsy/amd64/ia32-libs/download") strait from the repositories. But you might want to [read this post first.]("http://ubuntuforums.org/showpost.php?p=4417385&postcount=914") Because if you dont fix the issue it may stop other packages from downloading , like security updates.

---

### Post by grossaffe on 2008-03-10
> **Kilz said:**
> It exists and here is a [list of download locations]("http://packages.ubuntu.com/gutsy/amd64/ia32-libs/download") strait from the repositories. But you might want to [read this post first.]("http://ubuntuforums.org/showpost.php?p=4417385&postcount=914") Because if you dont fix the issue it may stop other packages from downloading , like security updates.

i already tried changing repositories.  tried several of them, none of which had ia32-libs in them.  some of them wouldn't even reload, i would get an error when trying to reload the list.

edit: i just went through the list of mirrors for the ia32-libs and found one that worked, but i couldn't install THAT because i was missing yet another dependency! (lib32gcc1) this is getting just a little aggravating.

---

### Post by Kilz on 2008-03-10
> **grossaffe said:**
> i already tried changing repositories.  tried several of them, none of which had ia32-libs in them.  some of them wouldn't even reload, i would get an error when trying to reload the list.

edit: i just went through the list of mirrors for the ia32-libs and found one that worked, but i couldn't install THAT because i was missing yet another dependency! (lib32gcc1) this is getting just a little aggravating.

It sounds like you are using a bad mirror, or have sources.list problems. You are talking about common packages.

---

### Post by Cappy on 2008-03-10
If ```
uname -m
```
doesn't print out "x86_64" then you aren't running 64-bit Ubuntu and you won't have ia32-libs.

If you ARE on 64-bit then make sure to ```
sudo apt-get update
```
before you try
```
sudo apt-get install ia32-libs
```

---

### Post by warp99 on 2008-03-11
They are located in the universe repository:

[http://packages.ubuntu.com/gutsy/ia32-libs](http://packages.ubuntu.com/gutsy/ia32-libs)

and lib32gcc1 is located in the main repository:

[http://packages.ubuntu.com/gutsy/lib32gcc1](http://packages.ubuntu.com/gutsy/lib32gcc1)

Someone else also mentioned they are very common packages. Using the Synaptic   Package manager you can enable the universe repository by going under **Settings > Repositories** then ticking the box **"Community-maintained Open Source software (universe)"**. 

After you reload the repositories the ia32-libs will be available for you to install. ;)

---

### Post by grossaffe on 2008-03-11
> **warp99 said:**
> They are located in the universe repository:

[http://packages.ubuntu.com/gutsy/ia32-libs](http://packages.ubuntu.com/gutsy/ia32-libs)

and lib32gcc1 is located in the main repository:

[http://packages.ubuntu.com/gutsy/lib32gcc1](http://packages.ubuntu.com/gutsy/lib32gcc1)

Someone else also mentioned they are very common packages. Using the Synaptic   Package manager you can enable the universe repository by going under **Settings > Repositories** then ticking the box **"Community-maintained Open Source software (universe)"**. 

After you reload the repositories the ia32-libs will be available for you to install. ;)

ok, i got the universe repository now, and it does have ia32-libs.  unfortunately it refuses to install because:```

ia32-libs:
 Depends: lib32gcc1  but it is not installable
 Depends: libc6-i386 (>=2.3.6-2) but it is not installable
 Depends: lib32z1  but it is not installable
 Depends: lib32stdc++6  but it is not installable
 Depends: lib32asound2  but it is not installable
 Depends: lib32ncurses5  but it is not installable

```

---

### Post by Jouke74 on 2008-03-11
Eh double post, see below...

---

### Post by Jouke74 on 2008-03-11
Check your internet connection and your repositories, see also for example if you can get updates, because here the things go wrong and you won't be able to install anything decent. After that install "build-essential" and Ia32-Libs you will need them sooner of later. Also make sure you have enough disk space still :-)

---

### Post by Kilz on 2008-03-11
> **grossaffe said:**
> ok, i got the universe repository now, and it does have ia32-libs.  unfortunately it refuses to install because:```

ia32-libs:
 Depends: lib32gcc1  but it is not installable
 Depends: libc6-i386 (>=2.3.6-2) but it is not installable
 Depends: lib32z1  but it is not installable
 Depends: lib32stdc++6  but it is not installable
 Depends: lib32asound2  but it is not installable
 Depends: lib32ncurses5  but it is not installable

```

That is the same error we found in the flash thread [Read this post]("http://ubuntuforums.org/showpost.php?p=4416703&postcount=913") and the answer is [in this post.]("http://ubuntuforums.org/showpost.php?p=4416703&postcount=914") The whole discussion on this error [started here ]("http://ubuntuforums.org/showthread.php?p=4417385") in post 911. You are using a bad repository mirror.

---

### Post by warp99 on 2008-03-11
> **grossaffe said:**
> ok, i got the universe repository now, and it does have ia32-libs.  unfortunately it refuses to install because:```

ia32-libs:
 Depends: lib32gcc1  but it is not installable
 Depends: libc6-i386 (>=2.3.6-2) but it is not installable
 Depends: lib32z1  but it is not installable
 Depends: lib32stdc++6  but it is not installable
 Depends: lib32asound2  but it is not installable
 Depends: lib32ncurses5  but it is not installable

```

Something is very very wrong. Those packages are available in the main repositories which should be enabled by default. Open a terminal and do the following:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.bak
```

then use the attached sources.txt file instead (see bottom) and do the following:

```
sudo cp sources.txt /etc/apt/sources.list
```

then update the package manager:

```
 sudo apt-get update
```

after that go into Synaptic, install ia32-libs and everything should be fine. :)

Edit: If you want to turn off the universe and multiverse repositories after you install ia32-libs just go into Synaptic under Settings > Repositories then un-tick the boxes for universe and multiverse, then reload.

Edit: Also in Synaptic under the Settings > Repositories dialog box go to the "updates" tab and un-tick the "Unsupported updates (gutsy-backports)" box. You can install them if you want, but they may be more trouble then you can handle.

---

### Post by grossaffe on 2008-03-11
> **warp99 said:**
> Something is very very wrong. Those packages are available in the main repositories which should be enabled by default. Open a terminal and do the following:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.bak
```

then use the attached sources.txt file instead (see bottom) and do the following:

```
sudo cp sources.txt /etc/apt/sources.list
```

then update the package manager:

```
 sudo apt-get update
```

after that go into Synaptic, install ia32-libs and everything should be fine. :)

Edit: If you want to turn off the universe and multiverse repositories after you install ia32-libs just go into Synaptic under Settings > Repositories then un-tick the boxes for universe and multiverse, then reload.

Edit: Also in Synaptic under the Settings > Repositories dialog box go to the "updates" tab and un-tick the "Unsupported updates (gutsy-backports)" box. You can install them if you want, but they may be more trouble then you can handle.
apparently apt-get update doesn't work because i need to run apt-get update :mad:
```
W: GPG error: http://packages.medibuntu.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by warp99 on 2008-03-11
> **grossaffe said:**
> apparently apt-get update doesn't work because i need to run apt-get update :mad:
```
W: GPG error: http://packages.medibuntu.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

It worked you just need the signing key for packages.medibuntu.org to get rid of the error message, it's nothing fatal:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Now the error message will go away. Mediabuntu is a **very** nice repository of software that cannot be included in the ubuntu repositories:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Check it out. You won't be disappointed. ;)

---

### Post by grossaffe on 2008-03-11
> **warp99 said:**
> It worked you just need the signing key for packages.medibuntu.org to get rid of the error message, it's nothing fatal:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Now the error message will go away. Mediabuntu is a **very** nice repository of software that cannot be included in the ubuntu repositories:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Check it out. You won't be disappointed. ;)

well right now i'm in the middle of updating, i think the list you gave me told my computer that it needed lots of updates or something, because it found 205 updates.
is that just one line of code?  because it looks like several commands strung together.

edit: after the updates and installation of ia32-libs and the flash plugin thing, it all works.  thanks for the help.

---

### Post by warp99 on 2008-03-11
> **grossaffe said:**
> well right now i'm in the middle of updating, i think the list you gave me told my computer that it needed lots of updates or something, because it found 205 updates.
is that just one line of code?  because it looks like several commands strung together.

Yes it's one line with several commands strung together. Just cut/paste the entire string into the terminal to add the signing key. It's only to remove the error message, nothing else. You can still download from packages.medibuntu.org, but you will always get this error message unless you add the signing key.

If you have that many updates it must have been a while since you've had a correct sources.list file. :)

---

### Post by grossaffe on 2008-03-11
> **warp99 said:**
> Yes it's one line with several commands strung together. Just cut/paste the entire string into the terminal to add the signing key. It's only to remove the error message, nothing else. You can still download from packages.medibuntu.org, but you will always get this error message unless you add the signing key.

If you have that many updates it must have been a while since you've had a correct sources.list file. :)
i probably never had a correct one, i just recently installed ubuntu onto that laptop.  one of the first things i tried to do after finally getting the proper video-driver working was to get flash working.  i'm wondering if there was something wrong with my install-cd.

---

### Post by warp99 on 2008-03-11
> **grossaffe said:**
> i probably never had a correct one, i just recently installed ubuntu onto that laptop.  one of the first things i tried to do after finally getting the proper video-driver working was to get flash working.  i'm wondering if there was something wrong with my install-cd.

Most likely your sources.list file was corrupted by some install script along the way. You should backup your new sources.list just in case:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.bak
```

Also with the medibuntu repositories enabled you also have access to any special media codecs and the libraries to play encrypted DVDs (libdvdcss). So have fun! :)

---

