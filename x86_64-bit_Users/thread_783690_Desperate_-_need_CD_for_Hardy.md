---
title: "Desperate - need CD for Hardy"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2008-05-05
I am writing this on my desktop because I have messed up the network on my laptop, which is my main computer. I messed it up by installing wicd in an attempt to fix the wireless after mupgrading from Gutsy to Hardy x86_64. However, I cannot reinstall network-manager because now I have no network at all on the laptop. The only way I will be able to reinstall network manager is via the CD. I have all the Hardy CDs, but nothing I can do will get Synaptic to see the CD. 

In Synaptic I go to Settings > Repositories and then on the Third-Party Software tab. Then I click on the Add CD-ROM button, which pops up a box that says Please Insert a Disk into the Drive. I insert the Ubuntu Hardy desktop x86_64 CD in the drive and click on OK. A popup says "Scanning disc for index files, then "The disk is called <can't read the rest because it disappears too fast>." And then it says "unmounting CD-ROM." That's all it says, and afterwards Synaptic still does not see the CD-ROM. I am using Ubuntu Hardy x86_64 and I have tried other CDs as well, e.g., the Alternate Install CD. No way can I get Synaptic to see the CD drive.

If I can't get Synaptic to see the CD drive, how can I ever repair Network Manager?

I'm desperate here. I hope someone can help. :(

---

### Post by Jouke74 on 2008-05-06
If you did not mess up synaptic and apt too much you should be able to select the Ubuntu CDROM repository on the FIRST tab. It's listed in the box under the main, restricted etc.. Otherwise you can also just plug in the CD in the drive, let it read by Nautilus and double click the DEBs. It will complain about dependencies, but for all programs there are not too many of them. To install the dependencies double click those debs first.

---

### Post by utUtu on 2008-05-06
> **John Jason Jordan said:**
> I am writing this on my desktop because I have messed up the network on my laptop, which is my main computer. I messed it up by installing wicd in an attempt to fix the wireless after mupgrading from Gutsy to Hardy x86_64. However, I cannot reinstall network-manager because now I have no network at all on the laptop. The only way I will be able to reinstall network manager is via the CD. I have all the Hardy CDs, but nothing I can do will get Synaptic to see the CD. 


If I can't get Synaptic to see the CD drive, how can I ever repair Network Manager?

I'm desperate here. I hope someone can help. :(

The easiest way is to connect through your wired ethernet port.

---

### Post by sp0nge on 2008-05-06
If you can get any necessary data off the laptop, or if there is nothing that can't be replaced, I would recommend you just wipe the drive and start from scratch. I'm an advocate of backing up data, hopefully you have. A fresh install would be the easiest way to fix the issue, IMHO.

---

### Post by John Jason Jordan on 2008-05-06
> **sp0nge said:**
> If you can get any necessary data off the laptop, or if there is nothing that can't be replaced, I would recommend you just wipe the drive and start from scratch. I'm an advocate of backing up data, hopefully you have. A fresh install would be the easiest way to fix the issue, IMHO.
That thought occurred to me also, but getting the data off without a working network would have been a pain. Luckily it is now morning, the coffee is working, and I was just able to figure out how to get the ethernet working again. I'm not an expert on these things and I just couldn't figure it out last night.

So I no longer need to do things from the CD, although figuring out how to do so would be good in case something like this happens again.

---

