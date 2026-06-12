---
title: "(K)Ubuntu on amd64 HP zvXXXX laptop"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruudiculus on 2005-12-19
Hello,

I've written a short manual that can be used in order to get a amd64 HP laptop running (K)Ubuntu graphically as soon as possible. I've installed Ubuntu on my zv6251EA laptop and it works great now!

I hope this manual may help you get through the post-installation (configuring the wireless network card and the video adapter) as quickly as possible. See attachments below for the needed drivers and the manual.

Please let me know when something is incomplete, wrong (or great!)

Good luck!

[ATTACH]4694[/ATTACH]

[ATTACH]4695[/ATTACH]

[ATTACH]4696[/ATTACH]

---

### Post by makushimu on 2005-12-20
Good job! 

I use Ubuntu 5.10 on the amd64 HP lappy as well (zv5410us) and love it :D 

Edit: I would add maybe a note or something about the installation of some gui tools for wifi (gtkwifi for instance) and installtion of the amd64 (K8 )-specific kernel...

---

### Post by ruudiculus on 2005-12-26
Well that's a good idea, but I don't have much experience with different 64-bit processors and instaling linux. The normal 64-bit distro's of (K)Ubuntu install nicely, so I think I don't include that in the manual.

The wifi idea is something that I would like to include, but there's a problem here. on a laptop you would like to use different wireless profiles for different locations. I've used KNemo, Wifi Radar and the standard network configurators included in the normal installation of (K)Ubuntu, but they all don't work fine. What I miss is the autodetect and connect part. I still have to go edit my interfaces file and 'ifup' my wlan through terminal. I'm thinking of writing a completely new network connection application myself, but it is a matter of time here: I'm used to Delphi and Windows, so I'll try to learn Anjuta now.

In the mean time I can add a little bit more extensive explanation of how to configure wifi to he manual. So much to do though: this will take a while.

---

### Post by peholmst on 2006-01-24
Did you get the 3D-acceleration up and running as well? Which kernel version do you use and which ATI-driver? I keep getting an error about invalid kernel versions while loading DRI....

Btw, I'm using the 32-bit version of Kubuntu on my HP zv6279ea, as it was easier to find working applications for that platform.

Apart from this little graphics-problem (and HAL's CD-ROM messages), I'm very pleased with this laptop so far.

-Petter-

[QUOTE=ruudiculus]
I've written a short manual that can be used in order to get a amd64 HP laptop running (K)Ubuntu graphically as soon as possible. I've installed Ubuntu on my zv6251EA laptop and it works great now!
[/QUOTE]

---

### Post by ruudiculus on 2006-01-24
No 3d acceleration yet. I will try that soon though.

So, you've got HAL messages too on a 32 bit system? It's a weird message and another problem to be solved. My to-do list is always growing ;)

[LIST=1]
[*]Optimizing ATI driver
[*]solving HAL message problem
[*]Writing network configurator program
[*]Meanwhile optimizing a network configurator script
[*]and lots of other small stuff...
[/LIST]

When I've got something done I'll post i on these forums off course! :) (I think everybody wants a network configuration program better than KWifi, Knemo, Wifi Radar etc.)

---

### Post by peholmst on 2006-01-24
[QUOTE=ruudiculus]
So, you've got HAL messages too on a 32 bit system? It's a weird message and another problem to be solved. My to-do list is always growing ;)
[/QUOTE]

So is mine ;). Too bad nobody has been able to come up with a day with 30 hours in it...

About the 3D-acceleration, I believe installing the ATI-drivers using dpkg (there are a few howtos out there) fixes the kernel version problem, however if you do this you're screen will go black and the only choice you'll have is a hard reboot. Of course there are no errors in the logs what-so-ever, i.e. the drivers seem to believe they work fine. The question is whether this is an ATI-problem or a (K)Ubuntu-problem. I'd like to know who to blame... ;-)

About the HAL-error, I've tried to set the "storage.media_check_enabled" to false on my CD-ROM drive, but it does not work. :confused: I've tried to disable all kinds of stuff with no success. To me this is clearly a bug, I'd like to know whether it's been reported or not, and to whom it should be reported.

About networking, I'm planning to use netenv, though I haven't had the time to write any scripts yet. Too many exams right now. :(

-Petter-

---

### Post by JorgeLedezma on 2006-02-01
The links doesnt works!

[QUOTE=ruudiculus]Hello,

I've written a short manual that can be used in order to get a amd64 HP laptop running (K)Ubuntu graphically as soon as possible. I've installed Ubuntu on my zv6251EA laptop and it works great now!

I hope this manual may help you get through the post-installation (configuring the wireless network card and the video adapter) as quickly as possible. See attachments below for the needed drivers and the manual.

Please let me know when something is incomplete, wrong (or great!)

Good luck!

[ATTACH]4694[/ATTACH]

[ATTACH]4695[/ATTACH]

[ATTACH]4696[/ATTACH][/QUOTE]

---

### Post by ruudiculus on 2006-02-02
As you can see my new signature points to some webspace containing all the files that were previously behind those links.

Attachments can't be very large and signatures can't be of infinite length, so that's why I dropped the files on a webserver.

Good luck with them!

---

### Post by javaTard on 2006-02-03
I have a zv5000 with the 64 bit. Wifi radar works great for it, and it can be gotten right off of synaptic.
I love it

---

### Post by ruudiculus on 2006-02-04
I know the program. It is simple to use and it uses profiles; ideal for laptop use. BUT: it doesn't work for me unfortunately. It can connect but it can't get an IP address (so it can't connect in the end :-# ) And when I want to close the windows it gets ZOMBIE, so the idea is great and simple, but something went wrong during the  implementation. I now use the Wireless Connection Manager, sdaly it doesn't support profiles...

---

### Post by peholmst on 2006-02-07
I managed to get 3D-acceleration!! I just had to configure the graphics card to use UMA instead of sideport (in BIOS).

-Petter-

---

### Post by sithia on 2006-02-09
How does one determine if 3D acceleration is in effect? I'm having no luck running glxinfo or glxgears. Both give errors about RGB. glxinfo can't find "RGB GLX visual". glxgears gives back a "couldn't get an RGB, Double-buffered visual" error. I'n new to ATI (and doubt I'll make the mistake again).

---

### Post by RAOF on 2006-02-09
[QUOTE=sithia]How does one determine if 3D acceleration is in effect? I'm having no luck running glxinfo or glxgears. Both give errors about RGB. glxinfo can't find "RGB GLX visual". glxgears gives back a "couldn't get an RGB, Double-buffered visual" error. I'n new to ATI (and doubt I'll make the mistake again).[/QUOTE]
If glxinfo isn't working, you've **almost certainly** got no 3D acceleration working.

---

### Post by sithia on 2006-02-10
After I completely trashed my install by updating to dapper (no sound, no network, no decent video, etc.) I reinstalled breezy. I did a quick search here and found a thread I hadn't seen before: [http://www.ubuntuforums.org/showthread.php?t=124635]("http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=719834") (the "ATI driver" section). Their laptop isn't a zv6000 but I followed that set of instructions and it worked perfectly! Both glxinfo and glxgears are working. With fgl_glxgears I'm getting 155 to 185 FPS and the screen is running at a very crisp looking 1280x800. I also have my BIOS set with SidePort+UMA.

---

### Post by netspy on 2006-03-03
I am happy to have found this topic..finally more people with a  HP Pavillion with linux on it. I have the ZV6025EA. Also  Ati Radeon 200M XPress and  WLAN wich was hard to get it working.

I currently use Suse 10.0 (not this forum, i know) but had the same issues (ATI & WLAN) So it is not a specific ubuntu issue. I am downloading the DVD of ubuntu, because i thought it would solve all my problems. (alas!).... 

I don't really care for 3d (although it would be great to get it working of course) but wich resolution are you guys using? I now use (1280x800) but i want i higher resolution for working with OpenOffice Spreadsheet...... This is not possible. Also installed many different kind of drivers from Ati (default .run files and self-compiled .bin files but nothing helped....keep getting the mesa driver .....)

---

### Post by whiskeyclone on 2006-03-03
This looks great.  

I've been strugling to get Ubuntu running on my HP/Compaq NX6125. I had no problems with my old Z4400. It is an Xserver problem - terminal runs fine and I've had other linux distros running fine (namely Gentoo). If anyone has any ideas for ATI fix for live cd that I haven't tried that would be a huge help. 

If anyone would care to take a peep at my question [here]("http://ubuntuforums.org/showthread.php?t=138605"), which has been largely ignored, I'd be most thankfull.

---

### Post by ruudiculus on 2006-10-11
Have you managed to install Dapper Drake yet? ;) 

I've updated my Dapper Drake Installation Guide for HP zv6251EA laptop's which use an Ati Mobility 200M video card. When you also have that one in your laptop the video card part of my guide should work.

Good luck!

---

