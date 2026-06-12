---
title: "networking problem on imac G3"
date: 2006-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by croberts134 on 2006-03-18
My work computer is an older iMac G3 that runs OS 9.  It now dual boots Ubuntu and OS 9 and I am hoping to be able to eliminate OS 9 completely.  I have been loving Ubuntu since installing it last Saturday (yes I went in on the weekend just to install an OS).  

Anyways, the only problem I've had is with networking.  During the install, Ubuntu wasn't able to automatically configure networking.  So I skipped that step and decided to do it later.  I had to manually input the IP Address, Subnet Mask and Router Address.  I got these values directly out of OS9 where networking works fine.  Even after inputting these values, networking does not work in Ubuntu even though when I switch to OS9 it works fine.

I searched the forums for an answer but haven't found anything (or I don't know what I'm looking for).  This is the obstacle keeping me from permanently switch Ubuntu.  Any ideas would be appreciated.

---

### Post by Rxke on 2006-03-19
you say: "I had to manually input the IP Address, Sub...." 

When did you do that and where? after the install in the graphical nework-configuration utility? (under system/administration/network)

---

### Post by croberts134 on 2006-03-19
[QUOTE=Rxke]you say: "I had to manually input the IP Address, Sub...." 

When did you do that and where? after the install in the graphical nework-configuration utility? (under system/administration/network)[/QUOTE]

Yes....sorry for leaving that out.  That is where I entered all of my network configuration details.  It was post install in the graphical network-configuration utility.

---

### Post by jdp on 2006-03-19
Is OS 9 set for DHCP, and you just copied the values that it shows in the TCP/IP Control Panel?  If it does use DHCP, just set Ubuntu to use DHCP as well.

---

### Post by croberts134 on 2006-03-19
[QUOTE=jdp]Is OS 9 set for DHCP, and you just copied the values that it shows in the TCP/IP Control Panel?  If it does use DHCP, just set Ubuntu to use DHCP as well.[/QUOTE]

I tried setting up Ubuntu to use DHCP but that failed (well the network config graphic interface said the network was active, but all attempts to go to multiple websites failed).  I ended up copying the values from the TCP/IP Control Panel once I failed at using DHCP a few times.

---

### Post by spangemonkee on 2006-03-19
Got to a terminal window (CTRL-ALT-Command + F1). Login. type *ifconfig* and see if the results are the same as what you type in under the gui.

---

### Post by 3rdalbum on 2006-03-20
I notice you didn't mention Domain Name Server addresses. When I upgraded from dialup to broadband I couldn't access any websites, until I figured out that I needed to input the DNS addresses.

Have you put those in?

---

### Post by croberts134 on 2006-03-21
I have input the DNS addresses and confirmed in the terminal that the values match what I entered under the GUI.  As soon as I boot OS9 instead of Ubuntu the networking works just fine.  Any ideas?

---

### Post by sulobanks on 2006-03-21
Perhaps you should check with the network admin at your work.  I've seen a few routers that limit access to specific computer names and/or mac addresses.  Since you've got the same information in both systems, it makes me wonder if there is something locking your ubuntu system out at the router level.  If it's a pain in the butt to talk to your network admin, you might try making sure your ubuntu system has the same host name as your os 9 system.

---

### Post by croberts134 on 2006-03-22
This might be dumb but how do I check the host name in OS9?  Its not hard to talk to our Network Admin....but he told me when I started that I'd never get Linux working without his help.  So, I guess its an ego thing :D

---

### Post by spangemonkee on 2006-03-22
[QUOTE=croberts134]This might be dumb but how do I check the host name in OS9?  Its not hard to talk to our Network Admin....but he told me when I started that I'd never get Linux working without his help.  So, I guess its an ego thing :D[/QUOTE]

Apple Menu -> Control Panels -> TCP/IP

---

### Post by jdp on 2006-03-22
It could require a DHCP Client ID to get a lease.  Check the TCP/IP control panel for that too.

---

### Post by croberts134 on 2006-03-24
So I went into work excited to try some more suggestions to get Ubuntu working.  I start up the computer and up comes an apple!  Our IT/Network Admin not only replaced Ubuntu on my computer but upgraded the Apple OS too!  So sad.

He quoted me some policy on unauthorized software on company computers....except before I installed Ubuntu I asked him if I could!  Argh.  I hate the corporate world sometimes.  Well I guess this is just an excuse to dust off the old IBM Thinkpad I have in a corner at home and make it a Linux box now that I love Ubuntu.  Thanks for the help everyone.  I'm sure it won't be long before I'm back.  :p

---

### Post by Rxke on 2006-03-24
Whoa, if one tried to pull a trick like that with me... :evil: 

I hope you didn't lose any work?

---

### Post by croberts134 on 2006-03-24
Thankfully not.  We keep all of our work on our fileserver and its back up so I could throw my computer out a window and not lose anything.  But I was so angry that he threw out my hard work after he told me it was alright.  If it wasn't Friday.....

---

