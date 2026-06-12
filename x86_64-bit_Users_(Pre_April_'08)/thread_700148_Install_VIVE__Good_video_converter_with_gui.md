---
title: "Install VIVE / Good video converter with gui?"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingleer on 2008-02-18
I have tried and failed to install vive

[http://vive.sourceforge.net/](http://vive.sourceforge.net/)

It's a video converter that has an easy to use i386 deb file, but no amd version. 

Does anyone know of an equivalent program for the 64 bit version of ubuntu. It must have a gui, and be easy to install (ie no compiling stuff manually because that's beyond my skill level if there a tonne of dependencies missing and the missing dependencies have missing dependencies etc).

---

### Post by erginemr on 2008-02-18
You should focus on **ffmpeg **(backend) and **WinFF **(GUI frontend), both of which receive high praises in the Linux community. No compiling is required, but I am not sure about 64 bit support though.

Another option is **avidemux**.

---

### Post by kingleer on 2008-02-18
> 
You should focus on ffmpeg (backend) and WinFF (GUI frontend), both of which receive high praises in the Linux community. No compiling is required, but I am not sure about 64 bit support though.


WInff has no 64 bit version

> 

Another option is avidemux.



It's a video editor. I'm kinda looking for a stand alone video converter. Something simple.

---

### Post by kingleer on 2008-02-18
Never mind. I solved my problem the 32 bit version of winff installs fine if I do the following 


cd ~/Desktop
sudo dpkg --force-architecture -i Nameofthefile.deb


source: 

[http://tghc.org/32apps.html](http://tghc.org/32apps.html)

> 
64bit versions of Ubuntu can run 32bit applications. In one sense it is multiarch, but it is not automatic multiarch. We can install the application, but we must manually take care of dependencies. To install a 32bit application, get the .deb for it. You can get it from the creators site or download it here. Use the package search. Find the application, click on the i386 download. Then save it to your desktop.

Once it is on your desktop. Open up a terminal type in

cd ~/Desktop
sudo dpkg --force-architecture -i Nameofthefile.deb

Now that you have the application installed type the name of the application in the terminal. If the application starts up you are done. If not you will get an error telling you it cant find a lib. In this case we may need to manually add a lib.
There are a few 32bit libs already packaged for 64bit dapper. Before we get into adding some manually it is a good idea to make sure you have whats been packaged installed. The first time you try to install a 32bit run this command.

sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl dpkg-dev

Then type in the application name and try again. If you still get an error when it cant find a file we need to add it. Highlight the files name in the terminal, right click on the highlight and chose copy.
Go back to the Ubuntu packages page but this time we will search the contents of a package. Click on the package in the results page. The package dependencies page will open. There will be a download box

The download table links to the download of the package and a file overview. In addition it gives information about the package size and the installed size.
Architecture 	Files 	Package Size 	Installed Size
amd64 	[list of files] 	1029.5 	5436
i386 	[list of files] 	1011.2 	5384
powerpc 	[list of files] 	1036.3 	5448

Its near the bottom of the page most of the time. Click on the i386 download. The mirrors page will open, find one near you and save the download to your desktop.
One of the packages you installed above will allow you to extract the contents of .deb files. So find the .deb file right click on it, and chose "Extract Here". A folder will extract, inside will be a data.tar.gz . Right click on it and chose "Extract Here".  It should extract a data folder, or a usr folder. Find the usr fonder and drag it to the desktop.
Inside of the usr folder is a lib folder. It contains 32bit libs. On a 64bit system they go in /usr/lib32. You can copy them there with this command in a terminal if the usr folder is on your desktop.

cp -r ~/Desktop/usr/lib/* /usr/lib32/

Keep trying to launch the application in the terminal. Find out what libs it needs and repeat the process until the application launches.



---

### Post by johnnybirdman on 2008-02-18
> **kingleer said:**
> WInff has no 64 bit version



It's a video editor. I'm kinda looking for a stand alone video converter. Something simple.

Try thinliquidfilm.

I have it running on GG 64-bit, works fine to convert vids for my ipod.

[http://thinliquidfilm.org/](http://thinliquidfilm.org/)

J.

---

