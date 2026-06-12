---
title: "Install from DVD, -not- LiveCD!"
date: 2008-01-05
forum: openSUSE and SUSE Linux Enterprise
---

### Post by SomeGuyDude on 2008-01-05
Okay, now obviously no bit of advice like this is universal, but here's something I found.

I put the 10.3 LiveCD in (the KDE one), and while it installed and ran and I enjoyed it, it was a buggy mess. So I decided to try again, this time with the big honkin' DVD, and by gum it was dynamite despite the longer installation process and more disk space used.

So use the LiveCD to get a feel for OpenSuSE, but if you want to install the thing, take the time and download the DVD. It makes an already dang nice OS a treat. I might go to this thing full-time.

:guitar:

---

### Post by Incense on 2008-01-05
I have a live install running on my other system that I have had not issues with (Other then the community repo URL),  but I did encounter a few strange quarks on my notebook. Like you I reinstalled with the DVD, and all was well. That's interesting, I wonder what they did different?

---

### Post by SomeGuyDude on 2008-01-05
I'm curious about that myself. The goofiest things would not work right, like the system clock always had me on GMT off the LiveCD. And Compiz worked a hell of a lot more smoothly. Confusing stuff.

---

### Post by RebounD11 on 2008-01-07
Isn't  the installer from the live cd a lot like Ubuntu's installer? I remember the gnome live cd was sth like that. I hate that installer, I can't configure anything during the installation and with ubuntu I couldn't do it that easily even after installing... anyway the live cd install is or should I say was for me a disaster. I liked about openSuSE that I could configure my printer and my scanner during the installation and not worry about it later...

Even in Fedora I can do sth like that at the first boot.

---

### Post by 67GTA on 2008-02-02
Is there any big differences between CD/DVD other than package selection and what you guys have stated? I know the DVD comes with the non free stuff unlike the CD. After installing it on my daughter's Dell desktop, I thought I would try it on my HP desktop. Since I've learned how to use zypper, and the introduction of the "one click install", Opensuse is looking really good to me right now. I have been getting increasingly aggravated with Kubuntu's buggy behavior, and lack of development. I know Opensuse has always been big in pushing KDE. The only thing I will miss is the debs:)
How well does alien conversions work on opensuse?

---

### Post by Incense on 2008-02-02
> **67GTA said:**
> Is there any big differences between CD/DVD other than package selection and what you guys have stated? I know the DVD comes with the non free stuff unlike the CD. After installing it on my daughter's Dell desktop, I thought I would try it on my HP desktop. Since I've learned how to use zypper, and the introduction of the "one click install", Opensuse is looking really good to me right now. I have been getting increasingly aggravated with Kubuntu's buggy behavior, and lack of development. I know Opensuse has always been big in pushing KDE. The only thing I will miss is the debs:)
How well does alien conversions work on opensuse?

Alien works great! I use it all the time to convert DEBS.

 The CD has a problem with the community repos, and a couple other things, but I've had it working alright on one of my systems.

---

### Post by 67GTA on 2008-02-02
I used the live cd to install it on my daughter's Dell. I haven't noticed anything wrong yet except for the community repos bug. I just added them manually. I didn't know if it was worth downloading all those GB's. I don't use a lot of the stuff that comes with the DVD anyway. I would only add a few apps/games, and the non free stuff to the CD install. I'll give the CD a go tonight.

---

### Post by Incense on 2008-02-02
> **67GTA said:**
> I used the live cd to install it on my daughter's Dell. I haven't noticed anything wrong yet except for the community repos bug. I just added them manually. I didn't know if it was worth downloading all those GB's. I don't use a lot of the stuff that comes with the DVD anyway. I would only add a few apps/games, and the non free stuff to the CD install. I'll give the CD a go tonight.

The system just feels a bit more stable on the DVD install, that may just be me though. I have one computer that is running fine from a live CD install, so if it's working, then feel free to save your bandwidth. Everything is in the repos anyway. I do like how you can customize your apps during install on the DVD though

---

### Post by snakeeyes on 2008-02-02
I installed from the single kde cd, not the live one and the system is fine here. I think maybe its because its the first time opensuse made a live cd so they might be having some problems. What is the community repo bug u all r talking about?

---

### Post by Incense on 2008-02-02
> **snakeeyes said:**
> I installed from the single kde cd, not the live one and the system is fine here. I think maybe its because its the first time opensuse made a live cd so they might be having some problems. What is the community repo bug u all r talking about?

When you go to YaST, and select Community Repos, you get an error saying "No URL is defined" or something like that, and it kicks you back to YaST. I posted the fix in the forums somewhere if it's bugging you (which is doesn't sound like it is). I know SomeGuyDude was really the one having problems with the Live CD install, which is why he started this thread.

---

### Post by snakeeyes on 2008-02-02
> **Incense said:**
> When you go to YaST, and select Community Repos, you get an error saying "No URL is defined" or something like that, and it kicks you back to YaST. I posted the fix in the forums somewhere if it's bugging you (which is doesn't sound like it is). I know SomeGuyDude was really the one having problems with the Live CD install, which is why he started this thread.
oh ok, no I never had this problem, I downloaded it the day it was released. Hey I still haven't upgraded to kde 3.5.8 think I need to cause 3.5.7 s working flawlessly, haven't had any bug except that in konqueror I can't play anything with the netscape plugin. Anyone else had that?

---

### Post by snakeeyes on 2008-02-02
What have most of u done about the konqueror flash plugin problem? I heard Novell will release a patch soon.

---

### Post by Incense on 2008-02-03
> **snakeeyes said:**
> What have most of u done about the konqueror flash plugin problem? I heard Novell will release a patch soon.

Use FireFox. ;) Reading the suseforums, it looks like the patch has already been pushed down, so you may just want to run the updater in YaST to make sure you have all the latest updates. 

I hear you can also use the official KDE3 flash from the KDE3 repo,

```
http://download.opensuse.org/repositories/KDE:/KDE3/openSUSE_10.3/
```

 I believe if you upgrade to 3.5.8 you would automatically receive that last update.

---

### Post by snakeeyes on 2008-02-03
Thanks that fixed that but whenever I use nspluginviewer to preview a movie downloaded from youtube then nspluginviewer crashes otherwise flash works perfectly.

---

