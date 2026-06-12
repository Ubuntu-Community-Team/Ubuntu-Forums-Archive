---
title: "how do i install diablo II?"
date: 2008-10-13
forum: Wine
---

### Post by strycx on 2008-10-13
I am completly new to ubuntu and i am trying to install diablo 2 and play it again. Someone told me to get WINE but i have no idea what it is or how to use ubuntu. I have tried typing in some codes but it usually says 

alicia@alicia-laptop:~$ sudo apt-get install wine
sudo: unable to resolve host alicia-laptop
[sudo] password for alicia: 


Keep in mind that i am not smart at all, yet i thought i could do this for some strange reason... any help would be very... helpful...

---

### Post by Gcentrex on 2008-10-14
> **strycx said:**
> I am completly new to ubuntu and i am trying to install diablo 2 and play it again. Someone told me to get WINE but i have no idea what it is or how to use ubuntu. I have tried typing in some codes but it usually says 

alicia@alicia-laptop:~$ sudo apt-get install wine
sudo: unable to resolve host alicia-laptop
[sudo] password for alicia: 


Keep in mind that i am not smart at all, yet i thought i could do this for some strange reason... any help would be very... helpful...

This is easy read this guide

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Then follow the instructions here 

[http://appdb.winehq.org/appview.php?versionId=49](http://appdb.winehq.org/appview.php?versionId=49)

If you have the download version then it will run right away after installing geko engine.

---

### Post by strycx on 2008-10-14
when i try to load it through wine it says 

UNHANDLED EXCEPTION:
ACCESS_VIOLATION (c000005)

I still had the cds from a long time ago, so i didnt download it, but i suppose i could try to find the gecko engine to see if that helps. any further information would be greatly appreciated.

---

### Post by Gcentrex on 2008-10-14
> **strycx said:**
> when i try to load it through wine it says 

UNHANDLED EXCEPTION:
ACCESS_VIOLATION (c000005)

I still had the cds from a long time ago, so i didnt download it, but i suppose i could try to find the gecko engine to see if that helps. any further information would be greatly appreciated.

Ok first off I would make sure you have the new version of wine 1.1.6 use the link I provided before to setup your system to auto update to the current wine version then install as normal and if an update shows up right after apply it. Make sure to remove your current .wine folder just incase run winecfg from the menu to setup a new .wine folder.

Next go to the Blizzard web site and go to the store page, register an account then look for verify email do that, wait for the email if you dont have it after 24 hours ask for it to be resent, once your verified you will be able to register your games CD-keys do it, then download the file to download the client, also make a note of the new cd-key thats is listed with the download as it will be a different one then on your cd case.

Now try to run it, it should then ask you if you want to install geko engine so do it, let the client download, after its downloaded install it enter the cd-key and it will run as it did in windows. Same with the expansion also.

---

### Post by strycx on 2008-10-15
I must be the king of bad luck. I have WINE 1.1.6 installed, but  whenever i download the gecko from "https://www.blizzard.com/account/" it begins to say  There was a problem authenticating your download. goto [https://www.blizzard.com/account/](https://www.blizzard.com/account/) to start a new download. 

I have started a new download several times, but no luck yet. I am like this close to going to 64 bit XP.

---

### Post by Gcentrex on 2008-10-15
> **strycx said:**
> I must be the king of bad luck. I have WINE 1.1.6 installed, but  whenever i download the gecko from "https://www.blizzard.com/account/" it begins to say  There was a problem authenticating your download. goto [https://www.blizzard.com/account/](https://www.blizzard.com/account/) to start a new download. 

I have started a new download several times, but no luck yet. I am like this close to going to 64 bit XP.

Gecko is the IE replacement rendering engine for Wine and will ask to be installed when required.

Hum I downloaded the WOW demo as in the full client from the site with no issue last night so that seems strange if it needs to be authenticated then use doing this instead try using a virtual machine to download the client but I have had no issue downloading Diablo 2 using wine so only thing I can think is use a virtual machine to get it, use VirtualBox listed in Add/Remove instead of getting another version.

---

