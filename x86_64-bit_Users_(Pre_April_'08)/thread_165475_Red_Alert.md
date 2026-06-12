---
title: "Red Alert"
date: 2006-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by obama on 2006-04-24
I need urgent help...urgently.  Here's the story.  I'm using a 733 mhz PowerMac G4 with Ubuntu 5.10/6.06 (we'll get to that later) a while back my cd drive suddenly and without warning completely ceased functioning.  Getting a replacement is out of the question.  Moving swiftly on to the present day.  I successfully used apt-get to upgrade from 5.04 to 5.10 and things had been going pretty smoothly since, aside from the cd problem and the fact that my onboard sound did not work.  Last night I decided to use update manager to install the beta version of 6.06 as described on the official site (link later).  The files were successfully downloaded, and the computer was roughly halfway through the installation when it came to the preconfiguration stage for gdm or some relative thereof and the process simply froze.  Seeing no other option, I shut down the computer and waited till today to see what I could do.  

Boy, was I in for a surprise.  The computer boots successfully until it comes time to load gdm at which point a cursor comes up and the screen flashes between the text-bootup data that was just shown and a login ttyl, as well as a watch cursor and an "X" cursor.  I can successfully log in via the ttyl if I type fast enough, and through the command "startx" I can start  Enlightenment.  However, hardly any applications outside of those supplied by Enlightenment (I have also tried IceWM and Blackbox) work at all.  Another problem is that I get a full-screen blue error message about X servers about every minute or so, and this will sometimes halt all process and freeze the computer. 

The only solution I can see, given that installing via foreign media is pretty much out of the question, is to stop whatever process is causing this destruction, and hopefully salvage my system via the command line.

Any help at all would be greatly appreciated.  I will be on later tonight to answer questions.

---

### Post by ssam on 2006-04-24
sounds like you are half way between 5.10 and 6.06. the best thing to do would be to get the upgrade finshed.

from the command line (once you have logged in) run
```
sudo /etc/init.d/gdm stop
```
to stop gdm from freezing the system
```
sudo apt-get dist-upgrade
```
to get the rest of the upgrade done.

---

### Post by obama on 2006-04-24
Thanks a million.

The first command worked like a charm, and the ttyl is useable and uninterrupted.

I tried to run the second command, but was told I needed to run dpkg first.  I did that and I was able to install quite a few programs, but dpkg had to quit because there were too many errors.

Next, I tried to run apt-get again, but was greeted with error messages:
```
W: Couldn't stat source package list http://archive.ubuntu.com dapper/main Packages (/var/lib/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-powerpc_Packages) -stat (2 no such file or directory)
```

I'm not sure what this means.  One possibility is that my computer isn't connected to the internet, which would make sense given that in startup I can't connect to the clock server at ntp.ubuntu.com

My next question therefore is: How do I make sure my wireless network card is activated/connected to the network from the command line?

If anyone has any more ideas, feel free.  I can't tell you how relieved I am that my computer might make it out of this unscathed.

---

### Post by obama on 2006-04-24
Wow.  That elation has been swiftly consumed by sorrow.

I just went to boot my computer up, and was presented with this message.

```
Segmentation fault
Alert! /dev/hda3 does not exist.  Dropping to a shell

Busybox v1.01 (Debian 1:101 4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands

/bin/sh: can't access tty; job control turned off
```

I am then presented with ```
#_
```, but I can't type any commands in.

I am seriously thinking about throwing my computer away or giving it to some charitable organization.  Does anyone know what I could do?  At this point booting from some non-cd media or from an external cd drive and wiping the hard drive clean seems to be my only option.

---

### Post by obama on 2006-04-24
Alright, stick with me here.  My new brilliant plan is to install linux on an external hard drive (by booting an install cd on one of my other PPC computers) and I can simply have my Powermac boot from that.  Is that possible?  

If not, would it be possible to reformat my HD and install linux again on my main system *from* an external drive?

---

### Post by aimislame15 on 2006-04-24
hmm.... have you tried zapping the pram? That might bring your comp back to life. The process is a tad complicated, but not too difficult to activate wireless from command line depending on the card you have. Is it an Airport extreme, or just airport?

---

### Post by ssam on 2006-04-25
can you not just get a new cdrom drive? it should take a standard IDE drive.

---

