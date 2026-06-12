---
title: "MyPaint Causing Internal Error?"
date: 2021-08-28
forum: Wine
---

### Post by wyattwhiteeagle on 2021-08-28
When I installed and tried opening MyPaint, I got an "internal Error" message.

I attached a detail.

UPDATE:

A quick google search returned a result showing this as a bug. (Bug 38990)
[https://www.winehq.org/pipermail/wine-bugs/2015-July/418562.html](https://www.winehq.org/pipermail/wine-bugs/2015-July/418562.html)

UPDATE 2:

The page at the above link mentions a NVIDIA video card.

While I was on Ubuntu Bionic Beaver, I was informed that the following command line was for computer's with an NVIDIA video card.
My laptop doesn't have an NVIDIA video card. It has an Intel video card.

> *sudo apt-get install ttf-mscorefonts-installer*

Is there a way to correct this without resorting to a "clean" install?

I've been considering changing to a minimal install.

If I do resort to that, I believe I'll not include the ttf-mscorefonts-installer when installing Wine (staging).

I'm not sure that ttf-mscorefonts-installer is the culprit.

Any suggestions?

---

### Post by monkeybrain20122 on 2021-08-28
I doubt that it has anything to do with that bug. If you look at the date it was from 2015 and the wine version was 1.7.x and people were talking about downgrading kernel 3.xx. Sounds like ancient history. Also ttf-mscorefonts is needed for many Windows apps and has nothing to do with Nvidia driver, it can be installed by installing ubuntu-restricted-extras which is useful apart from wine since it contains multimedia codecs.

You can use different versions of wine  by using playonlinux, it is in the repo.

---

### Post by wyattwhiteeagle on 2021-08-28
UPDATE 3:


Terminal says mypaint is not installed and any of it's variants are unable to be located.


In Applications under Settings, "MyPaint w64" and "MyPaint w64 (console debug mode)" appear to be installed.


When I click "Open in Software" at the top of the Settings window, Software Center displays the message, "Sorry, there are no details for that application."


I've tried...
```
sudo apt-get clean
sudo apt autoclean
sudo apt autoremove
rm -rfv ~/.cache/thumbnails
sudo du -sh /var/cache/apt
sudo apt-get update -y
sudo apt update
sudo apt full-upgrade
sudo apt autoremove --purge
etc

```

If terminal says it isn't installed, but Settings says it is...


I'm unable to...

Open it
Try it
Use it

I want mypaint gone.
 
How do I remove it?


> wyatt@wyatt-Aspire-E1-532:~$ sudo apt remove mypaint
[sudo] password for wyatt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'mypaint' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
> wyatt@wyatt-Aspire-E1-532:~$ sudo apt remove mypaint w64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package w64
> wyatt@wyatt-Aspire-E1-532:~$ sudo apt remove mypaint_w64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mypaint_w64
wyatt@wyatt-Aspire-E1-532:~$ 


---

### Post by monkeybrain20122 on 2021-08-28
I am not sure what you are doing. Wine apps of course won't show up in the system's software package manager. They are handled through wine and installed in the wineprefix in your $HOME. You can remove it with wine's sofware removal utility (in terminal type "wine uninstaller" without the quotes) or just delete the .wine folder in your home directory (but then it will delete everything that installed from wine) To delete the menu entry and desktop launcher, open your file browser, press ctr+h to show hidden files and go inside the hidden folder .local/share/applications, fine the .desktop file and delete it, it may be inside a subfolder called wine.

mypaint is in the repo, not sure why you need the Windows version and wine.

---

### Post by wyattwhiteeagle on 2021-08-28
> **monkeybrain20122 said:**
> I am not sure what you are doing. Wine apps of course won't show up in the system's software package manager. They are handled through wine and installed in the wineprefix in your $HOME. You can remove it with wine's sofware removal utility (in terminal type "wine uninstaller" without the quotes) or just delete the .wine folder in your home directory (but then it will delete everything that installed from wine) To delete the menu entry and desktop launcher, open your file browser, press ctr+h to show hidden files and go inside the hidden folder .local/share/applications, fine the .desktop file and delete it, it may be inside a subfolder called wine.

mypaint is in the repo, not sure why you need the Windows version and wine.

I don't want or need mypaint at all...windows version or otherwise.

I want it gone

I will try your suggestions

---

### Post by wyattwhiteeagle on 2021-08-29
This may be only a temporary solution

I'm sure there are other ways, but this is how I solved this issue...

1. Boot to LiveUSB
2. Open File Manager
3. Click "Search" at the top
4. Type the name of what you want to remove
5. After the search completes, open the properties of each one (configure File Manager to show hidden items and enable viewing the column "Command line")
6. Right-click on the command line next to "Parent folder"
7. Click "Select All"
8. Open Text Editor
9. Paste the command line
10. Save it to a location either onto another HD on your network or onto a seperate flashdrive (Not the LiveUSB or the main boot drive)
11. Reboot the main install
12. in terminal type wine uninstaller (it may open a message to update, go ahead and let it update)
13. From there, you can uninstall the one you want to remove
14. Open the text file you created
15. Browse to the different directories and move the items to the trash
16. Reboot
17. Run all clean, remove, and purge command lines in terminal
18. Run all update and upgrade commands

As far as I can tell, MyPaint w64 is nowhere on my system.

---

### Post by monkeybrain20122 on 2021-08-29
> **wyattwhiteeagle said:**
> This may be only a temporary solution

I'm sure there are other ways, but this is how I solved this issue...

1. Boot to LiveUSB
2. Open File Manager
3. Click "Search" at the top
4. Type the name of what you want to remove
5. After the search completes, open the properties of each one (configure File Manager to show hidden items and enable viewing the column "Command line")
6. Right-click on the command line next to "Parent folder"
7. Click "Select All"
8. Open Text Editor
9. Paste the command line
10. Save it to a location either onto another HD on your network or onto a seperate flashdrive (Not the LiveUSB or the main boot drive)
11. Reboot the main install
12. in terminal type wine uninstaller (it may open a message to update, go ahead and let it update)
13. From there, you can uninstall the one you want to remove
14. Open the text file you created
15. Browse to the different directories and move the items to the trash
16. Reboot
17. Run all clean, remove, and purge command lines in terminal
18. Run all update and upgrade commands

As far as I can tell, MyPaint w64 is nowhere on my system.


You are making it way more complicated. Actually only steps 12 and 13 are necessary. And then remove the .desktop file in ~/.local/share/applications and/or ~/.local/share/applications/wine. I don't know why the live usb or the network come in and why it is necessary to run 17 and 18, like I said, the package manager has nothing to do with Windows apps you installed through wine.

It is a simple operation really, you are overthinking it. Also, here is a tip you might find useful, you can configure the file browser (in Edit > Preference) to include a permanent delete option so it will bypass the trash folder. On another thread you were talking about you have very limited storage, so there is no point to let junks piling up in trash. Personally I think this is the most useless feature, if I delete something, I want it gone, not being moved to some hidden corner where it is sitting and taking up disk space.

---

### Post by mastablasta on 2021-08-30
think of wine prefix as computer inside you computer. so whatever you installed in wine prefix, can be "uninstalled" just by removing/deleting that prefix.

playonlinux has multiple prefixed running at once. you right click the one that is bothering you and select remove. and that's it.

---

### Post by wyattwhiteeagle on 2021-08-30
Thanks for the critique's

That's what worked for me, and I also said in that post that I'm sure there are other ways.

I'm not the only one making things more complicated.

Searching "Focal Fossa" or "Ubuntu 20.04 lts", most of the results are pointing to guides and tutorials for earlier version's and other flavour's of Ubuntu.

A lot of the guides and tutorials aren't "clear, easy to follow, step by step".

That leave's the new Ubuntu user's (windows os user's) who are trying to learn something new or different having to include "trial and error" into their learning process.

In turn, they end up with error's and other issue's in their Ubuntu experience's.

---

### Post by mastablasta on 2021-08-31
other flavours of Ubuntu (even PopOS or Mint) are the same if you use command line. Linux is modular and desktop (the GUI interface) is separated from OS.

if command makes sense and unless it doesn't require specific libraries, then usually the old tutorial i still valid. not always though.

on the other hand the Wine is a separate project and as i said Playonlinux (comes with install scripts even), Lutris, Crossover or Proton were all designed to make using wine a lot easier.  For example Proton in Steam is mostly preconfigured. so many times all you have to do is let the steam know to use proton for the game and Bob is your uncle.

---

