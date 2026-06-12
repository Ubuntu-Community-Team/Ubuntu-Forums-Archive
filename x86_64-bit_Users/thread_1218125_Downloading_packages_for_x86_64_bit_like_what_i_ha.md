---
title: "Downloading packages for x86 64 bit like what i have for 32 bit"
date: 2009-07-20
forum: x86 64-bit Users
---

### Post by ramnarayan on 2009-07-20
Hi

Over the past few days i have managed to setup my 32 bit system with 9.04 and will all the packages i think i may need , specially before returning to the wild broken internet zone.

However i also have an unfreed 64 bit pc that needs to be converted :biggrin:

i need to download all these packages and keep them together till i get to the machine.

I know i know keryxx etc but the *problem* is that i want to download exactly (or somewhat) what i have installed on my 32 bit system (basically to make my life easier) i will know what to download.

So is there anyway i can get a list of whats installed on my current system and feed it to some download too and make that get me those related packages for 64 bit.

Hope that was clear , however in summary i have a 32 bit fully set up and want the same on 64 bit but don;t have internet access (on the 64 bit) so how do i get almost the same set of packages to carry to the 64 bit.

thanks

---

### Post by ramnarayan on 2009-07-20
Yet another BUMP

---

### Post by Rizlaw on 2009-07-20
> **ramnarayan said:**
> Hi

So is there anyway i can get a list of whats installed on my current system and feed it to some download too and make that get me those related packages for 64 bit.

Hope that was clear , however in summary i have a 32 bit fully set up and want the same on 64 bit but don;t have internet access (on the 64 bit) so how do i get almost the same set of packages to carry to the 64 bit.

thanks


You can try the following, which I believe should work for all packages installed via Synaptic/apt on your 32bit system:

On your existing 32 bit Jaunty system, open Synaptic Package Manager, click on the "Files" menu, then click on "Save Markings as" and provide a filename of your choice and a location to save the new file. Also, make sure to check the box that says "Save Full State, not only changes" BEFORE you click the "Save" button.

This will save all of the package information about your 32bit Ubuntu installation. Install your basic Ubuntu 64 bit Jaunty OS, then copy the file to your new 64bit installation and go back into Synaptic Package Manager and click on the "File" menu, then "Read Markings" and find and load the previously created file with all of the info about your 32bit sources. Of course, this requires Internet access to download and reinstall all the packages. Since you seem to indicate that the 64 bit computer will not have Internet access, then you might try "aptonCD" which you can find here: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

The only thing I'm not absolutely sure about, never having done this from 32bit to 64bit, is whether the 64bit system will attempt to load 32bit packages or 64bit packages. My assumption is that it will try to load 64bit versions, if they exist, since your 64bit OS will be looking at 64bit repositories.

P.S. The "Synaptic" method will not pick up any packages you installed outside the Ubuntu Repositories from 3rd Parties or PPA's. If you have added packages from PPA's you probably have edited your "Sources" file to add 3rd party PPA's. You will have to modify your 64bit /etc/apt/sources.list to add the additional 3rd party PPA's before you attempt what I have outlined above. 

Also, "AptonCD" makes it clear that it will only copy packages installed via: apt, aptitude or Synaptic Package Manager. Therefore, any .deb packages from get-deb.net and installed via gdebi would probably not be copied by aptoncd.



Hope this helps a little.

---

### Post by SuperSonic4 on 2009-07-20
> **Rizlaw said:**
> You can try the following, which I believe should work for all packages installed via Synaptic/apt on your 32bit system:

On your existing 32 bit Jaunty system, open Synaptic Package Manager, click on the "Files" menu, then click on "Save Markings as" and provide a filename of your choice and a location to save the new file. Also, make sure to check the box that says "Save Full State, not only changes" BEFORE you click the "Save" button.

This will save all of the package information about your 32bit Ubuntu installation. Install your basic Ubuntu 64 bit Jaunty OS, then copy the file to your new 64bit installation and go back into Synaptic Package Manager and click on the "File" menu, then "Read Markings" and find and load the previously created file with all of the info about your 32bit sources.

The only thing I'm not absolutely sure about, never having done this from 32bit to 64bit, is whether the 64bit system will attempt to load 32bit packages or 64bit packages. My assumption is that it will try to load 64bit versions, if they exist, since your 64bit OS will be looking at 64bit repositories.

Hope this helps a little.

It mainly depends on if Synaptic saves them as "name" rather than "name-version-arch"

---

### Post by ramnarayan on 2009-07-20
Hi

Thanks for the help

But some more clarity on my part

my 64 bit machine will not come near an internet connection for quite a while - its a desktop - so what i need is someway of knowing what packages i must download off location and then take back - also i don't have another 64 bit machine to do an apton on. (and a problem with apton is at [http://ubuntuforums.org/showthread.php?t=1218253](http://ubuntuforums.org/showthread.php?t=1218253))

So even if i were to physically download the packages i need to have a kind of list in front of me and was just hoping there was some automated way of going through the list.

thanks

---

### Post by Rizlaw on 2009-07-21
> **ramnarayan said:**
> Hi

So even if i were to physically download the packages i need to have a kind of list in front of me and was just hoping there was some automated way of going through the list.

thanks

As far as a "list" is concerned, the first method I outlined produces a file which is nothing more than a "list", by name, of every package/dependency installed on your 32 bit computer as of the time you created the list. Unfortunately, the list is not alphabetical, nor is it grouped by application name/dependencies. Furthermore, it is subject to the same limitations I previously mentioned about 3rd party installed software. All you have to do is click or double click on the file created and you can see what I'm talking about. If this doesn't give you what you need, then I guess you'll have to wait for someone else to come up with better suggestions.

---

### Post by litspliff on 2009-07-21
my fear is that synaptic will grab the 32-bit packages, but AFAIK, they will still work if they aren't platform specific, but they will only run in 32 bit mode....someone correct me if i'm wrong....


my suggestion....use 32bit. you don't want to be stuck in the middle of the himalayas with a bricked machine, and 32 is much more stable/compatable with any packages you may be looking for. 


take a jaunty-32-DVD with you, and you should have a good selection of packages to do whatever with. get tarballs for whatever else you might need.

---

### Post by zwdev on 2009-07-22
I second Litspliff even more you can create a live backup for your installation and you just install everything in one click the same way it is on your offline machine. some 32bit packages will  install on 64bit but will create issues, I have tried it but it created a lot of headaches fixing the broken packages, I ended up installing a 64 bit version on my laptop and virtualizing the 32 bit to prepare the installation for my 32 bit offline system.

---

