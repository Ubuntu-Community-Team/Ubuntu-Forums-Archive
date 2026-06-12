---
title: "64 bit - Still can't get flash 10 to install for firefox"
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by sumpm1 on 2009-01-08
Oh my god, this has taken me hours!!! I just installed 8.04 64 bit and tried firefox and found that flash is a problem. Don't worry I read all of the threads and saw that there is a new version of 64-bit flash out. I followed the instructions here: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml) . I still was not able to view flash in Firefox 3.0.5. Firefox still says that flash is not installed just like when there is no flash installed at all.

While searching the Ubuntu x64 forums for flash problems, I found this thread: [http://ubuntuforums.org/showthread.php?t=1032477&highlight=flash](http://ubuntuforums.org/showthread.php?t=1032477&highlight=flash) .  I saw this code for removing any remnants of flash:

```
sudo apt-get autoremove flashplugin-nonfree
```

```
sudo updatedb && locate libflashplayer.so
```

There was another libflashplayer.so on my system and I went and removed it. Now the last code returns nothing, so good, system clean! But I created a plugins folder in the ~.mozilla folder and copied the downloaded libflashplayer.so into it. STILL Firefox does not recognize the plugin and flash is not viewable.

Help me out here guys. I knew x64 would be a pain, but for something so simple as flash?

---

### Post by mtausig on 2009-01-08
I installed the flashplayer und a x64 box a few weeks ago. I'm afraid can't remeber exactly what the solution was, but I believe it was a dependency issue.
Type 'ldd libflashplayer.so', and check wether there is some library missing.

---

### Post by CJ56 on 2009-01-08
There may still be some stuff left behind - check out Kilz' sticky at the top of the forum and then -

Well worth doing, one line at a time, is

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

As Kilz tells us to... This clears out all the gunge from previous installations and sets you up to -

Download the Flash 10 for 64-bit tar.gz from the Adobe website and close Firefox

Then extract the .so file and copy it into .mozilla/plugins in your Home Folder. 

Restart FF and it should work fine

---

### Post by sumpm1 on 2009-01-08
Hey guys, that is kind of what  I did, made sure to remove everything, then copied libflashplayer.so to ~/.mozilla/plugins and had no luck. I followed all of your commands, and if you are interested here is the output. Still same problem though. BTW: I am just downloading the plugin from the Adobe website and then extracting the ...so to .mozilla/plugins right? There are no longer any scripts involved like in Kilz thread?

```
dave@dave-desktop:~$ sudo apt-get -y purge nspluginwrapper
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.
dave@dave-desktop:~$ sudo apt-get -y purge mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.
dave@dave-desktop:~$ sudo apt-get -y purge swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.
dave@dave-desktop:~$ sudo apt-get -y purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.
dave@dave-desktop:~$ sudo rm -rfd /usr/lib/nspluginwrapper
dave@dave-desktop:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
dave@dave-desktop:~$ sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
dave@dave-desktop:~$ ldd libflashplayer.so
ldd: ./libflashplayer.so: No such file or directory
```

---

### Post by mtausig on 2009-01-08
> **sumpm1 said:**
> 

```

dave@dave-desktop:~$ ldd libflashplayer.so
ldd: ./libflashplayer.so: No such file or directory
```

Were you in the corect directory, when you executed this command (should be ~/.mozilla/plugins, whereever you put the lib)

---

### Post by sumpm1 on 2009-01-08
No, I wasn't in the correct directory thanks. Here is the output. Nothing I see special here. I just install x64 8.04 yesterday. It would be easier for me to just reinstall with 8.04 i386!

```

dave@dave-desktop:~/.mozilla/plugins$ ldd libflashplayer.so
	linux-vdso.so.1 =>  (0x00007fff9f3fe000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007fdc924be000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007fdc922a2000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007fdc91f9e000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007fdc91d8d000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007fdc91b29000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007fdc918a9000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007fdc91678000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007fdc910a9000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007fdc90e0e000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007fdc90bee000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007fdc909d4000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007fdc907c8000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007fdc90584000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007fdc90319000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007fdc900d3000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007fdc8fed0000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fdc8fccc000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007fdc8fa0b000)
	libnss3.so => /usr/lib/libnss3.so (0x00007fdc8f6c0000)
	libsmime3.so => /usr/lib/libsmime3.so (0x00007fdc8f495000)
	libssl3.so => /usr/lib/libssl3.so (0x00007fdc8f263000)
	libplds4.so => not found
	libplc4.so => not found
	libnspr4.so => not found
	libm.so.6 => /lib/libm.so.6 (0x00007fdc8efe1000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007fdc8edd3000)
	libc.so.6 => /lib/libc.so.6 (0x00007fdc8ea70000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fdc973db000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007fdc8e86f000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007fdc8e654000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007fdc8e451000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007fdc8e249000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007fdc8e02e000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007fdc8de16000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007fdc8dbf2000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007fdc8d9f0000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007fdc8d7ed000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007fdc8d5e8000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007fdc8d3df000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007fdc8d1dc000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007fdc8cfd3000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007fdc8cdcc000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007fdc8cbc1000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007fdc8c995000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007fdc8c76f000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007fdc8c541000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x00007fdc8c325000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0x00007fdc8c0fe000)
	libnssutil3.so.1d => /usr/lib/libnssutil3.so.1d (0x00007fdc8bee1000)
	libplc4.so.0d => /usr/lib/libplc4.so.0d (0x00007fdc8bcdd000)
	libplds4.so.0d => /usr/lib/libplds4.so.0d (0x00007fdc8bad9000)
	libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0x00007fdc8b89d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007fdc8b697000)
```

---

### Post by mtausig on 2009-01-08
Here we go. You are missing three libraries. All of them can be found in the ubuntu package "libnspr4-0d". Install it, restart firefox and check if it works.

---

### Post by bumanie on 2009-01-08
I think I used [this script]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") to get flash 10 working on my 64bit. Give that a go.

---

### Post by sumpm1 on 2009-01-08
> **mtausig said:**
> Here we go. You are missing three libraries. All of them can be found in the ubuntu package "libnspr4-0d". Install it, restart firefox and check if it works.

I don't know mtausig. My Synaptic shows that package being installed, and there is no option to reinstall.

---

### Post by sumpm1 on 2009-01-08
UPDATE: I gave up on Ubuntu 64 bit altogether. Just installed 8.04 i386, took under an hour.

---

### Post by ndale686738 on 2009-01-08
All you have to do is copy the libflashplayer.so to the right directory.

download 
```
http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
``` 
to desktop and extract it
open a terminal
```
cd Desktop
sudo mv libflashplayer.so /usr/lib/firefox-3.0.5/plugins/
```

Thats it! Reboot firefox if its running.

---

### Post by Yellow Pasque on 2009-01-09
> **sumpm1 said:**
> UPDATE: I gave up on Ubuntu 64 bit altogether. Just installed 8.04 i386, took under an hour.
Linux IS NOT Windows. Reinstalling the OS is rarely the best solution to a problem, especially once you start using/customizing the system. Try a little more patience next time.

---

### Post by jrusso2 on 2009-01-09
> **sumpm1 said:**
> No, I wasn't in the correct directory thanks. Here is the output. Nothing I see special here. I just install x64 8.04 yesterday. It would be easier for me to just reinstall with 8.04 i386!

```

dave@dave-desktop:~/.mozilla/plugins$ ldd libflashplayer.so
	linux-vdso.so.1 =>  (0x00007fff9f3fe000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007fdc924be000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007fdc922a2000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007fdc91f9e000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007fdc91d8d000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007fdc91b29000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007fdc918a9000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007fdc91678000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007fdc910a9000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007fdc90e0e000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007fdc90bee000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007fdc909d4000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007fdc907c8000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007fdc90584000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007fdc90319000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007fdc900d3000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007fdc8fed0000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fdc8fccc000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007fdc8fa0b000)
	libnss3.so => /usr/lib/libnss3.so (0x00007fdc8f6c0000)
	libsmime3.so => /usr/lib/libsmime3.so (0x00007fdc8f495000)
	libssl3.so => /usr/lib/libssl3.so (0x00007fdc8f263000)
	libplds4.so => not found
	libplc4.so => not found
	libnspr4.so => not found
	libm.so.6 => /lib/libm.so.6 (0x00007fdc8efe1000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007fdc8edd3000)
	libc.so.6 => /lib/libc.so.6 (0x00007fdc8ea70000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fdc973db000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007fdc8e86f000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007fdc8e654000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007fdc8e451000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007fdc8e249000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007fdc8e02e000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007fdc8de16000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007fdc8dbf2000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007fdc8d9f0000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007fdc8d7ed000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007fdc8d5e8000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007fdc8d3df000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007fdc8d1dc000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007fdc8cfd3000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007fdc8cdcc000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007fdc8cbc1000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007fdc8c995000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007fdc8c76f000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007fdc8c541000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x00007fdc8c325000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0x00007fdc8c0fe000)
	libnssutil3.so.1d => /usr/lib/libnssutil3.so.1d (0x00007fdc8bee1000)
	libplc4.so.0d => /usr/lib/libplc4.so.0d (0x00007fdc8bcdd000)
	libplds4.so.0d => /usr/lib/libplds4.so.0d (0x00007fdc8bad9000)
	libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0x00007fdc8b89d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007fdc8b697000)
```

No don't do that I am assured that using 64 bit Linux no longer has any problems and is just as easy to get working as 32 bit.  I am sure one of these 64 bit users can agree and help you find the solutions to any issues your having.

---

### Post by Yashiro on 2009-01-09
Well putting the plugin in your home/plugins on a fresh working Ubuntu 64 works.

---

### Post by jrusso2 on 2009-01-09
Oh you should not give up on 64 bit.  I am assured by the users of 64 bit Linux it is now as easy to use and set up as 32 bit Linux.

All the problems with flash and Java have now been fixed as well as WINE, codecs and drivers.  Any of these 64 bit users should be glad to help assist.  I would but I still use 32 bit.

---

### Post by steveneddy on 2009-01-09
> **CJ56 said:**
> There may still be some stuff left behind - check out Kilz' sticky at the top of the forum and then -

Well worth doing, one line at a time, is

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f [SIZE=2][COLOR=Blue]**/usr/lib/firefox-addons/plugins/**[/COLOR][/SIZE]libflashplayer.so
sudo rm -f [SIZE=2][COLOR=Blue]**/usr/lib/mozilla/plugins/**[/COLOR][/SIZE]flashplugin-alternative.so
```As Kilz tells us to... This clears out all the gunge from previous installations and sets you up to -

Download the Flash 10 for 64-bit tar.gz from the Adobe website and close Firefox

Then extract the .so file and copy it into .mozilla/plugins in your Home Folder. 

Restart FF and it should work fine

copy the Flash .so file to the directories that you just deleted everything from.

They are highlighted above.

The new Flash10 plugin for 64 bit Ubuntu goes in these directories:

```
/usr/lib/firefox-addons/plugins/

/usr/lib/mozilla/plugins/
```Put the Flash .so file in these two folders and it will work.

---

### Post by sumpm1 on 2009-01-11
> **Temüjin said:**
> Linux IS NOT Windows. Reinstalling the OS is rarely the best solution to a problem, especially once you start using/customizing the system. Try a little more patience next time.

I got plenty of patience, I'm reinstalling the OS aren't I? Plus I just installed 8.04 64 bit 2 days ago, so the install was fresh, and I spent TWO DAYS trying to get FLASH (of all things) to work. Without flash, I am kind of missing the internet, you know? I know you guys want to see 64 bit move forward, so do I. But this is one TINY bug that took me, a pretty resilient computer user TWO DAYS and probably FOURTY TRIES of moving the plugins, running scripts, running commands, searching that plugins/files don't exist, and restarting Firefox. You can try to CONVINCE me that the problem is me, and that is why i NEVER GOT FLASH TO WORK AT ALL, but had an easier time going to a fresh install of 32 bit and using flash IMMEDIATELY. But the truth is that this needs ironed out. It will get worked out fine in the next release I am sure.

But if 64 bit really is getting so great, I will be happy to install it on my next go around! For now, I had trouble with Flash, and had trouble finding debian packages for many apps that I can find no problem for i386 online. You can't put a value on your sanity!

---

### Post by Yashiro on 2009-01-11
Your problems stem from following random tutorials and taking conflicting advice from different people/posts.

I agree that the Flash issue needs sorting out but it's not as bad as you make out.

---

### Post by Yellow Pasque on 2009-01-11
> For now, I had trouble with Flash, and had trouble finding debian packages for many apps that I can find no problem for i386 online.

Which packages couldn't you find? It would be helpful to know so that someone could submit them to Ubuntu or build them in a PPA.

---

### Post by Max Torps on 2009-01-11
I followed the instructions and it also didn't work.

However, if you type ```
"about:plugins"
``` into the url bar of FF, you get a list of those installed. All fine and dandy.

In Firefox 3.0.5 Go to Tools>>Add-ons

Disable 
Div X web player 1.4.0.233
Quicktime Plug-in 7.2.0
Totem Web Browser Plug in 2.24.3

Restart Firefox...and it works.

I haven't drilled down to which plugin is causing the issue yet, I'm just happy that my 64 bit browsing experience "so far" is working.

I hope this helps.

---

### Post by nss0000 on 2009-01-11
MT

Good-0  you got FLASH to work! To maintain sanity in x64Ubuntu better not expect anything in-particular to work! It/they will of-course ... in time! Sometime. I've been running x64-U couple years and if you give a flying-gradeA-fluck about anything you will go nutz.

---

### Post by Cope57 on 2009-01-11
pebkac

---

### Post by sumpm1 on 2009-01-12
> **Cope57 said:**
> pebkac

At least I can confirm that the Ubuntu x64 forum has TROLLS working!!!

---

### Post by stchman on 2009-01-12
Installing Flash 10 in Ubuntu 64 bit is a breeze.  I have it on my (3) 64 bit Hardy boxes.  Simply uninstall Flash 9 and copy the 64 bit Flash 10 .so file to your ~/.mozilla/plugins folder.  Easy as pie.

---

### Post by Kilz on 2009-01-12
> **stchman said:**
> Installing Flash 10 in Ubuntu 64 bit is a breeze.  I have it on my (3) 64 bit Hardy boxes.  Simply uninstall Flash 9 and copy the 64 bit Flash 10 .so file to your ~/.mozilla/plugins folder.  Easy as pie.

It wasnt always that easy. But the easier it gets more and more recent converts to linux start to run it. Then the learning curve is forgotten about and everything is blamed on 64bit. But we will always get those that think all they should have to do is put a cd in and click ok. 
I love the freedom myself. I just built 2 computers for my house and not one cent of Microsoft tax. No more 32bit here.

---

