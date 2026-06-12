---
title: "64bit worth my time?"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mayur on 2007-10-03
Is 64bit really worth it?  I am building a media server soon that in the future will be connected via LAN to a HTPC to host files, but most of those files will still be accessible from other computers in the LAN.  It will also be a print server.

Ive read up on here to find out if 64bit is worth it or not but some of the threads i found are old.  I dont know if most of those problems have been fixed by now or not so I guess I will have to ask it again.

Im either going to get a Pentium Dual Core at 1.6ghz each or a Celeron D at 3.4xghz depending on my decision.

---

### Post by John.Michael.Kane on 2007-10-03
> **Mayur said:**
> Is 64bit really worth it?  I am building a media server soon that in the future will be connected via LAN to a HTPC to host files, but most of those files will still be accessible from other computers in the LAN.  It will also be a print server.
You are telling us what you want to do, however. We will also need to know the exact programs you want to run, As the programs one runs will dictate their problems, if any are to be had.

> **Mayur said:**
> Ive read up on here to find out if 64bit is worth it or not but some of the threads i found are old.  I dont know if most of those problems have been fixed by now or not so I guess I will have to ask it again.

What problems are you referring to?

1) Flash plugin works 
2) Dvd playback works
3) ripping, and transcoding of dvds can be done
4) Wine from my understanding works
5) skype works with the use of a script so I'm told.
6) Mp3 flac ogg is supported with some minor work

> **Mayur said:**
> Im either going to get a Pentium Dual Core at 1.6ghz each or a Celeron D at 3.4xghz depending on my decision.
Depending on the extent of the media server setup eg: How many things it has to do at one time you may honestly benefit more from running dual core, However. If this going to be a one trick server eg: A simple myth setup then you should be able to get a way with the celeron.

In the end no matter how much info is put fourth for you, and no matter how many members feel 64bit is golden, and good to go. You the user will have to make the choice of what is right for you,and you needs.

---

### Post by praxis22 on 2007-10-03
That largely depends on what you're doing.

Media related compression, etc, is often faster on 64bit, and dual core will certainly help. But 64bit or 32bit is more or a lifestyle choice. Do you want white bread or whole wheat?  

Generally speaking 64bit means you have to work a little harder, not much, but a little. If you're not prepared to learn, and/or are not interested in this sort of thing for it's own sake. Then 32bit is probably for you. If not welcome to the world of 64bit. I use it, I like it. YMMV.

---

### Post by Mayur on 2007-10-03
Basically the main purpose of this machine will be to host media files and stream them to other computers.  Basically file sharing.  Im also going to make a htpc so I may need to run mythtv backend so it can host the files or something...

---

### Post by reckless2k2 on 2007-10-03
yeah that's not really going to take advantage of the 64 bit bus. run it if you like but some things will be a little harder to get running but it should really hurt nothing. you'll only gain more knowledge.

---

### Post by praxis22 on 2007-10-03
Then I'd look for a tut on how to setup MythTV there is even [Mythbuntu]("http://www.mythbuntu.org/") look through that and follow it. If they tell you to go 32bit, go 32, if they say 64, go 64. 

Better to have something that tells you how, than to make an arbitrary choice, then retro fit. Unless of course, you live for that sort of thing. 

I think you'll find the really key thing for a server is to maximise throughput, which means optimising your file system, and your network for peak performance. 32bit or 64bit is an afterthought compared to that IMO.

---

### Post by Yellow Pasque on 2007-10-03
I think the question you should ask is, "Why not 64-bit?" If your hardware's capable of it, you might as well use it. It doesn't take extra effort or time to install, download, etc.

There are a few well-known issues that drive people to use the 32-bit version, but they all have fairly easy workarounds.

> I'm either going to get a Pentium Dual Core at 1.6ghz each or a Celeron D at 3.4 ghz

What do you mean by PD at 1.6 GHz each? Is that a 3.2 GHz model (PD 935)? I hope you're going with the PD 9x5 series for the sake of power consumption. I'm guessing you have an older S775 mobo that doesn't support Core(2)-based chips?

Also, I believe that any Celeron D that runs at 3.4 GHz will probably be 64-bit capable as well. Don't quote me on that, though.

---

### Post by steveneddy on 2007-10-03
I just installed 64 bit Ubuntu, and so far it really isn't that challenging. Most of what I need is already in the repos and the rest I'll just compile myself.

:popcorn:

---

### Post by jusmurph on 2007-10-03
Depends what your time is worth isn't it?

---

### Post by Kilz on 2007-10-03
> **reckless2k2 said:**
> yeah that's not really going to take advantage of the 64 bit bus. run it if you like but some things will be a little harder to get running but it should really hurt nothing. you'll only gain more knowledge.
Mythtv encodes what it records. Encoding is one area 64bit gets a nice performance boost. With a server there is less of a problem, because the browser plugins dont matter.


> **Temüjin said:**
> I think the question you should ask is, "Why not 64-bit?" If your hardware's capable of it, you might as well use it. It doesn't take extra effort or time to install, download, etc.

quoted because its the truth. I think people should stop asking should I and instead ask why not.
With a server there will even less reason to worry about 64bit. [There is a mythtv package]("http://packages.ubuntu.com/feisty/graphics/mythtv")  in the 64bit repos , the page says all. That means that all versions have a package. I also checked in synaptic on my machine.

---

