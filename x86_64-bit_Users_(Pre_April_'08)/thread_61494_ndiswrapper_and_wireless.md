---
title: "ndiswrapper and wireless"
date: 2005-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by h17m4n on 2005-08-31
Ok I'm a newb. I just got Kubuntu 5.04 AMD64 and I'm trying to get things to work.

I'm trying to follow these lines: 
> ndiswrapper -i /home/user/download/netbc564.inf

Then do:
modprobe ndiswrapper

At this point, you should be able to type the following in the console:
ndiswrapper -l
and see the following output:
netbc564 driver present, hardware present
To add this to your /etc/modules file, type:
ndiswrapper -m

But it seems ndiswrapper is not installed. The explanation on ndiswrapper's page on how to install it are not what I call user-friendly, as it is pretty hard to understand. I downloaded ndiswrapper-1.3rc1. Once I run "make install" from that dir, I get an error saying "Can't find kernel sources in /lib/modules/2.6.10-5-amd64-generic/build".

They ask for a kernel source from kernel.org, so I followed on to that site. I downloaded linux-2.6.10.tar.gz from that site(is that what the source is), and I think I'm ready to get things set up.

So please, if anyone could help me by telling me what to do or giving me links to easy howtos I'd be thankful.

---

### Post by mlomker on 2005-08-31
You'll need to:  apt-get install build-essential

That'll download the source and packages that you'll need to compile programs.

---

### Post by h17m4n on 2005-08-31
[QUOTE=mlomker]You'll need to:  apt-get install build-essential

That'll download the source and packages that you'll need to compile programs.[/QUOTE]
 so I went to "Run Command", click "Run in terminal window" and "As root" and typed that.

It says: build-essential is already the newest version

I think that if I get this kernel source thing working I will have a much easier time installing ndis and the driver...

I'm afraid to mess up the system trying to follow some hard guides...

btw I'm using the net on my windoze machine....

---

### Post by byen on 2005-08-31
well...this is what helped me.... try it out....might just work....goodluck!
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by h17m4n on 2005-09-01
[QUOTE=byen]well...this is what helped me.... try it out....might just work....goodluck!
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)[/QUOTE]
 Thx for the reply guys...

I tried following that guide byen... I followed every step but got stuck on the first line of step 3.

Here's what I get: 
Reading package lists... done
Building dependency tree... done
E: Couldn't find package ndiswrapper-utils


:-(

---

### Post by byen on 2005-09-01
ok...here goes....
If you have followed...ndiswrapper walkthrough step by step you will notice that in the earlier stages... you must have done :
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

Now what this does is removes all previous preconfigured...ndiswrapper stuff and starts out fresh...so now you again have to:
sudo apt-get install ndiswrapper-utils

If you are gettin the error:"E: Couldn't find package ndiswrapper-utils during apt-get install ndis-wrapper-utils."...im assuming you have not yet added/tweaked your repository list
to do that...go here and follow the instructions:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

after doing this go back to the walkthrough [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683) and try it out again. 

PS- remember... it might take a little patience but once you get things set up ...you will never turn back. Let us know if you are having trouble. goodluck.

---

### Post by h17m4n on 2005-09-01
[QUOTE=byen]ok...here goes....
If you have followed...ndiswrapper walkthrough step by step you will notice that in the earlier stages... you must have done :
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

Now what this does is removes all previous preconfigured...ndiswrapper stuff and starts out fresh...so now you again have to:
sudo apt-get install ndiswrapper-utils

If you are gettin the error:"E: Couldn't find package ndiswrapper-utils during apt-get install ndis-wrapper-utils."...im assuming you have not yet added/tweaked your repository list
to do that...go here and follow the instructions:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

after doing this go back to the walkthrough [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683) and try it out again. 

PS- remember... it might take a little patience but once you get things set up ...you will never turn back. Let us know if you are having trouble. goodluck.[/QUOTE]
 I did a fresh install of kubuntu and followed those instructions... did every single line, added the extra repositories, and when I ran the sudo apt-get install ndiswrapper-utils line I got the same error...

I'm running the Kubuntu 5.04 AMD64 Install distro... it should be the same as Ubuntu besides the fact that it uses KDE instead of Gnome right?

---

### Post by byen on 2005-09-01
> it should be the same as Ubuntu besides the fact that it uses KDE instead of Gnome right?
-yes. that is right.

Here is a link to the file that you can manually download:
[ndiswrapper-utils](http://packages.debian.org/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils_1.1-4_amd64.deb&md5sum=b417ec4eef5e191cc971204f313a9b43&arch=amd64&type=main) 
-save it in the home directory
- open terminal and type:
sudo dpkg -i  ndiswrapper-utils_1.1-4_amd64.deb
- then...follow the rest from the second line mentioned in the walkthrough (second code set). see if that works.goodluck. :wink:

---

### Post by h17m4n on 2005-09-01
[QUOTE=byen]-yes. that is right.

Here is a link to the file that you can manually download:
[ndiswrapper-utils](http://packages.debian.org/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils_1.1-4_amd64.deb&md5sum=b417ec4eef5e191cc971204f313a9b43&arch=amd64&type=main) 
-save it in the home directory
- open terminal and type:
sudo dpkg -i  ndiswrapper-utils_1.1-4_amd64.deb
- then...follow the rest from the second line mentioned in the walkthrough (second code set). see if that works.goodluck. :wink:[/QUOTE]
 I did what you told me and at first it said it couldn't find ndiswrapper-modules, so I just went ahead and typed sudo apt-get install ndiswrapper-utils. It said it Depends on module-assistant, gcc, and ndiswrapper-module which weren't going to be installed, and that I should have run the command sudo apt-get install -f.

When I run sudo apt-get install ndiswrapper-utils, it says "Package ndiswrapper-utils is not available, but is referred to by another package. This may mean the package is missing, has been obsoleted, or is available from another source."

Thx for your help. I really appreciate it

I dpkg the file you told me again, and ran the apt-get install ndiswrapper-utils, it says it depends on ndiswrapper-modules-1.1 which is not installable. :-(

---

### Post by byen on 2005-09-01
I know how frustating this might be...so relax,take some time off and then
do this..(.Some of these steps may report errors; just ignore them.)
Terminal commands:
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

now..this has cleared all the messed up previous stuff...so now we are starting fresh.

now save the file ndiswrapper-utils (from the link that i have given you)(into the home directory :/home/yourusername/)
now..open the terminal and type:
sudo dpkg -i ndiswrapper-utils_1.1-4_amd64.deb
(this will install the ndiswrapper utils..after this you *do not* have to do an apt-get install again)
next do this:
-Copy the bcmwl5.inf and bcmwl5.sys files to you home directory 
-Now remember that if you are not using broadcom drivers...these two files will be named xxxx.inf and xxxx.conf in you windows drivers folder or the cd that you get with the network card.

Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.

Now back to the terminal:
sudo ndiswrapper -i ~/yourdrivername.inf
sudo ndiswrapper -m

Now: in terminal type:sudo gedit
- This will open a text editor. Open every file in the directory /etc/ndiswrapper/bcmwl5(or your driver name folder)/ and replace every instance of RadioState|1 with RadioState|0

Reboot your PC. On restarting, the light on your wireless card should come on. If not, try enteringCode: sudo modprobe ndiswrapper

[QUOTE=jonny]5. Your card is now working. Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings. Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one. You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK. The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK. Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana. If everything works, you can delete the file from your desktop.

13. You might notice that the signal strength applet doesn't work properly. This is a known bug with these cards.

If you have trouble, try booting into Windows - if you dual boot - and checking that the card is enabled. Some laptops allow the wireless card to be switched off, usually with a special key combination, and I've not found a reliable way to make this work in Linux.[/QUOTE]

Now..this is what I did...and this worked...Im pretty sure...if you are careful...it might work for you too. So relax..have a coffee..take a walk and try it out..BEST OF LUCK!

PS- if some one else is looking for this info..its all here (thanks to jonny)
[http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10)

---

### Post by baylisscg on 2005-09-01
Hi,

   While I don't use ndiswrapper on my 64bit system I found [this page in the wiki](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29) very helpful when setting it up on my laptop. I prefer it to the other methods as it makes a .deb so it can be handled through dpkg/apt-get/synaptic. Unfortunately you will need to reinstall after each kernel upgrade.

---

### Post by h17m4n on 2005-09-01
[QUOTE=baylisscg]Hi,

   While I don't use ndiswrapper on my 64bit system I found [this page in the wiki](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29) very helpful when setting it up on my laptop. I prefer it to the other methods as it makes a .deb so it can be handled through dpkg/apt-get/synaptic. Unfortunately you will need to reinstall after each kernel upgrade.[/QUOTE]
 Thx for helping guys...

Byen, I went through everything you said twice and I when I restart the light doesn't come on. When I do sudo modprobe ndiswrapper, I get this error: FATAL: Module ndiswrapper not found.

:-(

My card is a broadcom. And I'm trying to set this up in my laptop.

If I go through baylisscg's suggestion and it doesn't work, will I be able to undo it?

---

### Post by h17m4n on 2005-09-01
When I follow baylisscg's suggestion, I get stuck on the 6th step. It says: 

dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make[2]: *** [common-epilog] Error 1
make[2]: Leaving directory `/usr/src/ndiswrapper-1.1'
make[1]: *** [binary] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.1'
make: *** [deb] Error 2

I really appreciate the help I'm getting. I never thought it would so hard to set things up in linux.

---

### Post by h17m4n on 2005-09-01
I followed the instructions under "Wireless using ndiswrapper" from this page(after doing the clean up commands): [http://www.cis.ksu.edu/~aruljohn/debian/](http://www.cis.ksu.edu/~aruljohn/debian/)
and the wifi signal light comes on. When I go to the control center and under Network Settings, I see wlan0 there but it is disabled. The problem now is that when I click Administrator Mode and type the password in, it just returns to the control center's initial page. 

Any help? :-(

I'm learning some bits.... I went to the konsole and ran "sudo kcontrol", which opened the control panel as root. But when I click "Enable" it quickly disables the card. I already set to automatic dhcp.

---

### Post by h17m4n on 2005-09-02
Got it. I was having a problem finalizing the steps. It would be installed and show up under network settings, but disabled. Whenever I hit enable it would disable itselft on the same second. So I ran "apt-get install ubuntu" and it installed gnome over kde. So I followed the guide starting from step 5 and bam! It worked!

Too bad I can't work with it on the distro running as "kubuntu", because I liked the kde environment better than gnome. It's a much more easier environment for windows users to adapt to. 

Thx for the help guys. I really appreciate and sry if I was a pain.

edit - After finalizing the settings under gnome, I just logged in under kde and the card was working!!! I'm actually posting from my wifi connection!!!  :grin:  \\:D/ 

Thx a lot guys!!! I owe you this one!

---

### Post by byen on 2005-09-02
hurray! wow...nice! phew...to tell you the truth ..im not sure how much my post helped you..but I just tried to make it simple and things just did not seem to work... I knew it was only a matter of time..but i wasnt sure your patience would hold.
Well...all said and done....Welcome to Ubuntu.glad we could be of help ;-) !

---

### Post by h17m4n on 2005-09-02
I wasn't understanding what the commands were and how they were done. Through your posts I started to understand how the whole thing works. I would consider myself an advanced windoze user, which helped me in the proccess, but I'm still a linux noob.

Thx a lot for you cooperation and patience! I owe you this one!

---

