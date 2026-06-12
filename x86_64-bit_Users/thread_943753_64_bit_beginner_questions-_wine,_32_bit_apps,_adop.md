---
title: "64 bit beginner questions- wine, 32 bit apps, adoption rate"
date: 2008-10-10
forum: x86 64-bit Users
---

### Post by DrRotwang on 2008-10-10
I read the sticky faq about 64 bit, and some of the threads.  Here's what's left of my questions:

If I run ubuntu 64 bit will that have any effect on vmware and/or virtualbox abd/or wine? Like, can I still run winxp 32 in vmware on top of ubuntu 64, or would I have to run xp 64?  Can 32 bit windows apps run over wine? 

From the sticky it says that "there are known ways of getting" 32 bit apps to work in ubuntu 64.  I take it that means it's going to require some "hacking" to do, right?  In other words, not just doing apt-get and 32 bit apps just run... it would be out of the normal easy way of doing things.

If I have 6 gig of memory and I run 32 bit ubuntu, will it at least use 4gb of the memory or will it freak out and go "OMG that's too much ram" and die?

And what is the adoption rate of ubuntu 64 vs 32?  How many ubuntu 64 users are there vs 32?

(And does anyone know if using kubuntu 64 instead will make any difference? I'm assuming no since it's just a window manager.)

thanks all

---

### Post by Sephoroth on 2008-10-10
Kubuntu and Ubuntu shouldn't make a difference as it is merely a different desktop environment (KDE vs GNOME).

I've run Ubuntu x64 releases since Gutsy and haven't had any problems related to WINE or VMWare (though I didn't need the latter of the two much).  The primary difference noted when I ran those was a very large performance gain :).  To answer your question, WINE and VMWare ran 32 bit applications/operating systems fine.

Regardless of how much RAM you have, the computer shouldn't "die".  32 bit Ubuntu releases shouldn't recognize that much RAM though 64 bit releases should have no problem doing so.

The only negative I have faced since switching to 64 bit releases of Ubuntu is crappier Flash support (though this seems to have improved somewhat) and a lack of Java applets.

---

### Post by Kilz on 2008-10-10
> **DrRotwang said:**
> I read the sticky faq about 64 bit, and some of the threads.  Here's what's left of my questions:

If I run ubuntu 64 bit will that have any effect on vmware and/or virtualbox abd/or wine? Like, can I still run winxp 32 in vmware on top of ubuntu 64, or would I have to run xp 64?  Can 32 bit windows apps run over wine? 
Sure you can, I have multiple virtual machines that are 32bit.

> **DrRotwang said:**
> From the sticky it says that "there are known ways of getting" 32 bit apps to work in ubuntu 64.  I take it that means it's going to require some "hacking" to do, right?  In other words, not just doing apt-get and 32 bit apps just run... it would be out of the normal easy way of doing things. That depends, are you looking to run an old 32bit program that has difficulty on 32bit let alone 64bit? Have you done a search [of the package site]("http://packages.ubuntu.com/") to find out if this is an issue?  

> **DrRotwang said:**
> If I have 6 gig of memory and I run 32 bit ubuntu, will it at least use 4gb of the memory or will it freak out and go "OMG that's too much ram" and die? That depends on your hardware and its bios version. Some boards may need to have the bios updated. Others were never meant to see over 4gb. But if your hardware specks are right, yes it should see all 6.


> **DrRotwang said:**
> And what is the adoption rate of ubuntu 64 vs 32?  How many ubuntu 64 users are there vs 32?
Who knows, why not start a poll. This forum is user to user help, I dont think we have counted that yet.


> **DrRotwang said:**
> (And does anyone know if using kubuntu 64 instead will make any difference? I'm assuming no since it's just a window manager.)

thanks all
Yes, you will have to look at that awful kde interface, but if thats what you want.

---

### Post by DrRotwang on 2008-10-10
> **Sephoroth said:**
> 
The only negative I have faced since switching to 64 bit releases of Ubuntu is crappier Flash support (though this seems to have improved somewhat) and a lack of Java applets.

Wow thanks for mentioning that actually, look what I just posted two minutes ago:
[http://ubuntuforums.org/showthread.php?p=5942788#post5942788](http://ubuntuforums.org/showthread.php?p=5942788#post5942788)

I think right there, the lesser flash support might be enough to make me stick to 32 bit.  thanks.

---

### Post by Sephoroth on 2008-10-10
If you require those applications posted in the other thread then you may have a hard time doing such things in Linux (harder in 64 bit than 32 bit).  AIR is still in an alpha phase on Linux and IIRC it is only available for 32 bit Linux releases.  I've heard Photoshop runs decently in WINE but if you need those applications to be running both stable and fast, I just suggest dual booting.  If that isn't possible it might be easier to keep running Windows.

On the other hand, if you have a strong computer, you could just run a VM for Windows XP.  Check [WINE's application database](http://appdb.winehq.org/) to see which programs run well in WINE.

---

### Post by Sef on 2008-10-10
>  					Originally Posted by **Sephoroth** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5942772#post5942772") 				
 				*The only negative I have faced since switching to 64 bit releases of Ubuntu is crappier Flash support (though this seems to have improved somewhat) and a lack of Java applets.*


Flash works fine on my 64-bit system.   It has worked well with Hardy and and Intrepid.

For Java, you can use [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956").   It works with most java sites.

---

