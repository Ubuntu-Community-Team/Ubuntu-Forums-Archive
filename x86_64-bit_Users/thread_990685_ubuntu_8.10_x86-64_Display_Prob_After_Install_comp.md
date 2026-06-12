---
title: "ubuntu 8.10 x86-64 Display Prob After Install completed"
date: 2008-11-23
forum: x86 64-bit Users
---

### Post by Motown on 2008-11-23
Hello.

Ubuntu 8.10 installed finished successfully and I rebooted. After the Ubuntu splash screen comes up all I get is a messed up picture with the screen resolution at 640x480.

Can anyone help me out here? These are my system specs

Core2Duo E8600.
Nvidia 8800GT
Asus P5e motherboard
4Gb of DDR2 800

Thanks a lot guys.

---

### Post by John Jason Jordan on 2008-11-23
> **Motown said:**
> Hello.

Ubuntu 8.10 installed finished successfully and I rebooted. After the Ubuntu splash screen comes up all I get is a messed up picture with the screen resolution at 640x480.

Can anyone help me out here? These are my system specs

Core2Duo E8600.
Nvidia 8800GT
Asus P5e motherboard
4Gb of DDR2 800

I don't know how to fix your problem, but I can say that if you are using Intrepid there are a lot of problems with video, mouse and keyboard. This is due to a major change in the /etc/X11/xorg.conf file. I would suggest you search the forums for "Intrepid nvidia 8800" and I'll bet you'll turn up some discussions and (hopefully) solutions.

---

### Post by punkybouy on 2008-11-23
You might try using Envy to install graphics drivers.

---

### Post by twisted_steel on 2008-11-23
Did you just install and reboot, or did you go in and grab the nVidia drivers?  I just did a 64-bit install last night with a 8800 GTS and got it to work once I went into System -> Administration -> Hardware Drivers.  I scrolled down and selected the version 177 (Recommended) driver.  I guess the main difference in our initial displays is I did get 1680x1050 on the first boot before I installed the nVidia drivers, though my second display was blank.

Installing the driver will also give you the nVidia control panel.  However, if you just try to run it from the System -> Administration menu, it will not save your configuration.  You need to go into System -> Preferences -> Main Menu and click on Administration.  Select "NVIDIA X Server Settings" in the right-hand pane and go to properties.  Put "gksudo " (that's a space) in front of the command and close out.

Here are my new system specs for reference: Core 2 Duo E8500, EVGA 8800 GTS (320 MB), Gigabyte GA-EP45-DS3L, 8 GB DDR2 800.

Oh, and welcome to the forums :)

---

### Post by kaspar_silas on 2008-11-24
I have exactly the same problem, I think. (Sadly I only found your post after I started my own)

> 
It seems that according to this discussion,
[http://www.nvnews.net/vbulletin/showthread.php?t=113682](http://www.nvnews.net/vbulletin/showthread.php?t=113682)
the NVIDIA drivers don't support 4gb of RAM. Does anyone have an NVIDIA driver working with 4gb?

A kernal patch (?) is given on page 2 but to be honest what this is totally baffles me.

I have tried Envy, using twisted_steel's (above) way and  building the driver using Nvidia's own script.

---

### Post by twisted_steel on 2008-11-24
> **kaspar_silas said:**
> I have exactly the same problem, I think. (Sadly I only found your post after I started my own)

...

I have tried Envy, using twisted_steel's (above) way and  building the driver using Nvidia's own script.

Do you have the same motherboard or video card as Motown?  From the looks of [this nVIDIA Readme]("http://us.download.nvidia.com/XFree86/Linux-x86_64/177.82/README/chapter-09.html") (scroll down to "64-Bit BARs"), your motherboard would have to support 64-bit BARs and would need to be mapping the PCI outside of the 32-bit range.  I have 8 GB working fine here, so I guess either my motherboard does not support this feature, or it consistently puts the PCI I/O addressing below the threshold.  I went through my motherboard manual and didn't find any references to BAR.

---

### Post by kaspar_silas on 2008-11-25
Twisted_steel I have to confess your answer goes over my head. 

However it seems page two of the link I sent agrees with your assessment. However it also contains a Patch. Is there any chance you could look at it and see if you reckon this will work. If so I can attempt a translation to my (2.6.27-8-generic) kernel.

O I don't have the same motherboard or card. I am actually using a Dell optiplex 755 with a 6200 Geforce card. I just thought I would throw in my two cents on the Nvidia drivers.

---

### Post by twisted_steel on 2008-12-09
> **kaspar_silas said:**
> Twisted_steel I have to confess your answer goes over my head. 

However it seems page two of the link I sent agrees with your assessment. However it also contains a Patch. Is there any chance you could look at it and see if you reckon this will work. If so I can attempt a translation to my (2.6.27-8-generic) kernel.

O I don't have the same motherboard or card. I am actually using a Dell optiplex 755 with a 6200 Geforce card. I just thought I would throw in my two cents on the Nvidia drivers.

kaspar_silas,

I came here to apologize for forgetting about this thread for 2 weeks, but I may have come across a useful post at the end of the thread you listed. In post #48 of the thread (link: [http://www.nvnews.net/vbulletin/showthread.php?t=113682&page=4](http://www.nvnews.net/vbulletin/showthread.php?t=113682&page=4)), *add2700* explains some steps that now work on their system.  The first link to the Ubuntu Forums page did not work for me, so I adjusted the URL to this page: [http://ubuntuforums.org/showpost.php?p=6122978&postcount=37](http://ubuntuforums.org/showpost.php?p=6122978&postcount=37). Let us know if this works for you.

---

### Post by twisted_steel on 2008-12-09
> **twisted_steel said:**
> kaspar_silas,

I came here to apologize for forgetting about this thread for 2 weeks, but I may have come across a useful post at the end of the thread you listed. In post #48 of the thread (link: [http://www.nvnews.net/vbulletin/showthread.php?t=113682&page=4](http://www.nvnews.net/vbulletin/showthread.php?t=113682&page=4)), *add2700* explains some steps that now work on their system.  The first link to the Ubuntu Forums page did not work for me, so I adjusted the URL to this page: [http://ubuntuforums.org/showpost.php?p=6122978&postcount=37](http://ubuntuforums.org/showpost.php?p=6122978&postcount=37). Let us know if this works for you.

Doing a little number conversion on the two patches, it appears that they set the range of memory locations that can be used to access the video memory. The 512 MB patch ends at 0xe0000000. If you convert that to decimal, and change the units, you get 3584 MB. Adding 512 MB gets you to 4096 MB, or 4 GB of memory. This keeps it away from the 2nd 4 GB of memory that users seemed to be running into problems with the current 64-bit memory mapping. I'm not sure why the 256 MB patch sets a lower end position than the 512 MB. With any luck a real fix will be worked out that can be incorporated into the actual kernel.

---

### Post by siddtharth on 2008-12-10
twisted_steel: I have the same problem only difference is I have 3gb RAM and NVIDIA 7600Go with has 128MB dedicated memory. I tried to modify the 256MB patch and changed 'r->end = 0xd0000000' to 'r->end = 0xc8000000' to created 128MB gap, but this didn't work so can you tell me if this is the correct way to do this for my config ? I have attached out put of `dmesg`

---

### Post by twisted_steel on 2008-12-15
> **siddtharth said:**
> twisted_steel: I have the same problem only difference is I have 3gb RAM and NVIDIA 7600Go with has 128MB dedicated memory. I tried to modify the 256MB patch and changed 'r->end = 0xd0000000' to 'r->end = 0xc8000000' to created 128MB gap, but this didn't work so can you tell me if this is the correct way to do this for my config ? I have attached out put of `dmesg`

Sorry for the delay. I don't have this problem myself and just happened to come across those patches. However, based on subtraction, it looks like the locations you picked create a 128 MB allocation. I'm not entirely sure how the locations are supposed to be calculated to be correct.

I do think I may have a reason why your patch did not work. You set the end location to 0xc8000000, which is greater than 3GB. I think the maximum end location for your memory is 0xc0000000 because you should not be able to access an address greater than your total memory size.

Maybe you can set the end to 0xc0000000 - 128MB, or 0xb8000000? That would make the start address 0xb8000000 - 128MB, or 0xb0000000. This is really just a guess, because it looks like the way the other patch was done was to just arbitrarily pick a base of 3GB and then just add in either 256MB or 512MB depending on the size. I guess you could just set your base to 2GB, but that seems a little low.

What I would try doing if I were you is print out some debugging statements in the kernel to see if you actually get into that if statement in the first place. A quick printk("In the if statement ...\n") or something like that should show up in a dmesg output. Try testing it outside the if statements first to see if it works properly. I guess the goal if it doesn't match is to find out what the start and end addresses are. My C is a little rusty, but I think you would use r->start and r->end to get the memory locations, which you could then print out as hexadecimal values. I found this site that has some info on kernel debugging using print statements: [http://www.linuxchix.org/content/courses/kernel_hacking/lesson5](http://www.linuxchix.org/content/courses/kernel_hacking/lesson5).

Maybe a little more than you were looking for, but hopefully it can get you closer to having a working video card :)

---

### Post by siddtharth on 2008-12-16
Thanks a lot man. I was completely forced to use vista as I oculdn't use my nVidia and 3GB RAM. I tried installing Fedora 10 so but that dosen't work either so  I'll go back to Ubuntu and the try your suggestions. let's see if it works. My C is a little rusty too but Thanks for the link that shouyld help me.

I got 2 Question's: when you say 
"I think the maximum end location for your memory is 0xc0000000 because you should not be able to access an address greater than your total memory size."

Does this mean that Total memory accessible cannot be more then 3GB ?
FYI: I have ubuntu x86_64

Also is there any quicker way to test this, the way I did is get the kernel source, apply the patch, compile the whole stuff and then install the deb's. This is exactly as suggested in the other post and it takes around 2hrs.

Thanks a Lot.

---

### Post by leemstradamus on 2008-12-16
Hello all, sorry if I make no sense but I am a total noob to Linux. I have been trying to try it out but find it much to much of a hassle for everyday use. I think I have the same problem here. I recently installed Ubuntu 8.10 x64 and when I went to install the Nvidia drivers from the update menu and restart the system loses the gui. I have no idea what to do and and just reinstalled it again this weekend but lo and behold it did it again. I need help please.

---

### Post by siddtharth on 2008-12-16
> **leemstradamus said:**
> Hello all, sorry if I make no sense but I am a total noob to Linux. I have been trying to try it out but find it much to much of a hassle for everyday use. I think I have the same problem here. I recently installed Ubuntu 8.10 x64 and when I went to install the Nvidia drivers from the update menu and restart the system loses the gui. I have no idea what to do and and just reinstalled it again this weekend but lo and behold it did it again. I need help please.

can you tell your machine details also can you upload output for command 'dmesg'

---

### Post by twisted_steel on 2008-12-16
> **siddtharth said:**
> Thanks a lot man. I was completely forced to use vista as I oculdn't use my nVidia and 3GB RAM. I tried installing Fedora 10 so but that dosen't work either so  I'll go back to Ubuntu and the try your suggestions. let's see if it works. My C is a little rusty too but Thanks for the link that shouyld help me.

I got 2 Question's: when you say 
"I think the maximum end location for your memory is 0xc0000000 because you should not be able to access an address greater than your total memory size."

Does this mean that Total memory accessible cannot be more then 3GB ?
FYI: I have ubuntu x86_64

Also is there any quicker way to test this, the way I did is get the kernel source, apply the patch, compile the whole stuff and then install the deb's. This is exactly as suggested in the other post and it takes around 2hrs.

Thanks a Lot.

For the first question, I assumed that perhaps the 0xc0000000 address would be the maximum because it is 3GB. However, I read up on it a little more in some other forum posts. Supposedly the entire address range 0xc0000000 to 0xffffffff is reserved for PCI addressing (see [http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2)). Someone on that same page said they picked the following address for the end (512 MB card): ```
r->end = r->start + (512 * 1024 * 1024) - 1;
```In your case of 128MB this would be 0xC7FFFFFF, which is one less than you and I had initially thought. It might be worth a shot to try changing it and see if that does it. Apparently the addressing problems come up whether you are running 32-bit or 64-bit versions of Linux. They are PCI related, and are not typically an issue.

Out of curiosity, in your original dmesg, before you tried patching things, did you see something like "BAR1 is 128M ..." or had it always been "BAR1 is 0M"?

I did come across a few links that might be of help.

[LIST]
[*] Red Hat Bugzilla bug: [https://bugzilla.redhat.com/show_bug.cgi?id=425794](https://bugzilla.redhat.com/show_bug.cgi?id=425794). This includes a patch that is a lot more involved than the 4 lines seen in the other patches out there.
[*] Comments from Linus: [http://lkml.org/lkml/2007/12/18/223](http://lkml.org/lkml/2007/12/18/223)
[*] Tons of info from someone else who is affected: [http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm](http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm)
[/LIST]
 
As far as your second question, I want to say there is a way to just recompile the changed kernel modules, but I have never done it. I hate to say it, but it might be safer to just wait the 2 hours.

---

### Post by leemstradamus on 2008-12-17
> **siddtharth said:**
> can you tell your machine details also can you upload output for command 'dmesg'
I have a q6600 - 4gb 800mhz ram - 2 8800GTS ssc (112sp)(g80)in sli - 10k RPM raptor HDD -  7.2k rpm 320gb HDD - EVGA 750i motherboard 

Sorry but I have no idea what this is "command 'dmesg'"

---

### Post by kaspar_silas on 2008-12-17
> **twisted_steel said:**
> kaspar_silas,

I came here to apologize for forgetting about this thread for 2 weeks, but I may have come across a useful post at the end of the thread you listed. In post #48 of the thread (link: [http://www.nvnews.net/vbulletin/showthread.php?t=113682&page=4](http://www.nvnews.net/vbulletin/showthread.php?t=113682&page=4)), *add2700* explains some steps that now work on their system.  The first link to the Ubuntu Forums page did not work for me, so I adjusted the URL to this page: [http://ubuntuforums.org/showpost.php?p=6122978&postcount=37](http://ubuntuforums.org/showpost.php?p=6122978&postcount=37). Let us know if this works for you.

Sorry I also forgot about this thread. Anyway I tried applying the patch but alas it didn't make any difference. Looking around this seems a not too uncommon problem that nvidia do know about.  I wonder why they have not fixed the driver. 

I am actually going to try once again at the end of today. If I can't get it to work after that I will buy another non nvidia card and move the nvidia card to another machine or in other words give up.

---

### Post by twisted_steel on 2008-12-17
> **leemstradamus said:**
> I have a q6600 - 4gb 800mhz ram - 2 8800GTS ssc (112sp)(g80)in sli - 10k RPM raptor HDD -  7.2k rpm 320gb HDD - EVGA 750i motherboard 

Sorry but I have no idea what this is "command 'dmesg'"

The command is run from your terminal. I am assuming you are running Ubuntu. To open the terminal, go to Applications -> Accessories -> Terminal from the main system menu. Once that is open, run the following command:
```
dmesg > dmesg-output.txt
```This will run the dmesg command, which gives you information about your computer starting up, events, etc, and save the output to the file "dmesg-output.txt". This should be stored in your user folder, e.g. /home/myuser/dmesg-output.txt. To attach it here, just add a new reply, click on the paper clip to add an attachment, and select your saved output.

---

### Post by twisted_steel on 2008-12-17
> **kaspar_silas said:**
> Sorry I also forgot about this thread. Anyway I tried applying the patch but alas it didn't make any difference. Looking around this seems a not too uncommon problem that nvidia do know about.  I wonder why they have not fixed the driver. 

I am actually going to try once again at the end of today. If I can't get it to work after that I will buy another non nvidia card and move the nvidia card to another machine or in other words give up.

If I understand the problem correctly, I don't know that getting a new NVIDIA card will help you. It seems like this is a BIOS-related problem where the addressing is set outside of the addressing that can be accessed by the driver. I wonder if this also means that ATI cards will have this problem, as the potential fixes patch the kernel itself.

---

### Post by siddtharth on 2008-12-17
> **twisted_steel said:**
> For the first question, I assumed that perhaps the 0xc0000000 address would be the maximum because it is 3GB. However, I read up on it a little more in some other forum posts. Supposedly the entire address range 0xc0000000 to 0xffffffff is reserved for PCI addressing (see [http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2)). Someone on that same page said they picked the following address for the end (512 MB card): ```
r->end = r->start + (512 * 1024 * 1024) - 1;
```In your case of 128MB this would be 0xC7FFFFFF, which is one less than you and I had initially thought. It might be worth a shot to try changing it and see if that does it. Apparently the addressing problems come up whether you are running 32-bit or 64-bit versions of Linux. They are PCI related, and are not typically an issue.

Out of curiosity, in your original dmesg, before you tried patching things, did you see something like "BAR1 is 128M ..." or had it always been "BAR1 is 0M"?

I did come across a few links that might be of help.

[LIST]
[*] Red Hat Bugzilla bug: [https://bugzilla.redhat.com/show_bug.cgi?id=425794](https://bugzilla.redhat.com/show_bug.cgi?id=425794). This includes a patch that is a lot more involved than the 4 lines seen in the other patches out there.
[*] Comments from Linus: [http://lkml.org/lkml/2007/12/18/223](http://lkml.org/lkml/2007/12/18/223)
[*] Tons of info from someone else who is affected: [http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm](http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm)
[/LIST]
 
As far as your second question, I want to say there is a way to just recompile the changed kernel modules, but I have never done it. I hate to say it, but it might be safer to just wait the 2 hours.

I always got "BAR1 is 0M".
I tried installing fedora 10 and so now I will have to install back Ubuntu before I can try out your suggestion. If this is a problem for everyone with more then 3gb RAM and Nvidia card then I would say this should be fixed at kernel level instead of each individual trying to patch the kernel.
That's why common people prefer to use win. as everything just works even if its not stable.

Any way's I'll start with a fresh install of ubuntu 8.10 x86_64 and try out twisted_steel's suggestion. 

I'll keep the post updated once I try it out.

Thanks!

---

### Post by siddtharth on 2008-12-17
> **twisted_steel said:**
> For the first question, I assumed that perhaps the 0xc0000000 address would be the maximum because it is 3GB. However, I read up on it a little more in some other forum posts. Supposedly the entire address range 0xc0000000 to 0xffffffff is reserved for PCI addressing (see [http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2)). Someone on that same page said they picked the following address for the end (512 MB card): ```
r->end = r->start + (512 * 1024 * 1024) - 1;
```In your case of 128MB this would be 0xC7FFFFFF, which is one less than you and I had initially thought. It might be worth a shot to try changing it and see if that does it. Apparently the addressing problems come up whether you are running 32-bit or 64-bit versions of Linux. They are PCI related, and are not typically an issue.

Out of curiosity, in your original dmesg, before you tried patching things, did you see something like "BAR1 is 128M ..." or had it always been "BAR1 is 0M"?

I did come across a few links that might be of help.

[LIST]
[*] Red Hat Bugzilla bug: [https://bugzilla.redhat.com/show_bug.cgi?id=425794](https://bugzilla.redhat.com/show_bug.cgi?id=425794). This includes a patch that is a lot more involved than the 4 lines seen in the other patches out there.
[*] Comments from Linus: [http://lkml.org/lkml/2007/12/18/223](http://lkml.org/lkml/2007/12/18/223)
[*] Tons of info from someone else who is affected: [http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm](http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm)
[/LIST]
 
As far as your second question, I want to say there is a way to just recompile the changed kernel modules, but I have never done it. I hate to say it, but it might be safer to just wait the 2 hours.

Found some thing interesting after reading through some of the links. In vista when I checked I found that Nvidia card is assigned address range "0xA0000-0xBFFFF	NVIDIA GeForce Go 7600".

So I'm thinking about forcing r->start and r->end to these values. Do you think this will work?
what about some other device that has address assigned in this range ?

---

### Post by twisted_steel on 2008-12-17
> **siddtharth said:**
> Found some thing interesting after reading through some of the links. In vista when I checked I found that Nvidia card is assigned address range "0xA0000-0xBFFFF    NVIDIA GeForce Go 7600".

So I'm thinking about forcing r->start and r->end to these values. Do you think this will work?
what about some other device that has address assigned in this range ?

I don't think the addressing maps well between the two operating systems.

Do you still have Fedora on there? It looks like the one bug link for Fedora that I posted is going to auto-expire soon. If this truly is a kernel problem, I would think it would show up in either distro and the patch could very well be the same.

Does your computer completely lock up when you run into the error? I was hoping you could look at /proc/iomem and see if you have any openings (and if they are reproducible). Here is the relevant section for my card:
```
e4000000-e7ffffff : PCI Bus 0000:01
  e4000000-e5ffffff : 0000:01:00.0
  e6000000-e6ffffff : 0000:01:00.0
    e6000000-e6ffffff : nvidia
  e7000000-e701ffff : 0000:01:00.0
```I've attached the rest of my /proc/iomem in case it is any help.

I read something in another thread from the "TJ" person who made the wiki page. It sounds like he was working on a re-write of the iomem allocation. I'm going to send him a PM and see if I hear anything back. Link to the post: [http://ubuntuforums.org/showpost.php?p=5722827&postcount=2](http://ubuntuforums.org/showpost.php?p=5722827&postcount=2).

---

### Post by twisted_steel on 2008-12-17
> **twisted_steel said:**
> Here is the relevant section for my card:
```
e4000000-e7ffffff : PCI Bus 0000:01
  e4000000-e5ffffff : 0000:01:00.0
  e6000000-e6ffffff : 0000:01:00.0
    e6000000-e6ffffff : nvidia
  e7000000-e701ffff : 0000:01:00.0
```

I forgot to add earlier that the total memory allocated for that bus location is 384MB. This is the total amount of memory that my video card (8800 GTS) has.

---

### Post by siddtharth on 2008-12-17
> **twisted_steel said:**
> I don't think the addressing maps well between the two operating systems.

Do you still have Fedora on there? It looks like the one bug link for Fedora that I posted is going to auto-expire soon. If this truly is a kernel problem, I would think it would show up in either distro and the patch could very well be the same.

Does your computer completely lock up when you run into the error? I was hoping you could look at /proc/iomem and see if you have any openings (and if they are reproducible). Here is the relevant section for my card:
```
e4000000-e7ffffff : PCI Bus 0000:01
  e4000000-e5ffffff : 0000:01:00.0
  e6000000-e6ffffff : 0000:01:00.0
    e6000000-e6ffffff : nvidia
  e7000000-e701ffff : 0000:01:00.0
```I've attached the rest of my /proc/iomem in case it is any help.

I read something in another thread from the "TJ" person who made the wiki page. It sounds like he was working on a re-write of the iomem allocation. I'm going to send him a PM and see if I hear anything back. Link to the post: [http://ubuntuforums.org/showpost.php?p=5722827&postcount=2](http://ubuntuforums.org/showpost.php?p=5722827&postcount=2).

I don't understand what you mean ? but yes I still have fedora 10 64 bit installed and x wont start but I can login into the terminal and try this.

---

### Post by kaspar_silas on 2008-12-18
> **kaspar_silas said:**
> Sorry I also forgot about this thread. Anyway I tried applying the patch but alas it didn't make any difference. Looking around this seems a not too uncommon problem that nvidia do know about.  I wonder why they have not fixed the driver. 

I am actually going to try once again at the end of today. If I can't get it to work after that I will buy another non nvidia card and move the nvidia card to another machine or in other words give up.

After many, many, goes at fixing this I think my conclusion is the patch, or the instructions anyway, do not work for me.

A quick search revealed twisted_steel was at least partly correct that other non-nvidia cards may have the same problem. This is a right pain, that I hope is fixed at source sometime soon. 

Anyway Happy Christmas all.

---

### Post by siddtharth on 2008-12-18
I just reinstall ubuntu 8.10 x86_64. I'm uploading output for dmesg and /proc/iomem. can someone please advise any fix?

---

### Post by siddtharth on 2008-12-30
has anyone tried latest kernel 2.6.28 ? change log say's something about 64 bit bars not sure if it is a fix for this issue ?
Anyways I'll try to update to latest kernel, let's see...

---

### Post by siddtharth on 2009-02-04
No Fix Yet! :(
this is great, linux dosn't support 64-bit bars and windows can!
so what's better now ? I like linux and really want to use it but the only problem is it dose't work!

---

