---
title: "bcm43xx-fwcutter - no internet"
date: 2007-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by nickdr on 2007-03-03
i know that bcm43xx-cutter works with my system, i have used it before, but it is a real pain to shut down my pc and unplug everything and then bring it downstairs and then have to shut down and unplug the other pc just to get a wired connection. i have a perfect wireless connection in windows, so is there any way that i can download fwcutter onto my flash drive, and then install in ubuntu? this way i don't need an active internet connection in ubuntu to install it?

thanks for any and all help!

---

### Post by John Jason Jordan on 2007-03-03
> **nickdr said:**
> i know that bcm43xx-cutter works with my system, i have used it before, but it is a real pain to shut down my pc and unplug everything and then bring it downstairs and then have to shut down and unplug the other pc just to get a wired connection. i have a perfect wireless connection in windows, so is there any way that i can download fwcutter onto my flash drive, and then install in ubuntu? this way i don't need an active internet connection in ubuntu to install it?
I looked in Synaptic for you because in Synaptic you can click on Properties and see what the dependencies are. It lists 

libc6 >= 2.4-1
debconf >= 0.5 | debconf-2.0

So as long as you have those installed it should be fine. You can find the .deb file in the repositories and download it.

---

### Post by nickdr on 2007-03-03
could you explain in depth a little more. i'm a linux noob and links and step by step instructions help me a lot. thanks!

---

### Post by John Jason Jordan on 2007-03-03
> **nickdr said:**
> could you explain in depth a little more. i'm a linux noob and links and step by step instructions help me a lot. thanks!
It's morning and my head is clearer. When I read what you said again I realize that I am not sure exactly what the problem is. I gather you have two computers, one running Windows and one running Ubuntu Edgy or Dapper, amd64. The Windows computer is plugged into the ethernet cable, which in turn goes to a modem, and then to the internet. Its connection is wired, but something must be broadcasting the wireless signal that you want the Linux computer to receive. 

What confuses me is why you have to shut down and move two computers to get the Linux computer a wired connection. You could just plug the ethernet cable that is currently going into the Windows computer into the Linux computer, which will get internet access for it, then install the bcm43xx tools and get the wireless working, then plug the ethernet cable back into the Windows computer. Ethernet cables can be hot-swapped like this without restarting the computer. So all you have to move is the Linux computer. Since you think you'd need to move two computers, I must be misunderstanding something about the situation.

As for installing the bcm43xx stuff, once you have the .deb file you can install it from the command line with (I think) "sudo dpkg -i /<path>/<name of .deb file>." I have been using Linux for only about a year, so I am not a guru at installing stuff from the command line, but I think .deb files contain headers telling dpkg what is needed to install the package, where it install it, and so on. I think if it needs something that is not installed you will get an error message about it.

Another thing that confuses me is that I could swear that the default installation of Ubuntu automatically installs the bcm43xx stuff. Therefore, I don't understand why it is not already installed. What kind of computer is the Linux computer? One thing that would help is knowing what kind of wireless chip it has. Run lspci from the command line and look for a line that looks like this:
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
And report back what it says.

---

### Post by nickdr on 2007-03-03
ok sorry i confused you so.

i am dual booting with windows and the windows install connects wirelessly. downstairs i have a second pc that is wired. if i wanted ubuntu wired i would need to bring this pc downstairs, meaning i would have to unplug everything. 

however i kept looking through the repos and found a amd64 deb file of bcm43xx-fwcutter. i installed it and the wireless connection is perfect now. i am typing this in ubuntu right now! thanks for the help!

---

