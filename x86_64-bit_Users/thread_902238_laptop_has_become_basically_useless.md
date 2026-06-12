---
title: "laptop has become basically useless"
date: 2008-08-27
forum: x86 64-bit Users
---

### Post by odwyerda on 2008-08-27
Hi I have just recently installed Hardy (64) on my new laptop Gatway T series
centrino T5750
4G DDR ram
250GB HDD.
This machine is about 10 days old and has no crap on it really.

Everything was working perfectly untill yesterday when everything decided to grind to a halt.

Terminal takes well over 30-45 to load and clicking on say a .txt. file takes anything up to a minuite.

Something has gone wrong and I dont know where. I have the same settings as my last laptop which had 1G ram and an intel celeron 1.4Ghz processor, extra desktop effects etc and that ran very well so this laptop should be more than able.

One thing that has started happening is the following error

Code:

There was an error starting Gnome Settings Daemon
Some things, such as themes, sounds, or background settings my not work correctly
The last error message was

did not recieve reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked a reply, the reply timed out expired or the network connection was broken.

Gnome will still to try and restart the settings daemon next time you log in.

I have compiz installed but trying to remove this has become a pain as my system is so so soooo slow that it cannot remove it.
Also I have looked here Ubuntu Forums - View Single Post - Error starting the GNOME Settings Daemon to fix the compiz problem but yet again my terminal is really slow so it may take a while ill update if it speeds things up


UPDATE:

Ok after the log in screen the desktop loads but with the above error in top corner and nothing else loads apart from background and desktop icons. If I try an close the error box it logs me out and process begins again.

Im thinking reinstall but should I install 32bit Ubuntu or is this more than likely not a 64-32 bit issue?

---

### Post by Thelasko on 2008-08-27
I'm thinking it's not a 64-bit only issue.  If you (can you?) open the system monitor and see what's going on?  It's likely that something in gnome locked up and is slowing down your machine.

Did you install anything yesterday or the day before?  What methods did you use?  Did you change any settings in Gnome or add any new hardware (even a camera or flash drive)?

---

### Post by Moop on 2008-08-27
It sounds like a compiz problem. You can disable compiz from the logon screen by choosing Session-Gnome.   64bit should work fine for you.

---

### Post by John Jason Jordan on 2008-08-27
> **odwyerda said:**
> Im thinking reinstall but should I install 32bit Ubuntu or is this more than likely not a 64-32 bit issue?
The lucky thing is that you don't have any data or personal configurations yet, so there is nothing serious to lose by reinstalling.

I would stick with 64-bit Ubuntu. There is very little incompatibility these days between 32-bit and 64-bit Ubuntu. 

I would also try a couple other distros. Fedora and Mint are pretty user friendly and good at detecting hardware and setting things up. I don't want to lose you to Ubuntu, but sometimes installing a different distro will give you a clue as to what went wrong.

If a reinstall of 64-bit Ubuntu and installs of other 64-bit distros all display the same problems, then try 32-bit Ubuntu. 

I don't know what the problem is that you are having now, but keep posting back with results. Thousands of people all over the world read these forums daily. Surely someone smarter than me will finally figure it out.

---

### Post by de0xyrib0se on 2008-08-27
An update got pushed out yesterday and there are multiple users reporting this same exact problem systems being crazy slow. I have not been able to see on the forums which update it is.

---

### Post by Thelasko on 2008-08-27
> **de0xyrib0se said:**
> An update got pushed out yesterday and there are multiple users reporting this same exact problem systems being crazy slow. I have not been able to see on the forums which update it is.

I received a kernel update last night, that was all.  If it's the kernel, you can load an old kernel from the grub menu.  Just use the next option down the list that isn't recovery mode.

---

### Post by de0xyrib0se on 2008-08-27
> **Thelasko said:**
> I received a kernel update last night, that was all.  If it's the kernel, you can load an old kernel from the grub menu.  Just use the next option down the list that isn't recovery mode.

Wasn't sure what the udpate was, just trying to point him in the right direction.

---

### Post by malachi1990 on 2008-08-28
Aother thing is to try and use the recovery mode to fix X-server.  I had a similar problem, and while it's not a complete fix, it did help tremendously.

---

