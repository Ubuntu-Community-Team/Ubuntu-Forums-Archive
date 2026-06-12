---
title: "Ubuntu/Kubuntu with WINE"
date: 2013-06-30
forum: Wine
---

### Post by Tom_ZeCat on 2013-06-30
Right now I have no Linux PC.  Previously I had an Ubuntu 8.04 PC, which has since crashed.  However, I have a Windows 7 PC that I'm thinking of overwriting (or MAYBE making a dual boot) and installing either Ubuntu 13.04 or Kubuntu 13.04.  I've never used WINE before, but am thinking of giving it a shot because there are a few applications that don't have Linux version that I must use.  I was poking around on the WINE web page and found a list of downloads ([http://www.winehq.org/download](http://www.winehq.org/download)).  Is it a different download depending on whether I choose Ubuntu or Kubuntu?  Obviously, the first option listed is for Ubuntu.  However, I was reading that Kubuntu is based on Debian, so is the right WINE the second link on that list?  Or is it the same WINE as Ubuntu.  

And, of course, I need to make a choice between Ubuntu and Kubuntu.  Ubuntu might be a good choice because I've used it before.  Kubuntu might be a good choice because it's KDE and I've found I really like KDE software.

---

### Post by Ji Ruo on 2013-06-30
It's the same in both Kubuntu and Ubuntu. The WINE developers suggest using the ppa version which is more recent than that offered in the main repositories. I'm not sure if the stable version of WINE is already installed in standard Ubuntu, if it is you will want to delete it first.

To install it in Kubuntu, find Muon Package Manager in the System section of your menu and follow the same steps.

You can also install it using a terminal: Press <Alt+F2> to get the top launcher and type in ```
konsole
``` to get a terminal. Then ```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```Then```
sudo apt-get update && sudo apt-get install wine
```Does the same thing as doing all of that in Muon.

Happy Kubuntu user here :)

---

### Post by Tom_ZeCat on 2013-06-30
Thanks, Ji Ruo.  Last night after I posted, I checked out both Kubuntu and Ubuntu via the DVDs without installing.  I think I really like Kubuntu's interface better.  However, I did really like Ubuntu's application repository where you can just go in and click what you want installed.  I didn't find it in Kubuntu, but maybe I just didn't look in the right place.  Does Kubuntu have that?  

Also, it looks like ext4 is now the standard K/ubuntu file system now?  It was ext3 when I last used Ubuntu.  I have a Gparted boot disk.  I could use that to partition off a section for Linux.

---

### Post by KARNVORbeefRAGE on 2013-06-30
For the first part, just try dual booting in case something goes wrong.  Plus, not all Windows programs like WINE so if you still have Windows 7 on your machine they will still be functional.

---

### Post by Mark Phelps on 2013-07-01
BEFORE you charge down the Wine path, you could save yourself a lot of trouble by going to the WineHQ website and using their Application Compatibility database tool to get the ratings of the apps and versions you want to install.  Anything not listed, or rated less than Gold is going to be a waste of your time because even if you do install it, so much will not work that it will essentially be useless.

---

### Post by Tom_ZeCat on 2013-07-08
An update: I've got Kubuntu with WINE up and running now.  That advice on installing the latest version of WINE was spot-on.  I initially just used the Synaptic Package Manager to install WINE 1.4, figuring the stable version they had approved would be just fine.  Then I installed one of my favorite must-have Windows apps, Treepad Business Edition.  It didn't run so well.  Its toolbar icons were whited out and the app kept freezing.  The resolution of the text making up the tree was not very good.  I upgraded to the latest WINE, version 1.6-rc4, and that solved all these problems except the last one.  The tree is still readable.  The WINE upgrade made Treepad at least usable.  It will get me by until they come out with the Linux version.  I wrote them and learned they are indeed planning that.  Right now only Treepad Lite is available for Linux and I need the features in Biz.  

I've submitted a review of Treepad Business on the Wine HQ review site.  I rated it Gold.  It's not Platinum because of the text resolution problem.  

I was not able to maximize Treepad to cover my whole screen.  I also could not drag a corner to make it bigger than a limited space covering a little less than half my screen.  Is this normal?

---

