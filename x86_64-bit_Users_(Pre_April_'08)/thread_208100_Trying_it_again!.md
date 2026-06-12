---
title: "Trying it again!"
date: 2006-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicoavz on 2006-07-03
Hey guys, I've dont have much to do this summer so I thought I would try to be less of a linux noob :)

A few months back I tried installed ubuntu and it simply would not run on my pc. Now that Dapper Drake is out I want to give that a try and hopefully get rid of windows.  I have not been able to find an ubuntu live cd (Dapper) anyplace. I have no problem with reformating my pc and trying Dapper, but before I do I wanna know if anyone with a similar set up has had success installing Dapper on their machine. My specs are:

Processor: 2.20 gigahertz AMD Athlon 64
Memory: 2 GiB
Video: (onboard) ATI RADEON Xpress 200 Series & (PCI-E) RADEON X700 Series

I remember there was alot of problems with ATI and the earlier ubuntu, and I remember reading someplace, months ago, that Dapper would fix them. 

If anyone has installed Dapper on a similar machine, let me know !  If so I will start playing with it tonite!  Thanks in advanced!

---

### Post by Indras on 2006-07-03
[QUOTE=nicoavz]Hey guys, I've dont have much to do this summer so I thought I would try to be less of a linux noob :)[/QUOTE]

Good, glad to have you on board.

[QUOTE=nicoavz]A few months back I tried installed ubuntu and it simply would not run on my pc. Now that Dapper Drake is out I want to give that a try and hopefully get rid of windows.  I have not been able to find an ubuntu live cd (Dapper) anyplace....[/QUOTE]

Just go to [http://www.ubuntu.com](http://www.ubuntu.com) and under desktop, hit the "Download" link.  From there, pick your locale and architecture (i386 for you).

The install CD is also a Live CD, so once you pop it in your drive and restart, it will boot to a full gnome desktop and let you play with all the software installed, like browsing the internet with firefox and playing the built in games.  Very handy while you wait for it to install.

[QUOTE=nicoavz]...I have no problem with reformating my pc and trying Dapper, but before I do I wanna know if anyone with a similar set up has had success installing Dapper on their machine. My specs are:

Processor: 2.20 gigahertz AMD Athlon 64
Memory: 2 GiB
Video: (onboard) ATI RADEON Xpress 200 Series & (PCI-E) RADEON X700 Series

I remember there was alot of problems with ATI and the earlier ubuntu, and I remember reading someplace, months ago, that Dapper would fix them. 

If anyone has installed Dapper on a similar machine, let me know !  If so I will start playing with it tonite!  Thanks in advanced![/QUOTE]

My hardware couldn't be any more different from yours... Pentium 4 2.66 Ghz, 1Gb RAM, AGP 8x Geforce FX 5600 Ultra.  So, I can't really offer any recommendations on your hardware, but I really don't see why it wouldn't work.  Just download the LiveCD and boot from it to get an idea of how it handles first.  Keep in mind starting all applications while on the CD will be many times slower than after it is installed.  But, at the very least, it will give you an idea of what is offered... openoffice/firefox/etc.

---

### Post by nicoavz on 2006-07-03
Thanks for the quick reply mate. I've already started downloading "64-bit PC (AMD64) server install CD" is that the right one? I dont see any other that says i386.


*edit* Ok I found i386 iso image in the small text list below :P. But I thought my processor was 64bit since its Athlon 64, or am I wrong about that what Athlon 64 stands for exactly

---

### Post by jklasdf on 2006-07-03
Since you have an Athlon 64, you might want the amd64 version and not the regular i386 (although both will run fine, and currently the i386 version has more support for stuff like codecs and 32bit only applications). But if you've already started downloading (I assume?), it might be easier to just stick with i386. Otherwise the 64bit version that you want is ubuntu-6.06-desktop-amd64.iso (64-bit PC (AMD64) desktop CD).

[http://ubuntu.cs.utah.edu/releases/6.06/ubuntu-6.06-desktop-amd64.iso]("http://ubuntu.cs.utah.edu/releases/6.06/ubuntu-6.06-desktop-amd64.iso")

---

### Post by nicoavz on 2006-07-03
Well I have a few issues, which seam to be the same as the earlier ubuntu releases.  The live cd worked ok when I used my onboard ATI 128mb as primary video. When I changed the settings in the bios to use my PCI-E card as the main video, everything went wrong :(

Using AMD64 Dapper Distro this is what I got;
[[IMG]http://img98.imageshack.us/img98/4050/amd641ms.jpg[/IMG]](http://imageshack.us)

So I tried using the i386 Dapper Distro, everything was going well until this happend;
[[IMG]http://img98.imageshack.us/img98/5336/i38611ed.jpg[/IMG]](http://imageshack.us)

and right before I hit enter to diagnose the problem I got this;
[[IMG]http://img152.imageshack.us/img152/8172/i38621ni.jpg[/IMG]](http://imageshack.us)

Any tips on where to go from here? I'd realy like to get ubuntu installed today :*( 

Thanks in advanced!

---

### Post by Kilz on 2006-07-03
> **nicoavz]Well I have a few issues, which seam to be the same as the earlier ubuntu releases.  The live cd worked ok when I used my onboard ATI 128mb as primary video. When I changed the settings in the bios to use my PCI-E card as the main video, everything went wrong :(

Using AMD64 Dapper Distro this is what I got said:**
> [IMG]http://img98.imageshack.us/img98/4050/amd641ms.jpg[/IMG][/URL]

So I tried using the i386 Dapper Distro, everything was going well until this happend;
[[IMG]http://img98.imageshack.us/img98/5336/i38611ed.jpg[/IMG]](http://imageshack.us)

and right before I hit enter to diagnose the problem I got this;
[[IMG]http://img152.imageshack.us/img152/8172/i38621ni.jpg[/IMG]](http://imageshack.us)

Any tips on where to go from here? I'd realy like to get ubuntu installed today :*( 

Thanks in advanced!
First off, IMHO anyone running a amd64 bit prossessor should install the amd64 version. I dont know why people come into the "64bit" forum and tell people to install a 32bit os. I feel a rant post comming on.
Second, the 8.25.18 drivers are the worst drivers ever produced by ATI if you have a X series. There are new ones out from ati. 8.26.18 but they havent been made into .deb files for ubuntu yet.
If you want to try and salvage the i386(32bit) install try this.
```
sudo dpkg-reconfigure xserver-xorg
```
Keep clicking ok, untill you get to the screen resalutions. You will be able to hit the space bar and turn on and off resalutions. Dont turn on anything over 1152x864, keep agreeing, when its done reboot.
Personaly I suggest scapping it altogher, getting the amd64 version, turning on the x700 and doing a new install.

---

### Post by nicoavz on 2006-07-03
I did the sudo code you gave me and it just ended up giving me the same problem at the end.  

The only way I can get the live cd to work is by using the i386 cd and using my (onboard) ATI RADEON Xpress 200 Series as primary video (set it like that in bios).  Using i386 or the AMD64 distro will not work with my x700 video card, and using the AMD64 cd with the (onboard) ATI RADEON Xpress 200 Series doesnt work either =/

Now, im on the ubuntu live cd right now, and I am wondering if I should isntall it, and then somehow install my x700 drivers after the install (although I have no clue how)?  

I'd realy like to use that card since it has a dvi out for my nice monitor, and another out for another monitor.  This brings me to another question, currently I have a tri-mon set up, which I love.  Would I be able to do this with ubuntu? or atleast dual-mon?  

I'm going to try to using the 'alternate' distros from the download site, and see if those do me anybetter.

Anyway, gotta load into windows now :(

---

### Post by Kilz on 2006-07-03
[QUOTE=nicoavz]I did the sudo code you gave me and it just ended up giving me the same problem at the end.  

The only way I can get the live cd to work is by using the i386 cd and using my (onboard) ATI RADEON Xpress 200 Series as primary video (set it like that in bios).  Using i386 or the AMD64 distro will not work with my x700 video card, and using the AMD64 cd with the (onboard) ATI RADEON Xpress 200 Series doesnt work either =/

Now, im on the ubuntu live cd right now, and I am wondering if I should isntall it, and then somehow install my x700 drivers after the install (although I have no clue how)?  

I'd realy like to use that card since it has a dvi out for my nice monitor, and another out for another monitor.  This brings me to another question, currently I have a tri-mon set up, which I love.  Would I be able to do this with ubuntu? or atleast dual-mon?  

I'm going to try to using the 'alternate' distros from the download site, and see if those do me anybetter.

Anyway, gotta load into windows now :([/QUOTE]

I will tell you that I have a x200 myself. The live cd has never worked for me, I always install with the alternate cd. I think no matter what you do you are going to have to [install the ati drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). The stock ones just dont cut it. I usualy [download the ATI driver installer ]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")and [follow this set of instructions]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2").  I dont know if the duel or tri monitor will work.

---

### Post by Aceutosh on 2006-07-08
just skip this post

---

### Post by Teroedni on 2006-07-08
The alternate cd should have a higher success  yes:)

> **nicoavz said:**
> 
I'd realy like to use that card since it has a dvi out for my nice monitor, and another out for another monitor.  This brings me to another question, currently I have a tri-mon set up, which I love.  Would I be able to do this with ubuntu? or atleast dual-mon?  


As for you dual boot/tri mon

I think Tri mon is possibible but i have never tryed it myself
Here is a good howtoo for Dual monitors
[http://www.linux-magazine.com/issue/17/DualHead.pdf](http://www.linux-magazine.com/issue/17/DualHead.pdf)

---

