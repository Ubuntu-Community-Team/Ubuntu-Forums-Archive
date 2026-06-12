---
title: "A bit of help please... 9.04 64-bit"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by arashiko28 on 2009-04-24
Instead of doing several treads for this, I'll just expose all of my misdemeanors in one.

This is the fist time I use 64-bit Ubuntu, I have been an Ubuntu user for
about 2 years now. I'm using 9.04 release, and though I promise to be patient, this has to do with my everyday use of the computer.

1. Amsn doesn't run. I installed the tcl-tk 8.5 before running the installation file and when trying to run it, an error message comes back
> Loading Tkcximage failed. This module is needed to run aMSN. Please compile aMSN first, instructions of how to compile are in the file INSTALL now, as you might know, there is no installation file, I downloaded the script which you're supposed to run on terminal and it does practically the whole work.

2. Can't install adobe reader, tried the 9.1 version, though a couple of thread said that it does run the 32 bit version, for me it shows an error message about wrong architecture. The same goes with 8.1.4.

3. Even though I do have sound in every application and when turning on. Amarok doesn't run properly, it tries to change the playback device, since the other one doesn't work it just stays blank, if I try to play a song, goes mute but on fast forward, like scanning the song.

Note: I've already installed the libraries for 32 bit compatibility.
Installed and have working the flash from the sticky thread.

I do need adobe reader, I have too many books on pdf and evince is good for reading, but not for looking an exact subject on a 4500 pages book.

---

### Post by Kareeser on 2009-04-24
Why don't you install amsn from the repositories?

```
amsn:
  Installed: (none)
  Candidate: 0.97.2~debian-2ubuntu2
  Version table:
     0.97.2~debian-2ubuntu2 0
        500 [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) jaunty/universe Packages
```

Just type:
```
sudo apt-get install amsn
```

---

### Post by arashiko28 on 2009-04-24
Thanks, problem 1 half solved. even though I have amsn, it doesn't connect, I'm trying to solve that.
problem 2 solved by going to terminal and typing > sudo dpkg --force-architecture <packagename.deb>
Problem 3 still standing :(

---

### Post by jkarcz on 2009-04-24
I use the acrobat reader from the medibuntu repo. So far, I have filled out forms and lots of pdf's and still haven't broke it yet.

---

### Post by arashiko28 on 2009-04-25
I solved the reader problem, I keep having the aMSN, the downloaded file doesn't star and the one from the repos doesn't connect.:confused:

---

### Post by arashiko28 on 2009-04-25
PLEASE HELP!!!

aMSN doesn't work and I've done everything, and by that I mean EVERYTHING there's on the net and nothing works.

-I downloaded the tcl-tk 8.5 file and installed it after installing the compatibility libraries for 32 bit. it says that something is missing and to compile.
-I removed it and installed from synaptic, it opens but never connects
-I removed and installed via terminal, same thing, but I wanted to see if there was any error message, none, and yet I don't get any connection
-I went to the aMSN project home page looking for some other forum and found the version for 64-bit architecture and downloaded it, still no connection

I can surf the web, check my emails, use pidgin, download large files, watch videos online BUT aMSN just hangs trying to connect with no success

---

### Post by cariboo on 2009-04-25
I would suggest you uninstall the manually installed programs and use the repositories for installing programs.

---

### Post by arashiko28 on 2009-04-25
The repositories doesn't work, I chose it through synaptic and it's the same, it doesn't connect.

---

### Post by arashiko28 on 2009-04-26
BUMP!!!!!!!!!!!

There is not a single soul in this planet running aMSN on Jaunty 64-bit??!!!!!](*,)](*,)](*,)

---

### Post by stanca on 2009-04-26
I installed adobe reader through ubuntu-tweak or ultimatix.
Sorry but I don't use amsn too,I'm still an yahoo messenger fan so I have pidgin and gyachi.:popcorn:

---

### Post by Shriner on 2009-04-26
Installed from repos fine for me....are you sure you re-enabled the repos after the upgrade?

---

### Post by ubuntu27 on 2009-04-26
If you had installed amsn from the repositories instead of installing from source, you will had no problem.

I am using Ubuntu 64-bit, and aMSN works wonderfully. 



Try to un-install amsn, and delete every configuration files that might be hidden on your Home directory.

TO see hidden files, press Control (Ctrl) + H on your keyboard.

The folder or directory that you have to delete is .amsn


After that, install amsn using synaptic package manager.

---

### Post by arashiko28 on 2009-04-26
> **Shriner said:**
> Installed from repos fine for me....are you sure you re-enabled the repos after the upgrade?

I didn't upgraded, I made a fresh install and yes they're all enabled. The one from repos is the same thing, doesn't connect.

---

### Post by arashiko28 on 2009-04-26
> **ubuntu27 said:**
> If you had installed amsn from the repositories instead of installing from source, you will had no problem.

I am using Ubuntu 64-bit, and aMSN works wonderfully. 



Try to un-install amsn, and delete every configuration files that might be hidden on your Home directory.

TO see hidden files, press Control (Ctrl) + H on your keyboard.

The folder or directory that you have to delete is .amsn


After that, install amsn using synaptic package manager.

Hmm... seems that there was something wrong, though it didn't had anything from my previous installation, I did deleted the .amsn folder and now connects. Thank you.

---

### Post by illini on 2009-05-14
> **arashiko28 said:**
> Thanks, problem 1 half solved. even though I have amsn, it doesn't connect, I'm trying to solve that.
problem 2 solved by going to terminal and typing 
Problem 3 still standing :(

Hi, I thought this might need correcting.  To install Adobe Reader on 64 bit Jaunty, the deb file should be in the home folder by default, and then you need to type: (example)

sudo dpkg -i --force-architecture AdbeRdr9.1.0-1_i386linux_enu.deb

In your comment you left the -i out, which is important! ;)

---

