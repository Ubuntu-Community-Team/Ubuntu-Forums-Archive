---
title: "Creating a 32-bit chroot environment"
date: 2006-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrk112 on 2006-11-20
I've just installed Edgy 64-bit and would like to install a 32-bit chroot environment.. I've seen several guides on how to get it up and running but I don't know which would be the best guide to follow.

I actually picked one guide to follow but ran into some errors. So I thought I best ask which guide people use here? Or which one works with Edgy?

Thanks..

---

### Post by ravenon on 2006-11-20
I used the script found at 

[http://ubuntuforums.org/showthread.php?p=904320#post904320](http://ubuntuforums.org/showthread.php?p=904320#post904320)

You need to modify appropriate lines in it to say edgy (instead of dapper). It seemed to work fine. In particular, I installed firefox, flash, etc.

The only problem I have had is I use wireless. At home all is fine; when I am at the office on a different wireless network, I seem to lose my link to the web. I am not sure why.

---

### Post by Kilz on 2006-11-20
> **mrk112 said:**
> I've just installed Edgy 64-bit and would like to install a 32-bit chroot environment.. I've seen several guides on how to get it up and running but I don't know which would be the best guide to follow.

I actually picked one guide to follow but ran into some errors. So I thought I best ask which guide people use here? Or which one works with Edgy?

Thanks..

The Dapper chroot script that ravenon suggested is the easiest way to install a chroot. But be aware that a chroot is not necessary. It is a good idea if you plan on doing development or plan on installing hundreds of 32bit applications. Which most people will never need to do. But if you are not, it is realitivly easy to install 32bit applications without it.

---

### Post by incubus on 2006-11-20
As Kilz pointed out, if you just want to add a few 32bit programs to your Ubuntu 64bit installation, you don't need to set up the whole chroot system for that. He maintains a few packages himself as well as some great HowTos that are easy to follow.

That said, I'm myself a big fan of chroot environments.  I actually have one that I call "sandbox", which I use for compiling and installing things to test, with the idea of not polluting my main environment.  It's not even 32bit, it's a mirror of my 64bit system with all the extra junk.  With this approach, I rarely ever have any dependency, incompatibility, or space problem outside chroot. It's pretty much always a clean install.

If you still want to pursue the route you asked about, the best tutorials in my opinion are these ones:
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)
[http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64](http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64)

ravenon, it would seem odd that the connection problem is related to the chroot environment, as it merely "inherits" the config system from outside. Can you be more specific about what happens or which programs you're using?

mrk112, what error messages are you getting?

best,
incubus

---

### Post by tzulberti on 2006-11-21
Thanks for the tip, I was just looking for the same thing

---

### Post by mrk112 on 2006-11-22
Thanks for the replies..

I ended up following a combination of a couple of guides but I've got it working.. The errors were about locale settings but I've sorted them out..

Now I've installed a few programs I'd like to add them to my Gnome menu.. I know how to add things like Firefox but what command launches the Mplayer gui? If you just run Mplayer then it doesn't load the gui..

Also, how do I get the 32 bit applications to have the Gnome theme I'm using.. They seem to pick up the fact that I've changed the font size from default but the theme they use looks like Windows 95 style..

Thanks..

---

### Post by Biker on 2006-11-22
Last week I was searching too for a chroot 32-bit guide and found this excellent guide.

[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=dchroot.conf](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=dchroot.conf)

---

### Post by incubus on 2006-11-22
> **mrk112 said:**
> Thanks for the replies..

I ended up following a combination of a couple of guides but I've got it working.. The errors were about locale settings but I've sorted them out..

Now I've installed a few programs I'd like to add them to my Gnome menu.. I know how to add things like Firefox but what command launches the Mplayer gui? If you just run Mplayer then it doesn't load the gui..

Also, how do I get the 32 bit applications to have the Gnome theme I'm using.. They seem to pick up the fact that I've changed the font size from default but the theme they use looks like Windows 95 style..

Thanks..

mrk112,

I don't think I can offer much help, because I don't have mplayer installed and I don't use Gnome. Nevertheless, here goes my two cents.

One non-elegant way of finding the command for the GUI would be to install mplayer normally in your non-chroot system and then looking at the menu entry to see the command that opens the GUI.  After figuring that out, you can uninstall it.

A more elegant way of finding that would be:
```

$ dpkg -L <name of the mplayer package>

```

About the themes, I would believe that you need some package that takes care of that. If this is the case, you'd have to make sure you got it installed inside the chroot system.

I would have this list as the suspects for that job.
```

$ apt-cache search gnome |grep theme

```

incubus

---

### Post by mrk112 on 2006-11-24
Thanks for you're help incubus..

I found out that if I launch gmplayer then that gives me a GUI for Mplayer..

I installed the clearlooks gnome engine (because at the moment I'm using clearlooks) and it fixed the theme problem..

So I thought in order to prevent future problems (i.e. if I change theme etc) it might be a good idea to install ubuntu-desktop inside the chroot environment.. What do you guys think? Good or bad idea?

---

### Post by mrk112 on 2006-11-24
Well looks like I've answered my own question, it was a bad idea. I tried installing ubuntu-desktop inside the chroot environment and it ended up trying to start a hardware abstraction layer and a lot of other errors.

So I had another idea instead.. At the moment I have a partition for /, a partition for /home and a partition for swap. What if I add a new partition and install 32-bit Edgy. Then I could install 64-bit again and mount the partition containing 32-bit as /chroot? Then I'd have access to all the 32-bit applications, theme engines, anything..

Does this sound like a good idea or another bad idea?

---

### Post by incubus on 2006-11-24
mrk112,

I'm glad to hear that that one worked.

Installing the chroot in a different partition, instead of a specific directory, should in theory make no difference.  You can put the chroot environment anywhere and the result should be the same.

Now you've hit a point where you're trying to run duplicate programs that need exclusivity in the same computer.  This probably happened when you're installing all the ubuntu-desktop packages, because they have some scripts to run the daemons. Yeah, this is not a good idea.

But did the installation finish?  If it did, I believe you should be able to run the programs normally. (As a side note, make sure you have /proc mounted in your chroot).

Getting back to your idea, one difference that you would have by installing Ubuntu 32bit in another partition is that you would be able to boot into that installation and use it normally. If that's what you meant, you are absolutely right. Perhaps you may need this to install ubuntu-desktop as it is right now.  I don't know if there's a way of apt-getting without starting the daemons.

But then again, do you have that many 32bit programs that you need to run?  In my experience, I only need firefox and rar -- I don't use mplayer and the 32bit codecs.  Besides those, I don't think you'll have to worry that much about it.

best,
incubus

---

### Post by Sukarn on 2006-11-24
I say give it a try and let us know how it goes. I'm curious to know.

---

### Post by mrk112 on 2006-11-25
Thanks for the replies..

While attempting to install ubuntu-desktop inside my 32-bit chroot environment, it tried starting a couple of daemons and also ran into dependency issues with version numbers. I can't remember exactly what happened but in the end it finished with errors saying that it hadn't set up alot of packages. So seen as I was attempting to install ubuntu-desktop anyway, I thought about the idea of installing 32-bit as normal.

I've now set up two installations of Ubuntu Edgy and I believe it works quite well. The only real bug that I've noticed is that in my 32-bit Ubuntu, the splash screen at system startup looks like it should (very nice) but in my 64-bit Ubuntu, it's graphically corrupted. After installing both 32-bit and 64-bit, I set up the 32-bit as /chroot/ and it runs 32-bit applications perfectly. I have no theme / icon / cursor problems (as I did before) and other common problems when using a 32-bit chroot such as no sound in Flash don't seem to be present.

Not only do 32-bit applications work inside my 64-bit installation but I also like the fact that I've got a 32-bit Ubuntu to fall back on in case anything goes wrong. I didn't realize that support for AMD64/EM64T was so new in Debian and I've noticed alot of people complaining about stability issues with applications such as OpenOffice, Sun's Java etc.

I'm in the middle of writing down exactly what I did so that when I need to set it up again, I will know exactly what to do. If anyone wants me to post a link to it then I will.

---

### Post by mrk112 on 2006-11-25
Ran into my first problem and wondered if you guys can help me..

This is what my fstab currently looks like:

/home			/chroot/home		none	bind		0 	0
/tmp 			/chroot/tmp 		none	bind		0 	0
/media			/chroot/media		none	bind		0 	0
/dev			/chroot/dev 		none	bind		0	0 
/usr/share/fonts	/chroot/usr/share/fonts	none	bind		0	0
proc-chroot 		/chroot/proc		proc	defaults	0 	0
devpts-chroot		/chroot/dev/pts		devpts	defaults	0 	0

As you can see, /home and /media use exactly the same method, but 32-bit apps can't seem to access CDs or my USB memory stick (where as they can access my home).. Any ideas?

---

### Post by incubus on 2006-11-25
hey mrk112,

I'm glad it worked. chroot is really something special.

I believe you could try to add a line such as:
```

/media /chroot/media none bind 0 0

```

I don't have a flash drive with me, so I don't know where the USB drives are mounted.

By the way, can you run a test for me?  Can you run "top" inside the chroot and tell me if it works?  I'm curious about mounting proc as proc-chroot.

Thanks,
incubus

---

### Post by mrk112 on 2006-11-25
Thanks for the reply incubus..

I already have that line in my fstab and it doesn't work :( 

I've checked that CDs and my memory stick and they are created inside /media so it should work?!

Can I ask what 'top' does? I ran it and nothing seemed to happen..

---

### Post by incubus on 2006-11-25
Oops, sorry I missed that line.

Ok, it could be proc.  In the good ol' times (Dapper and before), using proc-chroot worked just fine.  Now for some reason in Edgy it's not doing its magic anymore.

Try:
```

/proc /chroot/proc none bind 0 0

```

"top" gives you a list of the running processes and the resources they are taking.  I like to use it to see if /proc is mounted inside the chroot.

incubus

---

### Post by mrk112 on 2006-11-25
Ok I'll change proc-chroot to /proc but what about devpts-chroot? Do I want to change that to /dev/pts.. I have to admit I don't know what it's for :oops:

---

### Post by incubus on 2006-11-25
Leave that there for now hehe.

You may have to restart the computer, unless you're willing to umount and mount those lines manually. : )

incubus

PS: although you could try:
```

$ sudo mount -a

```

---

### Post by mrk112 on 2006-11-25
No change I'm afraid..

---

### Post by incubus on 2006-11-25
Ok, but you solved one problem before it came up. : )

So outside chroot you can see your CD or USB mounted in /media/cdrom, right?

What do you see inside chroot in /media ?

incubus

---

### Post by mrk112 on 2006-11-25
I'm confused, which problem did I solve? Using nautilus I've checked and /proc doesn't match up with /chroot/proc using proc-chroot or /proc in fstab..

If I plug in my USB memory then it puts it in /media/usbdisk.. If I look in /chroot/media then a folder called usbstick is there but it has no contents..

---

### Post by incubus on 2006-11-25
mrk112,

Try this workaround till we find something more elegant. (warning: ugly hack ahead haha)
```

$ sudo mkdir /chroot/media/cdrom0
$ sudo mkdir /chroot/media/usbdisk

```

Put this in fstab:
```

/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/media/usbdisk /chroot/media/usbdisk none bind 0 0

```

Run:
```

$ sudo mount -a

```

incubus

---

### Post by incubus on 2006-11-25
By the way, what you solved with the /proc thing is that before that the programs inside chroot would not be able to see your system resources, which are all in /proc.  Some programs would complain about that (refuse to work). 

incubus

---

### Post by mrk112 on 2006-11-26
Thanks again incubus..

I changed my fstab to point directly at cdrom or usbdisk but it hasn't made any difference.. If I put in my usb memory stick it still doesn't show anything in /chroot/media/usbdisk..

I really don't understand why it isn't working because everything else in fstab is..

---

### Post by Biker on 2006-11-26
> **mrk112 said:**
> Also, how do I get the 32 bit applications to have the Gnome theme I'm using.. They seem to pick up the fact that I've changed the font size from default but the theme they use looks like Windows 95 style..

Thanks..

[http://www.ubuntuforums.org/showthread.php?t=307194](http://www.ubuntuforums.org/showthread.php?t=307194)

---

### Post by incubus on 2006-11-26
> **mrk112 said:**
> Thanks again incubus..

I changed my fstab to point directly at cdrom or usbdisk but it hasn't made any difference.. If I put in my usb memory stick it still doesn't show anything in /chroot/media/usbdisk..

I really don't understand why it isn't working because everything else in fstab is..

that's very odd, mrk.  I tried it myself and it seems to work fine.  I wonder if it has to do with the order of the mounts.  I think you have to do this before mounting the cdrom or flash drives.

Can you try to umount the cdrom and usb drive, mount the directories inside /chroot/media, and then mount the cdrom and usb?  Or the other way around.


incubus

---

### Post by mrk112 on 2006-11-27
I've tried mounting /chroot/media before mounting a CD/usbdisk and after but nothing seems to work.. I just don't understand why it manages to create a directory for usbdisk but not the contents?!

---

