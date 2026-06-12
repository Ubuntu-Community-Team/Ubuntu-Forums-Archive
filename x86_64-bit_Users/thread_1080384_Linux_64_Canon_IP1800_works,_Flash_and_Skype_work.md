---
title: "Linux 64 Canon IP1800 works, Flash and Skype work"
date: 2009-02-25
forum: x86 64-bit Users
---

### Post by 3Miro on 2009-02-25
Hi Everyone,

after days spend on forums and searching for many answers, I got my system working just as I want it to. I will share my experience with the community so that I can hopefully help someone else. Most of the material below will be taken and summarized from other posts/treads, but it will probably be nice to see it in one place.

Why 64-bit: I need a 64-bit architecture for my work and no 32-bit OS would see all of my RAM. Not to mention that the on my CPU (AMD X2) the 63-bit works notably smoother.

Why not 64-bit: The main problem is that third party support for 64-bit architecture is iffy. Getting my printer (Canon IP1800), Adobe Flash, Skype and some other non-community programs to work is tricky. Hopefully this will help you help you set up your 64-bit system.

Issue 1: Printer Canon IP1800 and I guess you can use that for many other printers

Canon "supports linux", however, they only provide couple of RPM files that naturally work only on Red-Hat related distros. Ubuntu needs debs. Some good community members have created appropriate .deb files that I have listed below. Note those are for ubuntu and related 8.04 and 8.10.

[http://rapidshare.com/files/202347202/CanonIP1800-8.04.tar](http://rapidshare.com/files/202347202/CanonIP1800-8.04.tar)
[http://rapidshare.com/files/202347741/CanonIP1800-8.10.tar](http://rapidshare.com/files/202347741/CanonIP1800-8.10.tar)

You should be able to extract the files, then double click and install them. The 8.10 version has one extra step, you need to type in the terminal:
sudo ln -s /etc/init.d/cups /etc/init.d/cupsys
The name of the cups (common unix printing server) has been changed in 8.10

If you install the files + the extra step on 8.10, reboot the printer and it should work just fine.

The problem is that holds only for a 32-bit system. The driver simply does not work for a 63-bit system. The source rpm provided by canon cannot be compiled on a 64-bit machine since it contains not only source code (as it is supposed to), but also compiled libraries (as it is not supposed to). The compiled libraries are already 32-bit and cannot be changed.

To use this printer, one has to either use 32-bit only (and less ram), dual-boot between 32 and 64 bit (I have done this for years and it is pain you know where) or use Virtual Box, which is the solution I am going to describe. The "obvious" way to use VB is to start it and move all the files that you want to print to the client and then print them. It is a bother at the best, everyone wants to be able to just hit the print button in Firefox or Open Office and print. The solution is to share the printer and connect to it from the 64-bit machine a a network printer.

Requirements:
-install 64-bit ubuntu (or actually this should work with any 64-bit Linux). 

-I recommend at least 1GB of ram (most people that want to use 64-bit systems have way more than that)

-The procedure would take about 5-9GB of hard drive space.

-Download Virtual Box from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), you also want the manual, it is very well written. The Open Source version of VB that comes with the ubuntu repository (add/remove programs) does not have USB support. The other version is "free for personal use", read the licence statement. 

- download a 32-bit ubuntu or ubuntu related .iso file. (8.04 or 8.10)

- download one of the drivers (depending on the 32-bit system that you have)

Install the VirtualBox .deb file by double-clicking on it. To get it to work with the USB, I had to start it with sudo:
sudo VirtualBox
and then keep the terminal open. You may not have to do that.

Create a new virtual machine by clicking on new and following the instructions. With the printer on, go to VitualBox settings and select the USB tab, add the printer as a USB device (follow the instruction in the manual)

Optional step: if you are on a network and want other computers to share the printer as well (apart from the desktop I also have a laptop and I am able o directly print from either one of them), go to the network tab and select Host Interface in place of NAT. (You need to have a router and everything else set up for the network, what this would do is, it would add another device on it).

Run the machine and install ubuntu 32-bit (point it to the .iso file, it is faster). Ubuntu-32 (client) would run in a window within the 64 bit machine (host). Give a name for the computer to be something like Print-Server or whatever.

You  want to install guest add-ons, select from the machine window: Device: guest add-ons. On the 320bit client, you will see a mounted CD-rom icon. Open it and run the file that says something like Linux-32-bit. If it does not work, you may have to do this with sudo:

cd /media/cdrom0
sudo name-of-the-linux-32-file

From Device, on the client window go to USB and select the printer. Follow the instructions to install IP1800 on the client. (Note: from device you can create a folder that would be shared between the host and the client, follow the VirtualBox manual for that). 

After the printer has been installed, go to localhost:631 on your browser. That connects you to the cups server working on your client 32 bit ubuntu. Go to administration and select "share printer". Apply changes and the CUP would restart.

So far everything is on the Client 32-bit system.Not on the host 64-bit one, goto localhost:631 and from administration select: see other shared printers. Apply changes and you should see another printer now. You will probably see the original printer connected to your system, but it would not print. You should also see another printer that says: Canon [email]IP1800@xx.xx.xx.xx[/email] where the xx stand for some numbers. You should be able to print on that one. Select is as the default one for your applications.

The above solution is not as good as having the printer natively on your system, but it is better than dual-booting or being stuck in 32-bit more and waiting the extra ram that you have. The printer would be available without having to constantly move files between the host and the client, when you want to print, just hit print. Virtual Box needs to work only when you print and you can shut it off otherwise to use all of the available resources (i.e. the extra ram that VB takes).

I hope this helps you.

---

### Post by 3Miro on 2009-02-25
OK the first part was long, now I hope be somewhat shorter.

I have both 64 bit laptop and 64 bit desktop computers and I often use skype. Here is how I installed it:

download the .deb uuntu file from skype.com

go to the terminal/konsole/whatever you have:
sudo dpkg -i --force-architecture skype....deb

skype...deb is the skype file you downloaded.

If it complains about dependencies, use the package manager to install the missing libraries. Then you should be able to just run it from the menu.

It works on both the laptop (ubuntu 8.10-64) and desktop (kubuntu 8.10-64 KDE 4.1 and KDE 4.2).

Encountered problems:
skype runs, but without sound. Solution: kill pulseaudio. Happened on my latop, use either
killall -9 pulseaudio
(or maybe with sudo) or terminate the processes from the System Monitor. Restart skype.

skype runs, has sound, but the microphone is not working. I am always having this problem on the desktop. 

Go to the sound mixer program and open the tabs for input and microphone (from preferences). 

Make sure the mic is working (unmute that in playback mode,you should be able to hear yourself). 

Then go to input mode, select microphone and boost the signal. 

Then go to skype -> preferences -> sound. Remove the check from "Let skype adjust the mic volume".

Make a test phone call, it should work.

---

### Post by 3Miro on 2009-02-25
I had issues installing flash on the Kubuntu desktop, but I will post those on the flash tread.

---

