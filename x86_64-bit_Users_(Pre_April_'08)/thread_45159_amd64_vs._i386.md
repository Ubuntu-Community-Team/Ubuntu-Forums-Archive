---
title: "amd64 vs. i386"
date: 2005-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by wing on 2005-06-29
I was wondering how much performance you actually get, and I was hoping that this thread would be somewhat of an informative thread on the matter, so that people can make a decision.

Basically, what are the benefits of using amd64 or i386? What are the failings?

From my experience with Hoary on amd64, and on an i386 chroot, AMD64 has:

> The benefit of running natively on 64-bit and the performance gains that it entails

But are the performance gains so great so as to justify using it over i386?

The benefits of i386 on the same system would be:
> Greatly increased repository availibility (backports in particular),
More up-to-date packages on the ubuntu repositories,
Easier configurability regarding things like Macromedia Flash, mplayer and win32 codecs,
Mono (okay, this is just for me :) but I like using muine a lot)

at the cost of not utilizing the benefits of the new architecture.

I would bid you all to provide any information about the benefits/failings of each choice that you have, such as benchmarks, lectures on the subject, developer comments, whatever you can bring.

I am not sure how, but this somehow managed to post within another thread.

---

### Post by Big Venus on 2005-06-29
Depends on what you do with your system...

On the net alot and using office apps... Go buy a 32bit system...

Graphics and gaming and programming, go buy a 64bit...

---

### Post by wing on 2005-06-29
[QUOTE=Big Venus]Depends on what you do with your system...

On the net alot and using office apps... Go buy a 32bit system...

Graphics and gaming and programming, go buy a 64bit...[/QUOTE]

What I meant was, what is the best option for an amd64 system, installing the amd64 distro, or installing the i386 distro?

---

### Post by dewey on 2005-06-29
If you know what you're doing, or are willing to learn, no reason not to go with 64bit.
If you're lazy, or want the system to "just work" with everything like flash, go with 32bit.

In either, just be sure to use the updated kernels, like 686,k7,and k8.  I never had any visually noticeable speed increase with my system, but my system is greatly uneven.  Amd64 3000+ with 512mb of 2100 DDR ram(Not even supported by my motherboard officially) and an 8mb cache IDE drive.  Not to mention the horrid radeon 9200 se.

---

### Post by FluffyElmo on 2005-06-29
Here are my experiences...though I too have a poor video card so no game results here:( Generally I've found speeds to be very comparable between 64bit and 32bit. 64bit feels a *little* slower starting programs but faster otherwise...though the difference is close enough I may be imagining it ;)

Video encoding performance has been quite good. I've seen 110fps+ doing a straight encode of a DIVX file to MPEG2, less with various filters. DVD to DIVX is ~45fps at default settings, I haven't tried tuning it at all. Performance can vary widely depending on the codec implementation used, but overall scores are very good and much faster than my friends 32bit Athlon.

Also, Java performace is very good. I've noticed boosts with Azureus and Eclipse in particular as well as some code I've developed. However Java seems to use more memory under the 64bit system so there is a tradeoff for the increased performance.

---

### Post by Big Venus on 2005-06-29
Agreed, I like the 32bit one, but knowing that I wasn't using the system's true abilities, I download the 64bit back in Fedora 3 and have been 64bit since.

If it bothers you about not using Flash Player or some other programs you will be alright with 64bit. I tried to use the chroot to give me access to the 32bit form and had problems.

---

### Post by norman_h on 2005-07-01
64bit is the future.

At the moment software is still only just getting used to it.  Whilst lurking around gcc/glibc mailing lists I have come to understand that there is negligable performance difference **at the moment**.  The main difference at the moment is in the way that software handles large ammounts of data, eg large databases.  Given time, gcc4 will improve its compilation techniques and the performance of 64 bit binaries will begin to show their advantages over their 32bit equivalents.

Personally I'd go with the AMD64 instead of the i386 as it appears to offer the best bank for buck into the future...  especially when loads of the AMD CPUs support bi-arch (ie both 64 and 32 bit).  

I'm using an AMD64 in 32 bit mode as some software (mainly openoffice and closed source software) isn't quite ready for 64bit yet as some of the code was written for 32 bit only and needs to be fixed.  Nearly all of the basic GNU/GPL software for a core system is 64 bit ready, when more gcc optimisations for 64bit take place we shall see an improvement.  When OOo is fully 64bit compliant (and regularly released non-beta binaries are available), I'll be making the full-time change.

---

### Post by DRF on 2005-07-01
With most of AMD's range supporting 32bit and 64bit it makes sense to get something future proof. 

I decided to try 64bit Ubuntu (coming from 32bit Debian) and expected to have lots of problems but most of it has worked out the box.

Only 64bit specific problems I've come across so far (none of which bother me particularly) are:
Wine (But sounds like the commerical version can be compiled to work)
Realplayer (Which means a few of the internet radio stations I can't listen to now)
Flash (I don't visit many flash based sites so not an issue)
w32codecs (Not sure what this actually adds support for, I've gotten MP3's and AVI's to work and don't really have much media in other formats on my computer)

Most of those you can get working with some effort or using 3rd party versions, or at a push 32bit chroot. It's still quite common to see downloads of linux apps online still only having 32bit versions but with such large repositories I've not needed to go looking for programs online much.

I would say do your research if your undecided and make sure that any apps you can't live without have been ported. ([http://packages.ubuntu.com/](http://packages.ubuntu.com/))

If you want something thats minimal hassle go with 32bit.
If you can live without a few programs (and I'm sure companies like macromedia will soon start porting to AMD64 offically) but would like to extra performance go with 64bit.

When deciding between 32 or 64 bit Ubuntu I was nearly put off installing 64bit from some of the threads here but I've found it to be a good choice. I don't think it's been any more hassle to setup than 32bit ubuntu. (Except for a few  unsupported codecs)

Daniel

---

### Post by wiraone on 2005-07-02
I tried them all, the 64bit and 32bit versions .. I've tried other 64bit distributions too .. and lastly made my choice .. the 32bit version gives the same performance for my daily usage but with more applications available compared to the 64bit one.

---

### Post by Plankman on 2005-07-12
I've used 32bit Redhat 8 and Fedora Core 2 & 3. Currently I'm using Ubuntu 64bit. I'm very happy with it. Performance wise, it's great. I've just installed the Sun Java SDK 1.5 update 4 64bit and it works like a charm, except that the 64bit has no firefox plugin. There are a few problems like I can't print from OpenOffice and no flash like already mentioned, but 64bit is busy growing. In a few months there'll be more packages ported to 64bit and then it'll be great. At the moment I'm happy with 64bit and I'm not going back. :)

---

### Post by AllenGG on 2005-07-13
Wing, everyone above is right. But, if you bought a 64 bit machine, well.... I have several systems working in my office, a good 32 bit Intel machine with Hoary 5.04 i686, works 'way better than it did with M$ Windows, various flavours.
And a 64 bit system AMD64 Athlon, with 1 gig of memory, bit the bullet as soon as Hoary 5.04 came out, and I needed to use the machine right away. some problems, more software pkx came out, now it's much better than ever expected. Is instant fast ?
Even "mission critical" 5.04 works right off. Things change daily, go with 64 bit.
AllenG

---

### Post by Ubi on 2005-07-20
Instead of chrooting a 32-bit version of linux, would it be possible to use xen to run a 32-bit version?  

Modified:  I just check with Xen and according to [http://www.cl.cam.ac.uk/Research/SRG/netos/xen/roadmap.html](http://www.cl.cam.ac.uk/Research/SRG/netos/xen/roadmap.html) Xen 3.0 which is supposed to come out this month will support: "x86_64 Xen port. A port to Opteron/EM64T is already in progress and will support xen-x86_64 guest OSes with both 32 and 64 bit applications."

---

### Post by FluffyElmo on 2005-07-20
Another option would be qemu, it supports x86_64 as a host environment. The 'Qemu Accelerator' port isn't ready for 64bit yet but it is coming.
[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/) 

Though I have to say, I have a chroot running now and it isn't as bad as I'd heard around here, you may want to give it a try.

---

### Post by negatory on 2005-07-20
I have a chroot and haven't tried the 32bit version.
The 64bit version is excellent in speed (but I have a 3500+ amd64 so that might help a little) and everything that isn't in the repositories I compile it.
One thing I notice is the performance of mplayer between native 64bit and chroot 32bit.In the chroot mplayer takes more time to load movies compared to native 64bit... I don't know if this is a reliable performance test though...
Go 64bit...you won't be dissapointed.
Pedro Carrico

---

### Post by Ubi on 2005-07-21
FluffyElmo, what exactly do you have in the chroot environment?  Do you have a complete distribution with X window and all the applications?  If so, could you give us some tips on how you went about setting it up?  Thanks for your time...

[QUOTE=FluffyElmo]Another option would be qemu, it supports x86_64 as a host environment. The 'Qemu Accelerator' port isn't ready for 64bit yet but it is coming.
[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/) 

Though I have to say, I have a chroot running now and it isn't as bad as I'd heard around here, you may want to give it a try.[/QUOTE]

---

### Post by FluffyElmo on 2005-07-21
After I upgraded to Breezy a lot of stuff broke, including Java. So I basically use the chroot to run Java and Eclipse until they fix the 64bit versions. I also have MPlayer and Firefox/Flash installed out of curiousity as much as anything, though they have been useful for the odd file or website I can't view in 64bit.

They all run well, performance is much better than I would've expected. I created the chroot following the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) 

This took an hour or so to download all the necessary packages but otherwise went smoothly. After installing 32bit Synaptic I also installed the *ubuntu-desktop*, *xorg-common* and *xserver-xorg* packages. And maybe others I've since forgotten, it's been a while and I was more concerned with convenience than disk space. I then installed Java (i586) and Eclipse (32bit version) from the command line, and to my surprise Eclipse ran without a hitch. 

One other thing, I find I never use the *do_chroot* script. I just run *dchroot -d* from a terminal and start my 32bit programs from the command line. It helps me keep things straight and in my opinion setting additional programs up to run via the *do_chroot* script was the hardest part of the procedure and it's easy to run them from the command line.
 
Good Luck, hope it works as well for you as it did for me!

---

### Post by blazko on 2005-07-21
Hello all,

So, I am asking just being curious: I plan to buy a AMD64 PC. Primarily, it will not be a desktop machine but a VDR (Video Disk Recorder). Because using a TFT TV and want to use HDTV also, I want it to load into X/GNOME with auto-started tvtime app (just as I do now with my Celeron based VDR on Debian basis).

From time to time I use it as a surf-station, but do not need flash and that; it shall also be a web/file server also :-)

So, please forgive me these plain stupid questions (fyi: i browsed some 64 repositiries, but was not shure if these were the right ones...):

By installing a fresh Hoary 64...
- do I really get a complete 64bit system?
- with GNOME? :-)
- ALSA and libs there? I just need IEC953 (or so...) optical out support...
- are the main codecs/apps also there (mean MPEG and Ogg/Vorbis for my purposes)? I know that Windows Codes might be a problem, but I do not really need them
- I also need ffmped app+libs and imlib 2(from enlightenment?) for a special VDR PlugIn (GraphTFT)... are they there also?

So, if anyone has Hoary 64 it might be nice if he/she could answer some points or even have a look in his/her package list :-)

For me it is important
a) not to have any 32 libs on the box at all and
b) hopefully do not have to do chroot stuff...

Remember, this shall only be a basic system running X/GNOME and VDR.

If someone has already a VDR running on Hoary and/or the 64bit platform, I would also be very pleased to hear anything on it :-) E.g. is it worth compiling VDR on my own or are Debian packages working? ...:-)

Thanks and kind regards,
Timo

---

### Post by FluffyElmo on 2005-07-22
I haven't used VDR, and I'm not at my 64bit machine right now so I can't answer all your questions. But I'll take a stab at the ones I know and maybe someone else can fill in the gaps. So long as VDR supports amd64 I don't forsee any problems with what you want to do though. Hoary is a pretty quick install as well, so it may be worth just trying it.  

*- do I really get a complete 64bit system?*
Yes. There are a few 32bit libraries for OpenOffice but everything else is pure 64bit.

*- with GNOME?*
Yes. 

*- ALSA and libs there? I just need IEC953 (or so...) optical out support...*
I think it uses OSS by default, but I'm currently using ALSA from the repositories without any issues. Haven't tried the optical out but wouldn't expect trouble...

*- are the main codecs/apps also there (mean MPEG and Ogg/Vorbis for my purposes)? I know that Windows Codes might be a problem, but I do not really need them*
Yes, you have to install libcss2 for DVD playback, and there are some codecs you'll have to add from the repositories but generally I've had great luck with everything but later Windows Codecs. 
[http://amd64.ubuntuguide.org/#codecs](http://amd64.ubuntuguide.org/#codecs) 
[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback) 
[I]
- I also need ffmped app+libs and imlib 2(from enlightenment?) for a special VDR PlugIn (GraphTFT)... are they there also?[/I]
Do you mean ffmpeg? If so yes I have it running and it's very fast. However, the version in the Hoary repositories is reputed to be buggy so I built mine from source without trouble. I'm not sure if imlib 2 is there...I recall installing imglib2 at some point (for transcode?) though so you're probably OK on that score.
[I]
From time to time I use it as a surf-station, but do not need flash and that; it shall also be a web/file server also [/I]
No problems there. Firefox works perfect out of the box, and I have samba working with no more than the usual effort:)

As I mentioned at the start, all in all I think you'd be fine just trying it. Let us know how it goes, I for one have been thinking of getting a TV card and trying Myth or something similar so I'd be interested in people who get it working:)

Good Luck!

---

### Post by jon_gunnar on 2005-07-22
[QUOTE=wing]I was wondering how much performance you actually get, and I was hoping that this thread would be somewhat of an informative thread on the matter, so that people can make a decision.

Basically, what are the benefits of using amd64 or i386? What are the failings?
[/QUOTE]
For me it is really simple. I got one 64 bit system already. And I'm gonna set up a new X2 64 system in a few weeks. Way stay in the past?
There is still missing some apps, but nothing critical for me. Java is easy to compile, the flash I'm just happy to miss.
But I just want to get on, and see no point in waiting any longer. I got the system, I start using it.

---

### Post by blazko on 2005-07-23
FluffyElmo,

Thanks for your answers to my stupid questions!
I have begun to do a dry-run test on my current 32bit VDR with Ubuntu from Scratch. 
Please note that I have a DVB-s full featured card with onboard MPEG decoder and OSD; it is a Hauppauge Nexus-s 2.1/2.2.
Everything is working well except two/three things:

1) VDR Remote Plugin causes a segfault -> replaced using LIRC [ok]
2) OSD support is disabled in Ubuntu Kernel; not avail as module, thus had to recompile the kernel. Although using the Ubuntu .config and sources, nVidia Driver fails (must the inft be recompiled? Then I have to use the ones from nvidia.com i think...)
3) LIRC/Remote problems: /dev/input/event3 is mapped to my RC5 remote attached to my Nexus-s but does not fire events (neither in VDR' OSD nor with evtest /dev/input/event3)...

Btw. this is really getting OT here, perhaps I should open a new thread or even a HOWTO when being successful :-)

Thanks and regards,
Timo

---

