---
title: "[SOLVED] How do I change Login Screen Resolution"
date: 2007-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-12-16
Okay, so most of the issues of my video card have been worked out save one.

When I boot, my LOGIN screen is at 640x480 with something like an 8-bit depth.

How can I get this back to 1024x768 at 24-bit or even 16-bit?  It's really annoying.  The login screen is gigantic, and the font where I type in the username is so small you can't read it.

Thanks.

---

### Post by crjackson on 2007-12-17
Bump

---

### Post by lvleph on 2007-12-17
I hope [this ](http://ubuntuforums.org/showthread.php?t=613190&highlight=logon+screen+resolution)helps you.

---

### Post by lvleph on 2007-12-17
delete

---

### Post by crjackson on 2007-12-17
> **lvleph said:**
> delete

And you wanted to delete for what reason?

---

### Post by crjackson on 2007-12-18
bump

---

### Post by fridgebuzz on 2007-12-18
Mine was that way too when i first installed.  I had to correct my monitor settings to the correct ones and then reboot...hope this helps.

---

### Post by crjackson on 2007-12-18
> **fridgebuzz said:**
> Mine was that way too when i first installed.  I had to correct my monitor settings to the correct ones and then reboot...hope this helps.

Okay, my monitor settings are fine when looking at the splash screen, and looking at the desktop.  That resolution is perfect.  It's ONLY the longin screen when yo type in your username and password.  It's totally retarded...  I know it can be altered but I don't know how.  In fact, I prolly messed it up myself at some point when I tried the 10 billion attempts to get a working splash screen.  I just don't know how to make it 1024x768 like my splash screen is.

---

### Post by Purplecatty on 2007-12-18
same here!!  I've posted on that one too. No one gave me a good "fix it and shut up" solution..  Mine does that too..  Feisty was fine and dandy till I upgraded to Gusty Gibbon.  That's all I got.  I can change resolution on desktop and lock it  (System--Preference--Screen Resolution and set resolution and checkmark on Radio button "Make default for this computer ("your username-Desktop) only".  But it don't help with login screen at all.  I even download "startup-manager" and set it up.  Gave it a run and it doesn't resolve anything!  NOT even editing xorg.conf file helps!  I edited and saved it.  Gave it a run, it did worked for brief second (saw login screen in correct resolution) but it "crash and X11 restarted by itself then finally login screen show in same ol' out of phase resolution.  Frustrated! ](*,):confused:

Anyone help us!!!  We're not alone!!

Catty

---

### Post by crjackson on 2007-12-18
> **Purplecatty said:**
> same here!!  I've posted on that one too. No one gave me a good "fix it and shut up" solution..  Mine does that too..  Feisty was fine and dandy till I upgraded to Gusty Gibbon.  That's all I got.  I can change resolution on desktop and lock it  (System--Preference--Screen Resolution and set resolution and checkmark on Radio button "Make default for this computer ("your username-Desktop) only".  But it don't help with login screen at all.  I even download "startup-manager" and set it up.  Gave it a run and it doesn't resolve anything!  NOT even editing xorg.conf file helps!  I edited and saved it.  Gave it a run, it did worked for brief second (saw login screen in correct resolution) but it "crash and X11 restarted by itself then finally login screen show in same ol' out of phase resolution.  Frustrated! ](*,):confused:

Anyone help us!!!  We're not alone!!

Catty

I'm starting to think about a fresh install, but I really don't want to do that since everything else works perfectly.  I sure wish some old timer with the proper fix to this would sound off in here.  Probably wishful thinking at this point though.

---

### Post by John.Michael.Kane on 2007-12-18
Have you tried adjusting the resolution in your grub menu as well?
```
gksudo gedit  /boot/grub/menu.lst
```

Scroll down the text in editor until you find the following section:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash locale=pl_PL
```

Add the "vga=0x346" option (don't change anything else):

Also have you looked over your /etc/usplash.conf file

Example config:
```
# Usplash configuration file
xres=1680
yres=1680
```

Would you mind posting a copy of your xorg.conf using the below command.

```
gksudo gedit /etc/X11/xorg.conf
```

Last resort is a xorg reset
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Purplecatty on 2007-12-19
I decided to swap 17 inch monitor (I have two 17 inch monitors,  One that had login resolution problem was Acer 76c.  Recently, I just got Gateway2000 Crystalscan from my parent) I tested swapped monitor and login screen look normal now.  I realized that it's Acer 76c had problem.    I agree with you it's better off to leave it alone.  You might try swap another monitor to see if it can maintain it's resolution automatically from Ubuntu's resolution in login and desktop.   My parent's old Gateway Crystalscan have pincushion problem.  I managed to fix it by adjusting pincushion to nearly max and it look almost square but not perfect.  Who cares tho. As log as it work well with Ubuntu on both resolution.  It's worth it.  

 Some people only have one monitor and can't afford to buy 2nd one unless they got it free or cheap price for good working monitor.   Laptop display may have some issue (my Acer Aspire 5040wlmi laptop doesn't have problem with Ubuntu display refresh.  It automatically detect and set to 1280x800 perfectly.)

Thanks
Catty

---

### Post by crjackson on 2007-12-19
> **John.Michael.Kane said:**
> 
Last resort is a xorg reset
```
dpkg-reconfigure -phigh xserver-xorg
```

I tried everything you listed and this one worked perfectly.  I'll mark the thread as closed.  Thank you very much for your assistance.

---

### Post by John.Michael.Kane on 2007-12-19
> **crjackson said:**
> I tried everything you listed and this one worked perfectly.  I'll mark the thread as closed.  Thank you very much for your assistance.

I'm glad you was able to fix the issue with that command. Should you have any further issues please don't hesitate to post them.

---

### Post by shane4stef on 2007-12-19
Hi...Just wondered if anyone has suggested StartUp-Manager to you. You can get it from  the getdeb website. This is EXACTLY what you want I think. Have a look. Its under the category SYSTEM TOOLS. Ubuntu Tweak might be of some use too.:guitar:

---

### Post by crjackson on 2007-12-19
> **shane4stef said:**
> Hi...Just wondered if anyone has suggested StartUp-Manager to you. You can get it from  the getdeb website. This is EXACTLY what you want I think. Have a look. Its under the category SYSTEM TOOLS. Ubuntu Tweak might be of some use too.:guitar:

Already tried that and it didn't work with the LOGIN SCREEN, it was fine for the splash screen.

Problem already solved using
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

