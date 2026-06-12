---
title: "Distribution Jaunty 9.04 (64)"
date: 2009-10-02
forum: x86 64-bit Users
---

### Post by Gael33 on 2009-10-02
It's now almost time for the next distro 9.10 to be released, and being the careful chap that I am who always stays one distro behind for technical reasons hoping that most of the bugs have been ironed out ... is it safe for me as a relative newbie and techno-moron to now move up from 8.10 to 9.04?
Please bare in mind that I cannot fix things when anything goes belly-up. 
I have always upgraded in the past as opposed to a clean install ... am I doing the right thing?

---

### Post by pawhtiobo on 2009-10-02
Hi :)

Test it with the liveCD before you do the upgrade...or install it in a VM.

see ya...

---

### Post by Arup on 2009-10-02
I prefer clean install, you just boot off from Live CD and select manual when it gives you partition option, format that partition and install root at is / on it, leave swap alone, its automatically taken up.

9.04 will be quite a plesant experience and there is no need for you to hold off for subsequent upgrades as team Ubuntu is quite quick to resolve issues. I have faced little if any issues with every new Ubuntu distro, don't expect that in future as well.

---

### Post by Gael33 on 2009-10-03
> **Arup said:**
> I prefer clean install, you just boot off from Live CD and select manual when it gives you partition option, format that partition and install root at is / on it, leave swap alone, its automatically taken up.

9.04 will be quite a plesant experience and there is no need for you to hold off for subsequent upgrades as team Ubuntu is quite quick to resolve issues. I have faced little if any issues with every new Ubuntu distro, don't expect that in future as well.

Thanks for being so positive about upgrading to another Ubuntu distribution.
Another question (open to all) is if I upgrade using the "update manager" will it overwrite all my work that is stored in my Home Folder? If you recommend backing up my personal stuff ... what is the best way to do that? I will hold off the upgrade until I have heard from people who are more experienced than I.
Incidentally, I really enjoy and like the simplicity of Ubuntu and wish to continue using it.
Thanks,
gael.

---

### Post by Crystek on 2009-10-03
Upgrading using the Update Manager will not overwrite or delete anything in your home folder, however, you should back up your important files if something goes wrong during the upgrade (which is highly improbable). One way to do a quick and easy backup is to plug a USB flash drive into your computer and copy your important files to it. Then if you encounter problems during the upgrade and end up having to reinstall Ubuntu, you can plug your flash drive in and get your files back.

---

### Post by Gael33 on 2009-10-03
> **Crystek said:**
> Upgrading using the Update Manager will not overwrite or delete anything in your home folder, however, you should back up your important files if something goes wrong during the upgrade (which is highly improbable). One way to do a quick and easy backup is to plug a USB flash drive into your computer and copy your important files to it. Then if you encounter problems during the upgrade and end up having to reinstall Ubuntu, you can plug your flash drive in and get your files back.

Thanks for the reply, however ... I backed up my "Home" directory onto a separate usb drive and started the upgrade and was immediately confronted with a warning, "AMD fglrx graphics driver not supported by Ubuntu 9.04".
Where the hell do I go from here? I would have thought that after all this time someone would have come up with a fix or an alternative. I must say I was looking forward to the upgrade but this has burst my bubble :(

---

### Post by urugTON on 2009-10-03
Well, it's a bit of a complicated story. 

First, you are doing nothing wrong.  

The problem is in the version of Xorg that comes with Ubuntu 9.04 and the fact that you have an older ATI card.  I had an X300 that was working fine until I tried 9.04.  

I could get the X300 to work with 9.04, but I couldn't get my dual monitors to work properly.  I ended up spending $30 for a more up to date nVidia card that came with vendor supplied drivers.  Both monitors work fine on 9.04.

I spent a while trying to get the new open source drivers to play nice with my older ATI card.  Eventually I decided that I'd just upgrade the hardware.  Some number of months have passed since my failed attempt so you may have better luck.  Also note that I was trying to get dual monitors to work. OTOH, I was doing a clean install.    

Here's a place to start your search.  It's from May 6th and there are some heated words.  

[http://linuxoutlaws.com/forums/viewtopic.php?f=2&t=1631&st=0&sk=t&sd=a&start=0](http://linuxoutlaws.com/forums/viewtopic.php?f=2&t=1631&st=0&sk=t&sd=a&start=0)

For all the grumbling and swearing there were successes:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8046428](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8046428)

Let the forum know what card you have and what monitor(s) you are using.  Maybe someone has already managed to get your combination working, hopefully while doing an upgrade.

Good luck.

---

### Post by 3rdalbum on 2009-10-04
The open-source ati driver will work with your hardware.

There's no "fix" available, because the fglrx driver is proprietary.

I have heard that some users have manually installed an old version of Xorg in order to use the old fglrx driver.

---

