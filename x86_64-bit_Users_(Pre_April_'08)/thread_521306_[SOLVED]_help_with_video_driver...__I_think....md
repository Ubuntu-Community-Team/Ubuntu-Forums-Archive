---
title: "[SOLVED] help with video driver...  I think..."
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jeremy1138 on 2007-08-09
I have an hp laptop with the amd turion uprocessor and I have the ati radeon xpress 200m video card.  I am running ubuntu fiesty on this laptop(it's a dual boot system with windows xp and ubuntu on seperate partitions).  Anyway...  It was working fine until i started messing around with trying to get 3d window managers to work yesterday.  I tried using the beryl one...  I think that was what it was called.  At any rate, I couldn't get the window manager to work so I tried to find a driver for my video card that would work and I came across a program called envy.  I tried this program a few times clicking both the install ati driver and uninstall ati driver and it didn't appear to work.  I then tried restarting my computer...  and that's when I ran into real problems...  My computer won't start gnome at all now; all I can get is a command line which I really know nothing about...  Apparently linux is missing a module because of all the screwing around that I did with my video card driver?  If anyone can help me with this it would be wonderful because I really don't want to have to reinstall linux and then mess around with getting my wireless card to work again...  Also if anyone has any idea how I can PROPERLY install my video card driver that would be great too.  Again my video card is an ATI RADEON 200m in an hp laptop computer...  My computer model number is dv5020us.  Thanks in advance for any help anyone can give.  :-)

---

### Post by dabl on 2007-08-09
Boot recovery mode (to the command line), log in, and enter ```
sudo envy -t
```and re-install your graphics driver, including saving changes to xorg.conf.  When it's done, shutdown and restart and you should be able to boot normally.  I'll cross my fingers ...  :)

---

### Post by jeremy1138 on 2007-08-09
dabl, I tried that command yesterday and, for some reason, envy isnt working...  I don't think it can find the driver for my video card...  I think that's why I have this problem.  Is there some way I can get this working without using envy?

---

### Post by dabl on 2007-08-09
When you say "isn't working", do you mean Envy doesn't run when you enter the command as I wrote it, or do you mean it seems to run fine but then your video is still borked?

---

### Post by jeremy1138 on 2007-08-09
Envy seems to start just fine but gets some sort of error when I try to install the driver...  I believe it says md5 error...  I'm pretty sure that the reason I'm having this problem is because I tried to install the driver with envy, but it didn't work, and then I uninstalled the driver with envy thinking that it would fix the problem.  The uninstall obviously worked but now I believe that I have no video driver.  The startx command doesn't work to start gnome... All I get is errors.  I'm really a novice at this...  I hope I'm giving you the right information...  Thanks for your help.

---

### Post by dabl on 2007-08-09
An md5 error suggests a problem with a downloaded file -- probably Envy is grabbing a driver file and then checking it and it's not checking out as per its md5 checksum value.

OK, I don't know squat about ATI drivers, but probably we can get you back to a functional GUI by reconfiguring the x server.  I can't tell for sure what you've tried -- I have 2 paths to offer you:

1. ```
sudo dpkg-reconfigure xserver-xorg
``` and choose "YES" to the first question, regarding auto-detecting your graphics chip.  If you go through the script this way, and it still doesn't work right, then

2.  ```
sudo dpkg-reconfigure xserver-xorg
``` and choose "NO" to the first question, and then choose "VESA" on the second question, and finish the script.

Either way, when you finish and it dumps you back to the command line, you enter ```
startx
``` to restart the x server and get a GUI login.  :)

---

### Post by jeremy1138 on 2007-08-09
Dabl, thank you very much for your help.  I can't try this right now because I'm actually at work but I'm going to print this out and try it when I get home this evening.  I'll let you know if it works!  Thanks again!

---

### Post by dabl on 2007-08-09
> **jeremy1138 said:**
>   Thanks again!

Sure --- hope it helps.  That dpkg-reconfigure command is a good one to remember/write down somewhere.

But, try Envy again one of these days.  It's a real labor-saver on my system.  I would think that md5 checksum mis-match is a temporary issue with the ATI driver.  You'll want the ATI driver, not the VESA driver, in the longer term.  :popcorn:

---

### Post by jeremy1138 on 2007-08-09
The sudo dpkg-reconfigure command didn't work so I tried the envy program again.  It kina worked in that I can get into gnome now but it isnt working properly.  The ati driver isnt being used as far as i know.  I can't get the widescreen resolution on my laptop either.  So I tried to use the ati driver installer file name: ati-driver-installer-8.16.20.run and when I try to start it up I get an error that says 'Could not open the file /home/jeremy/Desktop/ati&#8230;ler-8.39.4-x86.x86_64.run using the Western (ISO-8859-15) character coding.'... What do I do about this?

---

