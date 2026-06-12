---
title: "Installing Matlab Release 14 Student Edition on Breezy AMD 64 - libXp library"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by UrbanFallout on 2005-11-16
Hi 

I started a new post because after looking: [here]("http://wiki.edubuntu.org/MATLAB"), [here]("http://newsreader.mathworks.com/WebX?14@71.svNZb7qVa1J.0@.ef0a82d"), [here]("http://http://help.nceas.ucsb.edu/index.php/Matlab_on_Ubuntu_5.04") [here]("http://http://www.ubuntuforums.org/showthread.php?t=53222&highlight=install+matlab")

I was still unable to install matlab student edition on my AMD64 with Breezy x86_64 installed. This problem only seems to affect the student version of Matlab R14 and only on the x86 version.

First off some background:

1. You do NOT need to copy the entire CD to your hard-drive to resolve this error:
> 
nick@arcturus:/opt/matlab7$ sudo sh /media/cdrom/install_unix.sh
Password:
/media/cdrom/install_unix.sh: /media/cdrom/unix/install: /bin/sh: bad interpreter: Permission denied
 
You just need to remount the cdrom over-riding the fstab options as follows:
```

sudo umount /media/cdrom
sudo mount -t iso9660 /dev/cdrom /media/cdrom

```

2. Next you get an error about being unable to access libc.so.6. 
I just installed g++, and changed a its permissions
```
sudo chmod 755 /lib/libc.so.6
```

3. Next you get an error because it can't find the glnx64 directory. This is not a problem, because we can use the -glnx switch:
```
sudo sh /media/cdrom/install_unix.sh -glnx86
```

4. However here's an error that I can't get around.
> nick@arcturus:/opt/matlab7$ sudo sh /media/cdrom/install_unix.sh -glnx86
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/cdrom0/unix/update/bin/glnx86/xsetup: error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory
    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .



I've tried the following things, none of which has worked:
1. Are my libxp libraries are installed? Yes they are, but I tried re-installing these.
2. I tried running /media/cdrom/unix/install
3. I tried running /media/cdrom/unix/update/bin/glnx86/xsetup
4. I tried these with the -t switch
5. I linked the libXp.so.6 file to the current directory, and the /lib32 directory.
6. I tried copying the CD to the hard-drive as suggested.
7. I tried looking at the script files, but none of them refers to libXp.so.6. This is buried within the xsetup binary, so I don't know where it looks.

Nothing appears to have helped.....

To pre-empt some obvious questions:
1. There is a 64 bit version of matlab - but not for students!
2. Service pack 3 fixes some of these issues, but the students don't get this!
3. I have contacted the mathworks and I'm waiting for their answers, if they come... which I'll post here when they arrive.
4. Several other people have had the same problems as me without luck.

Help!

Grateful thanks in advance.
Nick

---

### Post by UrbanFallout on 2005-11-17
OK... Partial success if you try this:

1. Install Breezy Badger x86, replacing existing Breezy i64 install. Ouch!

2. Insert matlab CD into drive

3. You'll need to remount the cd and then run the installation script as follows:
```

sudo umount /media/cdrom
sudo mount -t iso9660 /dev/cdrom /media/cdrom
sudo mkdir /opt/matlab7
cd /opt/matlab7
sudo sh /media/cdrom/install_unix.sh

```

4. An error code from the "oscheck.sh" script comes up, but this does not affect the actual installation, so ignore it. Just follow the instructions in the "Learning Matlab" manual.

5. Type "matlab", and it should just work, as long as you've created the scripts in the /usr/local/bin directory. (The install script asks you for this), otherwise try:
```
/opt/matlab7/bin/matlab
```

6. Viola! A fully working Matlab 7 (student edition) with IDE.

Time for take three, which will be reinstalling Breezy ia64 and trying to get chroot32 up and running, before installing matlab. I had no luck this morning but I'll keep everyone posted.

Hope this very suboptimal approach helps someone.
If anyone has any other suggestions in the meantime...

Nick

---

### Post by UrbanFallout on 2005-11-17
Yay!

Alrighty then... Take 3! Nearly there, I might have some extraneous steps though. 

I reinstalled Breezy i64. Without changing the graphics drivers, I ran installed a 32 bit chroot environment as per the instructions at the [32 bit Chroot Howto]("http://ubuntuforums.org/showthread.php?t=24575"). 
I made one slight change, all [COLOR="Blue"]hoary[/COLOR]'s were replaced with [COLOR="Red"]breezy[/COLOR]'s.
So why mention graphics drivers. Well some for some reason it stopped me installing synaptic in step 5 of the Chroot Howto. I have no idea why, but I'll look into this later.

Now for the installation part:
1. Enter the chroot environment:
```
dchroot -d
```

2. Several key packages may be missing which require installation:
```
sudo apt-get install libxp6 libxt6 libxtst6

```

3. Now insert the matlab cdrom, remount it and run the install:
```
sudo umount /media/cdrom
sudo mount -t iso9660 /dev/cdrom /media/cdrom
sudo mkdir /opt/matlab7
cd /opt/matlab7
sudo sh /media/cdrom/install_unix.sh -glnx86

```

4. The new chroot32 environment for some reason still considers itself to be of ia64 architecture. So the matlab install script merrily churns away, installs all the binaries to .../glnx86 directories and makes its own scripts point to .../glnxa64 directories which don't exist. Very annoying, so we simply symlink wherever necessary:
```

cd /opt/matlab7/bin
sudo mv glnxa64 glnxa64.old
sudo ln -s glnx86 glnxa64
cd /opt/matlab7/extern/lib
sudo ln -s glnx86 glnxa64
cd /opt/matlab7/sys/java/jre
sudo ln -s glnx86 glnxa64
cd /opt/matlab7/sys/java/jre/glnx86/jre1.4.2/lib
sudo ln -s i386 amd64

```

5. The last step is because matlab can't access a terminal window. I'm not sure how this works, but the /chroot/dev/pts directory is not properly mounted. You need to remount this. So in a new terminal window (not chroot) go:
```

sudo umount /chroot/dev
sudo mount --rbind /dev /chroot/dev

```

6. Now finally to remove the oscheck error message, open up the oscheck.sh file:
```

sudo gedit /chroot/opt/matlab7/bin/util/oscheck.sh 
```
Goto line 150, comment it out and insert a version number so looks like follows:
```

# ver=`/lib/libc.so.6 | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
ver=`objdump -x /lib/libc.so.6|egrep "      GLIBC_"|tail -1|awk -F_ '{print $2}'`

```

7. Now you can type "matlab" and it should work without any errors or fuss. 

When I get time I'll try neaten this lot up into a proper tutorial.

Hope this helps. Any comments are welcomed.
Nick

---

### Post by Aphorism on 2005-11-21
Not an expert on this, but you *have* tried Octave yes?  Open Source.  Chance of being on every distribution.  TONS of 3rd party libraries.  Free.  Etc.

---

### Post by UrbanFallout on 2005-11-22
I have used Octave a fair amount, and it is pretty good.
Unfortuately too much of my code is in mex functions, and porting everything across at this stage of my PhD is a bit too much to contemplate. :(

Matlab also has an extremely polished gui which just makes debugging etc soo much easier.

Call me lazy but....

Nick

---

### Post by burntwater on 2005-11-22
I have Matlab R14 installed on Breezy with no problems whatsoever, so this applies only to the Student Edition it seems.

In terminal:
```
richard@xenon:~/Documents/D.Eng/thesis$ uname -r
2.6.12-9-amd64-k8
```
In Matlab:
```
>> version

ans =

7.0.4.352 (R14) Service Pack 2
```

Although every time I start it in the terminal I get this message:
```
/usr/local/matlab704/bin/util/oscheck.sh: line 150: /lib64/libc.so.6: Permission denied
```

---

### Post by Belisarius on 2005-12-13
Hi,

I've been trying to install Matlab Student Version on my Breezy AMD64 system. I have a 32-bit chroot setup (running Firefox now) and the install had gone OK following the instructions above however I cannot get the GUI to come up. When I launch from terminal I get:

```
Warning: Unable to load Java Runtime Environment: /usr/local/matlab7/sys/java/jre/glnx86/jre1.4.2/lib/i386/libjava.so: symbol fork1, version SUNWprivate_1.1 not defined in file libjvm.so with link time reference.
Warning: Disabling Java support.
```

```
I installed java through synaptic (in 32 bit chroot) and get:
andy@Scipio:/usr/local/matlab7/bin$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
```

Originally the .so files it couldn't find were libjvm and libverify. I added the paths to these to an envirement variable LD_LIBRARY_PATH which cleared those two errors and led to this.

Any help would be much appreciated as I need this up and running ASAP. Please post questions if you need more info.

Many thanks in advance.

Andy

---

### Post by UrbanFallout on 2006-01-02
Hi Belisarius

Re: Missing java runtime environment.

1. It could be you missed out **step 4** in the instructions above. I had to perform a re-install today, but I excluded step 4 by mistake and got the same problem. Symlinking the directories properly solved this.

2. Alternatively it could some kind of conflict between the JRE matlab installs, and the one you've installed, namely: Blackdown. Perhaps you could try uninstalling the Blackdown JRE or remove it from memory. i.e.
```
ps -a | grep jre
kill -9 <insert jre process number>

```
3. Another possibility is to reconfigure the matlab java settings. I haven't had to do this this myself but a brief search revealed  [this hint]("http://http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/linuxemu-matlab.html"), where they suggest:
> 10.5.3 Linking the Java™ Runtime Environment
Change the Java™ Runtime Environment (JRE) link to one working under FreeBSD:
# cd $MATLAB/sys/java/jre/glnx86/
# unlink jre; ln -s ./jre1.1.8 ./jre


Let me know how you get on.

Cheers
Nick

---

### Post by UrbanFallout on 2006-01-02
Logging a correction to the third post above on 2 Jan 2006: 
1. Fixed missing "-glnx86" switch for installer
2. Put package installs all on one line

Nick

---

### Post by equivsys on 2006-01-04
I came across this problem when running Matlab over AFS on an install of Ubuntu Breezy amd64.  Well there were actually two problems one is the libXp.so.6 issue.  To get around this I simply downloaded a 32bit version of the library and put it in /usr/lib32 and then ran "ln -s /usr/lib32/libXp.so.6 /usr/lib/libXp.so.6" (I have no programs that need a 64bit version of that library so this is not a problem).  This solves that issue nicely.

The other issue I ran across is that Matlab also wants a 32bit version of java of course so for this I simply grabbed a 32bit version from sun and installed it in /usr/lib32 and then used the environment variable MATLAB_JAVA to let matlab know where I put it.

---

### Post by J77 on 2006-01-13
Three commands (as root):

umount /media/cdrom
mount -t iso9660 /dev/cdrom /media/cdrom
/media/cdrom/install_unix.sh

worked fine for me :)

---

### Post by equivsys on 2006-01-13
That is because some of the newest versions of MATLAB have an amd64 specific binary set and in this case, yes everything will work fine.  However, those of us working with an older version will have to make use of the 32-bit binaries.  Which will bring up the problems being discussed.

---

### Post by UrbanFallout on 2006-01-14
Hi

Thanks equivsys for your hints. I've gotten matlab running my symlinking to the 32 bit libXp.so library. I never realised that this file was 64bit, since the documentation states: "X11 X Print Library libxp6 is an obsoleted library. Some old binaries still depend on this".

I have a question though, how did find and download this file? By using synaptic or by downloading it manually by clicking on "i386" in the ubuntu repository [here]("http://packages.ubuntu.com/breezy/x11/libxp6")?

Regarding java issue, I didn't need to download another version of java. I simply did the following:
```
export XLOCALELIBDIR=/usr/lib32/X11/locale
matlab
```
as per instructions in post number 8 [here]("http://ubuntuforums.org/showthread.php?t=40392&highlight=locale+set+CX").
Clearly for convenience you can either add the first line to ~/.bashrc (dodgy) or $(MATLAB)/bin/matlab (preferable). 

Lastly, I ought to mention I had several issues when compiling mex files. You must have gcc-3.3 installed. Now, calling vanilla gcc at the command line defaults to version 4. For your average program with multiple header and library files, this is fine right up until the final link using mex (or the decoded mex scripts - I'll explain in a later post - ask here if you want to know more). 

The solution to this is to replace "gcc" and "g++" in $(MATLAB)/bin/mex with "gcc-3.3" and "g++-3.3".  

Thanks to everyone who replied.
When I get time I'll put this into a howto.

Cheers
Nick

---

### Post by UrbanFallout on 2006-01-14
Change Log:
1. Updated ver line in step 6 of post #3 above, to accurately report current version of your libc libraries.

---

### Post by equivsys on 2006-01-14
Thanks UrbanFallout for the information about compiling mex files.

---

### Post by socsuj on 2006-01-17
Thanks UrbanFallout and everyone else for the tips.  A couple things I'd like to add:

1. The student version of Matlab R14SP3 does not come with the 64 bit binaries.  Of course I found this out after buying it.

2.  As of R14SP3 the documentation CD no longer needs to be in the drive when starting Matlab however an activation script must be run after installing Matlab.  I ran into problems with this script as I would get the following error:

```
awk: program limit exceeded: sprintf buffer size=1020
        FILENAME="-" FNR=36 NR=36
Unrecognized option: -root
Could not create the Java virtual machine.
```

After a little poking around I found that Ubuntu installs mawk, a light version of awk.  One of the limitations of mawk is the sprintf buffer size.  To get around this error I had to install gawk and get the script to use gawk rather than mawk.  I did this by simply replacing all of instances of "awk" in $MATLABROOT/bin/actiavtion.sh with "gawk"

Also, this error will likely keep you from being able to activate Matlab during the installation process.  Before runnng Matlab for the first time the mawk/gawk problem should be fixed and then Matlab should be run for the first time through sudo as the activation process downloads and writes files in directories only writeable by root.

3.  After getting Matlab installed I had problems getting the desktop started and I was getting errors about X not supporting my locale.  I traced this back to the 32 bit Java that Matlab installs and got the solution from the following blog [http://www.adap.org/~edsel/blog/archives/42#comments]("http://www.adap.org/~edsel/blog/archives/42#comments")

Basically, Java correctly looks in /usr/lib32/libX11.so.6.2 however this file incorectly points to /usr/lib/X11/locale.  To fix this you need to open /usr/lib32/libX11.so.6.2 with a text editor with binary file capability, search for /usr/lib/X11/locale and replace "/usr/lib/X11/locale" with "/usr/l32/X11/locale".  A symlink then needs to be made to /usr/l32

```
ln -s /usr/lib32 /usr/l32
```

The reason for the symlink is that the string in the binary file must be the same number of characters so we can't just replace /usr/lib/X11/locale with /usr/lib32/X11/locale

I think that's it, hopefully it helps.

---

### Post by oonoon on 2006-01-31
Hi, I'm installing matlab7 on ubuntu x86_64 breezy, i made many of the required manipulations, I've got through many different errors but there's still

expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/uname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

when i run matlab
i checked into the /$MATLAB/sys/op/glnx (and glnx64) and there's no so.6 lib and in /lib also. So what can i do?
Thanks

---

### Post by equivsys on 2006-01-31
It seems like MATLAB cannot find libc.so.6 and uname, which is an error I have yet to see.  On my stock breezy amd64 setup I get the following results.

```
marten@euclid:~$ locate libc.so.6
/lib/libc.so.6
/lib32/tls/libc.so.6
/lib32/libc.so.6

```

```
marten@euclid:~$ which uname
/bin/uname

```

If you do not then there maybe something wrong with your environment variables.

---

### Post by oonoon on 2006-01-31
I get exactly the same results as yours...

---

### Post by UrbanFallout on 2006-02-02
Some quick questions might shed some light on the situation:

1. What version of matlab are you using?
(To clarify: are you using a professional version v7.0.1, v7.0.2 or v7.0.3? Or are you using a student version v7.0.1 or v7.0.3?)

2. When are getting your error? (i.e. when you run the installation script or when you try to start matlab)

3. What manipulations have you made? (since there are several sometimes conflicting sets of advise in the above posts, i.e. have you installed a chroot environment and followed the instructions in post #3? or just replaced the libXp.so.6 link as per post #10?)

4. Have you installed the "build-essential" package?

Nick

---

### Post by claudio.divita on 2006-02-04
I have the same problem of [oonoon]("http://ubuntuforums.org/member.php?u=35942") so I tell you my situation:

> 
1. What version of matlab are you using?
(To clarify: are you using a professional version v7.0.1, v7.0.2 or v7.0.3? Or are you using a student version v7.0.1 or v7.0.3?)

I have R14 SP2, with Matlab 7.0.4, and it's a Professional Version

> 
2. When are getting your error? (i.e. when you run the installation script or when you try to start matlab)

When I start matlab

> 
3. What manipulations have you made? (since there are several sometimes conflicting sets of advise in the above posts, i.e. have you installed a chroot environment and followed the instructions in post #3? or just replaced the libXp.so.6 link as per post #10?)

The only manipulation that I made is
```
sudo chmod +x /lib/libc-2.3.5.so
```
Because this file is pointed by the symlink /lib/libc.so.6

> 
4. Have you installed the "build-essential" package?

Yes, I do

I have installed Breezy on a HP xw8200 and my Kernel is  2.6.12-10-amd64-xeon

---

### Post by claudio.divita on 2006-02-04
I've also tried to run $MATLAB/bin/glnxa64/MATLAB, but the result is:
```
*** glibc detected *** malloc(): memory corruption: 0x00000000005a17a0 ***

```
And the execution is aborted

---

### Post by gaspra on 2006-02-04
[QUOTE=claudio.divita]I've also tried to run $MATLAB/bin/glnxa64/MATLAB, but the result is:
```
*** glibc detected *** malloc(): memory corruption: 0x00000000005a17a0 ***

```
And the execution is aborted[/QUOTE]

You may try to use this:

add the following two lines to the very beginning of file ".matlab7rc.sh" which is in folder $MATLAB/bin (or $MATLAB/bin/glnxa64/ if you use different executable script):

    LD_ASSUME_KERNEL=2.4.1
    export LD_ASSUME_KERNEL

I have tried to manage Matlab 7 SP2 to work on Breezy x86-64 but no luck. Seems like you are very close to success. I am currently running Centos x86-64 and I have to make the change as I described above since I got the same error message as you got.

---

### Post by claudio.divita on 2006-02-05
[QUOTE=gaspra]You may try to use this:

add the following two lines to the very beginning of file ".matlab7rc.sh" which is in folder $MATLAB/bin (or $MATLAB/bin/glnxa64/ if you use different executable script):

    LD_ASSUME_KERNEL=2.4.1
    export LD_ASSUME_KERNEL
[/QUOTE]

I've already added these lines to file [FONT="Courier New"].matlab7rc.sh[/FONT] that is in folder [FONT="Courier New"]$MATLAB/bin[/FONT]. You think that I should them in the script that is under [FONT="Courier New"]$MATLAB/bin/glnxa64/[/FONT] directory ??

---

### Post by QuantumCowboy on 2006-02-12
I had a load of problems installing Matlab on amd64 under SuSE 10.  The solution was to make it think that i was in a 32-bit environment add also the tag -nocp to the installer script.  The 64-bit patch for *nix systems can be downloaded from Mathworks later and installed.  Note that you must be in the installation (destination) directory for the install to work.  I've noticed some similar threads, so if you see anyone else having this problem, the following may work for you as well.  Note this is for Matlab 7.0, the full version.  If you don't have multiple CDs in the student version, skip the parts for the other CDs.

# put CD1 into the drive

mount -t iso9660 /dev/cdrecorder /media/cdrecorder
mkdir /usr/local/matlab7
cd /usr/local/matlab7
cp [license files] ./
/media/cdrecorder/install -glnx86 -nocp

# This will install the files from disc 1.  When it asks you to put in disk 2, say 
# skip, also skip 3 if it asks.  Replace cd1 with cd2 in your drive.

mount -t iso9660 /dev/cdrecorder /media/cdrecorder
/media/cdrecorder/install -glnx86 -nocp

# this installs cd2's data.  skip cd3, and replace cd2 with cd3 in your drive.  
# once again:

mount -t iso9660 /dev/cdrecorder /media/cdrecorder
/media/cdrecorder/install -glnx86 -nocp

# install and start the license server:

./install_matlab 4 -glnx86
/usr/local/matlab7/etc/lmstart -glnx86

# now you should be operational:

matlab -glnx86

---

