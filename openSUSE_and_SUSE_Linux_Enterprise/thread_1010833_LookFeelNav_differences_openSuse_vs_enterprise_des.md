---
title: "Look/Feel/Nav differences openSuse vs enterprise desktop?"
date: 2008-12-14
forum: openSUSE and SUSE Linux Enterprise
---

### Post by xarte on 2008-12-14
I had a look at the demo on the Suse site, and it looked pretty swish - loved the three-D desktop cube.

But I lasted about 15 minutes on openSuse. Couldn't find anything I wanted, it just seemed awkward compared to Ubuntu. I wondered if there was much difference between various editions and whether I'd be happier with a professional desktop or if I should just stick with Ubuntu. Not so many bells and whistles but its interface seems to make sense to me.

---

### Post by Growbag on 2008-12-15
Did you try the KDE or the Gnome version?

Fifteen minutes is no way near enough time to get the feel of a distro in my experience, you need to spend at least a week.

And the hardest thing is that you really have to be in the right frame of mind as well.  By that I mean going into it with the mindset of "I just want to see if there is any fabulous feature that will make me want to switch", never works because you are simply comparing what you don't recognise, to something that you are familiar with.

If you find yourself thinking "doing xx is so much easier in yyy distro", then just forget it and go back to yyy distro because you will be just wasting your time.

I'm not having a go at you, or being condescending, but you really have to do it with an open mind. Something that is quite hard to do.

I always start with a clean install of the new distro, then I have a list of all the applications that I really NEED to use.  It they are not available, then I look for provided alternatives and see if I can live with those instead.

Of course you will then need to know that the distro supports all your hardware.

Next try customising it to your tastes, sort of the "icing on the cake".

Use it exclusively for a week or so, and you will then start to find out what you like, and what you dislike.  And also maybe find different ways of doing the same job, ie in opensuse I like to refresh my repos and do updates using the command line "zypper" programme instead of the GUI version because it's faster and less complicated.

First opinions are only "skin deep". More often than not, the real beauty is in the details, something that unfortunately takes a little time and commitment to discover.

So relax, take your time, have fun, and use the distro that you feel most comfortable with.  There is no "Holy Grail" Linux distro, it's all down to YOUR personal preferences :).

---

### Post by xarte on 2008-12-15
Thanks Growbag. Good advice.

It was the KDE version. I really didn't give it a chance at all, I'll admit! That initial disorientation really threw me, and it seemed a bit ugly compared to Ubuntu - though I should know better than to be swayed by a pretty gui, since it's whats underneath that matters. But then the commercial edition did look glitzy!

Great idea about noting down essential apps. 

I have to use the propietary ATI and Broadcomm drivers but these seem fine with most distros. I'll have to look into the AMD64 thing to find out about the differences. 

I think I need another computer. I need to have this one working, which doesn't really give me much time and space to play. I really want to experiment with some bare-bones Linux - Arch.

I should have a go at VirtualBox.

---

### Post by ibutho on 2008-12-15
The SLES/SLED versions are pretty much similar to openSUSE. Version 10 of SLES/SLED is primarily based on openSUSE 10.1, but has obviously been polished up and got a lot of bug fixes over the years. I agree with post 2, when trying out a new distro, you really need to approach it with an open mind and give it time.

---

### Post by Growbag on 2008-12-16
I bought a really useful thing for playing with distros, it's a USB dongle that takes those tiny micro SD cards.

I bought a stack of 8gig microSD cards, and simply insert a new one into the dongle each time I want to try a new distro.

Unfortunately they are quite expensive, and you can probably pick up 4gig USB sticks a lot cheaper, but they take up more pocket space.

I can then simply boot and run an entire distro without having to touch my hard drive :).

It runs a little slower than a hard drive of course, with short pauses when accessing the "disk", but it is a very flexible system and you get to run a fully functional OS, rather than a cut down virtualbox machine.

Also very handy (and cool for showing off) to carry with you and boot on any machine (that allows you to boot from USB of course!) that you find while out and about :).  Just set the video mode to "vesa" and you have a portable OS!

---

### Post by xarte on 2008-12-17
Oh I was just eyeing some memory sticks today.... actually my laptop has a built in multicard reader (sadly NOT the old Flash card I have lying about) so that could work pretty well. I'll have to see if Linux is talking to it or not. Now that I think about it, I DO have one of those small SSD cards from my old PDA.

Funnily enough I just installed VirtualBox. Not quite as plugnplay as the magazine said - had to add some packages. I THINK it's working now, just waiting for some updates and will have a play later. Not much memory though.

The APC mag has a tutorial on creating a RAID array with a bunch of memory sticks and a USB hub so I thought I might have a play with that. 2g ones are cheap - 8gig will set you back seventy bucks. ouch.

:-k Oh could I ask another dumb newbie question: with virtual box or using a thumb drive, can I do a ground-up install of Arch (or slackware or whatever I'm playing with) just as though I was installing it on an empty hard drive then?

 I'm dead keen to experiment, but this install of Hardy seems nice and stable (the webcam is even working) so I kinda don't want to mess with it.

(just thought: I guess the card reader is really a peripheral it won't boot from? .. better go google....)

---

### Post by Growbag on 2008-12-17
You might have a problem with the card reader, I have had limited success in simply reading those things, from working perfectly (ASUS laptop), to complete system freeze on insertion (HP laptop).

That's why I bought an SD card to USB adapter, as USB is much more universal and simpler standard.

Plus if you get the microSD cards, you can also use a micro to normal SD adapter for use in cameras/computer, so you get the best of both worlds.  Then you can also use them in your mobile phone as well :).

I was looking at a 16gig microSD card in Officeworks last week, although the price was higher than 2x8gig cards, it was still quite tempting.

Webcam drivers are kernel based, the reason your camera is now working with the latest version of Ubuntu is that it has a slightly more uptodate kernel.  This is also true about card readers and other devices.  Generally the better device support comes with later kernels.  One reason I never seriously adopted PC LinuxOS. it uses an older kernel and has no support for my wireless card.

Of course you could simply (simply?) download, compile, and install the vanilla kernel from kernel.org, but then you would lose some distro-specific features.

But it certainly is fun playing around ;).

As for your question:

*Oh could I ask another dumb newbie question: with virtual box or using a thumb drive, can I do a ground-up install of Arch (or slackware or whatever I'm playing with) just as though I was installing it on an empty hard drive then?*

Yes, you can.  Just be careful where the distro puts the GRUB bootloader.  You will want it on the USB stick, NOT on your hard drive.  That can be a bit hard to figure out with some distro's installers, so be careful.  It won't (read as: SHOULDN'T!!!) mess with your current hard drive installation, but if it doesn't detect all your current OSs in menu.lst, then you will have to rebuild them.

As a complete safeguard against that behaviour, and to make things simpler, I simply remove my hard drive when installing onto a USB stick.  Then there is no doubt.

And it is NOT a dumb question, the only dumb question is the one you didn't ask because you thought it was too dumb to ask :D.

---

