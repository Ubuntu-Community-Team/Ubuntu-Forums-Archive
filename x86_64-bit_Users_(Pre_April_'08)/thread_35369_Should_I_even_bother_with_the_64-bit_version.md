---
title: "Should I even bother with the 64-bit version?"
date: 2005-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by VincentP on 2005-05-18
I have the 32 bit and 64 bit ISOs burned to CD, so I can install either of them.  I don't want to have to go through a bunch of crap to get simple things working, that's why I'm considering just installing 32-bit.  Is the performance difference noticeable enough to make the nuisances worth my time?

---

### Post by Jarz Corp on 2005-05-18
Well, lets see how I can paraprase this witout being deleted by the MOD.

The crap as U so delicately put it is the same on both platforms, fiddling with a display driver to get full force 3d support, fiddling with some other stuff to get sound to work at and almost acceptable level, depending on your soundcard of course. Installing java buy hand, and even worse spending days googling to find a version newer then the blackdown one at suns website, they do not want to support 64bit on the personal cpu platform, not until their major sponsor microsoft says go anyway.

The major "hurdles" and they aren't even that because they can't be solved by U or anyone in this forum. Realplayer NO GO, Flash NO GO, Codecs for different formats, and sometimes formats that should work on linux, NO GO.

The only way, no matter what people brag about in this lovely and most helpfull forum,  are U going to get these 3 pests to work without chroot, and then U might as well install 32bit from the bottom up. 

So many websites these days are based on crappy flash, and the only reason for me staying on 64bit is because I am an old angry man, pissed off by the fact that I got this kick-ass cpu that not even the OS I really love and chose myself doesn't support because Intel-Microsoft-Sun says it shouldn't be so.

Ohh the cherry on top. U will have to do loads of small tricks to get a lot of stuff to work, that might just be an Ubuntu thing, but I dont think so. Like making your own scripts for ET and Army Ops to get them to run, let me know if U want them.

---

### Post by zxc on 2005-05-18
> Ohh the cherry on top. U will have to do loads of small tricks to get a lot of stuff to work, that might just be an Ubuntu thing, but I dont think so. Like making your own scripts for ET and Army Ops to get them to run, let me know if U want them.

Why don't you publish them all in a thread ;)

---

### Post by pointym5 on 2005-05-18
I've had very few issues. I don't want to play any games, I hate Flash and RealPlayer, and the Java 1.5 SDK works great.  Sound worked without any work on my part (other than to figure out I'd hooked up the front audio incorrectly, which was of course not Ubuntu's fault at all).

---

### Post by Jarz Corp on 2005-05-19
Well ZXC because they are all in here somewhere.

But U've got a point there, I will try and gather up all my tidbits and post them in one way or the other, and then they might be of help to others and they might not.

---

### Post by Jarz Corp on 2005-05-19
Well if U dislike Realplayer and flash that much it surely isn't aproblem, except the 1,5 sdk doesn't have a webplugin and a webstart build into it.

I dislike Real to, but I really miss listening to BBC while I do whatever it is I do for countless hours on this thing.

---

### Post by Fascination on 2005-05-19
I dont think a day goes by without considering dropping down to 32bit; I love gaming, and of course the amount of trouble Im having with getting the ATI drivers to function to their full power and setting up a 32 bit eviron just to play games is really annoying.
The only thing thats stopped me so far is that things can only get better - hopefully now that we are starting to see more media focus on 64bit we might see some more support (maybe even Flash for 64bit! *gasp*).
I must confess though, I would have thought that a lot of the issues that have been brought up regarding Ubuntu's 64 bit release would have been addressed by Ubuntu staff themselves - right now it looks like they've banged together a 64bit version then stopped working on it.

---

### Post by Jarz Corp on 2005-05-19
I am sorry to say that it feels like U are spot on.

The Reposotories that worked right after I installed have stopped, and some reps are empty in the amd64 section.

So we can only hope that 64bit is the way to go, and that the wintel corp thing won't stop all development on the components we miss, as they have done right through to the linux world. It amazes me still that even though these kickass cpus have been on the market for 2 years now, sun-macriomedia-real have stopped everything until wintel would let them continue

---

### Post by FluffyElmo on 2005-05-19
To be fair to the Ubuntu developers, once Hoary was released development shifted to the next version (Breezy). The Hoary repositories see security updates only and are for those who need a stable system. The Breezy repositories see active development and are for those who can tolerate occasional instability (and *large* regular updates) for the latest features.

External repositories that have stopped working for me track debian unstable, not Ubuntu so their dependencies have since moved on from where Hoary is. Moving to Breezy will generally fix any issues. I'm not suggesting you jump to Breezy right now, it still hasn't settled down much according to reports but in another month or so it should be fine. 

*VincentP*: It's going to take some time to get even 32bit setup the way you want it and fully functional. 64bit has those same issues and a few additional issues all it's own. Performance wise I've seen a real performance increase in video encoding and Java development, while basic business apps are too close to call. 

So should you make the jump? It depends what your doing, and what you want from the system. If minimal fuss is paramount go 32bit. If you're feeling adventurous, try 64bit...I've had few real problems and I'm enjoying it :-)

*Everyone*:I haven't tried streaming Real files, I will when I get home. But I have been able to play Real video/audio files (and WMV7) for a while now through Totem-xine or Mplayer. It's probably because I have ffmpeg installed, though I also installed pretty much everything in Synaptic with 'codec' in the name or description ;-)

---

