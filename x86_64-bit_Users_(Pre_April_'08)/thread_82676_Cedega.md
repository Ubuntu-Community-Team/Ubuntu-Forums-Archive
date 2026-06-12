---
title: "Cedega"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shadow6363 on 2005-10-27
I was wondering if anybody has gotten Cedega to work on Ubuntu 64-bit or knows if Cedega 5.0 will support 64-bit?

---

### Post by RAOF on 2005-10-27
I know **how** to get cedega working, with just [one flaw...]("http://www.ubuntuforums.org/showthread.php?t=81732")

On the other hand, it looks like I've got wine working at least.  If you just grab the i386 breezy binary debs from [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/), you can install them using 
```
sudo dpkg -i --force-architecture <thingy.deb>
```.  Actually, if you can find a cedega .deb, the same trick may work.

Edit: updated --force-architecture

---

### Post by superhew on 2005-10-27
thanks RAOF for the advice!

however i just want to point out that you forgot a '-'. command should read:

```
 sudo dpkg -i --force-architecture <thingy.deb> 
```

the only reason i correct you is because some noobs (like myself) could really go crazy over this. luckily dpkg gives good advice:

```
dpkg: conflicting actions --field and --install
```

thanks again for the help. im gonna try it out now!

---

### Post by Kemotaha on 2005-11-01
I use it all the time.  I subscribed to Transgaming so I use Point2Play and the only thing I have to is add /lib32;/usr/lib32/ to the path inside the winex call.  I have not had anyproblems with it.  

Oh BTW you want to install point2play_small for the deb.

Kemo

---

### Post by dragze on 2006-01-02
Hi all, RAOF i am hoping you or someone else will be able to solve my problem! :O right i followed your instructions on how to install wine, i got the wine.deb from the site (latest version) and tryed to install it following your instructions. Well i recieved a few errors and as you guessed it wont install, now me being a linux noob means that i dont really understand what the error mssg is tryin to tell me! so here goes, you guys can have a bash!: > ~/My Downloads$ sudo dpkg -i --force-architecture wine_0.9.4-winehq-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: considering removing xwine in favour of wine ...
dpkg: yes, will remove xwine in favour of wine.
(Reading database ... 60802 files and directories currently installed.)
Unpacking wine (from wine_0.9.4-winehq-1_i386.deb) ...
[COLOR=Red]dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.4-winehq-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/ole32.dll.so')
Errors were encountered while processing:[/COLOR]
 wine_0.9.4-winehq-1_i386.deb
 
Hope someone knows the problem behind this cause i really want to use breezy 64bit but i really need wine too, fingers crossed!! :)

Thankyou in advanced!
Michael

---

### Post by Shed on 2006-03-04
[QUOTE=dragze]Hi all, RAOF i am hoping you or someone else will be able to solve my problem! :O right i followed your instructions on how to install wine, i got the wine.deb from the site (latest version) and tryed to install it following your instructions. Well i recieved a few errors and as you guessed it wont install, now me being a linux noob means that i dont really understand what the error mssg is tryin to tell me! so here goes, you guys can have a bash!:  
Hope someone knows the problem behind this cause i really want to use breezy 64bit but i really need wine too, fingers crossed!! :)

Thankyou in advanced!
Michael[/QUOTE]
I'm in the same boat for this :).

---

### Post by RAOF on 2006-03-05
That problem is caused because the wine servers are awful - they drop out all the time.  What you've got is a corrupted (incomplete) deb file.  Download the wine deb using something that understands about resuming.

From a terminal
```

wget http://wine.sourceforge.net/apt/breezy/wine_0.9.9-winehq-1_i386.deb

```
Will get you the lastest wine (as of 2006-03-05).

---

### Post by Shed on 2006-03-05
[QUOTE=RAOF]That problem is caused because the wine servers are awful - they drop out all the time.  What you've got is a corrupted (incomplete) deb file.  Download the wine deb using something that understands about resuming.

From a terminal
```

wget http://wine.sourceforge.net/apt/breezy/wine_0.9.9-winehq-1_i386.deb

```
Will get you the lastest wine (as of 2006-03-05).[/QUOTE]
Thanks, I'll try to download again.

---

### Post by Shed on 2006-03-05
I still get this error :( :

```
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 88831 files and directories currently installed.)
Unpacking wine (from wine_0-1.9.9-winehq-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0-1.9.9-winehq-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/oleaut32.dll.so')
Errors were encountered while processing:

```

---

### Post by Coolit on 2006-03-05
Woops! didn't read Shed's question properly and and answered the initial posters question, I'll leave this post here anyway as it may be useful to someone :)


Here's my experiences and what I had to do to get Cedega 5.1 fully working under 64bit breezy with an Nvidia. 

Like you I had a few issues, firstly you'll need to install the latest Nvidia drivers as per this thread, [http://ubuntuforums.org/showthread.php?t=75074&highlight=driver+guide]("http://ubuntuforums.org/showthread.php?t=75074&highlight=driver+guide") Use **method two**. 

As Cedega runs as a 32bit app and all the games need to run in 32bit its important when installing the Nvidia drivers that you do Draugen's tip and install the OpenGL32bit compatibility libraries (see the end of the first post for this, Tip: do this first before installing the drivers). When installing the drivers it will ask you if you wish to install the 32bit compatibility libraries, in the guide it says to answer no, you need to answer yes here.

Once the install completes, install Cedega using the "sudo dpkg -i --force-architecture *.deb" line as suggested. If all has worked Cedega will pass the 3D/OpenGL tests. I found that if using the driver in the apt repository 3D acceleration fails although it does work, weird.

Hope this helps :-)

---

