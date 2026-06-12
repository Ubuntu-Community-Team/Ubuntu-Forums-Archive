---
title: "Problem Installing Ubuntu on Acer Aspire 5002wlmi"
date: 2006-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by komputes on 2006-09-18
I really wanted to start using Ubuntu but here I am back on windows because the install did not work.

I downloaded Ubuntu 6.06, burned the .iso and rebooted and got booted into linux with a small hard drive icon saying install. First time, that would not open so I restarted again, this time i double clicked on the hard drive and put in my name and all and then it froze gain. I restarted. I double clicked on this hard drive icon once again and it finally gave me the chance to partition my drive. I made a 512mb swap and a 10gb ext3, then I was sure it was going to install. It satyed on the Installing... 0% screen all night.

I was ready to try installing Ubuntu one more time. This time I downloaded ubuntu-6.06.1-desktop-amd64, hoping that the update since 6.06 would fix the installation problem. The same thing happened, I got as far as the disk partition manager, and then the computer simply froze. I tried this about 5 times, every time with the same result.

So I downloaded the alternate 64-bit install which was recommended if I ran into any problems. I checked the MD5, and I burned the iso to a disc. I booted in text mode and gor the following error:

[    38,5480920] agpgart: Apeture conflicts with pci mapping.


It then continued by showing me the text mode install which seems to be folded on itself. I'm pretty sure I can guess the cause of this. It's probably the SiS video driver which I might have to specify. 


Does anyone know how I can do this from the command line interface? I probably have to type F6 and add something to the boot options to specify my video driver to sis. Help anyone???



[IMG]http://www.uploadfile.info/uploads/4ce1e83c9f.jpg[/IMG]

---

### Post by kuja on 2006-09-18
Did you check the md5 of the cd after you burned it? You can verify if it burned correctly probably by  selecting "Check CD for Defects" in the screen that you numbered 1. 

You mention an SiS video driver though...  Ubuntu **should** detect that okay, it's one of the many video drivers that is available that Ubuntu includes.

Edit: Wait a minute, I just now noticed that you're on a laptop....  Silly me not to look at that... 

Try pressing F4 (and maybe the other screens that involve pressing Function keys) when you get to the screen with the options on how to boot. it might have options related to your VGA, or perhaps something else that might otherwise help you.

---

### Post by komputes on 2006-09-18
> **kuja said:**
> Did you check the md5 of the cd after you burned it? You can verify if it burned correctly probably by  selecting "Check CD for Defects" in the screen that you numbered 1. 


I checked the MD5 of the ISO before burn. I did check the CD for defects, it gave me the same folded screen so I couldn't see the result, but it did go through the whole thing. I will try the F4 thing and get back to you.

---

### Post by komputes on 2006-09-18
:grin: Whoa! I'm happy to report that I am currently posing a response in Ubuntu using Firefox. We did it, thank you. I will share my knowledge with all so that future users witha Acer Aspire 5000 or more specific Acer Aspire 5002WLMi understand what they need to do to be able to install Ubuntu on their box.

1 )Download ubuntu-6.06.1-alternate-amd64.iso
2 )Download [MD5Checker]("http://www.softgears.com/WinMD5.html") Utility
3 )Run MD5 and make sure it equals to b9a5be3a5858ade278d664d41310a4ab (version specific) to make sure that your copy has not been tinkered with.
4 )Burn the iso disc image with your burn software of choice Nero/EasyCD/etc
5 )Reboot with the disc in the drive
6 )On the boot screen press F4 and select 640x400 instead of VGA
7 )Select Text install and follow the instructions for install
8 )At network configuration, plug in your ethernet and run DHCP (this will allow automatic updates)
9 )At Disk Partition Manager select your configuration (keep in mind 256MB swap[logical] and 2GB ext3[primary] are the min. requirements)
10 )Enjoy

Now to get NDISwrapper to work so that my wireless card works...
Also I've heard that the PCMCIA card slot doesn't work (no drivers). I hardly use it but I like to know that everything on my machine is compatible and working.

[CENTER]
:grin: Happy Happy, Joy Joy, Happy Happy, Joy :grin: [/CENTER]

---

### Post by alexfittyfives on 2006-09-26
Hi,

Good work on the install!

I'm thinking of getting one of these to run Ubuntu on... Did you get the wireless up and running? How's the performance and are there any other niggles?

Thanks!

---

