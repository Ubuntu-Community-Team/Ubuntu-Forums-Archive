---
title: "Reinstall default graphics drivers"
date: 2009-07-12
forum: x86 64-bit Users
---

### Post by DitchingMS on 2009-07-12
System: Q6600 64 bit quad core, 2 gb RAM, ATI 2900 graphics, 64 bit Jaunty, NO dual boot


Hi all,
I've posted on here a few times with no success and this is my last attempt. I downloaded Jaunty and installed on a new hdd a few weeks back. Everything worked fine, I downloaded lots of new software from add/remove programs app and the next time I started up I got the loading screen, the moving line and then thrown into a corrupt graphics screen. The system is completely unusable and just freezes on a completely messed up screen. Key presses do nothing and I have to hard reboot. I tried to go into all of the options using grub and tried every option but nothing fixed the problem. I then used the forums to guide me through uninstalling the graphics drivers which I think are the problem. I don't know 100% but I am pretty sure I selected to download and install newer graphics drivers from the upgrade menu. They weren't downloaded from the ATI website, they were the ones in the default programs list.
Anyway, I have tried about 20 methods of finding out which drivers I'm using and then setting the default ones back in place but I can't get anything to work. I can't actually use grub to get into recovery mode because it's password protected and doesn't seem to use my default system password. I have tried using the live cd to boot from but I can't use this to interact with the hdd installation. I am totally helplessly stuck and while I could reformat and do it all again I'm really annoyed that this is my only option AND if it happens again (very likely by the looks of it) I won't know how to repair it. I really want to make Linux work for me and as crappy as Windows is at least I'm fairly confident that I can repair driver issues without having to format my whole hdd.
It's the first time I've used Linux and I just need to be guided through this step by step! Hope you guys can help, and asap as reformatting is coming very soon!
Thanks

---

### Post by philinux on 2009-07-12
Not being able to get into recovery is odd. You must have done something there.

Anyway if you can boot normally lets have a look at your xorg file from the terminal.

```
cat /etc/X11/xorg.conf
```

---

### Post by giancast on 2009-07-13
I understand your frustration. I ran into the same issue. I installed Ubuntu64, everything was running fine, then I decided to update the drivers and my screen got garbaged immediately. This happened only on the 64Bit. I have a second hard drive with the 32Bit version and it is working fine. My solution, not the one that you want to hear was to just reinstall. With my system it takes 14 minutes from the moment I put the CD in and reboot, until I have a working Ubuntu. So instead of pulling my hair trying to figure out what went wrong, a quick reinstall and I was up and running. The person that answer asks about your xorg.cfg, more than likely this file will be empty, mine is. How do I know? Well my 64Bit install does not give me my maximum monitor resolution 1600x1200 it only gives me 1280x1024. My 32Bit from day one gave me 1600x1200, so I was trying to figure out what could be different so I looked at the xorg.cfg and it is empty in both 32 and 64Bit Ubuntus. Give yourself a break, reinstall, there will be plenty of times in the future for you to learn not as a first time user/installer. That is the fun of Linux.

---

### Post by DitchingMS on 2009-07-14
Thanks both for your replies. I would say that's correct about Xorg, as I've gone through the .conf before and found nothing of note. It just has brief, generic pieces of text and nothing which sounds specific to my system. From the research I've done it appears that Jaunty's new X does not use Xorg.conf as an actual prompt to load the drivers, as it used to in the old Ubuntu's - it uses another source to prompt it to load the drivers and xorg.conf is a kind of mirror. If someone could explain how I can simply load up the log file I will try to do that? Just for clarity, I tried to 'fix graphics problems automatically' in the grub menu and this made no difference and when I loaded from the live cd and manually rebuilt the xorg.conf back to its default it did not work (I bet they are the same operation).

To confirm, I am using 64 bit and if I've got a very good reason to I will downgrade to 32 - but having spent a bomb on a new system and having very little to show for it it wouldn't be my first option. I just installed 32 bit Ubuntu on my girlfriend's pc (yes I will have to bail her out when it goes wrong) and thought I would check the .conf - but it reads just the same as mine. I looked through the log but there are a lot of lines which look like graphics drivers and I can't really see what I'm looking for.

As regards recovery, I got into the grub recovery menu, went to a command line but it asked for a password. When I typed in my usual admin password the keystrokes wouldn't register and when I pressed Enter it still rejected my password. After trying about ten variations I gave up but read afterwards that in the command line Linux does not display keystrokes and yet works anyway. However, I couldn't enter the right password regardless. Questions: Is the command line working properly and should it appear in this mode not to accept keystrokes? Do I have the right password? How can I get the right password? If I find the right password how can I set the default graphics drivers back to the way they were?

You make a valid point about just reinstalling anyway but I'm very uncomfortable about this. If I choose to do it I want a dead cert way to backup and restore my system SIMPLY a la Windows System Restore (ok so it's not the best example). Because I want the best system I want to load it up first time and customise it and download apps. How can I reinstall all the gigabytes of free stuff I got for it last time without downloading it all again?

As much as I love the idea of Linux and the user support is great I just can't justify all the messing around. There's no point in it being the most stable OS in the world, fast loading and virus free and free to buy - if I spend more time ***** footing my way through the settings and reinstalling things because of a botched install of some stupid app? It may be a great concept but it really needs some intelligent recovery modes for us noobs.

Please keep me updated guys.

Thanks again

---

