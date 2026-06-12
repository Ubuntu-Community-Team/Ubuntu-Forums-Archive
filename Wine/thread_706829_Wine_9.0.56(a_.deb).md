---
title: "Wine 9.0.56(a .deb?)"
date: 2008-02-24
forum: Wine
---

### Post by Twitch6000 on 2008-02-24
Hey have they got a .deb for ubuntu on the new version of wine yet?
I wanna know because I haven't used my ubuntu in a little bit and it seems this patch might let me run everything I need.

---

### Post by SBFC on 2008-02-24
No, there isn't one ready yet. Some users have created debs of their own and shared them, however. Look for other Wine .56 related threads.

You could also install it from source.

---

### Post by kindofabuzz on 2008-02-25
yes there is a deb version [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by SBFC on 2008-02-25
> **kindofabuzz said:**
> yes there is a deb version [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

If you'll notice, he was asking for a deb of the _newest_ version of wine, not whether or not wine debs existed in general.

---

### Post by orgy on 2008-02-25
compile it yourself!

sudo apt-get build-dep wine
sudo apt-get install checkinstall

download latest wine.tar.gz, uncompress it and then do:

./configure --prefix=/usr
make depend
make
-- wait 15 to 30 minutes, depends on your computer
sudo checkinstall

When doing sudo checkinstall accept all the defaults and thats it, you got yourself the latest wine installed on your system!

---

### Post by Twitch6000 on 2008-02-25
> **orgy said:**
> compile it yourself!

sudo apt-get build-dep wine
sudo apt-get install checkinstall

download latest wine.tar.gz, uncompress it and then do:

./configure --prefix=/usr
make depend
make
-- wait 15 to 30 minutes, depends on your computer
sudo checkinstall

When doing sudo checkinstall accept all the defaults and thats it, you got yourself the latest wine installed on your system!

See I understand all of that until the configure make depend and make parts =[.
Explain that to me.Thats the only reason why I hate tar.gz's and other things lol.

---

### Post by orgy on 2008-02-25
ok, do this.

download the lastest version of wine, which is here: [http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.56.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.56.tar.bz2)

place it on your desktop, right click it and extract it.

Then open up a console or terminal wich is in Applications-> Accessories

and type this:
1.
sudo apt-get build-dep wine
2.
sudo apt-get install checkinstall
3.
cd Desktop/wine-0.9.56
2.
./configure --prefix=/usr
4.
make depend
5.
make
6.
sudo checkinstall

When you do this last step it wiill ask you for some info, just press ENTER when it does.

And that's it. thats what all you have to do, easy huh?

---

### Post by SBFC on 2008-02-25
Wine also has it's own install tool that runs configure/make/make install for you, if you prefer.

After sudo apt-get build-dep wine you can cd into the extracted wine source directory and run ./tools/wineinstall. After it is done configuring it will prompt you for root password so that it can install after make is finished.

---

### Post by Twitch6000 on 2008-02-25
ok did that and it works but in the app menu I don't see wine but,I can load .exe's so help?

---

### Post by orgy on 2008-02-25
there's no app menu for wine.

Press alt+f2, and type: winecfg, there you can configure wine.

---

### Post by Twitch6000 on 2008-02-26
> **orgy said:**
> there's no app menu for wine.

Press alt+f2, and type: winecfg, there you can configure wine.

There usally is when you install it with a .deb =[.

---

### Post by orgy on 2008-02-26
what kind of menu?

a menu for wine?
or a menu for the windows apps u installed through wine?

if the second, then yes, there should be a "Wine" menu.

---

### Post by Zaphod on 2008-02-26
this menu?

---

### Post by Twitch6000 on 2008-02-26
> **Zaphod said:**
> this menu?

yeah that menu I didn't get one =[.Although other then that I can still run wine just fine :/.

---

### Post by Sleaka J on 2008-02-27
It seems you only get the menu when you install it via a package manager.

I hope they bring out the DEB soon enough. I'm waiting...

---

### Post by wsamh on 2008-02-27
I tried to make a package by following the instructions on this post but I was getting a message saying I need to install a  flex package. What is it and how do I get it? But to help you guys. I think you have to remove the previous version first, then install the new version. I read that if you install over the previous version you might encounter problems. So how do I get a flex package?

---

### Post by Meow27 on 2008-02-27
it shouldn't take that long to upload the deb up there.
perhaps the wine devs dont know about it?

---

### Post by CarpKing on 2008-02-27
> **Meow27 said:**
> it shouldn't take that long to upload the deb up there.
perhaps the wine devs dont know about it?

I'm not sure who exactly runs the official repository.  The last version's deb didn't come out till a few days before this version was released, but in the past there was usually only a day or two delay.  Maybe whoever runs it is really busy lately?

---

### Post by blackdragon1157 on 2008-02-27
Scott Ritchie handles the Ubuntu packages for Wine.  He must be pretty busy, 9.55 was in the repos somewhere near the 20th (~2 weeks late).

---

### Post by nerdymark on 2008-02-29
I created a deb for the Hardy users. You can get the deb here:
[URL="http://nerdymark.com/hardy-wine-0.9.56-deb"]http://nerdymark.com/hardy-wine-0.9.56-deb
[/URL]

---

### Post by Mr.Johnny on 2008-02-29
Even after doing apt-get build-dep wine, mine complains about libxi and libxinerama, so besides that I also do

$sudo apt-get install libxi-dev 
$sudo apt-get install libxinerama-dev

what does "checkinstall" do?

I always do:

$ sudo su
$ apt-get build-dep wine
$ apt-get install libxi-dev 
$ apt-get install libxinerama-dev
$ ./configure --prefix=/usr
$ make depend && make
$ make install

---

### Post by orgy on 2008-02-29
checkinstall creates a deb and installs wine from it, so u can remove it through synaptic if you want.

Nothing wrong with the way you do it.

---

### Post by Mr.Johnny on 2008-02-29
That means I can create a *.deb package and install it in several machines?

---

### Post by orgy on 2008-02-29
i know it generates a .deb, im not sure it works on other machines, haven't tried that.

---

### Post by jharadie on 2008-02-29
GREAT directions, thank you! (said the noob)

> **orgy said:**
> ok, do this.

download the lastest version of wine, which is here: [http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.56.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.56.tar.bz2)

place it on your desktop, right click it and extract it.

Then open up a console or terminal wich is in Applications-> Accessories

and type this:
1.
sudo apt-get build-dep wine
2.
sudo apt-get install checkinstall
3.
cd Desktop/wine-0.9.56
2.
./configure --prefix=/usr
4.
make depend
5.
make
6.
sudo checkinstall

When you do this last step it wiill ask you for some info, just press ENTER when it does.

And that's it. thats what all you have to do, easy huh?

Before follwing this I had Synaptic installed, tried to run, got massive errors, esp Page Errors.  Did Synaptic Complete Remove (purge), rebooted, followed above steps.  Now I'm getting:

Application tried to create a window, but no driver could be loaded.
Unknown error (998).
Application tried to create a window, but no driver could be loaded.
Unknown error (998).
err:ole:apartment_createwindowifneeded CreateWindow failed with error 998

My info: Ubuntu 7.10, all updates as of this post, kernel 2.6.22-14-generic.  Celeron 2.8G CPU, 2G RAM, S3 Unichrome Pro VGA Adapter (PCI), (FWIW) Bt878 card.

Wonder if screen resolution might be part of the problem?  Currently running 1280x1024.

Thanks.

Tried 1024x768 and 800x600, got same errors.  Obviously I need a different or additional driver, how do I figure it out?

Thanks.

---

### Post by Melhisedek on 2008-03-01
Just a quick question... As wine has "Stubs for all the d3dx9_xx dlls."  with this last release... Should I remove the ones I copied in from Windows to get some games working and disable  native support?

---

### Post by zebulon M on 2008-03-01
> **Melhisedek said:**
> Just a quick question... As wine has "Stubs for all the d3dx9_xx dlls."  with this last release... Should I remove the ones I copied in from Windows to get some games working and disable  native support?
Nah, stubs don't actually contain any new code. If native .dlls were necessary before, they probably still are necessary. But u can always check the status of the games in the Application database, maybe they are working better in wine now.

---

