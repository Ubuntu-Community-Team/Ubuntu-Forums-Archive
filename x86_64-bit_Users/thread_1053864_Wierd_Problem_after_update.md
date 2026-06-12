---
title: "Wierd Problem after update"
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by mc6415 on 2009-01-29
I ran an update last night, and since rebooting this morning I keep getting graphical corruption on screen after the loading bar, however when I pressed escape at GRUB I decided to try a previous kernel, now when using this it boot's with no problems at all, no I'm wondering is there a way to either 'roll back' an update or tell my ubuntu to boot with the previous kernel version?

---

### Post by caljohnsmith on 2009-01-29
If you first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
If you change the line that says "default X" where X is a number, that determines which entry in your Grub menu gets booted by default if you don't do anything on start up. So if the kernel that works OK is say the 3rd entry in your Grub menu, you could change the default line to "default 2" since Grub numbering starts counting at 0, not 1. Thus:
```
default 0 --> 1st Grub entry
default 1 --> 2nd Grub entry
default 2 --> 3rd Grub entry
...etc.
```
Hope that helps.

---

### Post by mc6415 on 2009-01-29
> **caljohnsmith said:**
> If you first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
If you change the line that says "default X" where X is a number, that determines which entry in your Grub menu gets booted by default if you don't do anything on start up. So if the kernel that works OK is say the 3rd entry in your Grub menu, you could change the default line to "default 2" since Grub numbering starts counting at 0, not 1. Thus:
```
default 0 --> 1st Grub entry
default 1 --> 2nd Grub entry
default 2 --> 3rd Grub entry
...etc.
```
Hope that helps.

Thank you very much, that sorted my problem out completely :D

---

### Post by GordonPMartin on 2009-01-31
Thanks for this!  I had exactly the same problem at the same time as the first poster.

But I'm a new user, could you please enlighten me on what is going on here (or perhaps there is a document I can read)?:
[LIST]
[*]Why did a system update cause this to happen just to us?
[*]Am I now out of date until the next update?
[*]Or will this recent update get re-applied to me in the next day or two?
[/LIST]

I'm writing a blog about my experience with Ubuntu ([http://VistaVitals.blogspot.com]("http://VistaVitals.blogspot.com")) and will naturally be mentioning this incident.  I'd like to be as accurate as possible about what happened and the impact it will have on me and my system.

I had been banging away on my system the day previous to the system update.  I had force-installed a 32-bit package on my 64-bit system in an attempt to get Citrix ICA to work (following instructions).  I had also added a repository in order to install Wine (also following instructions).  It was shortly after the Wine install that I noticed the 24 updates and let them happen - then rebooted as requested and crashed during boot...


Thanks,

Gordon

---

### Post by caljohnsmith on 2009-01-31
Gordon, are you just having problems with the new 2.6.27-11 kernel? Have you tried booting a previous kernel like the 2.6.27-9 or 2.6.27-7 kernel from your Grub menu?

---

### Post by GordonPMartin on 2009-01-31
Yes, 2.6.27-9 works just fine from the grub menu.

My problem is solved, but I now have many questions in my mind.  I don't know how often this kind of incident happens, but I imagine this kind of recovery is no big deal for you Linux types.  I'm looking at this with an eye to usability for neophytes or for my user community at work (can I ultimately maintain this for 5,000+ people).  I'm not so sure...

I guess the update mechanism will see that 2.6.27-11 is installed (even though I am not using it) and not attempt to redeploy it?  I imagine that I will eventually learn to control the update process so I can vet updates in my environment before "normal" users receive it...

---

### Post by caljohnsmith on 2009-01-31
> **GordonPMartin said:**
> 
I guess the update mechanism will see that 2.6.27-11 is installed (even though I am not using it) and not attempt to redeploy it?  I imagine that I will eventually learn to control the update process so I can vet updates in my environment before "normal" users receive it...
I'm not sure what you mean by "redeploy" it? If the 2.6.27-11 kernel is giving you grief, you can simply uninstall it if you want, and just stick with the 2.6.27-9 kernel without any problem. But having the 2.6.27-11 kernel installed doesn't mean it will be used--you decide which kernel to use on start up in the Grub menu. So having 2.6.27-11 installed is not a problem, but you might as well uninstall it if it doesn't work with with your setup. If you go into Synaptic, you can select the "linux-image-2.6.27-11-generic" package and uninstall it. Also, when you download updates, the updater program gives you a list of the packages it is going to download, so you could always uncheck any packages you don't want. Is that maybe what you are looking for?

---

### Post by GordonPMartin on 2009-01-31
Good advice about using Synaptic to remove the -11 kernel.  I guess I was concerned that Synaptic wouldn't know whether or not I had received the kernel in the past and maybe try to install it once again.  I don't know how it tracks these things.  It sounds like it is intelligent enough and I won't have to deal with it again...

Thanks for your help!

---

