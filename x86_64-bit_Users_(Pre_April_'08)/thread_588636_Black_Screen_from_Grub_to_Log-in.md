---
title: "Black Screen from Grub to Log-in?"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by |2A|N on 2007-10-23
I just did a clean install from Gutsy 32bit to 64bit and now once I chose the kernel my LCD goes black into sleep mode till the log-in screen appears is this normal and if not how do I fix this? Yes I'm a newbie to Linux only been using it about 2 months or so. Any step by step explanation on how to fix this would be greatly appreciated and again this is a fresh clean install not an upgrade :)

---

### Post by ACLerok on 2007-10-23
So what you're saying is that you don't have a splash screen with the bar filling up under the Ubuntu logo?

---

### Post by |2A|N on 2007-10-23
> **ACLerok said:**
> So what you're saying is that you don't have a splash screen with the bar filling up under the Ubuntu logo?

Yep :confused:

---

### Post by |2A|N on 2007-10-23
I have been all over the forums and the net looking for a solution and came up empty, does anyone have a solution? ](*,)

---

### Post by |2A|N on 2007-10-23
I am still able to boot into Ubuntu but I have the same problems you just described, everything is black till the log-in screen appears then all works fine. It's a bit annoying but If there isn't a way to fix it I guess I will have to just deal with it I suppose. this only happens with 64bit the 32bit version doesn't do that so I dunno what the problem is.

Here is my specs

Intel C2D E6420
EVGA 650i Ultra
MSI 8600GTS
GSkill DDR2 800 4GB
Creative ExtremeGamer but using onboard sound

---

### Post by silentrhythm on 2007-10-23
I also have this problem, for a while I was also experience hanging on the black screen. 

Using gutsy 64 bit, with AMD X2 processor / nvidia 8500 series video card

---

### Post by |2A|N on 2007-10-23
Well I'm glad to see I am not the only x64 Gutsy User with this problem. So this could be a potential problem/bug with this Distro in some rare instances!? If anyone has this problem also or you have some clue how to fix it or what might be the possible cause please don't hesitate to post here to help us. Thanks in advanced!

---

### Post by Wuffles on 2007-10-23
I also had this problem.  I don't know how to fix it so that the splash screen is displayed, but I edited grub's menu.lst to change Ubuntu's entry from "... quiet splash" to "... nosplash" to see what was going on before x started rather than have a blank screen.

---

### Post by |2A|N on 2007-10-23
Is there anyone we could contact for technical support about this since no one of this forums seems to know how to fix this or they would have posted by now otherwise!?

---

### Post by crjackson on 2007-10-23
> **|2A|N said:**
> Is there anyone we could contact for technical support about this since no one of this forums seems to know how to fix this or they would have posted by now otherwise!?

Have you tried this [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4]("http://ubuntuforums.org/showpost.php?p=3569987&postcount=4")

It worked on my laptop, still trying on one of my desktops.

It's already been reported as a bug on launchpad.

---

### Post by Therion on 2007-10-23
Lots of people reporting this problem.  Happened to me in fact.  What I had to do to fix it:

Hit Escape during boot to enter GRUB.
Select "Recovery Mode"
You'll see the Kernel load, etc. and eventually you'll come to a command prompt.
When you do enter the following:
```
nano /boot/grub/menu.lst
```
Scroll down to the first instance of Kernel and find the loooong line of code.
Remove "Splash" from that line.
Ctrl+X to Save, answer "Y" to the overwrite, etc. and get back to the command prompt.
```
reboot
```

From there I immediately installed the restricted drivers for my video card, updated and was off and running.

What others have had luck with is editing menu.lst and *adding*** noapic noaplic nosplash** at the end of that long line where I simply removed the word "splash".  One or the other should work.

---

### Post by |2A|N on 2007-10-24
Ok will try this, thanks!

---

### Post by John Jason Jordan on 2007-10-24
> **|2A|N said:**
> Ok will try this, thanks!
I tried it too, but it didn't restore the splash screen. It did display the command line, however. I want to get the splash screen back with the progress bar. In the end it boots OK, but it's hard to tell where things are or if it is hung unless it displays some kind of graphical view of the boot procress.

---

### Post by orange2k on 2007-10-24
It is a known bug in Gutsy: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930)

I think that the detection of the monitor is the problem for usplash not showing up...
I have tried every solution to the problem offered so far, but with no luck...

What bothers me is the fact that Ubuntu developers went to change something that was working so good in Edgy and Feisty...

---

### Post by Saint Angeles on 2007-10-24
i had the same problem... after hours of searching i discovered what the problem was:

reboot in recovery mode and edit your /etc/usplash.conf file with your correct screen resolution.

I have a widescreen monitor and the usplash.conf had it set for 1440x1440 instead of 1440x900

reboot after you edit it, sit back, and breath in the fresh clean air of gutsy gibbon!

EDIT: oops! didn't see the link above my post.

---

### Post by nixx on 2007-10-24
glad i found this thread, i just installed gutsy 64bit last night over 32 bit feisty on my laptop and when this problem appeared on first boot after install, it didn't exactly instill me with confidence for gutsy, but as long as it's fixable.... must try it tonight when i get home.

---

