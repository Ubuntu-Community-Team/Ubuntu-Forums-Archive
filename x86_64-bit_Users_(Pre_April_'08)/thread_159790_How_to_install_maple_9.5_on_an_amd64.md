---
title: "How to install maple 9.5 on an amd64?"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ramos on 2006-04-13
I am trying to install maple 9.5 on my computer, as super user, but when I type the comand I receve the follow message:

root@dickens:/home/alexandre/Desktop/maple# ./installMapleLinuxSU
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.8198/Linux/resource/jre/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at com.zerog.ia.installer.Main.d(DashoA8113)
        at com.zerog.ia.installer.Main.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

I have been verified and I have these libraries, but I do not know why they are not found.

Thanks
Ramos

---

### Post by skunkydog on 2006-04-25
I'm on i386, but was having the same error while installing maple 10 on ubuntu 5.10 and I fixed it with **sudo apt-get install libxp6**
hth

---

### Post by ramos on 2006-04-25
I tried to use your suggestion but received what follow:

alexandre@dickens:~$ sudo apt-get install libxp6
Password:
Reading package lists... Done
Building dependency tree... Done
libxp6 is already the newest version.

after I tried to install Maple 10 and received the message above.

do you have another suggestion

---

### Post by Ecthelion on 2006-04-26
I managed to install by just running the installer...
problem is, i just can't find a way to run it now...
Is that normal?
This sounds stupid but: how do i have to start it up?
I can't find it in my programs and whan i type
 ```
maple
```
in the commandline i just get a message that the command doesn't exist...

---

### Post by skunkydog on 2006-04-29
Other than checking the path and making sure the libraries are in the path, I have no other ideas.  My libraries are all in /usr/lib and my path contains /usr/lib.

---

### Post by skunkydog on 2006-04-29
The program is called **xmaple**.  If you remember where you installed it, look in there for a folder called bin.  xmaple is in there.  For me, it was **/home/timmy/maple10/bin/xmaple**.

---

### Post by calvinthomas on 2006-07-31
Has anyone actually managed to install this on amd64, its my most important package and I don't know how to install it!

Calv

---

### Post by bmcage on 2006-08-04
Solution to installing Maple 9.5. The problem is with JAVA and LC_LINUX_ASSUME value, some other programms have the same issue. To solve it. Pop in the cdrom.
```
mkdir ~/tmpmaple
cd /media/cdrom0
cp -a . ~/tmpmaple
cd ~/tmpmaple
chmod u+w Linux/Disk1/InstData/VM/LinuxInstaller.bin

```

Now the tricky bit, a variable must be changed in the above file without adding or deleting characters. So only a replace of one character. So, use eg vi editor, with the r option to replace one character.

```
vi Linux/Disk1/InstData/VM/LinuxInstaller.bin

```
Go to line 2093, where it says: export LD_ASSUME_KERNEL=2.2.5
put cursor on the e of export, press r, then #, then press :w to write change, then :q to quit of vi. This should have changed the line into:
 #xport LD_ASSUME_KERNEL=2.2.5
WITHOUT changing the bit code of the installer.bin file.

Now, start the installer with 
```
linux32 sh installMapleLinuxSU
```
This indicates that Maple is in 32 bit encoding, and not 64 bit as the linux you use. Give serial number, install dir, and install completes.

To start Maple with install dir maple9.5:
```
cd ~/maple9.5/bin
linux32 ./xmaple &
```

Edit:
For people having problems finding the LD_ASSUME_KERNEL variable, use the sed command as in thread [http://ubuntuforums.org/showthread.php?t=283473]("http://ubuntuforums.org/showthread.php?t=283473")

---

### Post by sonmez on 2006-08-15
Hello,

I have Dapper on a 32 bit machine and trying to install Maple 10. Firt I could install it from the cd but could not run it so I followed bcage's instruction to fix the installer. But for some reason I could not save the file and exit is. I did change permission and all that. but I couldn't.  After I  press w to svae changes and q it stucks in recording forever. Could anybody help please. 

Thanks

---

### Post by sonmez on 2006-08-15
I wanted to let you know that I used the following help and it worked
[https://help.ubuntu.com/community/Maple](https://help.ubuntu.com/community/Maple)

---

### Post by Ecthelion on 2006-08-16
I have installed Maple 10 on my amd 64, and the only thing I had to do was installing some extra program...
Here's part of a mail that I also sent to maplesoft...

> By changing a line[1] in the maple startup script, so that I can get the error output from java, I get the following error output:
--------------
dl failure on line 773Error: failed /home/ecthelion/maple10/jre.X86_64_LINUX/lib/amd64/server/libjvm.so, because libstdc++.so.5: cannot open shared object file: No such file or directory
---------------

It seems to be a problem with the java vm, libstdc++.so.5 does not exist on a ubuntu 64bit system, only libstdc++.so.6 and libstdc++.so.6.0.4 .
By installing libstdc++5 the problem solved itself.
The command for installing this library on a ubuntu system is "sudo apt-get install libstdc++5", maybe it's useful to add it somewere a readme. 

> [1]
@ line ± 462 in ./bin/maple
--------------
eval "'${MAPLE_JRE_BIN}java'" -Xmx${JAVAHEAP}m ${JVM_OPTIONS} -cp "'$WKSCLASSPATH'" "-Dmaple.bin.path='$MAPLE/$MAPLE_SYS_BIN' ${VMOPTIONS}" "$WKSAPP" $PARAM $LOCALE 1>/dev/null 2>&1
---------------
Changed in:
--------------
eval "'${MAPLE_JRE_BIN}java'" -Xmx${JAVAHEAP}m ${JVM_OPTIONS} -cp "'$WKSCLASSPATH'" "-Dmaple.bin.path='$MAPLE/$MAPLE_SYS_BIN' ${VMOPTIONS}" "$WKSAPP" $PARAM $LOCALE
--------------- 

The problem that I had was that Maple 10 installed correctly, but that when I tried to start the graphical interface, nothing happend.
I could only start maple as commandline. (not graphical)

I hope this helps someone...


[NOTE: I'm talking amd64 so this probably wouldn't work on a 32-bit machine]
[NOTE: I installed using the [maple64bitlinux] version ]

---

### Post by bmcage on 2006-09-04
In reply to sonmez and Ecthelion, let me repeat that the guide I gave here to install is only for 32bit Maple on 64bit Ubuntu installed on AMD64. 
If you install 32bit Ubuntu, there is no problem with maple, or you can follow the guide on [https://help.ubuntu.com/community/Maple](https://help.ubuntu.com/community/Maple)
If you install new 64bit Maple 10, there is no problem.
On AMD64 wit 64bit Ubuntu, the 32bit installer crashes.
I do not like Maple 10 too much, so I keep installing 9.5, others might too.

---

### Post by calvinthomas on 2006-10-08
> **bmcage said:**
> Solution to installing Maple 9.5. The problem is with JAVA and LC_LINUX_ASSUME value, some other programms have the same issue. To solve it. Pop in the cdrom.
```
mkdir ~/tmpmaple
cd /media/cdrom0
cp -a . ~/tmpmaple
cd ~/tmpmaple
chmod u+w Linux/Disk1/InstData/VM/LinuxInstaller.bin

```

Now the tricky bit, a variable must be changed in the above file without adding or deleting characters. So only a replace of one character. So, use eg vi editor, with the r option to replace one character.

```
vi Linux/Disk1/InstData/VM/LinuxInstaller.bin

```
Go to line 2093, where it says: export LD_ASSUME_KERNEL=2.2.5
put cursor on the e of export, press r, then #, then press :w to write change, then :q to quit of vi. This should have changed the line into:
 #xport LD_ASSUME_KERNEL=2.2.5
WITHOUT changing the bit code of the installer.bin file.

Now, start the installer with 
```
linux32 sh installMapleLinuxSU
```
This indicates that Maple is in 32 bit encoding, and not 64 bit as the linux you use. Give serial number, install dir, and install completes.

To start Maple with install dir maple9.5:
```
cd ~/maple9.5/bin
linux32 ./xmaple &
```

I don't know if this is a dumb question but how do I know when i'm on line 2093? With vi it doesn't seem to tell me what line i'm on!

Calv

---

### Post by bmcage on 2006-10-09
if you do vi in the console, the bottom line should give you this info.
Eg, I do vi missfont.log, and the bottom line of vi is:
"missfont.log" 2L, 142C                      1,1           All

the 1,1 is the linenumber,columnnumber. Should be the same for you.

---

### Post by dimis on 2006-10-09
> **calvinthomas said:**
> I don't know if this is a dumb question but how do I know when i'm on line 2093? With vi it doesn't seem to tell me what line i'm on!
If you want to avoid vi (or any other editor) try the following:
Open a terminal and move into the path where you keep LinuxInstaller.bin. Then:
```
cat LinuxInstaller.bin | grep -n 'export LD_ASSUME_KERNEL=2.2.5'
``` If the output is _only 1_ line*, i.e. something like this:
```
2093:                               export LD_ASSUME_KERNEL=2.2.5
```
then you can do the following:
```
mv LinuxInstaller.bin LinuxInstaller.bin.bak
sed 's/export LD_ASSUME_KERNEL=2.2.5/#xport LD_ASSUME_KERNEL=2.2.5/' LinuxInstaller.bin.bak > LinuxInstaller.bin
./LinuxInstaller.bin
```
You are now ready to install Maple following bmcage's tip! :)


Regards,
dimis

-----
* Sorry for not checking the output of grep, but I am currently not at home.

---

### Post by calvinthomas on 2006-10-09
That worked brilliantly on getting maple 9.5 to work in Ubuntu 32bit Edgy, i'm gonna make a how-to for it now so its easy to locate for people trying to do it. Will give credit to the people on here.

Calv

---

### Post by Pistolpete2 on 2006-10-17
Hello I've got the 64-bit version of maple and I wan't to install it on my acer aspire 5024WLMi. (AMD64 Turion) Can I use the posts above? Because apparently the maple version u are talking about is a 32-bit version. 

greetings

Pistolpete

---

### Post by bmcage on 2006-10-23
As far as I understood other people, the 64 bit version Maple installer just works on a 64 bit linux. You should not use the directions in this post.

---

### Post by bmcage on 2006-10-27
For the interested, just installed Maple 10 on Edgy Eft, 32 bit version.
Failed with same type of errors. Reason is again another glibc version. The solution is given here: [http://www.ces.clemson.edu/linux/maple.shtml](http://www.ces.clemson.edu/linux/maple.shtml)
In short, for single user version: same as the instructions I gave for Maple 9.5 64 bit, but now in dir Linux/Disk1/InstData/VM, edit one byte of LinuxInstaller.bin, now on line 2134, changing 'export LD_ASSUME_KERNEL' into '#xport LD_ASSUME_KERNEL'

---

### Post by aikishugyo on 2007-11-20
For Maple9.5 on my AMD64 system, I followed the procedure hinted at  [Thomas Themel]("http://weblog.themel.com/?p=722")'s page.


0. If needed mount ISO file (maybe with '-o unhide' option).

1. go to installer directory, and execute it with 'bash -x <installer file>'

2. take note of the /tmp/<dir> where the stuff gets put, and 'cd' to there. Also note where the installer is being started with a 'sh <installer>' command, and go to the subdir where the installer is.

3. run the installer also with 'bash -x <next level of installer>', and take note of the errors.

4. at the terminal execute the lines from 3 above for 'CLASSPATH=<something>' and 'export CLASSPATH'.

5. Finally, for the line that has the java executable in it (it is a local java packaged with the installer and run from the /tmp/<something> directory with tons of options trailing), execute it but using *your* local java: 'java <trailing stuff copied from the exec ... line>'. Now the installer should run fine.

Worked for me in Gutsy. I haven't yet tried Maple 10, since there I have a monolithic file to run and need to read the help docs on this thread and others some more.

Cheers, Gernot

---

### Post by Jeanpaul145 on 2008-03-09
> **Ecthelion said:**
> I managed to install by just running the installer...
problem is, i just can't find a way to run it now...
Is that normal?
This sounds stupid but: how do i have to start it up?
I can't find it in my programs and whan i type
 ```
maple
```
in the commandline i just get a message that the command doesn't exist...

This is because maple 10 (and I imagine 9.5 as well) doesn't install the binaries to /bin.
I made a few symlinks as follows

```

sudo ln -s ~/maple10/bin/maple /bin/maple
sudo ln -s ~/maple10/bin/xmaple /bin/xmaple

```

assuming you installed maple 10 to your homedir.
maple is de cli client, xmaple is the swing GUI client.

---

