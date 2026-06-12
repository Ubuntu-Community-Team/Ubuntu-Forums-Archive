---
title: "help with ati installation"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jeremy1138 on 2007-08-09
ok so I tried to use the ati driver installer file name: ati-driver-installer-8.16.20.run and when I try to start it up I get an error that says 'Could not open the file /home/jeremy/Desktop/ati…ler-8.39.4-x86.x86_64.run using the Western (ISO-8859-15) character coding.'...  What do I do about this?  I'm not sure if it matters but I'm using an HP laptop model number dv5020us with an ati radeon xpress 200m video card.  The microprocessor is a 64 bit amd turion.  This laptop has a widescreen display and right now it's using a generic driver and is running at 1024x768 resolution (not widescreen).  I'm a real novice at this and I'm not sure what to do...  Any help would be greatly appreciated.  Thanks!

---

### Post by Kilz on 2007-08-09
The ati setup is difficult and can become a real problem. Here are links to 2 good pages on how to install those drivers.

[Make sure to do the preinstall checks]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Pre-Installation_Checks") Then [follow this method]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually").

Also 

[This page can also be helpful,]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") but its much more confusing as it deals with multiple versions of Ubuntu on one page.

---

### Post by jeremy1138 on 2007-08-09
ok none of this stuff works because I cant get that ati installer to start...  Something is screwed up...  Whenever I try to start that installer I get an error that reads 'Could not open the file /home/jeremy/Desktop/ati&#8230;ler-8.39.4-x86.x86_64.run using the Western (ISO-8859-15) character coding.'

---

### Post by Kilz on 2007-08-09
> **jeremy1138 said:**
> ok none of this stuff works because I cant get that ati installer to start...  Something is screwed up...  Whenever I try to start that installer I get an error that reads 'Could not open the file /home/jeremy/Desktop/ati…ler-8.39.4-x86.x86_64.run using the Western (ISO-8859-15) character coding.'

Right click on the file, choose properties, click on the permissions tab, check the box next to  "Allow executing this file as a program" then click close.

---

### Post by jeremy1138 on 2007-08-09
Thanks Kilz!  As I said I'm a real rookie at this so I have no idea what I'm doing...  It's working now...  Though beryl doesn't work...  Is that something that I'm going to have to deal with because I'm using an ATI card?

---

### Post by Kilz on 2007-08-09
> **jeremy1138 said:**
> Thanks Kilz!  As I said I'm a real rookie at this so I have no idea what I'm doing...  It's working now...  Though beryl doesn't work...  Is that something that I'm going to have to deal with because I'm using an ATI card?

Setting up Beryl is hard regardless of the video card you have.

---

### Post by Lonthong on 2007-08-10
Depending on the type of yr card, you might want to try from restricted drivers manager.
To run beryl / compiz / compiz fusion, you will have to install xgl as well.
Out of the three, for me compiz fusion is the best. So far no problem what so ever.

My card is integrated ATI X 1100 (basically is the same as x200).

Prior to Feisty, I always used proprietary ATI driver (Edgy & Dapper) & never faced installation problem.
However, at that time I never played with Berul nor Compiz.

---

### Post by michael37 on 2007-08-10
I am a fairly experienced user, and I still couldn't get ATI driver working from the ATI website.  Try this FAQ, you may find it easier.  It installs the same binary driver from ATI (called fglrx), but it makes it way easier.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=fglrx](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=fglrx)

---

