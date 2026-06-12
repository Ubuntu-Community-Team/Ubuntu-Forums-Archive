---
title: "noob help - configuring rt73 usb wifi in 10.3"
date: 2008-01-26
forum: openSUSE and SUSE Linux Enterprise
---

### Post by RostokMcSpoons on 2008-01-26
Help, please!

I've just trashed my  Ubuntu Feisty and Gutsy installations, and tried to install openSUSE 10.3 in the desperate hope that I can actually get my wifi to work for more than 10 minutes, *or even if/when I switch my pc off and on again * :???:

Frankly this now seems like a vain hope, because I'm still not getting an active connection.

And SUSE doesn't fill me with hope - the first time I logged in my screen refresh was set to 45hz!  What madness is that?  Since when was there *ever* a screen that worked below 60hz?  I nearly had a fit!   It's still at 60hz even though I've chosen VESA 75hz now.  If I can't get a screen refresh rate to work, I'll never get wifi to obey me :rolleyes:


So anyhow... I'm rather stymied, cos all the stuff I've learned for Ubuntu doesn't seem to work in SUSE... I open a terminal, type 'sudo ifconfig -a'  and it tells me that ifconfig isn't a command!  (I've fiddled with the settings in Network Manager, and had turned it off before trying that)

It's 5:30 in the morning and I've had enough - it seems to me Linux is a masochists delight, it's a cruel and unusual punishment only to be visited on your worst enemies.  

I need someone to walk me through this in baby steps or I shall spend all day tomorrow drowning kittens in a bucket, so help me God!!!

---

### Post by RebounD11 on 2008-01-26
Ok... let's begin :D

I assume you have an ATI video card since you said VESA (I might be wrong you might have been talking about your monitor :D). In order to set that up look here:

[http://en.opensuse.org/ATI](http://en.opensuse.org/ATI)

if you have Nvidia then look here: 

[http://en.opensuse.org/ATI](http://en.opensuse.org/ATI)

and if it's the monitor you have problems with, I suggest you do as I do, look it up, or it's specs, on the web (most likely you'll find them on the manufacturer's home page, but that's not always the case) and modify your Monitor section of the /etc/X11/xorg.conf file. You don't have to specify everything just the refresh rates  possible and a few other important things, here's how my Monitor section looks like:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Iiyama"
    ModelName      "HM703UT"
    DisplaySize     324    243
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection
```

And now for the wireless problem. I suggest you download and install the rt73 from Ralink's website and follow this tutorial (it's in the OpenSuSE wiki) here:

[http://en.opensuse.org/SDB:USB_Wireless_Adpater_Using_Ralink_RT73_Chipset_%28DWL-G122%29](http://en.opensuse.org/SDB:USB_Wireless_Adpater_Using_Ralink_RT73_Chipset_%28DWL-G122%29)

you have there the link to Ralink's download page.

If this doesn't work, try using the Serialmonkey drivers for rt73. For that you can follow this Ubuntu tutorial and adapt it to OpenSuSE... pretty much all you have to do is use su and login as root, instead of sudo (that's if you didn't set up sudo), anyway here it is: 

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Hope this helps :D

Good luck! OpenSuSE 10.3 is a great distro, enjoy it. 

PS If you want Compiz Fusion check this out: [http://en.opensuse.org/Compiz_fusion](http://en.opensuse.org/Compiz_fusion)

---

### Post by RostokMcSpoons on 2008-01-26
Hi, 

thanks for the reply...

firstly the monitor - well the good news is the crappy screen I've got is in the list, it's a Dell P790 15" crt, that cost me £1 off ebay ;)    Anyway, it's now humming away at 85hz.  So that's great.   I was just a bit weirded-out by it defaulting to 45hz - never *ever* seen that before, and it was in the middle of a very long night ;)   I got to bed at 7:30am in the end... that's late for a 40yr old :guitar: :)

So.. onto the main problem.

I've had a look at the first link... the mixture of non-native English and Linux is confusing, but I can remember how to do it from other threads I think.

edit:  oh blimey, just when I thought it couldn't get any worse - I've dragged the driver folder to my desktop, navigated into it in the Terminal, and then tried to 'make' only to be told there's no such command. (Oh, I'm in 'su' mode btw)

If I had any hair left to tear out after last night, itd' be on the floor now.




I think I hate Linux

---

### Post by RebounD11 on 2008-01-26
> **RostokMcSpoons said:**
> 
So.. onto the main problem.

I've had a look at the first link... the mixture of non-native English and Linux is confusing, but I can remember how to do it from other threads I think.

edit:  oh blimey, just when I thought it couldn't get any worse - I've dragged the driver folder to my desktop, navigated into it in the Terminal, and then tried to 'make' only to be told there's no such command. (Oh, I'm in 'su' mode btw)

If I had any hair left to tear out after last night, itd' be on the floor now.




I think I hate Linux

Don't give up so easily :) You might hate Linux but Linux doesn't hate you... 

if the terminal says 'command not found' it means that certain command is not installed (I gather from make not being installed that your OpenSuSE is installed from the Live CD :D). Since people have complained that Yast is pretty slow with package management I suggest you do the following:
```

su
{enter root password}
zypper install make
```

Now you should be able to compile the drivers... Make should work  :D

If there's any other problems feel free to ask... technical support is free of charge here :D

---

### Post by RostokMcSpoons on 2008-01-27
Hi, 

Thanks but I gave up.  I'm going to post a message in the Networking forum detailing my reasons and discoveries... maybe it'll help someone else.

So that's me and Linux parting company cos I've an *ahem* 'evaluation' copy of XP from a friend, and everything works peachily now :)

Maybe I'll return to it in the future when I've got different hardware to try it on.

---

