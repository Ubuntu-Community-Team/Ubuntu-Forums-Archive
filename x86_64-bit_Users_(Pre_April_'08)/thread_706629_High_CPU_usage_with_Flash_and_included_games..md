---
title: "High CPU usage with Flash and included games."
date: 2008-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by rs2k on 2008-02-24
I am fairly new to Linux but here's the problem I am having. When I use flash in Firefox the system uses nearly 100% CPU. When I have two browser windows with flash running It bogs down the entire system. I am using Compiz and the all the effects including the desktop cube are incredibly fast. I can spin the 3D cube with a browser running on 4 separate workspaces without a hint of slow down as the CPU runs at 9% - 12% But as soon  as I open up a game like Gnometris or a flash video (like youtube) the CPU usage goes up and stays up.

I am dual booting with XP and can run around 6 instances of flash before the systems starts to slow down, But that's because the system memory runs low, not because the CPU bogs down. I was able to run more when I had 1Gb of ram on this system.

Also, Google Earth runs so slowly in Ubuntu that is is useless. In Windows XP it runs quite quickly.

When nothing but the System Monitor is running my CPU usage fluctuates between 1%-3%

System specs:

Ubuntu 7.10 x86_64 from Live CD install
AMD Athlon 64 3000+ running on a 210/420 Mhz Buss
512Mb DDR Ram
Radeon 9800 Pro (R350) with drivers that the live install provided.

---

### Post by soxs on 2008-02-25
I would suggest you to either update your drivers to either version 8.02, 801 or 8.40.x. This should give you some speed boost. (Be aware of some difficulties installing them etc)

---

### Post by nisarg on 2008-03-16
Hi,

I am running into same issues. any ideas.
Everything running fine, compiz works perfect, cube and all effects. 
I have AWN dock installed, and with all its graphics and applications it seems running on fairly moderate CPU.
The moment I hit youtube or some forums (with flash ads i guess) CPU usage spikes up, and stays there until I dont close the page. Running more than 3 pages slows everything down.

Any suggestions anyone?
I am running Ubuntu 7.10 on IBM T40 with 512 RAM.

Cheers,

---

### Post by zxscooby on 2008-03-16
I had the exact  same problem with my toshiba laptop , 
Two things that i did to increase performance.
Installed an older version of flash  9.0.48
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1)
I also found that powernowd  was incompatible with my system.
when i disabled powernowd from running at startup all my flash ( and gnometris)worked perfectly.
i installed a different power management program , i forget which one.

---

### Post by nisarg on 2008-03-17
Hi, thanks for your response. 
i think i also running 'powernowd' - how can I check its compatibility? also, might sound silly - but it would great know more about this daemon. what does it do, why do you need it, etc etc and what its alternatives are.
I will check out the old version of flash...

thanks again

> **zxscooby said:**
> I had the exact  same problem with my toshiba laptop , 
Two things that i did to increase performance.
Installed an older version of flash  9.0.48
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1)
I also found that powernowd  was incompatible with my system.
when i disabled powernowd from running at startup all my flash ( and gnometris)worked perfectly.
i installed a different power management program , i forget which one.

---

### Post by zxscooby on 2008-03-18
sorry for the late reply.

Powernowd regulates the power of your cpu according to system load.
It is usefull to conserve battery power.

type```
 
man powernowd
```
in the terminal
also 
```
sudo powernowd 
```

should report any errors

---

### Post by nisarg on 2008-03-18
OK this is great thanks.
I think it doesnt seem to report any errors when I do 
```
sudo powernowd
```

It displays the version and some CPU details.
So - no errors - does that indicate a need to replace it? 
Did you do it because you had errors reported?

Regards,
Nisarg

> **zxscooby said:**
> sorry for the late reply.

Powernowd regulates the power of your cpu according to system load.
It is usefull to conserve battery power.

type```
 
man powernowd
```
in the terminal
also 
```
sudo powernowd 
```

should report any errors

---

### Post by zxscooby on 2008-03-20
may be another problem then. You can try to disable it and see how it goes by deselecting
it from your startup services. 
is the processor information its giving correct?

---

### Post by gsiliceo on 2008-05-04
I made this little guide to install the older version that is less cpu intensive.

First test your current version of flash here
[COLOR="Blue"][SHow my flash player version]("http://www.mediacollege.com/adobe/flash/player/version/show.html")[/COLOR]
Then normally you'd have to download a 94 meg package that adobe provides with lots of flash player version but i'd make it easier for you uploading just the recommended 9.048.
[COLOR="Blue"][Download it here 2.5 megs to your desktop]("http://www.mediafire.com/?znhecmwx0j4")[/COLOR]

Close firefox.

Then extract it, right click on the package and *"extract here"*
Open the folder and copy the file libflashplayer.so 
Now open a terminal and do this
> sudo nautilus
Once is opened go to /usr/lib/flashplugin-nonfree/
And paste the file you just copied, replace when asked. 
Then go back to the extracted folder in your desktop and double click the flashplayer-installer, and choose execute in terminal, then hit enter and you are done.

Test your new version of flash

---

### Post by Lan on 2008-07-05
Similar issue here: HighCPU about - Cpu(s): 83.0%us
This is when playing flash - ie. YouTube through Firefox

Still looking for solution -

DELL D810

Distributor ID: Ubuntu
Description: Ubuntu 8.04.1
Release: 8.04
Codename: hardy



Firefox: Mozilla/5.0 (X11;U;Linux i686;enUS;rv:1.9)Gecho/2008061015 Firefox/3.0

Installed Flash:
install_flash_player_9_linux.tar.gz



processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 13
model name : Intel(R) Pentium(R) M processor 2.00GHz
stepping : 8
cpu MHz : 1995.000
cache size : 2048 KB

MemTotal: 2075640 kB
MemFree: 1319220 kB
Buffers: 16568 kB
Cached: 344600 kB
SwapCached: 0 kB
Active: 473512 kB
Inactive: 199144 kB
HighTotal: 1179488 kB
HighFree: 514644 kB
LowTotal: 896152 kB





_____________________
Followed some of the above ^, although it didn't correct the issue until after removing the libs below. 

Ok, issue resolved for me.

I don't exactly know how I fixed it but here's what I did.

Removed two flash that were associated with mozilla.
Didn't document it but if I can remember correctly:

libflash-mozplugin - GPL Flash (SWF) Library Mozilla compatible plugin
swfdec-mozilla - mozilla plugin for SWF (macromedia flash)

Also went to this site to check Flash Version:
It gave me this code WIN 9.100. - something like that which decodes as Windows and version 9.100
[http://www.mediacollege.com/adobe/flash/player/version/show.html](http://www.mediacollege.com/adobe/flash/player/version/show.html)

I also went here to DL and install this Flash Version:
[http://www.mediafire.com/?znhecmwx0j4](http://www.mediafire.com/?znhecmwx0j4)

Going back to that ShowFlashVersion site: Results to : LNX 9,0,124,0. It's no longer displaying WIN 9.100.xx.xx

Everythings working good now. I'm ok with this Cpu(s): 35.9% than 85%

I'm not exactly sure which one corrected the issue

BTW. before this issue was "corrected" there's a huge grey play button inside a huge circle (>) taking the whole youtube screen. You press that and it plays. It doesn't have that anymore. :)

Thanks.

---

### Post by gsiliceo on 2008-07-05
You seem to have putted a lot of effort to that bug Lan, maybe you should try firefox on wine with the windows flash pluging. Or internet explorer.

---

### Post by Spinozaur on 2008-07-15
> **Lan said:**
> Followed some of the above ^, although it didn't correct the issue until after removing the libs below. 

Ok, issue resolved for me.

I don't exactly know how I fixed it but here's what I did.

Removed two flash that were associated with mozilla.
Didn't document it but if I can remember correctly:

libflash-mozplugin - GPL Flash (SWF) Library Mozilla compatible plugin
swfdec-mozilla - mozilla plugin for SWF (macromedia flash)

Also went to this site to check Flash Version:
It gave me this code WIN 9.100. - something like that which decodes as Windows and version 9.100
[http://www.mediacollege.com/adobe/flash/player/version/show.html](http://www.mediacollege.com/adobe/flash/player/version/show.html)

I also went here to DL and install this Flash Version:
[http://www.mediafire.com/?znhecmwx0j4](http://www.mediafire.com/?znhecmwx0j4)

Going back to that ShowFlashVersion site: Results to : LNX 9,0,124,0. It's no longer displaying WIN 9.100.xx.xx

Everythings working good now. I'm ok with this Cpu(s): 35.9% than 85%

I'm not exactly sure which one corrected the issue

BTW. before this issue was "corrected" there's a huge grey play button inside a huge circle (>) taking the whole youtube screen. You press that and it plays. It doesn't have that anymore. :)

Thanks.

Alright, I pretty much did what you did. I used the purge command to delete both of those files "*sudo aptitude purge*" then I checked that website and received the same message as you, the Win1000 or whatever. Then I downloaded the package but I didn't install, I don't know why but I didn't. Anyhoo, my Flash pages run smooth as butter now and I don't have the annoying gray button anymore.

My guess is that downloading flash, and swfdec in general conflicts with ubuntu's firefox pack and causes the massive CPU usage. I can't say that for sure but that's what i think. 

Thanks much Lan, I'm VERY satisfied.

---

