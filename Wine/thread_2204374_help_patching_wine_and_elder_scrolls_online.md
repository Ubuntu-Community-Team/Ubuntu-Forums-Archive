---
title: "help patching wine and elder scrolls online"
date: 2014-02-08
forum: Wine
---

### Post by mywars on 2014-02-08
ok now I'm completely lost, and dont know what I'm doing,
my distro is ubuntu 12.04
I just followed these guides:
first here 
[http://wiki.winehq.org/BuildingBiarchWineOnUbuntu](http://wiki.winehq.org/BuildingBiarchWineOnUbuntu)
installed wine64 and wine32
then this guide
[http://wiki.winehq.org/FAQ#head-8a17a13a8a4cda9e12e24a1ad4e1b1aaf043d581](http://wiki.winehq.org/FAQ#head-8a17a13a8a4cda9e12e24a1ad4e1b1aaf043d581)
but it doesn't say how to apply patch to wine, so I had to find it out by myself
followed this thread 
[http://ubuntuforums.org/showthread.php?t=712407](http://ubuntuforums.org/showthread.php?t=712407)
and this
[http://askubuntu.com/questions/272934/compiling-patched-wine-from-git](http://askubuntu.com/questions/272934/compiling-patched-wine-from-git)
and patch worked somehow...but not...

for game bug report is here
[http://bugs.winehq.org/show_bug.cgi?id=34388](http://bugs.winehq.org/show_bug.cgi?id=34388)
and they say it worked for them

the problem is neither of them says how to unninstall any previous versions of wine so I just left them intact
so I guess I have like 4 different wines? does it matter? or I did something wrong?

---

### Post by Arch_Nemesis on 2014-02-08
Normally when you install a new version of wine, it will actually go  through and automatically remove the old ones...  However, I am not 100%  sure that is a correct statement in -all- cases...  Your best bet would  be to actually check in the software center, and see which version(s)  are available.  It also sounds to me that you likely have a few packages  on your computer that you don't even need.  I would recommend doing a  few commands in the terminal

sudo add-apt-repository ppa:tualatrix/ppa  ##This will add the  application repository for the program that I will soon recommend  installing
sudo apt-get update      ##This command will update your  current repositories with the most up-to-date software, but however will  not install them.
sudo apt-get upgrade    ## This command will  actually fetch new versions of packages that exist on the machine,  through your current reposistories
sudo apt-get autoremove    ##This  command will remove packages that have been installed to satisify  dependencies for some package and is no longer needed
sudo apt-get  install ubuntu-tweak    ##This command will install the Ubuntu Tweak  program, which will be required for the following steps.

From there you want to go to your Dash and type in Ubuntu Tweak, or just Tweak, and open the program labeled "Ubuntu Tweak"

On that first screen that pops up after the program is done loading, and has completely opened, click on the "Janitor" button located towards the bottom right hand corner.  It will be located to the right of "System Cleanup", or can be located in the top 5 tabs of "Overview", "Apps", "Tweaks", "Admin", and "Janitor".

Once you are in the janitor area of the program, go ahead and select -everything-...  That is unless you use CD Tool to perform backups of your APT's...  It is also a good idea to make sure that you've done the command 'sudo apt-get update' before using this tool to clean everything out.

As for getting ESO to work... Honestly, I understand how you are right  now... I'm wanting to play my ESO Beta Account as well, but cannot do so  because I do not have the patience to completely mess up my wine  install, which seems to be working for WoW fine atm.  My highest  recommendation, would be to contact people on the Wine Sub-Forums of  UbuntuForums.org, or contact Wine directly through their forums, asking  for a highly detailed tutorial on how to install ESO.  Including all  terminal commands, starting from the ground up.  From there, if you find  someone who can help you, just go into the Software Center in Ubuntu,  and uninstall Wine...  OR... run the command

sudo apt-get remove wine

then  perform the above stated steps for installing and running Ubuntu  Tweaks.  Which will clean the system of any unneeded files that may be  related to Wine...  From there you can start fresh, with a brand new install of wine, where it is the only version of wine.  This will also allow you to follow any "tutorial" offered, from those who support Wine, to a "T".

---

### Post by sffvba[e0rt on 2014-02-09
*Thread moved to **Wine**.*

---

