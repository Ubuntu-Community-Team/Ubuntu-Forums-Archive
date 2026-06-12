---
title: "Howto: Installing Adobe Air 1.5 on Ubuntu 8.10 X86_64"
date: 2009-01-26
forum: x86 64-bit Users
---

### Post by Technoviking on 2009-01-26
Adobe AIR (Adobe Integrated Runtime) 1.5 was released last December. While not a 64 bit app yet, it is very easy to get the AIR 1.5 working on Ubuntu 8.10 AMD64 version.

1. Install needed libraries
```
sudo apt-get install ia32-libs
```

2. Download the installer
```
wget -c http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin
```

3. Install AIR
```
./AdobeAIRInstaller.bin
```
*(note may need to chmod +x AdobeAIRInstaller.bin, and will need sudo access)*

4. Copy extra Adobe library file
```
sudo cp /usr/lib/libadobecertstore.so /usr/lib32
```

5. Install AIR apps via web.

Let me know if people have problems with these instructions.

---

### Post by denizd on 2009-01-26
Are you sure that it work just as you describe? if so I think it is something wrong in my system. When I tried to install I got this  	bizarre error.

Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
 

I know that I have 32 bit libs

When I replace  /usr/lib/ with /usr/lib32/ in bash script error become something like 

Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64

do you have an idea how to make air work in ubuntu 8.10 amd64?

Thanks

Deniz

---

### Post by Technoviking on 2009-01-27
Are the following libraries in /usr/lib32?

[LIST]
[*]libnss3.so.1d
[*]libnssutil3.so.1d
[*]libsmime3.so.1d
[*]libssl3.so.1d
[/LIST]

---

### Post by denizd on 2009-01-28
I already did install this libraries as it is mentioned in adobe site.

And also mess around to find solution.

As you can see in my last post my problem is not related to this libraries.

it is some thing about gtk which insist to search for modules in /usr/lib instate of /usr/lib32

even though I replace GTK_MODULES="/usr/lib32/gtk-2.0/modules/libgail.so:/usr/lib32/gtk-2.0/modules/libatk-bridge.so"

---

### Post by yther on 2009-02-10
I got the same problem as denizd.

```
rassilon@miharu:~/Videos$ aptitude search ia32-libs
i A ia32-libs                                                                         - ia32 shared libraries for use on amd64 and ia64 systems
v   ia32-libs-gtk                                                                     -
v   ia32-libs-sdl                                                                     -
rassilon@miharu:~/Videos$ cd
rassilon@miharu:~$ wget -c http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin
--2009-02-10 10:02:10--  http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin
Resolving airdownload.adobe.com... 66.93.87.72, 66.93.87.71
Connecting to airdownload.adobe.com|66.93.87.72|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13553300 (13M) [application/x-macbinary]
Saving to: `AdobeAIRInstaller.bin'

100%[==========================================================================================================================================>] 13,553,300   160K/s   in 85s

2009-02-10 10:03:35 (157 KB/s) - `AdobeAIRInstaller.bin' saved [13553300/13553300]

rassilon@miharu:~$ chmod +x AdobeAIRInstaller.bin
rassilon@miharu:~$ ./AdobeAIRInstaller.bin

(setup:17014): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqt4engine.so: wrong ELF class: ELFCLASS64

(setup:17014): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqt4engine.so: wrong ELF class: ELFCLASS64
```The installer executes and presents the license agreement, but when I agree I do not get the sudo prompt, as I did when I successfully installed it on my laptop last night.  Instead, I get this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102856&stc=1&d=1234278704[/IMG]

So far, the only differences I'm aware of between the two systems, both running Intrepid x64, are:

[LIST]
[*]Laptop was installed several weeks ago, desktop was done 2 days ago.
[*]On the laptop, I downloaded the installer from Adobe's web site, on desktop I used wget.  (The link on the web site points to the same file, but for some reason wget didn't want to resolve adobe.com at the time I was trying.)
[/LIST]
I will mess around some more and report if anything works.

---

### Post by Jack2041 on 2009-03-03
:)                                                                                             [Mono Ammonium Phosphate](http://www.chemmax.com.cn/product/monoammonium_phosphate_food_grade.htm)

---

### Post by denizd on 2009-03-04
Even thou witt different ubuntu variants I was successful to install adobe air runtime without problem (I spend nearly entire week) I also get success to install some air aps but in result I coudn't find this aps anywhere...

So I think Adobe needs to do a lot job to make it work in x64 environment.

Deniz

---

### Post by lduperval on 2009-03-17
Did anybody get it to work with Hardy Heron (8.04)? If so, can you explain how. I'd like to spend less than a week to get it working. :)

I tried the instructions on the Adobe site and I still got the elf problems mentioned above.

My other option is to maybe use a VMWare image that mimics a 32-bit installation. Has anyone ever tried that?

L

---

### Post by lduperval on 2009-03-20
I followed instructions to get this working, but I still get this error:

%./AdobeAIRInstaller.bin 
Error loading the runtime (libsmime3.so: wrong ELF class: ELFCLASS64)

Any ideas? The files are in the right location.

L

---

### Post by syed mehdi on 2009-03-30
This page completely describes how to install Adobe AIR on ubuntu 64-bit. I have tried it and it worked perfectly.
[http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

-Syed

---

### Post by lduperval on 2009-03-31
Thanks for the link. I installed but it can't connect to the Twitter server. I tried installing another Air application and I see similar behaviour (I can't connect to the net). I also see an error 2022 (I think that's the number) when I try to install apps from the Adobe marketplace.

If anyone has any ideas, I'm all ears. :)

L

---

### Post by YigalB on 2009-04-01
> **Technoviking said:**
> Adobe AIR (Adobe Integrated Runtime) 1.5 was released last December. While not a 64 bit app yet, it is very easy to get the AIR 1.5 working on Ubuntu 8.10 AMD64 version.

1. Install needed libraries
```
sudo apt-get install ia32-libs
```


I tried running it and got failure: couldnt find package ia32-libs.

Any idea why?
also, is there a script that can run all the necessary commands in order to install Acrobat AIR on my Ubuntu?

---

### Post by YigalB on 2009-04-06
> **YigalB said:**
> I tried running it and got failure: couldnt find package ia32-libs.

Any idea why?
also, is there a script that can run all the necessary commands in order to install Acrobat AIR on my Ubuntu?

I have an answer for myself and for the others:
dont use the apt-get, simply download the file from the site, make it executable (chmod +x) and run it.

---

### Post by allandelmare on 2009-04-30
[http://goblog.vergilhost.info/](http://goblog.vergilhost.info/)

It's for 9.04 64 bit, which is what I'm running... Doesn't seem to be too different? Give 'er a try. Tweet Deck Runs great.

---

### Post by misfitpierce on 2009-05-03
Think I may have to try this out later... Been wanting to get Adobe Air for some cool web apps I have seen online avail for download... Seems like a cool program.

---

### Post by allandelmare on 2009-05-03
For anyone still having trouble (also makes Tweet Deck work):

[http://goblog.vergilhost.info/?p=5](http://goblog.vergilhost.info/?p=5)

---

### Post by kitrule on 2009-05-08
Installing required dependencies for BBC iPlayer Desktop on Adobe AIR (with Ubuntu Jaunty and ia32-libs v2.7ubuntu6)

In addition to following the steps in the first post-

If not already mentioned "sudo apt-get install lib32nss-mdns"
I had ELFCLASS64 issues with BBC iPlayer at this point which required me "sudo mv /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.sol"
"sudo cp /usr/lib32/gtk-2.0/modules/libcanberra-gtk-module.so.0 /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so"

Then

"wget http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgnome-keyring0_2.26.1-0ubuntu1_i386.deb"

"dpkg-deb -x libgnome-keyring0_2.26.1-0ubuntu1_i386.deb libgnome-keyring0_2.26.1-0ubuntu1_i386"

"sudo cp libgnome-keyring0_2.26.1-0ubuntu1_i386/usr/lib/* /usr/lib32"

"rm -r libgnome-keyring0_2.26.1-0ubuntu1_i386*"

Now, that should get BBC iPlayer working in Adobe Air on AMD64 for everyone in the UK.

Seems to be an ia32 libs problem and I'll probably discover I've got to backtrack that libcanberra hack when I next try to run a 64bit app.

I found it necessary to run the following command in order to have AIR run initially:
"sudo cp /tmp/air.**<6 random characters>**/Certs/usr/lib/libadobecertstore.so /usr/lib" (/lib32)

Sorry for hijacking the thread but this solution wasn't provided anywhere else and I suspect it can give hints to related problems using other programs in Adobe AIR on Ubuntu AMD64.

---

### Post by John Cheng on 2009-05-14
Following the instructions from Adobe, I was able to complete installing Adobe Air 1.5. I get sporadic problems, however, when using an Air application to open and save files (Balsamiq Mockups) - it seems to be related to these errors:

```

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

```

So it seems that Adobe Air will only partially work on Ubuntu 9.04 x86_64. This seems to be tracked in this [_[COLOR="Blue"]bug[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/190227"). However, there does not seem to be much activity lately.

---

### Post by FokkerCharlie on 2009-05-16
Hi Kitrule

I have been trying your instructions for iplayer, but:

```
sudo cp /usr/lib32/gtk-2.0/modules/libcanberra-gtk-module.so.0 /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
cp: cannot stat `/usr/lib32/gtk-2.0/modules/libcanberra-gtk-module.so.0': No such file or directory
```

Having a look, I see no libcanberra-gtk-module.so.0 in that folder, although libcanberra-gtk-module.so already exists.

I can follow all the other steps, which seem OK, but iplayer still does not work!

Could you prod me in the right direction?

Cheers
Charlie

EDIT:
Scrub that, it's working now- had to completely uninstall, and follow the link from Allendelmare.

Cheers

---

### Post by timgood on 2009-06-08
I have installed Air but when I try to install apps it segfaults. Launching Air Application Installer from the command line I get the following errors:

tim@tim-desktop:~$ /opt/Adobe\ AIR/Versions/1.0/Adobe\ AIR\ Application\ Installer
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

The installer does appear, but as soon as you select an application it will segfault. Any ideas?

---

### Post by afrodeity on 2009-06-10
Seriously need this for my Ubuntu Hardy 8.04 so that I can run tweetdeck. I downloaded the AdobeAIRinstaller.bin, did a chmod to make it executable, and followed the instructions but it doesn't do anything. Just hangs.

```
 afrodeity@afrodeity-desktop:~/Desktop$ sudo ./AdobeAIRInstaller3.bin
Error loading the runtime (libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory)

```

Am I the only one experiencing this problem? Is there something wrong with my machine?

---

### Post by ndviking on 2009-06-11
On my Jaunty system, libgtk-x11-2.0.so.0 is provided by the package named libgtk2.0-0. It might have a slightly different name in Hardy.

Use Synaptic to install the libgtk2.0 package and try running the Adobe AIR installer again.

---

### Post by afrodeity on 2009-06-12
libgtk2.0-0 is installed, maybe its broken in some way? There's a libgtk2.0-0-dbg which contains some libraries which I am installing, just in case.

UPDATE: no such luck.

---

### Post by Sir Rodness on 2009-07-01
> **syed mehdi said:**
> This page completely describes how to install Adobe AIR on ubuntu 64-bit. I have tried it and it worked perfectly.
[http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

-Syed

This worked for me as well.

---

### Post by timgood on 2009-07-03
Just as a matter of interest, are you running Intel or AMD?

---

### Post by afrodeity on 2009-07-03
Intel.

---

### Post by timgood on 2009-07-04
Interesting. Maybe it is a processor problem. I am running AMD and can't get it to work Of those who can't who else is running AMD?

---

### Post by rickle on 2009-07-10
TweetDeck was working, I moved my system to another drive,now It is working when my wife logs in, but I just get a blank TweetDeck screen with icons.  running from the console I get
 Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64

when my wife logs in she just gets the first canberra message.

somthing is not telling it where to look for the right libraries, any Ideas?
Oh, I'm running 9.04 64bit on AMD

---

### Post by afrodeity on 2009-07-10
pOSSIBLY a gENDER cONFLICT?

---

### Post by rickle on 2009-07-10
yep, it likes her, she don't keep messing with it all the time!

---

### Post by sk1312 on 2009-07-11
checkout this article 
[http://sneerwell.blogspot.com/2009/07/how-to-install-adobe-air-on-ubuntu.html](http://sneerwell.blogspot.com/2009/07/how-to-install-adobe-air-on-ubuntu.html)[http://sneerwell.blogspot.com/2009/07/how-to-install-adobe-air-on-ubuntu.html](http://sneerwell.blogspot.com/2009/07/how-to-install-adobe-air-on-ubuntu.html)

---

### Post by afrodeity on 2009-07-18
> **syed mehdi said:**
> This page completely describes how to install Adobe AIR on ubuntu 64-bit. I have tried it and it worked perfectly.
[http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

-Syed

something wrong with the PPA?
```

The following i386 packages will be installed:
libnss3-1d
Continue [Y/n]? y
Downloading ...
Failed to download file http://ppa.launchpad.net/tualatrix/ubuntu/pool/main/n/nss/libnss3-1d_3.12.2~rc1-0ubuntu2~fta1~hardy_i386.deb
The mirrors do not have the requested file or there is no internet connection
No packages to install

```

---

### Post by willprescott on 2009-07-25
> **timgood said:**
> Interesting. Maybe it is a processor problem. I am running AMD and can't get it to work Of those who can't who else is running AMD?

I think there is some truth in this. I've managed to get Air running just fine after a fashion with 9.04 on my Intel laptop, but on my AMD64 desktop I just cannot seem to get a resolution to the 3 gio module errors mentioned above.

Very frustrating - has anyone successfully managed to get Air working on an AMD64 system?

---

### Post by timgood on 2009-07-26
It is very frustrating that no-one seems able to pinpoint this problem. Come on guys, some ideas at least?

---

### Post by Khannie on 2009-07-28
> **lduperval said:**
> I followed instructions to get this working, but I still get this error:

%./AdobeAIRInstaller.bin 
Error loading the runtime (libsmime3.so: wrong ELF class: ELFCLASS64)

Any ideas? The files are in the right location.

L

I had this exact problem too on 8.04 x86_64 (which brought me to this thread). The (quick and very nasty) workaround which worked for me is:

edit: fixed with the not so nasty:
sudo ln -s /usr/lib32/libsmime3.so.1d /usr/lib32/libsmime3.so
sudo ./AdobeAIRInstaller.bin
sudo cp /usr/lib/libadobecertstore.so /usr/lib32

---

### Post by TVMA on 2009-08-04
I've tried everything under the sun to get it to work, I think there might be some truth in the AMD theory?

I'm running AMD quad core 2.2 with 9.04 64-bit.

---

### Post by aikiwolfie on 2009-08-10
I can't get it working and I'm on an Intel Core2 Quad. So the AMD theory is up in smoke.

---

### Post by djRobbieF on 2009-08-15
sudo apt-get install lib32nss-mdns

That should fix it or at least get you closer, I hope.  'Tis because of missing 32-bit libraries on your 64-bit platform.  My fingers are crossed for you!!

If no luck, read: [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

---

### Post by kingcharles1666 on 2009-08-21
> **Khannie said:**
> I had this exact problem too on 8.04 x86_64 (which brought me to this thread). The (quick and very nasty) workaround which worked for me is:

edit: fixed with the not so nasty:
sudo ln -s /usr/lib32/libsmime3.so.1d /usr/lib32/libsmime3.so
sudo ./AdobeAIRInstaller.bin
sudo cp /usr/lib/libadobecertstore.so /usr/lib32

Great tip, this made it work for me!

---

### Post by johnc@crosslink.net on 2009-08-23
> **djRobbieF said:**
> sudo apt-get install lib32nss-mdns

That should fix it or at least get you closer, I hope.  'Tis because of missing 32-bit libraries on your 64-bit platform.  My fingers are crossed for you!!

If no luck, read: [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

The key is this:
cp /usr/lib/libadobecertstore.so /usr/lib32
(as root, of course)
I needed AIR for the NYT Reader. I have lots of 32bit apps running already, so most of the libs were already installed.
In fact, I would go to Adobe 1st if this is the only 32bit app you're running. The page has step by step instructions.

---

### Post by timgood on 2009-09-21
Googling on this seems to indicate that there is a bug in ia32lib [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498) which does not link 32 bit libraries correctly so GTK doesn't know where to look for them. Nothing seems to be happening to fix this, so perhaps we should make a bit more noise? This makes sense because the output clearly shows the attempt to load gio modules from /usr/lib rather than /usr/lib32 even though the 32 bit versions are correctly installed and are present. This should be easily fixed surely?

---

### Post by nmrcy on 2009-09-24
i'm getting Error #2032 whenever i try to install stg to adobe air how can i solve this error?

---

### Post by sammyboy405 on 2009-10-19
Running AMD Turion X2  Ubuntu 9.10 beta 64

I can install Air All Daylong..  Works fine..

Till you want to install a .Air application ie Tweetdeck , Spaz, etc..

Then you get Segment Fault Errors.  

Im Pretty Sure this related to it being an AMD Processor. If anyone find an AMD Workaround Please share but I think this is going to fall in Adobe's Lap.

---

### Post by timgood on 2009-11-17
For all those of us with AMD processors who have struggled with Air - hope! Air 2 beta is now available and works on my machine, have got both iPlayer and Tweetdeck working fine.

---

