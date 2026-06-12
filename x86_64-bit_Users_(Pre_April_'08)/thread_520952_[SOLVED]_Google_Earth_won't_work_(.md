---
title: "[SOLVED] Google Earth won't work :("
date: 2007-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by RavanH on 2007-08-08
Has anyone got Google Earth running on Feisty AMD64 with ATI graphics (Radeon Xpress 200M in my case)?

On my system i've had GE installed from the Medibuntu repositories but it used to just hang at the splash screen so I uninstalled it a while back. Today, I reinstalled it but now when starting GE up, I get logged out of my session :confused: !!!

Can anyone tell me how to get googleearth running properly?

Thanks! :)

---

### Post by Kilz on 2007-08-08
> **RavanH said:**
> Has anyone got Google Earth running on Feisty AMD64 with ATI graphics (Radeon Xpress 200M in my case)?

On my system i've had GE installed from the Medibuntu repositories but it used to just hang at the splash screen so I uninstalled it a while back. Today, I reinstalled it but now when starting GE up, I get logged out of my session :confused: !!!

Can anyone tell me how to get googleearth running properly?

Thanks! :)

Do you have accelerated graphics? What is the response to ```
fglrxinfo
```.

---

### Post by RavanH on 2007-08-08
Hi Kilz, thanks for your quick response!

There are WEIRD things going on on my system... This is what I got:```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

But I had the latest fglrx drivers from ATI installed just recently :confused: Wherever did they go?!

Anyway, i'll be reinstalling the latest as you read this and report back later :)

---

### Post by RavanH on 2007-08-08
Ffffew... I'm back using the ATI driver ```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6650 (8.39.4)
``` which does seem to solve the issue of being thrown out of session...

But now I'm back at the original behaviour. After starting GE, it sort of hangs at the splash ('Initializing') and CPU goes up to 100% caused by the process googleearth-bin. After a looooong time, the proces dies and CPU is back to normal again. But no GE :(

Any ideas?

---

### Post by nuddernuby on 2007-08-08
I am sharing your frustration and have been experiencing the same situation.  Opened a thread entitled **Google Earth jumps to start-up screen** but with little progress so far. 

I shall be keeping a close watch on this thread, hoping that we find a solution.

---

### Post by McTek on 2007-08-08
> **RavanH said:**
> Has anyone got Google Earth running on Feisty AMD64 with ATI graphics (Radeon Xpress 200M in my case)?

On my system i've had GE installed from the Medibuntu repositories but it used to just hang at the splash screen so I uninstalled it a while back. Today, I reinstalled it but now when starting GE up, I get logged out of my session :confused: !!!

Can anyone tell me how to get googleearth running properly?

Thanks! :)

I'm running a simular system and getting the same result.
I downloaded and installed from GoogleEarth.

---

### Post by amarra on 2007-08-21
I've found the following workaround for ATI cards with fglrx

[http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen](http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen)

It works for me
Bye 
Antonio

---

### Post by Kilz on 2007-08-21
I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

---

### Post by lnxusr on 2007-08-22
Kilz's fix solved the problem for me (BIG Thanks :) ) on 32-bit Archlinux kernel 2.6.20 with fglrx 8.40.4, So will most likely work for Ubuntu. :guitar: I don't know about 64-bit though.

---

### Post by crjackson on 2007-08-22
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

It won't even install on my system as far as I can tell.  It seems to go through the install process then exits.

I can find no trace of GooleEarth on my computer.  Where would the installed files normally end up at?

---

### Post by crjackson on 2007-08-22
**What am I missing here?**

[08/22/2007 - 12:12.13] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
ia32-libs-kde is already the newest version.
ia32-libs-sdl is already the newest version.
ia32-sun-java6-bin is already the newest version.
lib32asound2 is already the newest version.
lib32bz2-1.0 is already the newest version.
lib32gcc1 is already the newest version.
lib32ffi4 is already the newest version.
lib32gfortran1 is already the newest version.
lib32ncurses5 is already the newest version.
lib32mudflap0 is already the newest version.
lib32objc1 is already the newest version.
lib32readline5 is already the newest version.
lib32stdc++6 is already the newest version.
lib32z1 is already the newest version.
gsfonts is already the newest version.
gsfonts-x11 is already the newest version.
alsa-oss is already the newest version.
m4 is already the newest version.
oss-compat is already the newest version.
dchroot is already the newest version.
linux32 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth
--12:08:17--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 66.102.1.91
Connecting to dl.google.com|66.102.1.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23,852,601 (23M) [application/octet-stream]

100%[=================================>] 23,852,601   587.03K/s    ETA 00:00

12:08:58 (578.29 KB/s) - `GoogleEarthLinux.bin' saved [23852601/23852601]

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.1.7076.4458..........................................................................

(setup.gtk2:23678): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)
Finished
Finished

!!SCRIPT OUTPUT END!!

---

### Post by lnxusr on 2007-08-22
> **crjackson said:**
> It won't even install on my system as far as I can tell.  It seems to go through the install process then exits.

I can find no trace of GooleEarth on my computer.  Where would the installed files normally end up at?
It will install to your Home directory ~/google-earth

---

### Post by Kilz on 2007-08-22
> **lnxusr said:**
> Kilz's fix solved the problem for me (BIG Thanks :) ) on 32-bit Archlinux kernel 2.6.20 with fglrx 8.40.4, So will most likely work for Ubuntu. :guitar: I don't know about 64-bit though.

Since I only run 64bit, you can be assured any fix I post will run on 64bit.

---

### Post by crjackson on 2007-08-22
> **lnxusr said:**
> It will install to your Home directory ~/google-earth

It didn't make there then.  It looks like I need to install something like a C compiler but I can't find anything in synaptic matching the **Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory** eror.

any suggestions?

---

### Post by lawnbowler on 2007-08-22
The files that Kilz attached was able to solve the problem for me in Ubuntu. Thanks very much :)

---

### Post by crjackson on 2007-08-22
> **lawnbowler said:**
> The files that Kilz attached was able to solve the problem for me in Ubuntu. Thanks very much :)

I can't get far enough along in the install process to to even create the folder where these files are to be placed.

---

### Post by Kilz on 2007-08-22
> **crjackson said:**
> I can't get far enough along in the install process to to even create the folder where these files are to be placed.

[Are you installing the bin file from google?]("http://earth.google.com/tour/thanks-linux4.html")

---

### Post by amariege on 2007-08-22
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

I had the same problem and those files solved it. I'm using feisy with amd64 and the open source drivers for ati card. :)

---

### Post by crjackson on 2007-08-22
> **Kilz said:**
> [Are you installing the bin file from google?]("http://earth.google.com/tour/thanks-linux4.html")

Yep...

---

### Post by heatpumpcontrol on 2007-08-22
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

Please tell me how to install these files... still learning Ubuntu

thx.

Update: used 
> sudo cp libGL.so.1 /opt/google-earth
> sudo cp libGL.so.1.2 /opt/google-earth

and it worked!!!... I guess I figured it out.... thanks

---

### Post by Kilz on 2007-08-23
> **crjackson said:**
> Yep...

and placing the GoogleEarthLinux.bin on the desktop then
```
cd ~/Desktop
sudo ./GoogleEarthLinux.bin
```
Does not install it?

---

### Post by crjackson on 2007-08-23
> **Kilz said:**
> and placing the GoogleEarthLinux.bin on the desktop then
```
cd ~/Desktop
sudo ./GoogleEarthLinux.bin
```
Does not install it?

It appears to go through the install process and then doesn't complete or it aborts.  No where on my HD is there a diredtory that I can find for googleearth after it's all said and done.

---

### Post by RavanH on 2007-08-23
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

WAHOOO!

I've said it before: Kilz, you :guitar: ! Thanks for this fix... Which - by the way: obviously - works perfectly for AMD64 :)

Trying to find the install folder of GE, I noticed it somehow has been installed into two folders: /opt/google-earth (this is the default one?) but also /usr/lib/googleearth ... The patch works on both installations (after copying the files to both directories) but now I have to decide which installation to remove because there can only be one earth, no? ;)

Update: Turned out that the /usr/lib/googleearth installation got there by way of Synaptic and the medibuntu repositories. It was a slightly older version so I removed that one...

---

### Post by oscarsfriend on 2007-08-25
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

Hi Kilz,

I just happened to stumble across this thread, and you helped me get google earth working perfectly (would seg fault before getting to splash screen).  Can I ask, where did you get the two files you attached from?  I have an nvidia gpu (and am using amd64 version of kubuntu feisty), so I am guessing these files have something to do with software 3D emulation. Right?

---

### Post by Kilz on 2007-08-25
> **oscarsfriend said:**
> Hi Kilz,

I just happened to stumble across this thread, and you helped me get google earth working perfectly (would seg fault before getting to splash screen).  Can I ask, where did you get the two files you attached from?  I have an nvidia gpu (and am using amd64 version of kubuntu feisty), so I am guessing these files have something to do with software 3D emulation. Right?

I got them from another thread, someplace. I cant remember where exactly.

---

### Post by oscarsfriend on 2007-08-26
Thanks, but it doesn't matter now as I just got it working without those files.  

Here's what I found for anyone interested...

I had the same segfault problem with wine, and to solve it I had to reinstall my nvidia drivers.  Now when I did this it asked me if I wanted to install 32 bit compatibility drivers -- I am fairly sure it didn't do this the first time around.  After this it worked no probs, and without the extra files.  My guess is that as I installed the 32 bit compatability libraries after my nvidia driver, it never bothered to install the 32 bit nvidia drivers.

Also, I tried the fix mentioned previously in the thread on a 32bit machine that was lacking 3D support, and it got google earth working on that (albeit a little bit slow).  So I'm sure the previous fix is using software 3D.  I'm also fairly sure google earth on  my 64bit machine is now running in full 3D, and this fix might well be worth trying out if you want to get things working faster.  Not sure if it'll work with other makes of graphic card, but maybe worth a try.

---

### Post by RavanH on 2007-08-26
> **oscarsfriend said:**
> I had the same segfault problem with wine, and to solve it I had to reinstall my nvidia drivers.  Now when I did this it asked me if I wanted to install 32 bit compatibility drivers -- I am fairly sure it didn't do this the first time around.  After this it worked no probs, and without the extra files.  My guess is that as I installed the 32 bit compatability libraries after my nvidia driver, it never bothered to install the 32 bit nvidia drivers.

I noticed slow performance too (software 3D?), so I would like to try your approach but only with an ATI driver (radeon xpress 200m :( ) but cannot quite follow... would you be so kind as to elaborate a bit more in n00b-lingo? As far as I understand it, you have both the 64bit and the 32bit Nvidia drivers installed on your system?

Thanks for any info :)

---

### Post by oscarsfriend on 2007-08-26
I don't know anything about the ati drivers.  So I don't think I can be of much help, but I'll tell you what I did.

nvidia have a script that I downloaded from their website and ran which installs the drivers for me.  I ran this script again, and it asked me if I wanted to install 32bit drivers as well, so I said OK.  It must have detected that I had the 32bit compatibility stuff installed (downloaded with apt-get -- search these forums for more info) then offered me this choice (or I must have refused previously, but I don't think so).

Yes, I have both the 64bit and 32bit libraries installed (or possibly special libraries for 32bit compatibility, I don't know).

I have no idea how the ati drivers are installed so it may be completely different for you.  Sorry I can't be of more help.

---

### Post by Kilz on 2007-08-26
This topic is about people with ATI graphics cards , not Nvidia. Those with nvidia will probably need another solution. Those that have nvidia cards are recommended not to confuse other ATI owners and not post in a thread dealing with ATI graphics.
Those that have ATI cards are best advised to use the [files attached in post #8]("http://ubuntuforums.org/showpost.php?p=3227468&postcount=8") of this thread. The fix is only for people with ATI graphics. People with ATI cards should also be able to see gears when they do the command ```
glxgears
``` If you dont see gears, or get an error you need graphics drivers. The fix will not work unless you already have working ATI graphics drivers installed.

---

### Post by oscarsfriend on 2007-08-26
> **Kilz said:**
> This topic is about people with ATI graphics cards , not Nvidia. Those with nvidia will probably need another solution. Those that have nvidia cards are recommended not to confuse other ATI owners and not post in a thread dealing with ATI graphics.

The solution you posted is generic, AFAICT, and works with nvidia and SiS cards (without hardware 3D working) as well -- I have tested it myself.  As I said above, I think the problem is to do with not having 32bit drivers on a 64bit system, which is why I posted.  The files you posted seem to bypass hardware 3D by using software 3D emulation (as far as I can tell, since you cannot tell me exactly where you got the files), which is great as a last resort, or if you can't get hardware 3D working, but will be slower than hardware 3D.  I thought this would be worth mentioning, as the information should also be useful to those with ati cards.

---

### Post by Kilz on 2007-08-26
> **oscarsfriend said:**
> The solution you posted is generic, AFAICT, and works with nvidia and SiS cards (without hardware 3D working) as well -- I have tested it myself.  As I said above, I think the problem is to do with not having 32bit drivers on a 64bit system, which is why I posted.  The files you posted seem to bypass hardware 3D by using software 3D emulation (as far as I can tell, since you cannot tell me exactly where you got the files), which is great as a last resort, or if you can't get hardware 3D working, but will be slower than hardware 3D.  I thought this would be worth mentioning, as the information should also be useful to those with ati cards.

It does? Wow, I thought it was only an ati fix.

---

### Post by oscarsfriend on 2007-08-26
> **Kilz said:**
> It does? Wow, I thought it was only an ati fix.
It is definitely some kind of generic software driver.  It would never have worked on two other graphic cards, otherwise.

---

### Post by DJSpeed on 2007-08-26
I love you!

---

### Post by thesoothsayer on 2007-08-27
Beautiful! Thanks! :)

---

### Post by RavanH on 2007-08-28
> **Kilz said:**
> It does? Wow, I thought it was only an ati fix.

Kilz, would you by any chance know how to get 32bit drivers for ATI (along with the normal 64bit one) working on a 64bit system? I downloaded the latest ATI and noticed both versions are in the package... 

Why? I want to try and test the previously mentioned NVidea methode with my ATI setup. But only if it can be done safely without trashing my Feisty install ;)

---

### Post by Kilz on 2007-08-28
> **RavanH said:**
> Kilz, would you by any chance know how to get 32bit drivers for ATI (along with the normal 64bit one) working on a 64bit system? I downloaded the latest ATI and noticed both versions are in the package... 

Why? I want to try and test the previously mentioned NVidea methode with my ATI setup. But only if it can be done safely without trashing my Feisty install ;)

Yes, both versions are in the same package. I installed the ATI drivers, [using these instructions for Feisty.]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") and Google earth works with the files I attached. I did not have to install anything else, and I believe (if I remember right) they were only 64bit packages.

---

### Post by RavanH on 2007-08-30
> **Kilz said:**
> Yes, both versions are in the same package. I installed the ATI drivers, [using these instructions for Feisty.]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") and Google earth works with the files I attached. I did not have to install anything else, and I believe (if I remember right) they were only 64bit packages.
That would be my guess too... But as oscarsfriend suggested (quote below), with the 64bit driver and the two-files-fix it appears GE runs in software 3D. I hoped it would be possible to get it all running on hardware 3D like with NVidea cards. To test it, I would somehow have to get the 32bit drivers on my 64bit system, correct?? If so, how could that be done - and ONLY if it can be done without messing up my Ubuntu installation?

> **oscarsfriend said:**
> Thanks, but it doesn't matter now as I just got it working without those files.  

Here's what I found for anyone interested...

I had the same segfault problem with wine, and to solve it I had to reinstall my nvidia drivers.  Now when I did this it asked me if I wanted to install 32 bit compatibility drivers -- I am fairly sure it didn't do this the first time around.  After this it worked no probs, and without the extra files.  My guess is that as I installed the 32 bit compatability libraries after my nvidia driver, it never bothered to install the 32 bit nvidia drivers.

Also, I tried the fix mentioned previously in the thread on a 32bit machine that was lacking 3D support, and it got google earth working on that (albeit a little bit slow).  So I'm sure the previous fix is using software 3D.  I'm also fairly sure google earth on  my 64bit machine is now running in full 3D, and this fix might well be worth trying out if you want to get things working faster.  Not sure if it'll work with other makes of graphic card, but maybe worth a try.

---

### Post by Kilz on 2007-08-30
> **RavanH said:**
> That would be my guess too... But as oscarsfriend suggested (quote below), with the 64bit driver and the two-files-fix it appears GE runs in software 3D. I hoped it would be possible to get it all running on hardware 3D like with NVidea cards. To test it, I would somehow have to get the 32bit drivers on my 64bit system, correct?? If so, how could that be done - and ONLY if it can be done without messing up my Ubuntu installation?

I dont know if thats possible with ATI. Feel free to try all the ways you can think up or find and then tell us how it went. :D

---

### Post by RavanH on 2007-08-30
> **Kilz said:**
> I dont know if thats possible with ATI. Feel free to try all the ways you can think up or find and then tell us how it went. :D

Hmmm... how to extract the 32bit debs from the script file... Installing the normal driver, I followed the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2) (probably similar to other how-to's) where **bash** is used to build the deb files. 

Would anyone know if there is an option in **bash** to force a different architecture? Or would there be another way to extract the desired drivers from the **.run** script file?

---

### Post by a-musing amazon on 2007-08-30
FWIW I run the ATI 3D restricted drivers and I also find that whenever I reinstall a new version of Googleearth, or previously whenever I compiled a new version of the ATI driver, either following the howtos or using Envy, then Googleearth would freeze on startup.

The problem seems to be in an incompatibility between the newer 32-bit libGLs ( /usr/lib32/libGL.so.1 ) and Googleearth.

The original one that came with Dapper  /usr/lib32/libGL.so.1.2 works, the later ones seem not to. Whenever you install Googleearth it overwrites the one you have with one that doesn't work.

Having got a copy of the shared library that works (I had to extract it from the .deb - you can use archive manager to open the deb and then extract it)I keep it in the /usr/lib32/ directory under another name (I just add a .old suffix) and then copy back it to correct the link after each install.

Marjorie

---

### Post by mariusthart on 2007-08-31
I got this to work without the libGL.so.1.2 file, using only the file libGL.so.1. According to this site:

[http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen]("http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen")

you should download an older ATI driver and extract the right file from it. The howto on the page  is written for 32 bit platform, but I downloaded an older 64 bit driver from ATI, located the file and put it in the google-earth directory.

It worked fine but it indeed uses software 3D instead of hardware 3D. Google earth warns me for that, but that is all. Perfromance will no doubt be less than when using hardware 3D, but at least I get some performance now.

Adding the libGL.so.1.2 didn't change a thing in my experience. Newer drivers also provide the files, but they don't work (I guess because they attempt to use the hardware).

---

### Post by a-musing amazon on 2007-08-31
In the (Ubuntu) distributions I've seen libGL.so.1 is simply a symbolic link to LibGL.so.1.2, so it would also work if your libGL.so.1 is just a renamed or copied LibGL.so.1.2. It can be slightly confusing since there are different versions, some the same size, and I've only found one of them that works. 

I think the one I have is from Dapper Drake,

The library is a 32-bit library, since Googleearth is only available in 32-bit, whether you get it from a 64-bit restricted package (as I did, where its in /usr/lib32/ or a 32-bit distribution where I presume it is in /usr/lib).

AFAIK the one I am using does employ hardware acceleration - its from the package xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.12-29.1_amd64.deb which you can get from
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.12-29.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.12-29.1_amd64.deb)

(I have downloaded it and run a diff against the my installed copy and they are the same).

To get it out of the .deb download it and then open it with package manager. Inside you will see a data.tar.gz. Left click on this and open with package manager, you then see the libGL.so.1.2 in /./usr/lib32. Its reported as being 627.4 kB but when you extract it its an exact 642476 bytes.

regards,

Marjorie

---

### Post by crjackson on 2007-08-31
Okay, let me see if I understand. If I open this file and copy the libs inside to my 32bit lib directory (on my 64 bit install), then google earth will run with 3D accelleration on my ATI card with fglrx drivers installed?

---

### Post by Kilz on 2007-08-31
> **crjackson said:**
> Okay, let me see if I understand. If I open this file and copy the libs inside to my 32bit lib directory (on my 64 bit install), then google earth will run with 3D accelleration on my ATI card with fglrx drivers installed?

I would copy them into the google earth folder just to be on the safe side.

---

### Post by crjackson on 2007-08-31
> **Kilz said:**
> I would copy them into the google earth folder just to be on the safe side.

Will it look for the libs in the google folder before looking at the standard 32 lib folder?

---

### Post by crjackson on 2007-08-31
> **Kilz said:**
> I would copy them into the google earth folder just to be on the safe side.

Do you plan to test this to see if you can get 3D hardware accell?

---

### Post by Kilz on 2007-08-31
> **crjackson said:**
> Will it look for the libs in the google folder before looking at the standard 32 lib folder?

It should, and yes Ill try. But it doesnt matter that much to me. Google earth is cool, but I dont use it that much. With my setup its fast even with software aceleeration.

Edit, I tried the libGL.so.1 and libGL.so.1.2 in that deb and google earth freezes just like before. Im going back to what works.

---

### Post by crjackson on 2007-08-31
> **Kilz said:**
> It should, and yes Ill try. But it doesnt matter that much to me. Google earth is cool, but I dont use it that much. With my setup its fast even with software aceleeration.

Edit, I tried the libGL.so.1 and libGL.so.1.2 in that deb and google earth freezes just like before. Im going back to what works.

Thanks - I won't even mess with it then.  It's not slow on my system either, I just wanted it if it worked.

---

### Post by a-musing amazon on 2007-08-31
> Okay, let me see if I understand. If I open this file and copy the libs
> inside to my 32bit lib directory (on my 64 bit install), then google 
> earth will run with 3D accelleration on my ATI card with fglrx drivers
> installed?
>
Interesting that it doesn't work for Klitz.

Although I'd just done a diff on it before, I've now copied it in properly and it still works OK. I certainly would not recommend copying the whole package since you (and I) are running Feisty and this is a Dapper (and much older ATI) based package. Unless you have sym-linked libGL.so.1 to libGL.so.1.2 it also won't make any difference.

This is what I have on my PC:

..........$ ls /usr/lib32/libGL.so* -al
lrwxrwxrwx 1 root root        12 2007-08-31 20:26 libGL.so.1 -> libGL.so.1.2
-rw-r--r--     1 root root 642476 2007-08-31 23:30 libGL.so.1.2
-rw-r--r--     1 root root 642552 2007-04-13 17:53 libGL.so.1.2.new
-rw-r--r--     1 root root 642552 2007-06-03 21:08 libGL.so.1.2.new2
-rwxr-xr-x   1 root root 642476 2006-09-24 12:02 libGL.so.1.2-old

The .old file is my backup of the lib that works, the .new and the .new2 ones are those installed by a new version of Googleearth or by the Feisty upgrade. Every time you install Googleearth.bin it overwrites the sym link.

regards,

Marjorie

(AMD 64x2 3800 @ 2.4 GHz, AsRock 939S56-M, Crucial DDR 1.5GB 2.5CL @ 500MHz, ATI X600 128 Mb)

---

### Post by RavanH on 2007-08-31
> **a-musing amazon said:**
> AFAIK the one I am using does employ hardware acceleration - its from the package xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.12-29.1_amd64.deb which you can get from
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.12-29.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.12-29.1_amd64.deb)

To get it out of the .deb download it and then open it with package manager. Inside you will see a data.tar.gz. Left click on this and open with package manager, you then see the libGL.so.1.2 in /./usr/lib32. Its reported as being 627.4 kB but when you extract it its an exact 642476 bytes.

Hi Marjorie, I followed your approach and it seems to work... GE feels a bit smoother but that might be only perception ;)

After that, I tried to do the same with the libGL.so.1.2 extracted from the fglrx-resticted package following version (2.6.17) but that resulted in the splash-screen-hang again. Same for the latest version straight from ATI's website... So I guess the latest version that works is 2.6.15. At least om my system :)

Funny thing: comparing 'your' version with the latest from ATI, I notice they are both **exactly** the same size but when doing a diff on them, I get the message that they are not the same - which is obvious, because only one works...

I also noticed that GE looks really weird when running it in a XGL session. The world looks all snowy and christmas like ;)... Anyone have that too?

--ravan

---

### Post by thekraut on 2007-09-02
Just to report that the 2 files Kilz mentioned right at the start of this thread did the trick for me.

Downloaded the  [libGL.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=41245&d=1187708216"), extracted the 2 files contained in it into the google-earth folder .

That was all I had to do - clicked on the desktop icon and it worked a treat.

Got a Dell 1501 Inspiron with 64bit AMD Turion x 2 (TL50)

---

### Post by mnb on 2007-09-02
> **RavanH said:**
> Ffffew... I'm back using the ATI driver ```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6650 (8.39.4)
``` which does seem to solve the issue of being thrown out of session...


Could you describe the steps you took to get fglrxinfo to report the right ATI card?  I'm having the same problem - i.e. after installing fglrx fglrx info reports:

display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1) 

and the fixes here: [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)  don't seem to fix the problem.  I'm getting desperate here...:(

Thanks,  Michael

---

### Post by crjackson on 2007-09-02
> **mnb said:**
> Could you describe the steps you took to get fglrxinfo to report the right ATI card?  I'm having the same problem - i.e. after installing fglrx fglrx info reports:

display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1) 

and the fixes here: [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)  don't seem to fix the problem.  I'm getting desperate here...:(

Thanks,  Michael

This is a thread about Google Earth. You need to go to my thread posted here.  There you will find the answer you seek.

[http://ubuntuforums.org/showthread.php?t=513315]("http://ubuntuforums.org/showthread.php?t=513315")

---

### Post by half-bite on 2007-09-02
Hi, 
This may sound silly, but I have read the posts on google earth and cannot find where to install the two downloaded files - I am running Linux Mint, and there doesn't seem to be an /opt folder - any ideas?

Thanks!

---

### Post by gtdaqua on 2007-09-03
Nvidia users with Kubuntu Feisty 64 and AMD64 follow this:


Install nividia-glx-new from Adept Package Manager and then run Google Earth. Works like a charm! 

No need downloading extra drivers and copying them on to folders.

---

### Post by Kilz on 2007-09-03
> **half-bite said:**
> Hi, 
This may sound silly, but I have read the posts on google earth and cannot find where to install the two downloaded files - I am running Linux Mint, and there doesn't seem to be an /opt folder - any ideas?

Thanks!

Depending on how it was installed it can be one of 2 places. If you installed it from the bin file from google its in /opt/google-earth I think.Since I LinuxMint is Ubuntu based I bet it uses the same deb file. If you installed it with a .deb file or with synaptic/apt/adept it should be in /usr/local/google-earth.

---

### Post by lazymints on 2007-09-19
Just clarification for the really cautious or confused;

you need to put the libGL.so.1 and libGL.so.1.2 files extracted from libGL.tar.gz in to /usr/lib/googleearth

this works for mint 3.0 and presumably other recent *buntus if you have installed google earth from medibuntu using apt or synaptic and your ati drivers using envy.

Thanks to Kilz for a working solution

---

### Post by osmanb on 2007-09-21
I have 64 bit AMD and 64 bit ubuntu feisty. GE is now working thanks to Kilz's solution.
:)

---

### Post by sjdude on 2007-09-24
I am running Feisty on an AMD64 Turion (Compaq V2410 laptop). I enabled the "restricted" ATI drivers in order to get Google Earth to work at all. After restarting, Google Earth worked exactly once. Subsequently, it would simply hang at the splash screen. I tried finding the "missing library", libCg.so, but decided to try an alternate approach. I added this:

[INDENT][FONT="FixedSys"]Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection[/FONT][/INDENT]

To the end of my /etc/X11/xorg.conf file, restarted X (CTL-ALT-BACKSPACE, or reboot if you prefer), and Google Earth now works perfectly for me. YMMV, but I'd rather disable an acceleration feature that, apparently, only Google Earth uses than install more libraries.

Have fun!

---

### Post by RavanH on 2007-09-24
> **mnb said:**
> Could you describe the steps you took to get fglrxinfo to report the right ATI card?  I'm having the same problem - i.e. after installing fglrx fglrx info reports:

display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1) 

and the fixes here: [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)  don't seem to fix the problem.  I'm getting desperate here...:(

Thanks,  Michael

Hmmm... dont remember what did the trick then... since, I've moved from Feisty to Gutsy testing but even now the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2) do the trick :) (only instead of 'bash ./ati-driver-installer-*.run --buildpkg Ubuntu/feisty' I use 'bash ./ati-driver-installer-*.run --buildpkg Ubuntu/gutsy')

Hope that helps you out.

---

### Post by Kilz on 2007-09-24
> **sjdude said:**
> I am running Feisty on an AMD64 Turion (Compaq V2410 laptop). I enabled the "restricted" ATI drivers in order to get Google Earth to work at all. After restarting, Google Earth worked exactly once. Subsequently, it would simply hang at the splash screen. I tried finding the "missing library", libCg.so, but decided to try an alternate approach. I added this:

[INDENT][FONT="FixedSys"]Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection[/FONT][/INDENT]

To the end of my /etc/X11/xorg.conf file, restarted X (CTL-ALT-BACKSPACE, or reboot if you prefer), and Google Earth now works perfectly for me. YMMV, but I'd rather disable an acceleration feature that, apparently, only Google Earth uses than install more libraries.

Have fun!

I have a feeling more than Google earth uses AIGLX. Copying 2 small files to the google earth folder is probably less of a problem since only Google earth will use them.

---

### Post by sjdude on 2007-09-25
> **sjdude said:**
> I am running Feisty on an AMD64 Turion (Compaq V2410 laptop). I enabled the "restricted" ATI drivers in order to get Google Earth to work at all. After restarting, Google Earth worked exactly once. Subsequently, it would simply hang at the splash screen. I tried finding the "missing library", libCg.so, but decided to try an alternate approach. I added this:

[INDENT][FONT="FixedSys"]Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection[/FONT][/INDENT]

To the end of my /etc/X11/xorg.conf file, restarted X (CTL-ALT-BACKSPACE, or reboot if you prefer), and Google Earth now works perfectly for me. YMMV, but I'd rather disable an acceleration feature that, apparently, only Google Earth uses than install more libraries.

Have fun!

The above has no effect after all. Instead, it takes restarting X to get it to work for me. I can run Google Earth exactly one time after starting X. After that, attempting to run it hangs every time. If I restart X, it works again, once.

Good luck!

---

### Post by mwacky on 2007-10-05
I copied the two files Kilz attached into my Google Earth folder and I no longer get caught on the splash screen, that's awesome, Thanks!

When starting google earth I get the warning about OpenGL and it runs sluggishly.  Any way to get out of the openGL mode.  I had GE running great, fast on this same machine with a Feisty 32 bit setup.  Currently I have Gusty AMD64 with Restricted Driver Manger ATI driver for a ATI Radeon Xpress 200M.  Do I need a better driver (beryl or envy)?

---

### Post by RavanH on 2007-10-05
> **mwacky said:**
> I copied the two files Kilz attached into my Google Earth folder and I no longer get caught on the splash screen, that's awesome, Thanks!

When starting google earth I get the warning about OpenGL and it runs sluggishly.  Any way to get out of the openGL mode.  I had GE running great, fast on this same machine with a Feisty 32 bit setup.  Currently I have Gusty AMD64 with Restricted Driver Manger ATI driver for a ATI Radeon Xpress 200M.  Do I need a better driver (beryl or envy)?

Did you install the restricted driver simply by activating it in the restricted driver manager, or did you download the latest from ATI's website? If you open a terminal screen and type ```
fglrxinfo
```
If you get a driver version lower than 8.40.4, you do not have the latest. Get it on [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) 

Then follow the instructions on 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)

Use the how-to for Feisty but only when doing the bash ...run command, change it for Gutsy like so:
```
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/**gutsy**
```

---

### Post by eph1973 on 2007-10-05
@Kilz

As usual, excellent solution.

> **Kilz said:**
> I have a feeling more than Google earth uses AIGLX. Copying 2 small files to the google earth folder is probably less of a problem since only Google earth will use them.

Just as a side note, for some of us running amd64's on laptops with the ATI Radeon cards have to run GNOME XGL with the AIGLX turned off in order to run Beryl.  So there's that.  But I am able to run Beryl, and using your solution, it worked just great.

---

### Post by mwacky on 2007-10-05
Thanks RavenH!

> Use the how-to for Feisty but only when doing the bash ...run command, change it for Gutsy like so:
Code:

bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/gutsy


Great tip, but when I try to unpack the driver I get the following:
```
mwacker@Milhouse:~/ATI$ sudo bash ./ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/gusty
Created directory fglrx-install.wR6237
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gusty
Requested package is not supported.
Removing temporary directory: fglrx-install.wR6237
```

I see the directory being created, but it is removed, because "Requested package is not supported"...  Can I force this? I don't care if it is not supported.  Sorry this may be a stupid question...

---

### Post by M.G. on 2007-11-02
> **amarra said:**
> I've found the following workaround for ATI cards with fglrx

[http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen](http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen)

It works for me
Bye 
Antonio

I didn't even need to reinstall the ATI drivers. Just tried "DISPLAY=:0 googleearth"command in terminal and it worked.:guitar:

---

### Post by dcstar on 2007-11-04
This works on my system, if someone else with AMD64 that is going to install Google Earth can try it to verify that it works on their system as well, it may be simpler than some of the other solutions in this thread:

[http://ubuntuforums.org/showthread.php?t=601272](http://ubuntuforums.org/showthread.php?t=601272)

---

### Post by kestas.j on 2007-11-04
> I see the directory being created, but it is removed, because "Requested package is not supported"... Can I force this? I don't care if it is not supported. Sorry this may be a stupid question...

To get Gutsy deb packages from install package use the following:

> bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/7.10

---

### Post by RavanH on 2007-11-04
OK, I ' ve been away from this thread since I marked it as SOLVED a while ago...

Now I am back :( because Google Earth doesn't run anymore since I installed the latests ATI 8.42.3 driver.

Anybody any ideas? Kilz?

EDIT: I should provide some more info -- before kliz fix (and with ATI fglrx 8.40.2 driver + XGL), it would hang at the splash screen, now (even with Kilz fix) after installing the new ATI 8.42.3 driver + AIGLX, the splash screen comes up, but after a short while vanishes again without at trace. No GE, nothing...

---

### Post by Kilz on 2007-11-04
> **RavanH said:**
> OK, I ' ve been away from this thread since I marked it as SOLVED a while ago...

Now I am back :( because Google Earth doesn't run anymore since I installed the latests ATI 8.42.3 driver.

Anybody any ideas? Kilz?

EDIT: I should provide some more info -- before kliz fix (and with ATI fglrx 8.40.2 driver + XGL), it would hang at the splash screen, now (even with Kilz fix) after installing the new ATI 8.42.3 driver + AIGLX, the splash screen comes up, but after a short while vanishes again without at trace. No GE, nothing...

8.42.3 is a new driver, from a new code base. It isnt simply an updated 8.40.2. I would recommend filing a bug report with ATI as its a driver issue, and the driver is proprietary.

---

### Post by RavanH on 2007-11-05
> **Kilz said:**
> 8.42.3 is a new driver, from a new code base. It isnt simply an updated 8.40.2. I would recommend filing a bug report with ATI as its a driver issue, and the driver is proprietary.

Ok, I have done that. See [http://ati.cchtml.com/show_bug.cgi?id=877](http://ati.cchtml.com/show_bug.cgi?id=877). Thanks :)

---

### Post by andresv on 2007-11-05
In my case, with a fresh ubuntu gutsy install (4.11.2007), kilz's solution (adding the two files) worked - thanks!

My googleearth is from ubuntu's repos - I only need to put the two files into

/usr/lib/googleearth

[INDENT]using, as is clear,

sudo mv libGL.so.1 /usr/lib/googleearth
sudo mv libGL.so.1.2 /usr/lib/googleearth
[/INDENT]

Thank you, kilz! :)

andresv

---

### Post by lifeempowered.com on 2007-12-18
Awesome! Worked perfectly for me!

Thanks!

---

### Post by C. Wizard on 2008-02-19
> **amarra said:**
> I've found the following workaround for ATI cards with fglrx

[http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen](http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen)

It works for me
Bye 
Antonio
Many Thanks it works for me. A little slow and jerky, but it works. Many Thanks!

---

### Post by Tyler H on 2008-03-23
I've been trying to get this to work for hours now. I've had two pots of coffee and am about to apply a battering ram to the side of my computer. Nothing has worked.

GE starts in terminal and then I get this.
"Xlib:  extension "XFree86-DRI" missing on display ":1.0""

I've applied both(as many versions as I could get a hold of)  libGL.so files to the GE folder with no luck.
I get the splash screen and then it dies.

I'm running AMD64 with a Radeon x1900gt w/ 8.37 Cat drivers.

Any knowledge would be much appreciated.

---

### Post by martin saint martin on 2008-04-01
i'm having the same "freeze @ splash" issue.  when i try to copy the libGL to /usr/share/googleearth i'm told that i don't have permission to write to this folder.  is there a way around this?

---

### Post by RavanH on 2008-04-01
> **martin saint martin said:**
> i'm having the same "freeze @ splash" issue.  when i try to copy the libGL to /usr/share/googleearth i'm told that i don't have permission to write to this folder.  is there a way around this?
Are you using **sudo** in front of the move command (in terminal window) or are you trying to do this with nautilus (or any other file browser) ? If the latter, use commands in terminal window instead. If you are already, AND you are using sudo, your login might not be in the sudoers list. A quick way around this is to become root for a short while by giving the command **su** and entering the root password. Then do the file move again...

---

### Post by martin saint martin on 2008-04-01
i was using the file browser method.  how would i do it using the command line?

---

### Post by RavanH on 2008-04-01
> **martin saint martin said:**
> i was using the file browser method.  how would i do it using the command line?
First you need to put the files into your home folder (you know, /home/[YOUR_USER_NAME]/ ) and then open a terminal window. You know how to do that, i suppose? 

In this post [http://ubuntuforums.org/showpost.php?p=3237385&postcount=20](http://ubuntuforums.org/showpost.php?p=3237385&postcount=20) user heatpumpcontrol describes the commands he/she used to copy the files to the directory where google-earth was located on that computer (in /opt/google-earth/ to be exact) ```
sudo cp libGL.so.1 /opt/google-earth
sudo cp libGL.so.1.2 /opt/google-earth
```

But in your case, it might be a different location. It all depends on how you got google earth installed on your system. 

To find the correct location use the command ```
whereis google-earth
``` and it might print something like ```
google-earth: /usr/lib/googleearth
``` and you can use that location to replace the one at the end of the **cp** command given above...

Good luck :)

---

### Post by gug@fnal.gov on 2008-04-06
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

I have an ATI Raedon 9600 and had trouble with googleearth. The first problem seemed to be killing the X session and returning me to a login screen. Enabling the restricted drivers resolved that problem, and next up was the hang at the splash screen with 100% CPU. Downloading the tar file of libGL.so libraries, extracting and copying them (sudo) to /opt/google-earth/ area did the trick. Thanks. Last night the forum didn't let me access the link to the tar file, user error probably, but I did find a download of libGL.so.1.2 elsewhere and renaming that to libGL.so.1 also worked. This morning once I was able to download these files I replaced the one from last night and it still works.

---

### Post by martin saint martin on 2008-04-07
here is where i'm stuck:

martin@martin-desktop:~$ cd ~/Desktop
martin@martin-desktop:~/Desktop$  chmod +x GoogleEarthLinux.bin
martin@martin-desktop:~/Desktop$ sudo ./GoogleEarthLinux.bin
[sudo] password for martin:
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
martin@martin-desktop:~/Desktop$ sudo cp libGL.so.1 /opt/google-earth
cp: cannot stat `libGL.so.1': No such file or directory
martin@martin-desktop:~/Desktop$ whereis google-earth
google-earth:

i downloaded and extracted the libGL from the Kliz post before running the sudo cp libGL... command.  here is some more of my trail and error:

martin@martin-desktop:~$ whereis googleearth
googleearth: /usr/lib/googleearth /usr/lib64/googleearth /usr/local/bin/googleearth
martin@martin-desktop:~$ sudo cp libGL.so.1 /usr/lib64/googleearth
cp: cannot stat `libGL.so.1': No such file or directory
martin@martin-desktop:~$ sudo cp libGL.so.1 /usr/lib/googleearth
cp: cannot stat `libGL.so.1': No such file or directory
martin@martin-desktop:~$ sudo cp libGL.so.1 /usr/local/bin/googleearth
cp: cannot stat `libGL.so.1': No such file or directory
martin@martin-desktop:~$ whereis libGL.so.1
libGL.so: /usr/lib/libGL.so.1 /usr/lib64/libGL.so.1
martin@martin-desktop:~$ sudo cp libGL.so.1 /usr/lib64/googleearth
cp: cannot stat `libGL.so.1': No such file or directory
martin@martin-desktop:~$ whereis libGL.so.1.2
libGL.so.1: /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.2 /usr/lib64/libGL.so.1 /usr/lib64/libGL.so.1.2
martin@martin-desktop:~$ sudo cp libGL.so.1.2 /usr/lib/googleearth
cp: cannot stat `libGL.so.1.2': No such file or directory

wtf am i doing wrong?

---

### Post by RavanH on 2008-04-08
> **martin saint martin said:**
> ...
martin@martin-desktop:~$ sudo cp libGL.so.1.2 /usr/lib/googleearth
cp: cannot stat `libGL.so.1.2': No such file or directory

wtf am i doing wrong?

Have you considered the possibility that it is not the destination that is causing the error, but the source? I mean, is the file libGL.so.1.2 in the directory where you issue the cp command from (be it either Desktop or home folder) or did you extract the files from Kilz's package to another location?

Make sure they are in your home folder and then try the above command again...

---

### Post by Ryuki_NdranC on 2008-04-13
Im having the same problem, but when i do:

```
whereis google-earth
```

i got:

```
google-earth:
```

when i do:

```
whereis googleearth
```

i got:

```
googleearth: /usr/bin/googleearth /usr/lib/googleearth /usr/lib64/googleearth /usr/share/googleearth /usr/share/man/man1/googleearth.1.gz
```

I installed googleearth trough repositories (medibuntu) and i already cp all the libGL.so.1 and libGL.so.1.2 into all the folders (including ~/.googleearth) and nothing seems to work. 
Should i install it from the bin file? why is not google-earth like you guys instead of my googleearth folders?

Thx in advance

---

### Post by Ryuki_NdranC on 2008-04-14
I don't wanna start a new thread, i have read them all but nothing works... :(

---

### Post by Tehrasha on 2008-04-15
My google-earth quit working after I upgraded to the latest kernel.
Installed the 2.6.15-51-386 kernel, recompiled and installed the nVidia drivers, and nothing dealing with 3d has worked since. Only get segfaults when launching 3d apps.

---

### Post by Xbehave on 2008-04-15
This solution broke a working google earth with
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

```
removing the files got googleearth back to its previous state (no-info & flikering while in compiz)

UPDATE: If i install the libgl.so.1.2 from my ati drivers, it doesnt break anything, but it doesnt fix my problem either.

---

### Post by Ryuki_NdranC on 2008-04-15
> **Xbehave said:**
> This solution broke a working google earth with
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

```
removing the files got googleearth back to its previous state (no-info & flikering while in compiz)

UPDATE: If i install the libgl.so.1.2 from my ati drivers, it doesnt break anything, but it doesnt fix my problem either.

I have the exact same video card in my laptop, and i can seem to make it work with googleearth, at least the one installed with medibuntu repositories. I followed this guide (and many others) and put the libGL.so.* in ALL the listed directories of googleearth and nothing... When i get home im gonna try with libGL.so.* + no compiz + restart and see if it works.

Anyone thinks there is a difference between the medibuntu installation and the source installation???

---

### Post by radamo on 2008-04-15
> **Xbehave said:**
> This solution broke a working google earth with
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

```
removing the files got googleearth back to its previous state (no-info & flikering while in compiz)

UPDATE: If i install the libgl.so.1.2 from my ati drivers, it doesnt break anything, but it doesnt fix my problem either.

Same issue for me.  With the files my complete system locks up.  Without the files I get a flickering start screen.  I have the latest kernel and driver with a Radeon 3850.

Thanks for all the help....
RA

---

### Post by marcellosales on 2008-04-26
[http://groups.google.com/group/earth-linux/browse_thread/thread/8eca0fe2595f18de/8fc2eba06db8cff5#8fc2eba06db8cff5](http://groups.google.com/group/earth-linux/browse_thread/thread/8eca0fe2595f18de/8fc2eba06db8cff5#8fc2eba06db8cff5)

---

### Post by martin saint martin on 2008-04-27
i've had some issues getting GE up and running in the past but i want to give it another shot.  i think that i should start from scratch with GE, due to the fact that i may have made a mess of thing in the past when i tried getting GE up and running.  so my question is how can i clear all GE from my HDD and start over for square one?

my lack of trust in ubuntu was holding me back.
upgraded to hardy and it worked. the how and why i've got no clue but w/gusty on GE it was a no go, but w/ hardy it works, f yah!!!(intalled via medibuntu instead of the google site and go f'in figure GE works)

---

### Post by bptonner on 2008-05-11
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

Similar issue on upgrade from Gutsy to Heron.
Presario 2100 Laptop with ATI chips.

Google Earth installs, but will only run as root. Hangs at splash screen when run as user.

Appears to be a problem finding the right library, which is not automatically installed in the /opt/google-earth directory.

Workaround:
sudo cp /usr/lib/libGL.so.1.2 /opt/google-earth
sudo chmod ugo+x libGL.so.1.2

and the same two commands for libGL.so and libGL.so.1

---

### Post by luaroif on 2008-07-24
> **Kilz said:**
> I had a similar problem. I found that at some of the newer drivers from ATI are the problem. The fix was to install the 2 files attached into your googlearth folder.

Mil gracias!!! Funciono!!!
Thanks!!

---

