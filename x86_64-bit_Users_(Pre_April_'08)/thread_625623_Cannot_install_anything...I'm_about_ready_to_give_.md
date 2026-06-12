---
title: "Cannot install anything...I'm about ready to give up and i'm a first time user!"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mattaus on 2007-11-28
I've recently installed Ubuntu 7.10 on an external HDD and after a lot of trouble I finally got it running on the damn thing. Originally I had the 32-bit version but I couldn't install anything and some people here suggested the 64-bit version as the PC I'm running it off has Vista 64 running on it at the moment. So I did that and things got a lot better. Except now when I try to install practically anything I get errors, followed by a message telling me certain dependencies could not be installed and to top it all off it then says Unsupported Architecture.

The main problem is related to trying to install the Drivers for my 2900XT. I downloaded the 7.11 drivers and did everything in the Wiki page but it still gives me the same errors every time. I've attached a picture of 2 methods I attempted (in the terminal, the picture is gray scale because I saved it as a gif image. All the ATI Headers are red in case that helps :) )

But yeah, everything I do relies on dependencies I cannot install ( no idea how! )

If anyone could help me that would be really great. I want to give Ubuntu a good go but as it stands I can't even test any applications on it other than the stuff it comes with :(

EDIT: And the same goes for the flash plug in. If I try to install it with *sudo apt-get install flashplugin-nonfree* (or whatever it is) I get the same sort of problems.

---

### Post by athomson on 2007-11-28
Hi 

The output message you posted gives you a big hint :-)

dpkg-architecture: not found

You need at least these two packages:

```
sudo apt-get install build-essentials debhelper
```

Search on the Forum for ATI install, this is a frequently encountered problem.

---
Andy

---

### Post by Cappy on 2007-11-28
Go to System-->Administration-->Software Sources
and check all of the check boxes except "Source Code" (which is optional)

And then try running > sudo apt-get update; sudo apt-get install dpkg-dev module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

The directions are at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually)

---

### Post by Rhubarb on 2007-11-28
An easy way to install flash on 64 bit ubuntu, is to visit a website that has flash on it (this does not work on youtube for some reason).
Try visiting [http://www.tomshardware.com/](http://www.tomshardware.com/)
Click on the install missing plugins, and follow the prompts.

---

### Post by Mattaus on 2007-11-28
Ah, see clues are useless to me at the moment because I dont know what im looking at :)

If Iw asnt playing TF2 right now in Vista I'd give it a try. Thanks heaps, soon as I get a chance i'll get right onto it.

---

### Post by Mattaus on 2007-11-28
Oha dn sorry Rhubarb, thats how I found out it wouldnt install, even that wouldnt work!

I might try the other suggestion and see if that helps.

---

### Post by Kilz on 2007-11-28
> **Mattaus said:**
> Oha dn sorry Rhubarb, thats how I found out it wouldnt install, even that wouldnt work!

I might try the other suggestion and see if that helps.

open a terminal and type in

```
sudo apt-get install flashplugin-nonfree
```

For the ATI driver problem. [Go here and follow this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually"). Copy (highlight and right click, choose copy) and then paste (right click on the terminal and choose paste) the commands into the terminal. This will avoid spelling and case mistakes.

---

### Post by Mattaus on 2007-11-28
I used Cappy and athomson's help and I managed to get it all installed fine. Flash even installed!

I now have the right resolutions for my desktop (yay) but now Im having problems getting 3D Desktop effects working. Though I'll try a little harder before I post anything here.

Thanks heaps to all!

EDIT: Got that working too! I can finally start using Ubuntu the way I want...lets see how long vista lasts now ;D

---

