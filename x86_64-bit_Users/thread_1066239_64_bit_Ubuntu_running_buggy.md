---
title: "64 bit Ubuntu running buggy"
date: 2009-02-10
forum: x86 64-bit Users
---

### Post by bart1452 on 2009-02-10
Hardy 64 bit and Hardy 32 bit both are unstable on my 2005 vintage Compaq Presario with an AMD 64 Athlon 3400+ and 1 Gig memory. It might have something to do with not getting a good connection on us.archive.ubuntu.com. I don't know if all the packages downloaded or not, but there were issues with retrieving packages during the installation and I instructed it to retry. I currently have 64 bit Hardy installed.

The problems include screen video corruption, window panels not working properly, total computer non-responsiveness except for the cursor moving for the mouse after windows are opened and closed several times. The only way out then is to force a BIOS shutdown. A screen shot of one incident is included from when I tried to configure the printer with HPLIP Toolbox.

One example is that while trying to forward an email, the address book window malfunctioned and the middle 95% would not scroll while the very top and bottom did. It was totally unusable.

Another example is when trying to view Yahoo! news video with Flash installed, the ad video runs and then the windows go blank with the word "Done" at the bottom.

I ran the recovery mode and tried to repair broken packages and got the following errors:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

W: You may want to run apt-get update to correct these problems

I ran apt-get update and it didn't work.

david@ubuntuSR1550nx:~$ sudo apt-get update
[sudo] password for david:
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
david@ubuntuSR1550nx:~$

All the apt-get update happened in a split-second so I don't think anything was downloaded and installed. Nothing changed in how the computer runs.

I love Ubuntu Hardy on my laptop and don't understand why it isn't working properly on my desktop. Is there a way to check that all the base system packages are installed and working and make sure things are configured properly?

---

### Post by Mikecore on 2009-02-10
First Off I would get 32 bit running smooth. If the installed failed I would redo it. Everything should be stable on hardware that old.

---

### Post by jespdj on 2009-02-11
It sounds like your computer has a number of different problems.

Try booting into the memory test program; select the memtest86+ option in the GRUB boot menu. Let the memory test program run for a few hours to see if it finds any memory errors. If it does, then the memory in your computer is physically damaged and you'll need to replace it.

Those download problems indicate that your network connection isn't working properly.

What graphics card do you have and what graphics driver are you using?

---

### Post by bart1452 on 2009-02-11
I had done a memory test and it passed after going through about 8 or 9 different tests. It appeared to be repeating the tests again so I exited the memory test program.

I have an SiS760 graphics chip on the motherboard and an SiS900 PCI Fast Ethernet card. I checked the SiS FAQ for Linux and default drivers have been a part of the Linux system for some time.

I've had no trouble downloading anything in the past, so there would have to be some quirk about it to not want to work well with the archive, but some things downloaded and others didn't want to. There must be some issues with the drivers on both the graphics and the ethernet hardware. The strange screen displays continue to appear when I attempt to install anything. The second screen shot is from installing 4NEC2 antenna modeling software in WINE. The working windows look transparent except for the print and they are pretty confusing when they overlay each other. Plus the "bullet traces" appear all over the desktop again, although they don't appear in the screen shot. Clicking a point on the desktop and pulling a box outline open will erase the bullet traces.

The same problems happened with 32 bit Unbuntu so I'm going to stick with 64 bit. Either the drivers for the hardware aren't very good or there is something wrong with another part of the system.

I would say that Windows XP Home works pretty well on the machine as long as I keep Service Pack 3 off of it so I'm going with the theory that the hardware is fine.

Something interesting is that when I click on the links in these lines:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

I get:
Not Found

The requested URL /ubuntu/...dy/Release.gpg was not found on this server.
Apache/2.2.8 (Ubuntu) Server at us.archive.ubuntu.com Port 80

Would that have anything to do with my archive problems?

---

### Post by jocko on 2009-02-12
> **bart1452 said:**
> I had done a memory test and it passed after going through about 8 or 9 different tests. It appeared to be repeating the tests again so I exited the memory test program.

I have an SiS760 graphics chip on the motherboard and an SiS900 PCI Fast Ethernet card. I checked the SiS FAQ for Linux and default drivers have been a part of the Linux system for some time.

I've had no trouble downloading anything in the past, so there would have to be some quirk about it to not want to work well with the archive, but some things downloaded and others didn't want to. There must be some issues with the drivers on both the graphics and the ethernet hardware. The strange screen displays continue to appear when I attempt to install anything. The second screen shot is from installing 4NEC2 antenna modeling software in WINE. The working windows look transparent except for the print and they are pretty confusing when they overlay each other. Plus the "bullet traces" appear all over the desktop again, although they don't appear in the screen shot. Clicking a point on the desktop and pulling a box outline open will erase the bullet traces.

The same problems happened with 32 bit Unbuntu so I'm going to stick with 64 bit. Either the drivers for the hardware aren't very good or there is something wrong with another part of the system.

I would say that Windows XP Home works pretty well on the machine as long as I keep Service Pack 3 off of it so I'm going with the theory that the hardware is fine.

Something interesting is that when I click on the links in these lines:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

I get:
Not Found

The requested URL /ubuntu/...dy/Release.gpg was not found on this server.
Apache/2.2.8 (Ubuntu) Server at us.archive.ubuntu.com Port 80

Would that have anything to do with my archive problems?
Probably not. Those links you pasted are wrong. The full address would be this one [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) (you may not see the full address here, but hover your cursor over it to see the full address in the bottom of the firefox window), they are just too long to show i the terminal, so they get truncated so they just show the beginning and the end of the url. That probably makes the links non-functional even if you click them in the terminal.
You probably just have a bad connection to the server, which fails some times (in your first post you show that it actually works other times, as when you ran "apt-get update", it downloaded the package lists just fine.
To download and install updated packages you need to run:
```
sudo apt-get up**date**
sudo apt-get up**grade**
```The up**date** command will just download new lists of available packages to make the apt system aware of what can be installed or updated. The up**grade** command will download and install any updates that are available for your installed packages.

---

### Post by bart1452 on 2009-02-12
Thanks.

I typed the URLs in and that's how the webpage printed them, but they were complete when I typed them. The errors had to be manually transcribed because the normal utilities weren't up and running yet.

I followed your directions and got this at the upgrade.

david@ubuntuSR1550nx:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@ubuntuSR1550nx:~$

 Maybe all the packages are now installed. The update manager put 15 packages in the other day. But things still get goofy. I had the occasion of scrolling in a window today and the top 95% was not scrolling. It looked like everything was sliding up underneath it. I rebooted and it straightened out. But that's how it always is - after a while things don't work right until I reboot.

Would one of the logs be of any help? I've got a lot of this in the Xorg.21.log

tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.

That's most of the log.

I guess what I need to do is go to terminal and type "ubuntu-bug -p linux" (without quotation marks) the next time a problem arises.

---

### Post by jocko on 2009-02-13
From your screenshots I am convinced that your problem is with the graphics drivers.
Are you using compiz? In that case try using metacity instead to see if the artefacts and corruption is still there.
Press Alt+F2 or start a terminal and type:
```
metacity --replace
```
If you are not using compiz, try starting it (I'm not familiar with SIS graphics on linux, so I don't know if they will actually work with compiz):
```
compiz --replace
```
Another thing to test if you are not using compiz:
```
gconf-editor
```
Browse to Apps-->metacity-->general and toggle the key "compositing_manager" on or off.

If none of these works, maybe you need to add some setting in /etc/X11/xorg.conf (when I google I can find a few very old posts about screen corruption on sis graphics, but nothing recent, and as far as I can see no solution either...).

---

### Post by bart1452 on 2009-02-13
Metacity seems to be the only one loaded and functioning. It can't find compiz, even though the Synaptics Package Manager says it's installed, and falls back to metacity. The computer locks up every time I try to access compiz and I have to do a hard shutdown.

I navigated to metacity > general > compositing manager and it was turned off (false) so I turned it on. I opened up 4NEC2 application which has reliably provoked the errors and it opened without any screen errors.

I don't know why compiz is not working because it appeared in the gconf-editor. As long as metacity works it's not an issue.

It looks like that was the trouble. Thank you for the help. I'd say off hand that the problem is solved. Now I can go to my bug report and say what is causing the problem.

---

### Post by Yellow Pasque on 2009-02-13
> I don't know why compiz is not working because it appeared in the gconf-editor. 
SiS graphics won't run compiz.

---

### Post by bart1452 on 2009-02-15
Are there any ideas about what makes it freeze but for the cursor? It reliably freezes when I open the BOINC application in an user account and often freezes when I open BOINC and change the preferences in the administration account. It also froze every time I put in a new application and ran it the for first time in the administration account.

---

