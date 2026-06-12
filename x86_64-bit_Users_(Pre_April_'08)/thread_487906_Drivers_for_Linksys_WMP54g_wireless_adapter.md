---
title: "Drivers for Linksys WMP54g wireless adapter"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by stevo1977 on 2007-06-29
i have spent much time searching these forums and the web at large on this issue (there is tons of stuff) and have yet to find a satisfactory solution (meaning that i still can't use my wireless card on ubuntu).  if i have missed something that may help, please direct me there.  also, i wasn't sure if this question would be more appropriate in this section or in the 'network/wireless' section, so i decided to start here. please advise if the other would be better.

currently i have ubuntu 6.06 (for amd64) installed on my amd64 2400 machine, with another partition for windows xp on the same hd.  i have ndiswrapper (and the gui, because i'm still adjusting to the terminal interface), but my main problem is that i can't find the proper .inf file to install, and i'm not even sure if ubuntu sees my card.  fyi, i have looked through my windows\inf folders and tried a number of them.  windows tells me that the driver for my card is 'rt2500.sys,' and a grep search tells me that the only file in the \inf folder with 'Rt2500.inf' (case-sensitive) is 'oem7.inf'.  i installed this .inf file with ndiswrapper, but the gui says that the hardware for this driver is not installed.

i know that the directions for windows xp (from linksys) tell you to install the drivers first, and then plug the card into the pci slot.  i tried restarting ubuntu after installing the 'oem7.inf' driver, but it still doesn't see what it's looking for.

please let me know what additional information i can provide that will help things along.  thank you very much.

stevo

---

### Post by titaniumlou on 2007-09-10
I'm having some problems too, I can't find the actual rt2500 dll files for a Windows 64 bit system.  I have downloaded the 64-bit driver from the ralinktech website, but since I don't have a 64-bit copy of windows, does anyone have suggestions for how I might be able to extract the dll's from that exe?

---

### Post by eph1973 on 2007-09-10
Have you tried downloading the driver from here:

[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843981&packedargs=sku%3D1150490054358&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4398154358B07&displaypage=download](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843981&packedargs=sku%3D1150490054358&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4398154358B07&displaypage=download)

Looks like you enter your version number and model number as found on your card.  I don't know if they will have a native Linux driver on that site (I did not have a model number to check out what the options were).  If not, I would recommend you just use whatever 32 bit drivers you can (32 bit software can run just fine on the 64 bit CPU) along with your ndiswrapper.

If you need help with ndiswrapper, check out this site:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I hope that helps a bit.  Good luck

---

### Post by tgalati4 on 2007-09-11
You may have to blacklist the driver that automatically gets loaded to get ndiswrapper to install properly.

---

### Post by titaniumlou on 2007-09-11
I thought that the 64-bit ndiswrapper wouldn't be able to properly load & run the 32-bit driver, am I wrong on that point?

Also, the Linksys site has a link to download the same files which came on the CD with the wireless card, but looking through there I don't think I saw a 64-bit driver on the CD.  Maybe I missed it somewhere?

---

### Post by eph1973 on 2007-09-11
What version and model number wireless card do you have?  If you have v4.0 or 4.1 (not sure about earlier models, I would have to do another search), you would have a ralink chipset on there, and they have 64 bit drivers available from their website: [http://www.ralinktech.com/ralink/Home/Support.html](http://www.ralinktech.com/ralink/Home/Support.html)

Concerning your other question, yes, my fault, you must use 64 bit drivers while you are using a 64 bit kernel.  However, you can use a 32 bit distro on a 64 bit machine, with no problems.  My apologies on that misunderstanding.  Certain other 32 bit applications can run in the 64 bit kernel, but you need to use 64 bit drivers with ndiswrapper while in a 64 bit kernel.  But from the looks of it, you should be able to get a 64 bit driver for your wireless card.  If you reply with the version number I asked for, I would be happy to help you locate a good 64 bit alternative driver (since, like I said, it looks like you actually have a ralink chipset on your wireless card).

---

### Post by titaniumlou on 2007-09-11
Thanks eph1973, I have been to the Ralink support site but the download they have for the Windows 64-bit driver is an installer exe, and I even tried running that in wine on my 32-bit laptop but didn't see any new dlls in the system32 folder.  Maybe there's some other way I can get the dll and/or .inf file out of that exe??

I get the impression all of this wouldn't be a problem if I had 64-bit Windows installed on the same machine I have running 64-bit Ubuntu, but I didn't feel like paying for the 64-bit version when I wanted to be running Linux primarily, and already had a 32-bit copy of Windows XP available.  Guess I should stop being such a cheapskate.  :-D

Anyway, my wireless card has model # WMP54GV4, so it's the v4.0 model of the WMP54G

Appreciate all your help thus far!

---

### Post by eph1973 on 2007-09-11
Here are two options:
Try this first:

```
sudo apt-get install rt2500 rt2500-source
```On my aptitude those are listed as universe packages under net.  There should be some documentation explaining what you should do with them.

Secondly:
[http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html)
You could download the Windows version from this website.  It looks like it has all the drivers automatically.  I don't know if it gives you the option of selecting a driver, or if it automatically detects your hardware and installs the appropriate driver.  You could try downloading it onto your Windows and running it, and see if it lets you extract a 64 bit driver from that file or not.

Sorry, but as of now, I am short on time, and must get going, have somewhere to be.  Good luck!

---

### Post by crjackson on 2007-09-11
> **stevo1977 said:**
> i have spent much time searching these forums and the web at large on this issue (there is tons of stuff) and have yet to find a satisfactory solution (meaning that i still can't use my wireless card on ubuntu).  if i have missed something that may help, please direct me there.  also, i wasn't sure if this question would be more appropriate in this section or in the 'network/wireless' section, so i decided to start here. please advise if the other would be better.

currently i have ubuntu 6.06 (for amd64) installed on my amd64 2400 machine, with another partition for windows xp on the same hd.  i have ndiswrapper (and the gui, because i'm still adjusting to the terminal interface), but my main problem is that i can't find the proper .inf file to install, and i'm not even sure if ubuntu sees my card.  fyi, i have looked through my windows\inf folders and tried a number of them.  windows tells me that the driver for my card is 'rt2500.sys,' and a grep search tells me that the only file in the \inf folder with 'Rt2500.inf' (case-sensitive) is 'oem7.inf'.  i installed this .inf file with ndiswrapper, but the gui says that the hardware for this driver is not installed.

i know that the directions for windows xp (from linksys) tell you to install the drivers first, and then plug the card into the pci slot.  i tried restarting ubuntu after installing the 'oem7.inf' driver, but it still doesn't see what it's looking for.

please let me know what additional information i can provide that will help things along.  thank you very much.

stevo

Okay - It looks like you have the same wireless card as me on one of my systems.  Here is the **[SIZE="3"][[COLOR="Red"]Link to my thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=483548")[/SIZE]** where I got mine working.  Have a good read and near the end you will find the working solution.  Just make sure you have the exact same chipset that I have posted in the thread.

---

### Post by eph1973 on 2007-09-12
I would try doing what crjackson did there.  Just skip to page 2 and follow the thread from there.  It looks like he got the same source files from serialmonkey.com.  They have a wiki, on a FAQ, that may be of some minor help here: [http://rt2x00.serialmonkey.com/wiki/index.php/FAQ](http://rt2x00.serialmonkey.com/wiki/index.php/FAQ)

But it looks like if you follow the complex instructions given in crjackson's thread, you should be able to get your wireless card going.  You can still try to sudo those two files, because they have all the source files you should need.  But anyhow, start reading from post #79 on crjackson's thread, and you should be able to follow it through to where you need to be.  The source files he downloaded from that website are available through sudo aptitude install rt2500-source (I downloaded the package from a debian site, and it has all those files he was talking about).  From there you should be good to go.  Looks like crjackson should be able to give you the nitty gritty details if you get stuck somewhere, also.  Good luck :-)

---

### Post by titaniumlou on 2007-09-18
Hi All, thanks for your suggestions, I did end up following the instructions in crjackson's thread & then everything worked for me!

I did have to change the encryption on my router to WPA instead of WPA2, but that was b/c RUTility didn't seem to be able to handle WPA2, though maybe I just messed up the config.

Anyway, thanks for all your help all, and sorry to hijack your thread Stevo

---

