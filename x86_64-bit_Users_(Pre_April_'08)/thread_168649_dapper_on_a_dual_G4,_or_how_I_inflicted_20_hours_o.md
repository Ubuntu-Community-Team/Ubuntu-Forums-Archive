---
title: "dapper on a dual G4, or how I inflicted 20 hours of pain on myself"
date: 2006-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by hotani on 2006-04-30
This all started when I read the "resize your HFS drive" thread and realized I could throw Ubuntu on my G4 and dual boot. I'm planning on building a PC in the coming months on which I will run Ubuntu so this seemed like a good way to take a more extended test drive than running it on my work machines.

Resizing the partition went off without a hitch. Then I tried installing the system from a Dapper beta 2 disk. For some strange reason it was taking *hours* to go through the steps - then finally errored out with the following:
[img]http://static.flickr.com/48/137474459_8c66ea2693_b.jpg[/img]

No problem, I'm relatively persistent; so I went back worked it over again paying careful attention to the partitions - making sure everything was happy and in the right place, then tried the install again. Same. Frakkin. Error.

That was 15 hours of my life I'll never get back.

Today I came at it again with a fresh perspective and considered the problem could be with the install disk itself. So I burned a new one at 8x and it worked. This is of course after I tried the [installer on the live CD](http://static.flickr.com/46/137820004_cc98c9b256_o.png)... but I won't go there now. The whole process was less than 30 minutes and I had a new system installed. 

I booted up, was met with the text-based boot loader asking me if I wanted OS X, Linux or CD - all is well in the universe, I typed "l" for Linux and in a few short moments I was looking at the login screen. An improvement with the new updates is that my M-audio revolution card works now, having sound is a good thing. Before it sounded like the first note of Clif Burton's *Anethesia* bass concerto... but Clif played other notes after that one, the broken audio driver plus my unsupported card would just grind along in monotone as it unsuccessfully tried to reproduce the login sound.

I do however still have the [same problem with my screen](http://static.flickr.com/55/133146129_8f061482b5_o.jpg), that awful vertical bar from the right side is still showing up on the left side, so I need to fix that one of these days.

After installing the updates, I rebooted and was still hunky dory. Then I decided to switch on SMP since I'm running a dual processor machine. I went to synaptic and was greeted by about 20 packages with "powerpc smp" in the names. I picked the ones that seemed to fit my system (non 64 bit), installed then rebooted.

Then the most agonizing problem I've ever seen was waiting for me. My monitor was shutting itself off (as in going to the screensaver) IMMEDIATELY. There was nothing I could do about it either. Every instant I wasn't moving the mouse, the screen was dimming and threatening to fade away to one of the random default screensavers. After a few ctrl-alt-backspaces I logged into a different session and the problem didn't exist there. But neither did the menus. Plus every applet in the menu crashed and I had a screen full of error messages. I have the screenshot sitting on the desktop on the ubuntu system (I'm back in OS X now since it is unusable now), but it's a beauty - I'll post it up as soon as I'm able. 

Anyway, OS X is a breath of fresh air right now. It has that whole "working" thing going for it... I can't say the same for PowerPC Ubuntu. ](*,)

---

### Post by robbyt on 2006-05-10
the screen issue is due to weirdness with the nvidia drivers, i switched out my nvidia card with an ati card and everything was smooth. 

The gnome weirdness is related to the SMP kernel, i've noticed that the clock is totally unstable in SMP.

see:
[http://www.ubuntuforums.org/showthread.php?t=168664](http://www.ubuntuforums.org/showthread.php?t=168664)

and:

[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/44040](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/44040)

---

