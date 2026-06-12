---
title: "Considering 64bit"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by phidia on 2007-05-04
Hey all! I've been using ubuntu since the hedgehog release and lurking here off and on.

I'm actually considering moving to 64bit. I've assembled 3 computers over the years and want to try a 64bit board. If I do it at all it will be the gigabyte GA-M55SLI-S4 this board is relatively inexpensive and has onboard 1394 which I want. The video card would be a Geforce 7600GS 256Mb pci-e and a Amd 64 X2 brisbane processor.

By no means do I consider myself an expert in linux or 64bit technology. I have some electronic training and also eletrical assembly experiance. Which is why I don't mind fooling around with this stuff.

I've read several threads here on 64bit ubuntu and SLI. It seems doable but I would like to know that if I have problems will I be able to use 32bit without any lost of the use I now have with a 32bit board and 32bit ubuntu.

And while I have read lots of threads here on SLI and 64bit I'm still not sure how using one gpu will work with an SLI board. Will that be a problem? I do use my computers for graphics and video editing but I don't need or want to use/buy two gpus at this time.

Any other thoughts ideas or wild guesses are appreciated. Thanks for reading this. :)

---

### Post by ronocdh on 2007-05-04
With a 64-bit proc you could certainly still use 32-bit Ubuntu and it would work OK. It just wouldn't be any fun. Using 64-bit would of course let you use both cores of your processor, so intensive processes would be much quicker.

I have no experience whatsoever with SLI, so I sorry that I cannot comment on that. But seriously, just go with 64-bit. ;)

---

### Post by phidia on 2007-05-04
> **ronocdh said:**
> With a 64-bit proc you could certainly still use 32-bit Ubuntu and it would work OK. It just wouldn't be any fun. Using 64-bit would of course let you use both cores of your processor, so intensive processes would be much quicker.

I have no experience whatsoever with SLI, so I sorry that I cannot comment on that. But seriously, just go with 64-bit. ;)

Appreciate the reply! 
I've been just reading what I could 64bit related and the other day I saw this thread [http://forums.droplinegnome.org/viewtopic.php?t=5535](http://forums.droplinegnome.org/viewtopic.php?t=5535) at dropline gnome.
I used to use slack but 11 didn't setup  well for me compared to slack10.2  this isn't to create an argument 
I am genguinely puzzled by 64bit (which apple has been using for years now-oddly enough ) the thread supplied seems to be saying that the dual core will work with 32bit is that wrong or have I mis-understood that post?

---

### Post by ronocdh on 2007-05-04
> **phidia said:**
> Appreciate the reply! 
I've been just reading what I could 64bit related and the other day I saw this thread [http://forums.droplinegnome.org/viewtopic.php?t=5535](http://forums.droplinegnome.org/viewtopic.php?t=5535) at dropline gnome.
I used to use slack but 11 didn't setup  well for me compared to slack10.2  this isn't to create an argument 
I am genguinely puzzled by 64bit (which apple has been using for years now-oddly enough ) the thread supplied seems to be saying that the dual core will work with 32bit is that wrong or have I mis-understood that post?
The generic Linux kernel that ships with the Ubuntu i386 image does provide support for [SMP]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing"); however, if I understand it aright, the sum total of the processing power tapped from both cores will never exceed 100% (where 200% represents both cores maxed out). So it's nice, but it's not anywhere near full 64-bit capability.

---

### Post by Cappy on 2007-05-04
I did a lot of research on this when I built my system a couple of weeks ago.
An AMD X2 system will run 60% faster on a 64-bit OS than a 32-bit OS.
An Intel Duo Core will run 40% faster on a 64-bit OS than a 32-bit OS.
A 2.7GHz Intel 64-bit OS runs at the same "speed" as an AMD 3.0GHz 64-bit OS. On a 32-bit OS the speed gap is huge so that's why all those benchmarks usually show Duo Core running much much faster than AMD's offerings. It's dishonest imo.

My T-force MoBo (same price as the mobo you are looking at but no SLI) works perfectly except I had to turn ACPI (no sleep/hibernate functions/processor scaling). Microphone is really really bad but I use my Audigy 4 anyway.

It's not especially hard to get 64-bit to work. Automatix supports 64-bit if you just want to do it that way but I didn't do that because it helps to learn how to install 32-bit programs if you ever run into a problem. If you run into a problem you just gotta package search on packages.ubuntu.com and select the i386 version, extract it with dpkg -x and go find the libraries in a subfolder and move them to your /usr/lib32 folder. It sounds hard but it's really easy. All your 32-bit stuff will work fine ^^

I personally have a 7900GS video card (just one). Those in SLI can run roughly as fast as the cheaper (384?) 8800s. ATI is coming out with new cards on the 14th but it doesn't really matter because they aren't much better than nvidia's and nvidias work better on linux anyway.

---

### Post by dabl on 2007-05-04
On my Intel Core 2 Duo X6800, I'm running Ubuntu 64-bit on one drive, and Kubuntu 32-bit on another (quadruple-boot, don't ask ...)

One thing to bear in mind is that non-repository .deb packages often check the system environment, and when they find it is 64-bit, they won't install. Happened just last night with GTK2, which I kinda need.  So you would be wise to check out what is in the 64-bit repositories and make sure everything you seriously need is available, because the chances of pulling it in from somewhere else and installing it aren't real good.  GoogleEarth, Flash, etc. etc -- you can read all the issues that people have with them.

On the positive side, I'm presently using Audacity and Gnome Wave Cleaner to record, and clean up some old vinyl record albums, and it's great to observe my overclocked dual CPUs both chewing through 180MB .wav files -- I'm sure it's far faster than anything 32-bit could do.  :)

---

### Post by Kilz on 2007-05-04
> **dabl said:**
> On my Intel Core 2 Duo X6800, I'm running Ubuntu 64-bit on one drive, and Kubuntu 32-bit on another (quadruple-boot, don't ask ...)

**One thing to bear in mind is that non-repository .deb packages often check the system environment, and when they find it is 64-bit, they won't install.** Happened just last night with GTK2, which I kinda need.  So you would be wise to check out what is in the 64-bit repositories and make sure everything you seriously need is available, because the chances of pulling it in from somewhere else and installing it aren't real good.  GoogleEarth, Flash, etc. etc -- you can read all the issues that people have with them.

On the positive side, I'm presently using Audacity and Gnome Wave Cleaner to record, and clean up some old vinyl record albums, and it's great to observe my overclocked dual CPUs both chewing through 180MB .wav files -- I'm sure it's far faster than anything 32-bit could do.  :)

All deb packages check to see what architecture they are being installed to. The packages in the repository just happen to be all amd64 packages. There is a control file in each deb file. It is set to a specific architecture. 
There are ways of installing even the ones that are set to i386. But there is a reason that some are set to an architecture. Some files like libraries are specific to the architecture. The place where the files inside the package are installed is also important. Different files go in different places in different architectures. So it takes some knowledge to install i386 packages.

---

### Post by Cappy on 2007-05-04
I wish they would make it so apt-get would automatically retrieve and install i386 packages if you're installing a 32-bit app on a 64-bit OS. It seems like it is more of a "standards" thing than a "we can't do it" thing because it sounds really easy to implement.

---

### Post by nss0000 on 2007-05-04
N000000000000000000000000000000000000000000000000000000000000000000000000


  1) you will get hives
  2) You galpal will leave with the milkman
  3)  your broker will sell your CSX nestegg and buy 5000 shares of IBM


Trust me ....
 nss
******

---

### Post by phidia on 2007-05-04
All replies, with the exception of nss000's :) extremely appreciated. I'm probably going to do it!!
"Milkman"? you are really showing your age. No one's seen one of those in a century or more.

---

### Post by John.Michael.Kane on 2007-05-04
This should get you going should you decide to install 64bit ubuntu

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by Tanker Bob on 2007-05-05
> **Cappy said:**
> I did a lot of research on this when I built my system a couple of weeks ago.
An AMD X2 system will run 60% faster on a 64-bit OS than a 32-bit OS.
An Intel Duo Core will run 40% faster on a 64-bit OS than a 32-bit OS.
A 2.7GHz Intel 64-bit OS runs at the same "speed" as an AMD 3.0GHz 64-bit OS.
Interesting data.  Where did you get the numbers?  I'd like to read the testing methodology.  I also did a lot of research before building my system a few weeks ago, but did not encounter those hard numbers.  Thanks!

---

### Post by Cappy on 2007-05-05
Here you go: [http://blogs.msdn.com/rickbrew/archive/2006/07/13/664890.aspx](http://blogs.msdn.com/rickbrew/archive/2006/07/13/664890.aspx)

I used the data available to figure out that the Intel is 10% faster at the same clock on a 64-bit OS. I don't think it's actually stated.

Edit: Oh yeah, I remember how I got 10%. The Intel Duo Core is 15% faster than the non-AM2 but I've read the AM2 reduces that gap to 3-5% so I estimated 10% +- 2% error.

---

### Post by ronacc on 2007-05-05
I just last week built up a new box almost identical to what you are considering , gigabyte GA55plus-s3g(rev2.1), amd64x2 4600 , nvidia 7600gs 256mb , 2gb ddr2. It works beautifuly with Feisty , it booted the live cd and installed with no boot parms . I am quite happy with the combo. I have been using 64bit exclusively for 3 years and wouldn't consider going back.

---

### Post by Rui Pais on 2007-05-05
> **Cappy said:**
> I did a lot of research on this when I built my system a couple of weeks ago.
An AMD X2 system will run 60% faster on a 64-bit OS than a 32-bit OS.
An Intel Duo Core will run 40% faster on a 64-bit OS than a 32-bit OS.


60% and  40% faster? would be a better world, one where those apply :)

at most you will see 20~30% for high cpu intense task and very specific ones...
in most cases you will not measure any real difference at all.

I used edgy 32b and 64b all time booting one and the other (close source apps that disn't work correctly on 64b) and never notest any speed up at all. 
No. One app i made for protein folding simulation run it for hours on 100% cpu and was faster. Times was reduced from 1,5 hour to 1h20mn. Great.

One should stick for the 64b cause they are the future. 
Don't bet much on speed, you may get disappointed.

---

### Post by Tanker Bob on 2007-05-05
> **Cappy said:**
> Here you go: [http://blogs.msdn.com/rickbrew/archive/2006/07/13/664890.aspx](http://blogs.msdn.com/rickbrew/archive/2006/07/13/664890.aspx)

I used the data available to figure out that the Intel is 10% faster at the same clock on a 64-bit OS. I don't think it's actually stated.

Edit: Oh yeah, I remember how I got 10%. The Intel Duo Core is 15% faster than the non-AM2 but I've read the AM2 reduces that gap to 3-5% so I estimated 10% +- 2% error.
Good data, thanks!

---

### Post by Kilz on 2007-05-05
> **Cappy said:**
> I wish they would make it so apt-get would automatically retrieve and install i386 packages if you're installing a 32-bit app on a 64-bit OS. It seems like it is more of a "standards" thing than a "we can't do it" thing because it sounds really easy to implement.

Its a to lazy Ubuntu developers, we are waiting on the Debian developers (who will never do it because of a political problem) and then we will just add eye candy to it kind of thing.

---

### Post by phidia on 2007-05-05
> **ronacc said:**
> I just last week built up a new box almost identical to what you are considering , gigabyte GA55plus-s3g(rev2.1), amd64x2 4600 , nvidia 7600gs 256mb , 2gb ddr2. It works beautifuly with Feisty , it booted the live cd and installed with no boot parms . I am quite happy with the combo. I have been using 64bit exclusively for 3 years and wouldn't consider going back.

Hey Ronacc, That's even the amount of ram I'm thinking of installing! Did you have any problem with the bios on that motherboard? I read some reviews that claimed gigabyte is using bios that caused problems for some users. I don't use windows so I'm not quite sure how I would update bios without it but I'll do some reading on that if I need to.

---

### Post by Cappy on 2007-05-05
> **Rui Pais said:**
> 60% and  40% faster? would be a better world, one where those apply :)

at most you will see 20~30% for high cpu intense task and very specific ones...
in most cases you will not measure any real difference at all.

I used edgy 32b and 64b all time booting one and the other (close source apps that disn't work correctly on 64b) and never notest any speed up at all. 
No. One app i made for protein folding simulation run it for hours on 100% cpu and was faster. Times was reduced from 1,5 hour to 1h20mn. Great.

One should stick for the 64b cause they are the future. 
Don't bet much on speed, you may get disappointed.

Heh, probably! The only thing I personally care about is my games being non-laggy. But that's me.

---

