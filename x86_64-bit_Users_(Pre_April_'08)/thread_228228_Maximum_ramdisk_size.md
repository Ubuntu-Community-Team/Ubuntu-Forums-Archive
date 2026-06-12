---
title: "Maximum ramdisk size?"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by eskwayrd on 2006-08-02
I've got a Dell PowerEdge 2900 with two Xeon processors and 24 gigs of ram (yes, 24 gigabytes of ram :-).

I want to create a large ramdisk to run an application that is fairly disk intensive that currently works on a fileset of about 9 gigs worth of data. Running the app from disk is fine except that it's too slow for interactive (ie web) use.

Unfortunately, I only seem to be able to create a ramdisk of at most 512 megs, and that's with the default 1k block size. I'm guessing that if I changed the block size to 4k, I could get a 2 gig filesystem, but that makes me suspect that I'm running into a 2 gig file limit somehow.

I've installed Ubuntu 6.06 for i386 systems, and that may be part of the problem: it's built for 32-bit processors.

Does anyone have any pointers/advice (other than 'do it some other way than using a large ramdisk')?

---

### Post by eskwayrd on 2006-08-04
Just an update, I've since installed Ubuntu 6.06 for AMD64 and switched kernels to the amd64-xeon variant. Still, I cannot get a functional /dev/ram* larger than 512megs with 1k block sizes. I did manage to get a 2 gig ramdisk to work with 4k block size, but no larger.

I poked around in the kernel source (I'm no C programmer, but I can get the gist of what's going on), and it looks like tha size of a ramdisk is contained in an int, so unless someone can point out something I've missed, it looks like I've confirmed that /dev/ram* can only be up to 2 gigs in size.

While poking around in the kernel source tree, I noticed the documentation for tmpfs. That seems to work, at least for allowing a large ramdisk. I setup a 20gig tmpfs mount, and sure enough, it let me stick 20 gigs in it.

Unfortunately, the performance of tmpfs appears to only be about 30 percent better than using a hard drive. I kind of expected a least one or two orders of magnitude better I/O speed. I've only just got this far, so I'll have to do some more performance testing to verify the situation.

It would be nice if anyone with experience doing this stuff with /dev/ram* or tmpfs or whatever else works could chime in with some advice.

---

