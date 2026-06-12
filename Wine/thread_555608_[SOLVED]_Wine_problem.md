---
title: "[SOLVED] Wine problem"
date: 2007-09-20
forum: Wine
---

### Post by Roque2 on 2007-09-20
I just installed wine from the unbuntu fiesty package manager and went to use it, all it does is freeze. I have uninstalled and reinstalled several times to try and get it to work. Any suggestions

---

### Post by fazavon on 2007-09-20
remove the .wine from your home dir (/home/username/.wine)

Then reinstall and run "winecfg" from the command line

be sure you are not root when you do this of it will create the .wine under the root home dir.

thanks

//j

---

### Post by cogadh on 2007-09-20
You might also want to install the latest Wine version instead of the Ubuntu repository version. The repository version is 0.9.33 while the latest is 0.9.45 and includes many DirectX and sound related fixes that 0.9.33 doesn't have. Get the .deb installer here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Roque2 on 2007-09-20
I just tried that one from the wine site and it installs fine and when I do the winecfg it hangs up and freezes my comp. I waited for like 20 mins to see if it was just maxing cpu usage out but still nothing.

---

### Post by cogadh on 2007-09-20
Are there any errors or other information output to the terminal when you run winecfg?

---

### Post by Roque2 on 2007-09-20
No its states that it is creating the wine cfg and then locks completely up.No errors

---

### Post by Roque2 on 2007-09-20
Need to get 0B/10.6MB of archives.
After unpacking 47.9MB of additional disk space will be used.
Selecting previously deselected package wine.
(Reading database ... 104937 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb) ...
Setting up wine (0.9.45~winehq0~ubuntu~7.04-1) ...

---

### Post by cogadh on 2007-09-20
Run each of these in a terminal individually:
```
sudo apt-get remove --purge wine
rm -r ~/.wine
sudo apt-get install wine
winecfg
```
That will uninstall and purge all of the Wine files, then delete any trace of the .wine directory, reinstall Wine and run winecfg. If that doesn't correct the problem, we may have to start getting really creative. :)

---

### Post by Roque2 on 2007-09-20
I would love to say that worked but again no joy... I have no clue why it says wine creating directory and then hangs. Must just not like me

---

### Post by hikaricore on 2007-09-20
What kinda hardware (video and otherwise) you got?

I've seen this behavior on shotty integrated video chipsets before.

---

### Post by Roque2 on 2007-09-21
I have a radeon 9200 graphics card and an amd athlon 2600+..
I am really new to linux so if you give me a line command I will be able to get you more info....

---

### Post by cogadh on 2007-09-21
What driver do you have installed for that card?

---

### Post by frychiko on 2007-09-23
I'm having exactly the same problem, with two different computers.
A complete purge does nothing on either comp so it must be a hardware problem. Geforce 8 series on both (installed driver from nvidia site). Different soundcards though in each.

---

### Post by kjander on 2007-10-06
Ive been having the same problem on my older laptop. it has an ati agp rage pro lt. im using a mach64 driver compiled for direct rendering. so its pretty possible the driver is flawed. wine runs fine on my desktop. im glad *someone* acknowledges that wine can crash. seems everyone else concludes that wine, at least on startup, is impervious :) wish that were true!

---

### Post by imnotrich on 2007-10-09
I am having a similar problem with the latest version of wine (downloaded at the behest of the automatic update thingamabob). 

When I try to open winecfg it hangs. 

I have been unable to uninstall/reinstall wine in synaptic or automatix...the process just hangs. 

I tried to remove from command line using apt-get and I am told wine is not installed and yet...I can still run the programs installed within wine, albeit they seem a little slower than I remember and when I try to install something new within wine...it also hangs my computer and I have to restart xwindows.

I'm just a noob and don't want to reinstall the entire os just because one program has become corrupt. That's something I might do in windows, but linux is supposed to be safer and more stable right? 

What can I do?

---

### Post by cogadh on 2007-10-09
Sometimes after a Wine update, you need to run "wineprefixcreate" to update Wine's registry, especially if you have manually created any registry entries. If you don't run it, the behavior you are describing may occur. If that doesn't fix the problem, then it is not likely that your Wine installation is corrupt, but rather something about your .wine directory is corrupt. For troubleshooting putposes, you can rename the current .wine folder and then run "winecfg" to create a new one and see if the problem still occurs.

---

