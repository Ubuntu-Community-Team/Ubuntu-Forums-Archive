---
title: "howto wireless internet on an ibook g4"
date: 2006-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by N'Jal on 2006-04-25
This guide was outdated and has been updated as of 14/01/07 (14th Jan for those who use month/day/year as opposed to /day/month/year).

Personally since the wiki covers most of this I saw little point in updating this however someone said it helped so I shall update it to make sure it stays relevant, however since the wiki is supposed to be the knowledge base I would advise you use that.

This is going to be a step by step guide going from a fresh install of edgy eft. I assume that since little has change and that the bcm43xx driver was included in 2.6.17 kernel (I believe) and since dapper uses that kernel this guide should work for both.

Section 1:

First off you need an network connection, but if your using wireless your going to have access to a router, plug in the network cable and set up the internet. if you know how to do this skip this section

Open networking [System -> Admin -> Networking].
Click the Ethernet connection.
Click properties.
Check the enable this connection.
Set it to dhcp [If you use DHCP].
Click ok.
Then activate the connection by clicking activate.
Hit ok.

Now to ensure the connection is up and running open a terminal and type:
```

sudo /etc/init.d/networking restart

```

Just to check it's working type this:
```

ping www.google.com

```

if you get a reply your network cable's working and it's on to section two, if not just reboot your machine it should work after that.

Section 2:

We need to install several programs in this section, they will be used later on in this guide, you will also need to ensure the universe and multiverse repo's are enabled. 

Follow the guide here if you do not know how to enable universe and multiverse [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Type this in the terminal after adding the universe and multiverse, on a fresh install upgrading took a while.

```

sudo apt-get update
sudo apt-get upgrade

```

Now we have access to download and install the programs we need. However before we do so, just check your card is compatible with this guide. Type this into a terminal:

```

lspci

```

Now since this guide is designed for use on iBooks, I will only mention the card here, I wont cover other cards that use the bcm43xx driver, this is a mac guide only. The card in MY iBook is this one:

```

0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

```

sudo apt-get install network-manager bcm43xx-fwcutter

```

Right once all these programs are installed we are on to section 3.

Section 3:

Here we actually are onto starting to work with the driver [oh at last], so again in the terminal type this and through recent developments it can mostly be done in one step.

```

sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

```

that's the driver downloaded, the firmware extracted and installed.

Section 4: 

To ensure the driver is installed and working properly:

```

sudo modprobe bcm43xx

```

To check everything thus far has worked type:

```

iwconfig

```

This will display all your wireless network connections, if you have a listing that has 'Broadcom' in it's nickname, it's worked.

Now we need to make the driver load on boot, always handy to do:

```

sudo gedit /etc/modules

```

Add the line 'bcm43xx' on a new line save and close the editor.

Section 5:

Now all the hard stuff is done we need to just set up the interface now,

Open the networking again. [System -> Admin -> Networking]
Click the wireless connection.
Click properties.
Check enable this connection.
Set it to dhcp [Assuming again you use DHCP].
Click ok.
Set the default gateway to the name of the wireless connection [in most cases eth0, but it's easy to see which one is yours].
Click ok.

Unplug the cable now, and first try this 

```

sudo /etc/init.d/networking restart

```

```

ping www.google.com

```

If this doesnt work, reboot and you should be online, but if it works without rebooting it would be better.

Thanks,
Njal

I hope this helps someone, but please bear in mind I'm no linux expert, I just read a lot and eventually it worked for me. and these were all the steps I took to make it work. thats all.

---

### Post by el3ktro on 2006-04-25
So far everything works on my iBook - but I don't get an IP for the wireless connection. DHCP is turned on of course, and I've disabled all encryption stuff. Any ideas what I could try?

Tom

---

### Post by N'Jal on 2006-04-25
type 

```

iwconfig

```

it should give you something like this

```

njal@serenity:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"W00T3R"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:16:B6:18:55:C2
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off

eth1      no wireless extensions.

sit0      no wireless extensions.

njal@serenity:~$

```

if it shows you connected to your router and the nickname it'll be a start, i have a hunch it might that you have a 802.11b network, can you confirm

if so i would like to link you to this thread [http://ubuntuforums.org/showthread.php?t=142727&highlight=bcm43xx]("http://ubuntuforums.org/showthread.php?t=142727&highlight=bcm43xx")

and go to step 4 and the whole script thing, it's possible to automatically set the script at boot time anyway though.

many thanks to spaceballl for providing lots of the information i used.

if you want to go ahead and try that by all means, let me know if it works. but i do know that wep works as we have a wep encrypted network that i am connected to, so it's possible to turn wep back on if you so need to use it.

---

### Post by blueboy0466 on 2007-01-09
will this work on opensuse
QUOTE=el3ktro;956680]So far everything works on my iBook - but I don't get an IP for the wireless connection. DHCP is turned on of course, and I've disabled all encryption stuff. Any ideas what I could try?

Tom[/QUOTE]

---

### Post by N'Jal on 2007-01-09
Don't see why it wouldn't work, but sometimes with different distros they save files and drivers and sources in different places, so it might, however it might not.

It's also worth noting that it's probably outdated now, since after a failure and reinstallation, these instructions no longer worked for me, there are probably a few easier ways to do it now.

---

### Post by wannabecanuck on 2007-01-11
First of all, thank you N'Jal for taking the time to break this all down for us newbies.  I greatly appreciate it.

In following your steps, I was doing pretty well until I hit a snag.  When I began Section 3, I get the follow message

```

________@xbuntu-laptop:~$ sudo apt-get install subversion build-essential network-manager network-manager-gnome nm-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nm-applet
________@xbuntu-laptop:~$ svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
bash: svn: command not found

```I hope this is a case of user error.  Thanks for your input.

Pete

---

### Post by N'Jal on 2007-01-11
As far as I can tell nm-applet is not critical for this, it was just a dependancy that seems to have beed added into the main network-manager package, as far as snv goes it worked for me, this is because I already have subversion installed, I can only imagine that all packages failed to install, remove nm-applet and it should all work, or so I imagine.

Though I canno't stress enough, It may be outdated now, my laptop itself has stopped working wirelessly, could be anything, ain't had the time to reinstall and check, if it does not work for you, please find another method. Having said that I hope this does work for you, but I can no longer guarentee it.

However, I have found some more issues with this guide that I shall try to fix, the most obvious one is the download for the firmware is missing, so i shall get a new url.

---

### Post by wannabecanuck on 2007-01-11
Fair enough.  What interested me more was the "svn: command not found."  Any thoughts?

---

### Post by N'Jal on 2007-01-12
it worked for me when i ran it (and I ran it just yesterday to test it), only thing i can think of is you don't have subversion installed, do you have it installed?

If so then I shall hunt for a tarball file you could download.

To be honest, the Ubuntu wiki has all the instructions for getting the card working and it would probably be better if you go and use the wiki, since it's supposed to be the knowledge base etc.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by wannabecanuck on 2007-01-14
This documentation helped and got my problem solved.  The WiFiRadar application appeared to aid in getting connected.

---

### Post by N'Jal on 2007-01-14
Well that the case I shall update this for use with edgy

---

### Post by ps851112 on 2007-01-22
Hi Njal, thanks a bunch for your post, helped me a great deal on the pre 1/14th update you just did.  I had to re-install due to hd failure ](*,) .  I tried your updated howto and it does not work for me any more.  do you happen to have the old commands?  i would greatly appriciate it.  THANKS

---

### Post by N'Jal on 2007-01-22
If you tell me where it failed I shall see if I can't work out where you need to go from, save you having to go through another howto.

---

### Post by ps851112 on 2007-01-23
I'm pretty sure the drivers installed properly but the connection manager that was installed only shows "wired network" connection as a selection.  I have tried manually connecting by typing in my SSID.  I know my router is enabled for 802.11b and i have disabled the encryption.  I get an IP but no route (nothing in network servers & no web pages).  Any ideas?

I have no problem going back through the old how to if you still have it, as i know this did work and i have the airport.kext file from my OSx partition which last time i was able to export the driver from.

---

### Post by ps851112 on 2007-01-23
Alright, i got it working.  Not sure what i was doing wrong and what commands i typed to get it to work but its working (manually that is).  Know of any reason why the network manager gnome wont display my network?  or do you know of a good wireless network manager that works with bcm43xx?

---

### Post by N'Jal on 2007-01-23
I am afriad I don't, I was reading up on this and they recomend using a speciific driver for some reason, I don't know why, so I followed the example, as long as it has worked then thats cool, but the howto no longer worked for me, I had tried on a couple of occasions, and couldn't get it working on my iBook. This is the reason I have updated my tutorial.

---

### Post by ps851112 on 2007-01-24
Cool, thanks a bunch for looking into to this, the important thing is i can get online with my wireless, even if i have to type the SSID in manually.  Next up is waiting for flash to be release :mad: , lol.  I might have the money for a new laptop by then :lolflag: .
Thanks again!  :biggrin:

---

### Post by xofs on 2007-02-27
Wow!
Thanks so much for the step-by-step.
6.06 on my iBook G4 and the only glitch was the wireless.
I followed the steps and it works like a charm!

Thanks again, good job!

---

