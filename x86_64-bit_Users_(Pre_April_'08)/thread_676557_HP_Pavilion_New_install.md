---
title: "HP Pavilion New install"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by MacLellan on 2008-01-23
Alright here it is...
I am currently have an HP Pavilion dv2000   (underneath is actually dv2310ca)
CPU is AMD Turion 64x2
and I am running Vista... 
Anyway, I'm looking to make the switch, but am curious if I'm currently wasting my time.

I have been and will be scouring through the forums for the answer.
any help would be great.




Thanks in advance

---

### Post by Mikecore on 2008-01-23
I have a dv2000 ( dv2210us ) same processor. I had some issues with Ubuntu the first time 
I tried to install it. HP's BIOS was causing it to lock up randomly. So until HP released its latest BIOS for my laptop it would not run Ubuntu stably. I did update my BIOS and now everything is working great. So first thing I would do is download Ubuntu boot it and see if everything works. If it doesn't I would go to HP's website and see if there is a update for your BIOS. If there is I would install it and try again. Hopefully then everything works great for you. I am really loving this laptop with Ubuntu installed on it. ( I'm not dual booting just Linux no Micro(Hell) ). As for 64bit or 32bit. The thats up to you, but read carefully before to make a choice. i tried 64bit it was a bit too buggy for me. So i am currently running 32bit Gusty. Good luck! post back let us know how you make out.

---

### Post by MacLellan on 2008-01-23
Perfect... 
thanks for the info, 
I'll give it a try and see how it goes.

Thanks Again.

---

### Post by drussell13 on 2008-01-24
Hello,
MacLellan, did you by chance have any luck with this?   I am having a heck of a time with a Pavilion dv2000 (dv2500).  When I boot to Gutsy live, the video does not come up, it drops me back down to command line.  I was able to boot using the "Safe Graphics Mode"..... The resolution was terrible, 800x600 I think, and no wireless etc......  Just doesn't look like its gonna work for me, and am furious cause I just bought this laptop and absolutely refuse to use Windoze.  If anyone has any tips to get me going, I'd certainly appreciate it.
Thank You!

---

### Post by Yellow Pasque on 2008-01-24
drussell, go to System -> Administration -> Restricted Drivers Manager and see if Ubuntu offers any drivers for your wireless. As for the video, you may need an updated driver or something. Go ahead and install it and then we can get your video working.

---

### Post by Mikecore on 2008-01-24
> **drussell13 said:**
> Hello,
MacLellan, did you by chance have any luck with this?   I am having a heck of a time with a Pavilion dv2000 (dv2500).  When I boot to Gutsy live, the video does not come up, it drops me back down to command line.  I was able to boot using the "Safe Graphics Mode"..... The resolution was terrible, 800x600 I think, and no wireless etc......  Just doesn't look like its gonna work for me, and am furious cause I just bought this laptop and absolutely refuse to use Windoze.  If anyone has any tips to get me going, I'd certainly appreciate it.
Thank You!

Please post your system spec's i.e. type of Processor, video card, and wireless card manufacture.

---

### Post by MacLellan on 2008-01-25
Hey...
Yeh, everything is working good so far with the exception of my built in speakers.... I'm not getting sound... 
A few other problems arose but were quickly fixed with help from here.

---

### Post by drussell13 on 2008-01-25
Sorry about that.....The specs on this machine are.....
Processor - AMD Turion 64 X2 TL-58
Graphics - NVIDIA MCP67M
Wireless - Broadcom 802.11 b/g WLAN

But, yeah Temüjin, I think I might do that, is just go ahead and install Gutsy, and see if we can configure after the fact.  I appreciate any help you might be able to give in this particular area.
Thanks!

---

### Post by Yellow Pasque on 2008-01-25
For reference, here's that other thread where we hammered out MacLellan's issues. [http://ubuntuforums.org/showthread.php?t=676973](http://ubuntuforums.org/showthread.php?t=676973)
If you have additional issues, I'm fairly confident that myself or someone else can straighten them out.

---

### Post by drussell13 on 2008-01-25
Thanks for the link to MacLellan's issue.  That helped out alot.  So heres my current scenario.  I did end up getting Gutsy installed!!   The restricted drivers picked up the nvidia card, however, I can't seem to change my resolution from 800x600.  (I wonder what model of monitor I need to choose in Screen and Graphics?)  Right now its just "Plug and Play".  

Other issues....  Wireless is still a no go, I have it hard wired right now writing this.  lspci shows the following "Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)"  Any ideas on that?  

Other than that, sound works as does everything else.  If i get those 2 issues, I have a rock solid laptop!  I appreciate everybody's help in getting this laptop going!
Thanks

---

### Post by drussell13 on 2008-01-25
Sorry, posted too soon.  Graphics are 100% good to go.  I choose the Generic LCD 1280x800 and looks great.  So the only other thing I can't figure out is the wireless.  I know Broadcoms are always a pain.  But, any pointers would be great.
Thank You

---

### Post by Mikecore on 2008-01-26
Did you activate it under the restricted driver manager? and if so did you tell it to down load  the firmware from the net or did you extract if from the windows driver files.?

---

### Post by MacLellan on 2008-01-26
I'm pretty sure I downloaded it... 

it worked great afterwards.

---

### Post by drussell13 on 2008-01-28
In the Restricted Drivers manager, the only thing it shows me is the nvidia card.  There is nothing for the wireless card.  I know on some previous laptops ive used that had the Broadcom, I was able to use the restricted driver for that.  But, I don't see that in there.  Do you think I'll have to do ndiswrapper??
Thanks

---

### Post by Mikecore on 2008-01-28
that could work.

---

### Post by Ronicstar on 2008-02-04
Can someone help me with the sound on my dv2000? I got everything form the graphics to the wireless working.  I followed the link and tried that, but after i did everything it said i didn't have a sound card, so i rebooted and now it says i have one, but the sound still isn't working...thanks

---

