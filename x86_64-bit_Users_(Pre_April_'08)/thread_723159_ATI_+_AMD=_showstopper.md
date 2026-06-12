---
title: "ATI + AMD= showstopper?"
date: 2008-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by studo77 on 2008-03-13
After a very unsuccesful testing of the new 8.3 drivers for ATI-graphics. I decided to test out the Hardy-alpha. 

By default it will install the 8.3 drivers, but these do not work on AMD64.  so now i can choose to go 7.10(64) with old drivers, or 8.10(64) with only 2d or my final solution 8.10(32). So because of my hardware i am not able to use my hardwares potential in a newer Ubuntu release.:confused:
I do not see the final release to have changed this, a lighter version of this problem i had with Gutsy, i am only able to install form alternative CD, not a liveCD. (which, to me, is a showstopper for newbies)


As i see it, this is a step backwards. Apparently not that many uses AMD or ATI. But in the near vicinity of the people i know, i can not propose Ubuntu as an alternative, they have this type of hardware.

Ok, if money is spent, it is better used on HW than a Vista-license.

---

### Post by Shakey_Jake33 on 2008-03-13
Just like to point out that my AGP-based X1650XT in my spare machine does not work with newer ATi revisions (8.1/2/3), and have to install an earlier revision using Envy.  So if 8.3 gets installed automatically, that's a big problem.

---

### Post by Jouke74 on 2008-03-13
@studo77 I am going to prove you wrong...

My machine :
AMD X2 4200
Asus EAX1600 Pro
2 GB Corsair
74 GB WD raptor + 250 GB WD caviar.

uname -a produces:
2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

I did:
1. Clean install from Gutsy AMD64 Alternate.

2. No restricted drivers touched, so this is started from Vesa 
(otherwise it will require more steps like blacklisting and uninstalling earlier stuff, also the old configuration files of fglrx seem to interfere).

3. Updated the system fully, this is important for updated xorg.

4. Downloaded the latest ATI driver 8.3

5. Then did this:

> sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms ia32-libs

> sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy

> gksu gedit /etc/default/linux-restricted-modules-common
   Type: DISABLED_MODULES="fglrx"
   save
   close

> sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb
   This will produce errors for amdcccle.

> sudo apt-get install -f
   This forces the dependencies to be installed.

> sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
   Can only be done after previous step.

> sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb
   All of them need to be redone.

> Then type "Y" when asked to overwritre the compiz files.

> sudo aticonfig --initial
    Needs to be done for cccle to work. 

Result after some more installing (VLC + Conky) and changing some desktop color + nautilus settings: 
[IMG][[IMG]http://img260.imageshack.us/img260/1756/desktopdi2.th.png[/IMG]](http://img260.imageshack.us/my.php?image=desktopdi2.png)[/IMG]

(The background is my wife, the video my sons with my father, so stay nice :-))

The only thing that does not work smooth is the XV video overlay under Compiz. Hence, I did not enable the video overlay.

Conclusion: At least on a X1600 card most things work.

---

### Post by studo77 on 2008-03-22
For many users that method will not be available. I can't find the page where i read the amd64 and 8-3 driver combination. Thought it was on wiki.ubuntu.com but not entirely sure.

Anyway on there this ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) gives a lot of combinations where you are in trouble on AMD64 system.

A lot of people will be using Ubuntu, and not sure of that series of commmands. They will use the built-in Proprietary drivers manager or use Envy. And thereby fail, and having to reinstall their system. If your method works for all amd64 systems, why is it then not he way it is installed in one or both of the above? And having done that way of install, what about updates and upgrades, do they work. Or will you have to do another series of terminal commands. It is not very userfriendly.

Personally i thought "a win-license or a nvidia-graphics?" Chose the latter, and it goes straight from box, using Proprietary drivers manager.

---

### Post by Jouke74 on 2008-03-22
From the link you gave it shows this:

> Install from ati.com (latest version of drivers)
Instructions for Ubuntu 7.10 (Gutsy) with ATi 8.443.1-1 and above binary drivers

As of the new 8.443.1-1 drivers, installation is greatly simplified using Dells Dynamic Kernel Module Support Framework ([WWW] [http://linux.dell.com/dkms](http://linux.dell.com/dkms)). To begin first install the needed packages:

sudo apt-get install dpkg-dev debhelper libstdc++5 dkms

You will then need to build the installation packages with the downloaded ATi drivers (ensure the ATi drivers have the execute flag set first):

./ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy

Then install the binary drivers:

sudo dpkg -i fglrx-kernel-source_<version>.deb

Run the following command to install the Xorg driver

sudo dpkg -i xorg-driver-fglrx_<version>.deb

Finally run aticonfig to build your new xorg.conf if you have not done so before:

sudo aticonfig --initial


As you can read, most commands are similar. Only where the problems start, I do different things... I also also install the Catalyst contol centre which is not done following this wikki. They are simply avoiding the problem by not instaling amdcccle. I force install it with symlinking the library.

I on purposely did not say anything about an upgrade / update from an older ATI driver because I am not sure if it works correct. You need to blacklist and remove lot's of stuff. Also the old config files seem to interfere with the new driver. I agree with you that an upgrade / update from an older driver will likely lead to failure! I don;t know how it is going to be with new updates as this is the most recent driver. Other security updates install fine until now.

My background came b.t.w. from the Phonorix forums:
[http://www.phoronix.com/forums/showthread.php?t=8204&page=2](http://www.phoronix.com/forums/showthread.php?t=8204&page=2)

Yes, Nvidia or using the Restricted drivers is much easier. But in essence you're using older drivers when using the restricted, and for ATI that means a big difference.

You can use Envy as well, and for some people this does seem to work with the newest ATI drivers. Here mileage might vary. I don't know I never have used Envy.

---

### Post by crjackson on 2008-03-22
> **studo77 said:**
> After a very unsuccesful testing of the new 8.3 drivers for ATI-graphics. I decided to test out the Hardy-alpha. 

By default it will install the 8.3 drivers, but these do not work on AMD64.  so now i can choose to go 7.10(64) with old drivers, or 8.10(64) with only 2d or my final solution 8.10(32). So because of my hardware i am not able to use my hardwares potential in a newer Ubuntu release.:confused:
I do not see the final release to have changed this, a lighter version of this problem i had with Gutsy, i am only able to install form alternative CD, not a liveCD. (which, to me, is a showstopper for newbies)


As i see it, this is a step backwards. Apparently not that many uses AMD or ATI. But in the near vicinity of the people i know, i can not propose Ubuntu as an alternative, they have this type of hardware.

Ok, if money is spent, it is better used on HW than a Vista-license.

Well I guess I've just been very lucky.  I've got several AMD64 machines with ATI graphics cards.  I installed the 8.3 drives using Envy and they ALL work very nicely.  I suspect after a couple more releases most everyone will be pretty happy.

---

### Post by hangfire on 2008-03-22
> **studo77 said:**
> 
Ok, if money is spent, it is better used on HW than a Vista-license.

I found this thread because today for the, oh, maybe tenth time, my Gutsy Gibbon 64 on AMD 754/ATi 9550 went into flashing screen mode. I say flashing, but few flashes, mostly black screen. This is after January when I downloaded the last of the "good" fglrx ATi drivers from their web site and fixed it in place so it couldn't be updated. Don't know what broke it THIS time. Didn't get a new kernel, so that's not it.

I ended up swapping in an old 9200 and doing the usual dpkg-reconfigure --force xserver-xorg . Memorize this command (like I did). If you go the 64 bit on ATi video route, you'll be using it often.

And get used to jumping through MAJOR hoops to get various kinds of video running... and keep it running.

I do have to say, I did have EVERYTHING working for two solid months before an update broke it again. Funny thing, when I let it do an update, I was thinking to myself, "gee, I don't fear these anymore, forcing it to not update the fglrx driver really worked wonders for me." Ha!

Next card- nVidia. Not that they don't have driver problems under Linux, but wow, not the pain I've gone through with THIS setup. I'll get a 8800 of some stripe and trickle down one of the 6 or 7 series to my Linux box.

Later, gotta go and fix my various video modes now.
-HF

---

### Post by studo77 on 2008-03-23
> **hangfire said:**
> 
Next card- nVidia. Not that they don't have driver problems under Linux, but wow, not the pain I've gone through with THIS setup. I'll get a 8800 of some stripe and trickle down one of the 6 or 7 series to my Linux box.

Later, gotta go and fix my various video modes now.
-HF

I can tell you that it will be a lot easier. I bought a 8500 card, and i have not yet seen any problems. Of course there will be some, but i think it will be minor sompared to ATI. I am not doing any gaming, except for a Nexuiz a few times. It performs great. If i am to give advice for newcomers to linux, i will telle them to stay away if they have an ATI-card, especially with a AMD64-processor.

---

### Post by Jouke74 on 2008-03-23
Funny enough the 8800 can also cause black screens after a Gutsy install, posts enough on the forum about that. The solution is also simple, turn the splash into nosplash at the kernel boot options in grub. Anyway, I agree with the posters that ATI is more hassle than Nvidia. This is also well know in the linux world. Just hope that ATI will get better at supporting Linux, which is mainly due to the influence of AMD by the way!

---

### Post by studo77 on 2008-03-23
oh yes, it is not the linux communitys fault at all. It is doing a great job, that multitude of involvement is truely a proof that globalization can be good.

---

