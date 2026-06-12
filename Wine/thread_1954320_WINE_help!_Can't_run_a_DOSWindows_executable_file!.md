---
title: "WINE help! Can't run a DOS/Windows executable file!"
date: 2012-04-07
forum: Wine
---

### Post by StaRRx on 2012-04-07
So here is me my story (which you can skip, but it'll make me feel better :-|):

A few months ago I let me cousin borrow my very good laptop for a day or two so he can do some school work since his outdated dinosaur wouldn't start. All he had to do was use the interwebz and Microsoft word, what harm would that do? A lot, apparently. I'm a HUGE gamer both PC and console, more PC. I played a competitive game called A.v.A which is graphically pleasing as well as gameplay. I had my laptop always cleaned and up to date to play the game smoothly and overall I had one hell of a gaming laptop. It was running windows 7 Home premium ( factory installed ) and I never had any problems with it until my cousin gave me back my laptop. I started up my laptop but it took like 10 minutes, but beside that everything run fine so I didn't suspect anything till the next morning. I was going to google something but it took forever to boot up but it didnt even boot. I got some strange 0xce000009 error and since then I've bought a brand new HDD and installed Ubuntu 11.04 on it and was satisfied until now. I have been playing Minecraft and Urban Terror on Ubuntu for 2 months now. But last week my old clan buddy said hes getting the clan back together to enter a competition and the cash prize is a total of $2,000. As soon as he said that I rushed to get Windows 7. 


The problem:

I didn't have the installation CD but I had the activation code so I got the .ISO version. I have a .ISO file that if I can find a way to run I can run the setup right now but I can't seem to run it with wine. I also have a setup.exe windows file that SHOULD run fine with WINE but it doesn't. I get a "Program error". What it exactly says: "The program setup.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience." Then it tells me it may be caused by a problem in the program or a deficiency in Wine. I have only used Ubuntu for web browsing and a couple games so I have now idea whats going on. If anyone could tell me how to RUN the .ISO ( not mount ) I'll be good since It'll start the setup ( not the setup.exe I was talking about ). Now, if anyone could help with WINE I will be fine also. If you need any other information just ask.

---

### Post by Max Blyss on 2012-04-07
Hey, I'm only a couple years into Ubuntu, so I may be blowing smoke, but - 

I think you'd have to load Win 7 in Virtualbox or something.  While I'm not too familiar with the limitations in Wine, I don't believe it is geared to run an OS, it's just a Windows emulator for programs, games, etc...

If I read you post wrong, or am wrong in my idea, please let me know.):P

---

### Post by StaRRx on 2012-04-07
Thanks for the reply.

Im not trying to actually run Windows 7 using Wine just run the setup which is a Windows program. But since this is kind of complicated and shiz I'll wait for a couple more replys then just find a installation cd of vista or xp.

---

### Post by Redblade20XX on 2012-04-07
I don't think you can run the windows installer inside linux. You should just burn the .iso to a cd or create a bootable usb and load it through the bios, the normal way. Just my opinion!

- Red

---

### Post by StaRRx on 2012-04-08
> **Redblade20XX said:**
> I don't think you can run the windows installer inside linux. You should just burn the .iso to a cd or create a bootable usb and load it through the bios, the normal way. Just my opinion!

- Red

If only I knew how :/ Thanks for the reply, I'll search around google.

---

### Post by Karlchen on 2012-04-08
Hello, StaRRx.

Removing all the distracting and irrelevant details from your initial post, what seems to be the situation is this:

[LIST]
[*]Currently you are running Ubuntu on your notebook.
[*]You wish to re-install Windows 7 on it.
[*]You have downloaded a genuine Windows 7 ISO installation image.
[*]You have got the required installation keycode. (Can be found on the bottom cover of the notebook.)
[*]You are trying to install Windows 7 from inside Ubuntu/Wine.
[/LIST]
Final verdict on this approach: No. This cannot be done.

Instead proceed like this:

[LIST]
[*]Burn the downloaded ISO image to a DVD. Do not simply write the ISO file as a data file to the DVD. Instead burn it as an image to the DVD. The burning programme should have an option to create a bootable DVD from the ISO image file.
If you do it right then you will have a bootable Windows 7 installation DVD.
[*]Boot your notebook from this installation DVD. Install Windows 7 on your notebook. When prompted enter your keycode in order to activate Windows 7
[/LIST]

**The questions which you should decide upon before starting to install are these**:

[LIST=1]
[*]Do you want to keep Ubuntu installed on your machine and add Windows 7 as a second system?
[*]Or do you want to replace Ubuntu and replace it by Windows 7?
[/LIST]
In case you wish to replace Ubuntu by Windows 7 you will have to remove the existing Ubuntu filesystems and partitions from the machine. Ubuntu uses Ext4 filesystems which Windows 7 cannot use and does not even recognize.
You should boot the machine using a Ubuntu live CD/DVD, launch gparted and remove any existing Ubuntu related filesystems.
Next you can boot your Windows 7 installation DVD and start installing Windows 7.

In case you wish to keep Ubuntu and add Windows 7 as a second OS - dual boot system - you may have to free up enough disk space so that the Windows 7 setup will find enough unused disk space which it can use to install Windows 7.
In this case, too, you should boot the machine using a Ubuntu live CD/DVD, launch gparted and reduce the sizes of the Ubuntu filesystems.
Once done, you can boot your Windows 7 installation DVD and start installing Windows 7.

Sorry, cannot be more precise at this point in time without knowing any details on available harddisk space, the existing partitions etc pp.

Kind regards,
Karl

---

### Post by oldos2er on 2012-04-08
Thread moved to Wine.

---

### Post by StaRRx on 2012-04-08
> **Karlchen said:**
> Hello, StaRRx.

Instead proceed like this:

[LIST]
[*]Burn the downloaded ISO image to a DVD. Do not simply write the ISO file as a data file to the DVD. Instead burn it as an image to the DVD. The burning programme should have an option to create a bootable DVD from the ISO image file.
If you do it right then you will have a bootable Windows 7 installation DVD.
[*]Boot your notebook from this installation DVD. Install Windows 7 on your notebook. When prompted enter your keycode in order to activate Windows 7
[/LIST]



Thank you Karlchen! But using Ubuntu I have no idea how to do this using a USB. I've tried countless times using a 4gb USB. I would just burn it to a DVD but I don't have one bigger then about 700mb. And about clean booting Windows 7, how big of a disc would I need? And where could I find a download for it?

Many thanks, StaRR!

---

### Post by forrestcupp on 2012-04-08
[Here is an older HowTo](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html) that tells how to create a bootable Windows 7 USB stick from your iso file in Ubuntu. It's an older article, but it should still work the same. When you do the part with GParted, just make sure you are really messing with your USB stick and not your hard drive. After you complete this, keep the USB stick plugged in, and when you boot up your computer, press whatever key it says will take you to the boot menu when it flashes on the screen in the beginning. When you get to your BIOS boot menu, choose to boot to the USB, and install Windows 7.

> **Karlchen said:**
> 
In case you wish to replace Ubuntu by Windows 7 you will have to remove the existing Ubuntu filesystems and partitions from the machine. Ubuntu uses Ext4 filesystems which Windows 7 cannot use and does not even recognize.
You should boot the machine using a Ubuntu live CD/DVD, launch gparted and remove any existing Ubuntu related filesystems.
Next you can boot your Windows 7 installation DVD and start installing Windows 7.You were right on about everything, but this part is unnecessary. You can delete, add, and format partitions from within the Windows 7 installation. It doesn't matter what filesystem they have because it's accessing the partition table, and not trying to browse them.

---

### Post by StaRRx on 2012-04-08
> **forrestcupp said:**
> [Here is an older HowTo]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html") 

You were right on about everything, but this part is unnecessary. You can delete, add, and format partitions from within the Windows 7 installation. It doesn't matter what filesystem they have because it's accessing the partition table, and not trying to browse them. 
  Thanks for the link! and I don't have to make the Live cd?

---

### Post by Karlchen on 2012-04-09
Hello, forrestcupp.

Thank you for correcting my error about what the Windows 7 installation programme can do: I was not sure whether the Windows 7 setup would be able to remove a Ubuntu partition (ext3, ext4). So I suggested to use Ubuntu to do so.

Thank you for clearing up how to achieve the goal directly.

Happy Easter days.
Karl

---

### Post by Karlchen on 2012-04-09
Hello, StaRRx.
> **StaRRx said:**
> I don't have to make the Live cd?No. The article explains how to use a live USB stick instead: [B][Create A Bootable Windows 7 USB Drive From Linux (Tested On Ubuntu)]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html")

[/B][I]By the way, you cannot install Windows 7 from a CD, because a CD is too small to hold the installation package. The downloaded Windows 7 ISO installation package will be much larger than 700 MB. The article which forrestcupp pointed you to explains how to use a USB drive instead of using a DVD.

[/I]But in any case you will need to have the complete Windows 7 installation ISO file. Therefore this question confuses me a bit: > **StaRRx said:**
> And about clean booting Windows 7, how big of a disc would I  need? And where could I find a download for it? because a previous statement in this thread suggested you had already downloaded the Windows 7 ISO file. > **StaRRx said:**
> I didn't have the installation CD but I had the activation code so I got the .ISO version. I have a .ISO file

In case you should not have the needed Windows 7 ISO file, please, use this link to determine which ISO file you need and which ISO to download: [**[SOLVED] Official Windows 7 SP1 ISO Image Downloads  **]("http://www.w7forums.com/official-windows-7-sp1-iso-image-downloads-t12325.html")

_Note:_
In case you have lost the Windows 7 installation keycode which the vendor of your notebook had attached to the bottom side of your notebook, installing Windows 7 with the help of a downloaded ISO file will give you a 30-days-trial version.
In case you have got the Windows 7 installation keycode which the  vendor of your notebook had attached to the bottom side of your  notebook, you can use this keycode during the installation process or afterwards to activate your Windows 7 Home Premium.

Anyway, as soon as you have got the required Windows 7 installation ISO file, you should proceed exactly as explained in the article which forrestcupp pointed you to:  **[Create A Bootable Windows 7 USB Drive From Linux (Tested On Ubuntu)]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html")**

Note the last sentence in the article: > After Unetbootin is done, you can use the USB stick to install Windows 7  on any computer that supports booting from an USB drive. What you have achieved at this point in time is this: you have got a bootable USB stick which holds the complete Windows 7 installation package. Now you need to boot your notebook from this stick and go through the Windows 7 installation steps.

Good luck,
Karl

---

### Post by forrestcupp on 2012-04-09
> **Karlchen said:**
> 
In case you should not have the needed Windows 7 ISO file, please, use this link to determine which ISO file you need and which ISO to download: [**[SOLVED] Official Windows 7 SP1 ISO Image Downloads  **]("http://www.w7forums.com/official-windows-7-sp1-iso-image-downloads-t12325.html")

Thank God for legal ISO downloads. Those came in handy for me a while back. I only wish they still had the Vista ISOs available for an old laptop that I have. I probably can dig up the old DVD somewhere, but it won't have the service packs slipstreamed in.

---

### Post by Dlambert on 2012-04-09
WinUSB works great!

---

### Post by StaRRx on 2012-04-15
THANK YOU!!! You guys are absolutely amazing. The best community EVER! I used UNetbootin and everything went so smoothly. I started fresh and everything is running great! Thanks again! You all are the best!

SOLVED!

---

