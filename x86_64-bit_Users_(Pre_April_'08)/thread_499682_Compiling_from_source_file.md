---
title: "Compiling from source file"
date: 2007-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by dryder on 2007-07-12
Hi,

As I understand it, compiling from a source code produces working code, put simply.

I have a driver source code. If I compile it in 32 bit Feisty it works OK.

Why would compiling it in 64 bit Feisty not produce a 64 bit working result? Source code is a set of instructions - surely the compiler outputs the code in 32 bit or 64 bit depending on the mode one is in? Or is it that the device must understand 64 bit code (which seems logical) - in which case why not produce a 32 bit driver that works in the 64 bit environment?

David

---

### Post by jpkotta on 2007-07-12
Ah, but that is the crux of the matter.  If it really didn't matter to the compiler whether things were 32 or 64 bit, then everything would be available for both.  We would have 64 bit Flash, etc., because even though we don't have the source, Adobe does, and it would be trivial for them to recompile.  

Obviously, this is not how things work.  I think one of the main problems is making assumptions about the sizes of certain variable types.  For example, long ints are 64 bits on 64 bit systems and 32 bits on 32 bit systems.  Maybe a programmer assumed that a long is definately 32 bits, and thus that program will fail on 64 bit systems.  I try to use the types defined in <stdint.h> whenever I need something of some specific bit length.

Your suggestion of compiling a 32 bit program that runs in a 64 bit system (which is absolutely possible on x86 chips), is perfectly valid, and is used quite a bit.  But it only works if everything used by the program is also 32 bit.  That's why you need ia32-libs (it is the bare-minimum for running programs), and possibly other 32 bit libraries.  In the case of a kernel driver, the kernel is already 64 bit, and you can't run a 32 bit kernel along side it.

---

### Post by dryder on 2007-07-13
Hi jpkotta - thanks for replying.

Defining the situation, I'm trying to compile the source code for the Canon LBP3000 - and the extracted folder has a folder in it named 'libsx86_64' which one might reasonably think has something to do with the 64 bit environment. My chip is x86 so I felt it was hopeful.
> ...compiling a 32 bit program that runs in a 64 bit system (which is absolutely possible on x86 chips), is perfectly valid, and is used quite a bit. But it only works if everything used by the program is also 32 bit.
As it runs under CUPS and, as far as I can tell, the same printers are installable in Feisty 64 as in 32 I also felt: i) not every driver was 64 bit, ii) if so then CUPS in Feisty  64 could cope with 32 bit/64 bit drivers.

Trying to use the 32 bit drivers gave me the "Wrong architecture" error - aha, methinks 'I must compile the 64 bit driver then', assuming the folder  'libsx86_64' had something to do with making a 64 bit driver. New unknown: is CUPS 64 bit and 32 bit useable? I can't find the answer to that one. Obviously the h/w must understand it, though ...

A lot of programs in Feisty 64 bit are 32 bit programs (Boinc, efax ... in fact the 64 bit version of Boinc (not in the repository) does not work properly. So - as you say, 32 bit mode is quite possible. (There certainly wouldn't be many scanner drivers in 64 bit native).

Which leaves my printer driver conundrum where? Just waffling I suppose! :-)

I did a lot of research on the net before starting the thread and came to the conclusion that addressing the question of what one might expect to work in Feisty 64 bit is very hard to find, making the move to 64 bit arduous and off-putting.

David

---

### Post by jpkotta on 2007-07-13
Did you try [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#head-39af38a4d6040e3ace3675b50fd392e7882dd804")?

It sounds like others have gotten it working.  From what I understand, printer drivers are usually userspace drivers, so you can use 32 bit drivers with a 64 bit system.  

64-bit isn't that hard...until you have that one piece of hardware that doesn't work.  If you ever have a choice, go with an HP printer, I've had better luck with them.  That said, I run Ubuntu at work and the printer there is a Canon (not your model though), and it was no more difficult to set up than other printers I've used.

---

### Post by dryder on 2007-07-13
Hi jpkotta,

No, :oops: . I had not tried this. I will try it now. Obviously my searches were not thorough enough to find it, which annoys me. Thanks for the link ...

David

---

### Post by dryder on 2007-07-14
Thanks for the link - but I am unable either to fully understand the method [[COLOR="Blue"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit")  or to get the method to work to alien in 32 bit mode under the Feisty 64 bit architecture.

Truthfully, the driver installation is simple (tried it in 32 bit) so it is my lack of understanding or methodology of the alien/chroot part. (I had to use Dapper repository as it seems Hoary is not available).

That is quite a complex way 'just to do alien' on a 32 bit driver in ...64 bit. How many would find it simple or would want so much extra installed on their machines for that one task they have? A simplified method with explanation of "How to alien a 32 bit rpm driver under 64 bit ... " would be really useful.

My symlink would not even work, though I've created them before - so it must be something I am not understanding, methinks.

David

---

### Post by jpkotta on 2007-07-15
Since I have a chroot, I converted the rpms to debs and uploaded them to the wiki.  It would be wise to get your 32 bit chroot working, because they are very handy.  Try [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot).

---

### Post by dryder on 2007-07-15
(I though I had already posted this but I must have just previewed instead of Submitting)

> Since I have a chroot, I converted the rpms to debs and uploaded them to the wiki. It would be wise to get your 32 bit chroot working, because they are very handy. Try [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot).

jpkotta,

How can I express my appreciation enough other than a sincere 'thank you'?

Your chroot instructions are **THE** way to *help explain the steps and what they achieve* rather than the usual 'cut and paste this' which achieves a result but do not help us understand what we are doing. Not that I and others are ungrateful for "cut and paste" help - indeed we are very grateful, but you have gone the extra step and helped me (others too) understand 'why'. I have learned more with your instructions than with any other. Truly a wish others would follow and thereby help us increase our knowledge (those who do explain, thank you to you too!). Thank you! =D>

And thank you also for the deb files and the checksum/md5sum.

David

---

### Post by jpkotta on 2007-07-16
You're welcome.  Give a man a fish, teach a man to fish, etc.  Plus, most people who try Linux are curious and want to learn about computers -- that's how I got into it.  So I always try to explain things behind the scenes.

BTW, if you think I did that debootstrap wiki page, I didn't, but I have contributed to it.  You can thank unknown wiki editors for that.

---

### Post by dryder on 2007-07-21
jpkotta,

I now have a clean feisty 64 bit install on a separate disk so I am back to this printer install.

You said the deb files you uploaded to the wiki needed --force-architecture.

My command was:
sudo dpkg -i --force-architecture cndrvcups-common_1.30-2_i386.deb cndrvcups-capt_1.30-2_i386.deb

As you compiled them in chroot presumably --force-architecture avoids me needing to use chroot for these debs?

Is that correct? I don't know if it is possible to force architecture using the GDedi Package Installer but I am using the terminal for most things.

Many thanks,

David

---

### Post by Kilz on 2007-07-21
> **dryder said:**
> jpkotta,

I now have a clean feisty 64 bit install on a separate disk so I am back to this printer install.

You said the deb files you uploaded to the wiki needed --force-architecture.

My command was:
sudo dpkg -i --force-architecture cndrvcups-common_1.30-2_i386.deb cndrvcups-capt_1.30-2_i386.deb

As you compiled them in chroot presumably --force-architecture avoids me needing to use chroot for these debs?

Is that correct? I don't know if it is possible to force architecture using the GDedi Package Installer but I am using the terminal for most things.

Many thanks,

David

If you are using a i386 chroot , you shouldnt need to force install any i386 packages. The force is used to install i386 packages to the amd64 install. Be very careful about forcing in files, especially if the files exist as 64bit versions. You may end up overwriting a 64bit version of a file and fubar your Ubuntu install. Secondly, a good rule to remember is never , ever , under any circumstances force in libraries.

---

