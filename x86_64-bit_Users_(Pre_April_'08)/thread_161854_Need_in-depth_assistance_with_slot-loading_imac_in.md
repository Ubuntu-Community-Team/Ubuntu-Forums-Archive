---
title: "Need in-depth assistance with slot-loading imac install."
date: 2006-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doobie9 on 2006-04-17
Hey, everyone, hope this isn't too long for you. This is my first post here on the forums, sort of my first little 'bean' I suppose. Ironically, I'm drinking coffee as I type this post out in wonderful Openoffice on the very computer I seek assistance with. It is my brother's computer and he needs it to run Ubuntu because it's very important that he understands well Linux for his career goals – and it's very important for me to learn Linux for my own peace of mind (More on this later). 

	The computer is a 600 MHZ iMac slot-load with 774084k total RAM, according to the top command. So that's about right. It has a MASHITA CD-RW drive (Something someone with a slot-loading iMac may be familiar with!) and an Apple USB extended keyboard (Which doesn't work quite right, F12 simulates a right-click!) with a standard Apple infrared mouse, which works quite well.

	On Easter I installed Unbuntu on a second partition, and the dual-booting seemed to work fine until it loaded and then started locking up – then I thought all was lost until I found a helpful post on this forum about disabling dri and then everything booted up fine. Now, not to clump a bunch of issues into one post, but I do believe that many of these problems may have a common source that someone who has installed Ubuntu on a similar machine may be able to recognize, so now – in no particular order, the issues with my Ubuntu Breezy 5.10 PPC installation:

	Things we cannot do:

	#1:  Put computer to display and full-blown sleep. In fact, sleep isn't even recognized as an option. I've downloaded powerprefs like some others have said to do on these forums and that caused the computer to fully black out and lock out (Not even control-shift-F1 would get it out) and the only way out was to press the reboot button on the side of the machine (It was fine after reboot). 
	For his purposes, he needs the ability to set the monitor to sleep while he's downloading big files – like, say, Ubuntu updates and stuff. This computer model has a CRT that gets hot, so this issue tops my list. I don't want this software to wear out the monitor.

	#2: Sound playback problems. Headphones don't work. I put them into the headphone slots in the front of the machine but the sound keeps coming out of the speakers. Another problem is Mp3 playback. Although I have downloaded all the gstreamer stuff, mp3s still do not play in anything (Not Juk, not Rhythmbox etc. etc.) except XMMS – which is buggy and not very usable. For instance, the volume control and EQ windows don't work in XMMS, and dragging the application window around is sluggish and weird and slows down other applications. 

	#3:Can't burn CDs. It recognizes the built-in CD-RW device (The standard slot-loading Apple iMac CD burner of about circa 2001 – if you know about any issues with this I'd appreciate any help). CDs, however, do read. Although Audio CDs aren't quite being recognized. 

	#4: Can't change monitor brightness or geometry. Right now it's quite dim and I need to make sure the room is dark to see much on-screen. And the default geometry is kind of off. This part may be related to lack of sleep control. 

	#5: Can't access Mac-partition files because of permissions. The command used to mount the drive is: 
sudo mount -t hfsplus -o "ro" /dev/hda3 /media/mac
	I hope that's right. I only know a few basic commands. The drive reads fine, but a lot of it can't be accessed because something really funny! Turns out that Linux roughly understands many of the OSX permissions, didn't think it'd do that. Also, it's read-only. I need a command that will allow him to write onto special shared folders (I think it's a good thing that some permissions are recognized, don't want Linux to go to war on OSX!).

	Most of these problems basically boil down to a need for Ubuntu to acquire more control over this machine, and that's why I included them in on relatively big post. So that someone who has tried this OS on the same machine might be able to shed some light on the problem. These all may have a root cause that may be a bug in the system, or an error on my part – I just want to get them fixed and hope to benefit from someone else's experience. I see some of the people here on this forum touting machines similar to this one; 500 and 700 mhz slot-loading iMacs, so I know there is probably a way to properly configure this machine but I just don't know how. So, I am humbly requesting instructions. I am very enthusiastic and willing to learn new things. :)

	Thanks!

---

### Post by linear on 2006-04-17
Can't answer all of these, but here's what I know:

F12 for right-click is what it's supposed to do, believe it or not.

#2: Yes, headphones don't work. Reportedly bug in alsa driver; no fix in sight. Other things that depend on alsa may not work either. Some people have recommended installing the totem-xine package instead of totem-gstreamer for better support of audio formats.

#3: Burning should work, but maybe not in Nautilus. Try GnomeBaker and see if that works for you.

#5: Well, it's read-only because you're mounting it read-only ("ro"). A search should turn up information in the forum on how to do what you require.

---

### Post by Doobie9 on 2006-04-18
I changed ro to rw, and that worked :). Remember that from some man file I read years ago. I used to be very interested in Unix operating systems.

Thanks, I'll try some of you suggestions and see how that works out for me :).

---

### Post by Doobie9 on 2006-04-18
And also, does the alsa drvier screw up all headphones? Because I booted a Dapper Drake Live CD on an iMac G4 and headphones worked with that.

---

### Post by linear on 2006-04-18
It's something specific to the chipset in the iMac G3. It's been written about [here]("https://wiki.ubuntu.com/MartinEricRacine").

---

### Post by Doobie9 on 2006-04-18
Oh, ok. BTW, the Xine engine works for Amarok as well as totem. I think Amarok is much better.

The Xine engine didn't work for Kaffiene, though.

---

### Post by Lanrond on 2006-04-24
[QUOTE=Doobie9]#1:  Put computer to display and full-blown sleep. [/QUOTE]
You don't have this feature in Breezy for iMacs.
[QUOTE=Doobie9]#2: Sound playback problems. Headphones don't work. I put them into the headphone slots in the front of the machine but the sound keeps coming out of the speakers. Another problem is Mp3 playback.[/QUOTE]
Playing mp3 needs decoders. I suggest to browse the forum and try to install some suggested decoders.
[QUOTE=Doobie9]#3:Can't burn CDs.[/QUOTE]
With "Gnomebaker" you should.
[QUOTE=Doobie9]#4: Can't change monitor brightness or geometry.[/QUOTE]
Install "xvidtune". For more insights go [here]("http://ubuntuforums.org/showthread.php?t=83973").
[QUOTE=Doobie9]#5: Can't access Mac-partition files because of permissions.[/QUOTE]
Use "rw" instead of "ro".

---

### Post by Doobie9 on 2006-04-24
[quote=Lanrond]You don't have this feature in Breezy for iMacs.

Playing mp3 needs decoders. I suggest to browse the forum and try to install some suggested decoders.

With "Gnomebaker" you should.

Install "xvidtune". For more insights go [here]("http://ubuntuforums.org/showthread.php?t=83973").

Use "rw" instead of "ro".[/quote]

From the bottom up:

I did change 'rw' to 'ro', even edited my fstab to get it to do this automatically, and in breezy that worked quite well. Except now that I've upgraded it to Dapper the drive mounts right, but I can't write to it. It just keeps mounting read-only. And the 'rw' option is still in the fstab.

I'll be sure to try installing that. But I did adjust the geometry and brightness through the mac os and those settings kept when ubuntu booted.:D

I installed gnomebaker, no success with that. ](*,)

I got mp3s to play using the xine decoder. Non of the gstreamer decoders would work. That may have changed with dapper -- I need to test that.

Evidently, there's still no sleep-mode for iMacs in dapper either :(. I ought to make a bug report on this. :-k

 

 Thanks for responding.:)

---

