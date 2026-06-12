---
title: "Macromedia Flash and Realplayer Difficulties"
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by urbandryad on 2006-05-05
I guess you may have heard this before: I can't get flash to install properly on my computer. It sucks. I can't visit any of my favourite sites well, I can, but they don't look very nice with those green puzzle peice things asking me to install flash all the time. I can't watch flash movies. Its getting to be a problem.

What do I do? Macromedia flash doesn't support my labtop hardward. I'm running Ubuntu Breezy Badger 5.10 on a G3 blueberry clamshell iBook.

I also can't get realplayer to install. I just need to be able to watch .RM movies. Can anybody help me with this? :confused:

---

### Post by louis_nichols on 2006-05-05
I don't think flash has any hardware issues. You should eb able to sort out this issue by installing from synaptic the package "flashplugin-nonfree" which is the macromedia plugin. The package "realplayer" is also in synaptic and should work.

Good luck!

---

### Post by slux on 2006-05-06
Flash will not work on PPC since it's proprietary software and only a x86-version is available but I guess the original poster knew that. We have some hope for a free flash implementation fairly soon in the form of GNU Gnash. I think they're pretty close to doing a first release which will certainly not be perfect (no sound support might be the major thing) but hopefully it's the first of many versions and we'll finally get new free flash.

As for your realplayer issue, what's the problem you're having? There's a PPC version of that even though it is proprietary.

---

### Post by urbandryad on 2006-05-06
I guess flash will have to wait then.

As for realplayer, the problem is I can't install it. It shows up grayed out in "Add Applications" and I can't seem to find it anywhere in synaptic at all. When I try to download from their website I can't find the Linux-On-PPC version. Maybe somebody can help me out? I think I have a problem with my repositories, but I have all the official, non-free, multiverse, universe etc repositories set up. Hmmm...

---

### Post by calum on 2006-05-06
[QUOTE=urbandryad]I guess flash will have to wait then.

As for realplayer, the problem is I can't install it. It shows up grayed out in "Add Applications" and I can't seem to find it anywhere in synaptic at all. When I try to download from their website I can't find the Linux-On-PPC version. Maybe somebody can help me out? I think I have a problem with my repositories, but I have all the official, non-free, multiverse, universe etc repositories set up. Hmmm...[/QUOTE]

PPC versions of RealPlayer and HelixPlayer (the open source version of RealPlayer) are downloadable from [https://helixcommunity.org/project/showfiles.php?group_id=154]("https://helixcommunity.org/project/showfiles.php?group_id=154") (although HelixPlayer comes as an RPM, so you'll have to convert it to a deb using alien)... specifically, the latest version of RealPlayer for PPC is [this one]("https://helixcommunity.org/download.php/1346/realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin").

---

### Post by urbandryad on 2006-05-07
Okay, so I have the file, but what do I do with it? You didn't explain that part?

I double clicked it and it made this folder called Realplayer, but there was no icon I could click to run the program, just a bunch of weird system, files, no menu icon either. >__>

---

### Post by calum on 2006-05-07
[QUOTE=urbandryad]Okay, so I have the file, but what do I do with it? You didn't explain that part?

I double clicked it and it made this folder called Realplayer, but there was no icon I could click to run the program, just a bunch of weird system, files, no menu icon either. >__>[/QUOTE]

Run the .bin file as root from wherever you downloaded it to.  It will install everything to the right place, including the desktop menu.

---

### Post by urbandryad on 2006-05-07
Okay, this really doesn't help me. I know I have to run it. HOW do I run it? What do I go into to do this? What do I type? I'm not an expert I'm a newbie. Kay? ;__;

---

### Post by calum on 2006-05-07
[QUOTE=urbandryad]Okay, this really doesn't help me. I know I have to run it. HOW do I run it? What do I go into to do this? What do I type? I'm not an expert I'm a newbie. Kay? ;__;[/QUOTE]

Ok, assuming you downloaded the file to your desktop, open a terminal and type these three commands, pressing return after each one:

cd ~/Desktop
chmod a+x realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
sudo realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin

at this point you'll be prompted to enter your password.  Then step through the installation questions you're asked, accepting the default values (just press enter without typing anything) when it asks you about installation locations.  When it's finished, you should be ready to go... if it doesn't show up on your Applications menu straight away, try running the command "pkill panel" in your terminal window, which will cause the panel at the top and bottom of your window to briefly disappear, then reappear.

---

### Post by calum on 2006-05-07
[QUOTE=urbandryad]Okay, this really doesn't help me. I know I have to run it. HOW do I run it? What do I go into to do this? What do I type? I'm not an expert I'm a newbie. Kay? ;__;[/QUOTE]

Ok, I'm doing this from memory, but assuming you downloaded the file to your desktop, open a terminal and type these three commands, pressing return after each one:

cd ~/Desktop
chmod a+x realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
sudo realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin

at this point you'll be prompted to enter your password.  Then step through the installation questions you're asked, accepting the default values (just press enter without typing anything) when it asks you about installation locations.  When it's finished, you should be ready to go... if it doesn't show up on your Applications menu straight away, try running the command "pkill panel" in your terminal window, which will cause the panel at the top and bottom of your window to briefly disappear, then reappear.

---

### Post by urbandryad on 2006-05-07
I do the last one and it says 'Command not found'

---

### Post by calum on 2006-05-07
[QUOTE=urbandryad]I do the last one and it says 'Command not found'[/QUOTE]

My mistake... try:

sudo ./realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin

instead.

---

### Post by urbandryad on 2006-05-07
Okay, that worked. I installed it. But it won't play any files. The whole player turned blank when I try to play a .rm file. >> *sigh* I'm not having a good day.

---

### Post by calum on 2006-05-07
[QUOTE=urbandryad]Okay, that worked. I installed it. But it won't play any files. The whole player turned blank when I try to play a .rm file. >> *sigh* I'm not having a good day.[/QUOTE]

You're not alone unfortunately; video playback broke for me a while back, and seems to have done for other users too (e.g. [this thread]("http://ubuntuforums.org/showthread.php?t=85024") and [this one]("http://ubuntuforums.org/showthread.php?t=155371")).  Works fine for me with audio-only streams and local audio files, though, so it still has its uses.

---

### Post by kingred on 2006-05-08
do what i do, print the forum out so you have it ready for next time :)

trust me saves headaches in the long run :D

---

### Post by surroundu on 2006-05-15
OK, OK.... So, to get this straight, we cannot have flash at this point in time- for PPC. Right? A buddy put FC5 on his PC and has RealPlayer, Java and Flash running. This isn't a plug for FC5- rather that he has a PC and I have a Mac... so it's because of my Mac that I cannot have flash? So are we really out of luck until Gnash? 

I love Ubuntu, but not having my kids be able go to nick.com once in a while sucks. If we could get these Wintel staples going on Ubuntu PPC, it's be so much easier to never look back.

---

### Post by 3rdalbum on 2006-05-16
There's gplflash too, but the best it's ever done on my PPC was display the first frame of the movie. And it caused a lot of crashes, but I've heard that it's because I used the prepackaged version.

---

### Post by Ptero-4 on 2006-05-16
[QUOTE=surroundu]OK, OK.... So, to get this straight, we cannot have flash at this point in time- for PPC. Right? A buddy put FC5 on his PC and has RealPlayer, Java and Flash running. This isn't a plug for FC5- rather that he has a PC and I have a Mac... so it's because of my Mac that I cannot have flash? So are we really out of luck until Gnash? 

I love Ubuntu, but not having my kids be able go to nick.com once in a while sucks. If we could get these Wintel staples going on Ubuntu PPC, it's be so much easier to never look back.[/QUOTE]

You can always have an OSX inside mol for when your kids want to use their flash based websites.

---

### Post by slux on 2006-05-16
First alpha of GNU Gnash is out and it's (the source) downloadable from a GNU mirror. It's not ready for prime time yet at all but it does show some movies without sound. Notably, the ones I tried on weebls-stuff.com worked. OTOH, bunch of stuff on newgrounds.com failed. :P

So basically right now it's just for very early testing but they're making progress.

---

