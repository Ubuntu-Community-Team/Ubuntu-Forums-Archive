---
title: "[SOLVED] Medal Of Honor AA Linux Installer cannot find 32 bit lib!!!!!!!!!!!!!"
date: 2008-09-11
forum: x86 64-bit Users
---

### Post by go_beep_yourself on 2008-09-11
I've tried everything known to man about 64-bit to get this thing working, but the script still isn't finding the 32 bit libs. I even placed them in /lib32. I also tried putting the 32 bit libs in their own directory and telling ldconfig to check for libs there both through command line arguments and /etc/ld.so.conf. I tried LD_PRELOAD and LD_LIBRARY_PATH. None of that worked. I got these 32 bit libs from here. [http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2).

```
chris@ubuntu:~/Downloads$ sudo mv -iv ../.32bitLibs/libgtk-1.2.so.0* /lib32/
`../.32bitLibs/libgtk-1.2.so.0' -> `/lib32/libgtk-1.2.so.0'
removed `../.32bitLibs/libgtk-1.2.so.0'
`../.32bitLibs/libgtk-1.2.so.0.9.1' -> `/lib32/libgtk-1.2.so.0.9.1'
removed `../.32bitLibs/libgtk-1.2.so.0.9.1'
chris@ubuntu:~/Downloads$ sudo ./mohaa_1.11beta3-english.uk.run 
Verifying archive integrity... All good.
Uncompressing Medal of Honor: Allied Assault 1.11beta3-english.uk Installer..........................................................
/home/chris/.setup6911: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
chris@ubuntu:~/Downloads$ 

```
Anybody who doesn't mind testing this on their own 64-bit Ubuntu, the file is just 14 mb available from a torrent here.

[http://liflg.org/?catid=6&gameid=8](http://liflg.org/?catid=6&gameid=8)

//EDIT

the same results happened from both of the english files, us and uk.

---

### Post by Kilz on 2008-09-11
> **go_beep_yourself said:**
> I've tried everything known to man about 64-bit to get this thing working, but the script still isn't finding the 32 bit libs. I even placed them in /lib32. I also tried putting the 32 bit libs in their own directory and telling ldconfig to check for libs there both through command line arguments and /etc/ld.so.conf. I tried LD_PRELOAD and LD_LIBRARY_PATH. None of that worked. I got these 32 bit libs from here. [http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2).

```
chris@ubuntu:~/Downloads$ sudo mv -iv ../.32bitLibs/libgtk-1.2.so.0* /lib32/
`../.32bitLibs/libgtk-1.2.so.0' -> `/lib32/libgtk-1.2.so.0'
removed `../.32bitLibs/libgtk-1.2.so.0'
`../.32bitLibs/libgtk-1.2.so.0.9.1' -> `/lib32/libgtk-1.2.so.0.9.1'
removed `../.32bitLibs/libgtk-1.2.so.0.9.1'
chris@ubuntu:~/Downloads$ sudo ./mohaa_1.11beta3-english.uk.run 
Verifying archive integrity... All good.
Uncompressing Medal of Honor: Allied Assault 1.11beta3-english.uk Installer..........................................................
/home/chris/.setup6911: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
chris@ubuntu:~/Downloads$ 

```
Anybody who doesn't mind testing this on their own 64-bit Ubuntu, the file is just 14 mb available from a torrent here.

[http://liflg.org/?catid=6&gameid=8](http://liflg.org/?catid=6&gameid=8)

//EDIT

the same results happened from both of the english files, us and uk.

I suggest using [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") to install 32bit libraries. That way the right library will be placed in the correct location.

---

### Post by Thelasko on 2008-09-11
> Medal Of Honor AA Linux Installer
I didn't even know such a thing existed.  I have an old AA disk around here somewhere, I'll have to try it out.

---

### Post by go_beep_yourself on 2008-09-11
> **Kilz said:**
> I suggest using [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") to install 32bit libraries. That way the right library will be placed in the correct location.

Does getlibs dump the libs in /lib32? Does it have a way of getting a list of libs it installed and removing them?

---

### Post by go_beep_yourself on 2008-09-11
> **Thelasko said:**
> I didn't even know such a thing existed.  I have an old AA disk around here somewhere, I'll have to try it out.

Okay, hope to hear from you soon about that.

---

### Post by Kilz on 2008-09-11
> **go_beep_yourself said:**
> Does getlibs dump the libs in /lib32? Does it have a way of getting a list of libs it installed and removing them?

It doesnt just dump them to my knowledge. It will preserve any folders they may be in. No, I dont think getting lists and removing them is possible, Ubuntu is not multiarch. 
But then nether is what you described above. In both cases the rm command works.

---

### Post by go_beep_yourself on 2008-09-12
I thought since the game is 32 bit, the lib needed was 32 bit, but it really needed 64-bit libgtk1.2 installed.

---

### Post by Kilz on 2008-09-12
> **go_beep_yourself said:**
> I thought since the game is 32 bit, the lib needed was 32 bit, but it really needed 64-bit libgtk1.2 installed.

Then please mark this solved in the thread tools at the top of the thread.

---

