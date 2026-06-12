---
title: "Dual Boot 64-bit and 32-bit"
date: 2009-02-13
forum: x86 64-bit Users
---

### Post by jamesrl on 2009-02-13
Is there a way to dual-boot so you have a 64 bit and 32 bit ubuntu 8.10 installed?
I have intel core 2 duo processor and have been happily running in 64 bit linux for a while now.  99% of the stuff I do works in 64 bit mode, and works faster (I do lots of scientific computing with 64 bit floats).  Due to a long story (see below), I need a real 32 bit version of linux running on my laptop.

So I partitioned a section of my hard drive off, downloaded and installed 32 bit ubuntu 8.10.  However, I just found out the hard way that the /boot doesn't differentiate between a 32-bit and 64-bit versions of 
abi-2.6.27-11-generic
config-2.6.27-11-generic
initrd.img-2.6.27-11-generic
System.map-2.6.27-11-generic
vmcoreinfo-2.6.27-11-generic
vmlinuz-2.6.27-11-generic
so all of my 64 bit boot files were lost.  So I'm pretty sure I can get a 64 bit and 32 bit version running if I use different ubuntu versions 8.04 vs 8.10, but this seems like a big problem.  [At the moment I'm trying to just get my 64 bit version working again.]

LONG STORY: I want to install the student version of matlab, which I then bought, but later found out that the student version is only available in 32 bit mode (despite a 64 bit version of matlab existing).  Now using 32 bit libraries, I was eventually able to get matlab itself running though it was giving exceptions as it kept trying to run in 64 bit mode and use 64 bit java, etc.  However, I couldn't install  add-on packages like [wavekit]("http://www.math.rutgers.edu/~ojanen/wavekit/node5.html") that I need to use.

---

### Post by Yellow Pasque on 2009-02-13
Do you have a seperate /boot partition? If so, did you tell the 32-bit install to use it? The next time, explicitly tell the installer not to use the /boot partition (this will put the /boot files in the same partition as the 32bit install)

As for getting your 64-bit /boot files back, I'm not sure how you would go about that without reinstalling. You could download the kernel and extract the boot files directly: [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb) , right-click on the file and open it with "Archive Manager" (if Archive Manager/file-roller doesn't want to read .deb's, install 'binutils' and 'ar'). All of the /boot  files are there except for initrd, which is generated when the .deb is installed. I don't know if it's possible to generate one without actually having the appropriate kernel modules installed (and I doubt the 32-bit one will work).

If you don't mind foobar'ing your 32-bit install, you could try to force install that .deb on your 32-bit system.

---

