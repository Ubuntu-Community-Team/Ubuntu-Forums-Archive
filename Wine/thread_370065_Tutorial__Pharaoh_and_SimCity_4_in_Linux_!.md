---
title: "Tutorial : Pharaoh and SimCity 4 in Linux !"
date: 2007-02-25
forum: Wine
---

### Post by ramses9167 on 2007-02-25
Hello !

(I'm French, so excuse my mistakes :P )

I have written 2 two tutorials which explain how to install Pharaoh and SimCity 4 in Ubuntu 6.06 LTS :D .
These tutorials are in french.... but easy to understand.
So, I agree that members translate these tutorials. :)

Links :
Pharaoh (and the add on "Cleopatra") : [http://doc.ubuntu-fr.org/pharaon](http://doc.ubuntu-fr.org/pharaon)

SimCity 4 : [http://doc.ubuntu-fr.org/simcity4](http://doc.ubuntu-fr.org/simcity4)

Bye

(Can you correct my mistakes please ? I would like to improve my English :P )

---

### Post by Breepee on 2007-02-25
Nice! Do you know if wine runs Simcity 4 better than Cedega. I tried Cedega (since it supports it 'officially', but it misses some sounds and isn't very fast compared to Windows.

---

### Post by ramses9167 on 2007-02-25
I have no sound problems. And.... SC4 is faster in Linux than Windows !
in my tutorial, there is a part about display settings

---

### Post by Breepee on 2007-02-26
With sound problems I mean that most effects (like creating a road) doesn't generate a sound like it in Windows does.

And, I of course mean performance with the same settings in both cases. I play it 1680x1050, everything high, and in Linux I can't see the cars driving smoothly...

---

### Post by RotoGrip on 2007-02-26
Hope someone can translate this soon to English. I cannot get Cedega to install SC4.

---

### Post by ljkelling on 2009-02-19
my feeble attempt at making these understandable in english, even though it's been a while. but i was halfway through translating them for the poster ahead of me before i realized it was so old, and also.. i needed it for my use anyway ;D



[B]
Pharaoh[/B]

Pharaoh is a game of management/strategy, that consists of construct a city in Ancient Egypt, while taking care to manage the resources, nourish the population, do commerce, push back the invaders, etc&#8230; the game provides several campaigns/scenarios.  

Pharaoh can be installed automatically thanks to the utilitye PlayOnLinux.  To learn more, go to the wiki page dedicated to PlayOnLinux.  


[B]

Configure the cd-rom reader[/B]

Normally, this is detected automatically by Wine, but one never knows (and then it is easy to do).  Insert the Pharaoh CD.  Open a terminal and type winecfg.  

Go in the Drives tab, click on the button "Auto Detect" (1), next select the line letter where it is marked &#8220;/media/cdrom0", (2), click on Show Advanced, then in the drop box labeled "Type" (3)select CD-ROM.  Click on OK. 



[B]
 Install Pharaoh.[/B]

(Make sure to insert the disc).  Open a terminal, and type:  

cd /media/cdrom0 
wine autorun.exe

The installation program starts up, follow the simple instructions to complete installation.  Then at the end, leave the installation program.  Pharaoh is installed, and now we'll again configure winecfg!  


[B]

Configure winecfg[/B]

Open a terminal and type winecfg (again!).  Then go on the tab "Applications".  Click on Default Settings in the white table, and put the operating system Windows 98.  

Go next on the tab "Graphics", then check " Allow DirectX applications to stop the mouse leaving the window&#8221;.  Check " Emulate a virtual desktop" and give a resolution of 1024 by 768.  

Go to the Audio tab, the load can last 5 or even 10 seconds.  Next to Hardware Acceleration, select Emulation and check "Driver Emulation".  Select OK.  




**Have fun!**  

Now, to play, open a terminal, type:  

cd ~/.wine/drive_c/SIERRA/Pharaoh 
wine Pharaoh.exe

Next, in the game go in and change  the resolution to 1024 by 768.  

Enjoy;)


[B]

 Problems. [/B] 

Know that for all problem/notices/suggestions, there is a topic on the forum:  [http://forum.ubuntu-fr.org/viewtopic.php?id=85273](http://forum.ubuntu-fr.org/viewtopic.php?id=85273)

Note that it is not recommended to have installed XGL/Beryl. 
[I]
 Impossible to attain the Audio tab in winecfg! [/I] 

Go in a terminal and type:  

sudo mv /usr/lib/wine/winearts.drv.so /usr/lib/wine/old_winearts.drv.so 
sudo modprobe snd-seq



[B]
Install the expansion Cleopatra Queen of the Nile[/B] 

One considers that to install Pharaoh (necessary for the expansion), you followed the preceding instructions.  

Insert the expansion CD.  

In terminal, type:  

cd /media/cdrom0 
wine autorun.exe

Follow the instructions, and you'll have a complete installation!  

Next, in terminal:  

cd ~/.wine/drive_c/SIERRA/Pharaon/ 
wine Pharaoh.exe

Either that works and this is much better for you, or it asks you to insert the CD while it is already present.  ***(TRANS. NOTE: Sorry, that sentence made.. very little sense to me. So it probably makes little sense to you. My French is really not so good. Ha ha ;D)***

The only solution that I have tested and that works, is to install the crack no cd, and to replace the Pharaoh.exe of ./ wine/drives_c/by the Pharaoh.exe crack!  

I cannot get you the crack no cd, but know that if you look well for it (using Google for example), you will find it.  

/!\ ATTENTION!  Know that the usage of a crack no cd without possession of the original IS FORBIDDEN! and is authorized only to launch the game/!\

Once the game has launched, change the resolution to 1024 by 768.  


[B]

Conclusion[/B]

I learned two things while trying to run Pharaoh:  -Wine is sometimes more effective using the terminal than the graphic interface - The emulation of an office, the version Windows, the emulation, are essential, easy adjustments to make, and terribly effective:)  

Know that for all problem/notices/suggestion, there is a topic on the forum.



[B]
Links:
[/B]
Pharaoh on Winehq:  [http://appdb.winehq.com/appview.php?iAppId=223](http://appdb.winehq.com/appview.php?iAppId=223)

---

### Post by ljkelling on 2009-02-19
again, i tried, please don't be too rough on my shoddy translations ;D

**SimCity 4**


SimCity 4 is a game published by EA Games, which make it possible to build and manage a city, its services, its infrastructures, its budget, etc. But not only one city, a whole area! You will be able to establish commercial connections between your cities:) 

SimCity 4 was installed and launched successfully on this configuration: * Desktop PC Acer
* 1024 Mo of RAM 
* Graphics card nVidia GeForce 7300 GS (3D acceleration must be activated!) 
* Processor AMD Athlon 64bits 4400+ Dual-core. 
* Chart its Realtek AC97 
* Keyboard and optical mouse by Acer 
* Screen TFT 19 inches Benq connected in DVI. 
* Wine 0.9.19 
* Ubuntu Linux 6.06, core Linux 2.6.15-28-k7 SMP. 

For an easy, clean, and optimal installation of SimCity 4, scripts for PlayOnLinux are available (SimCity 4 and SimCity 4 Deluxe). More info at PlayOnLinux 

**I. Installation of Wine** 
I tested SC4 (SimCity 4) with version 0.9.19 of Wine, a utility which will enable you to use Windows software on Linux. To install Wine, you thus have the choice: 
* You install the any last version, that I did not test but which must run, while following Doc. (Necropotame: Version 0.9.44 goes much better at home) 
* Or like me, you install version 0.9.19. To be done, uninstall all versions of Wine present on your computer (that will not erase your Windows programs). Open a terminal (Applications&#8658;Accessories&#8658;Terminal) and type: 

sudo apt-get remove --purge wine libwine 

Then get the package of the 0.9.19: [http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.19~winehq0~ubuntu~6.06-2_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.19~winehq0~ubuntu~6.06-2_i386.deb") 
Once downloaded, install locally and double click on it. If the installation worked, you now have version 0.9.19 of Wine:) 
[B]

II. Configuration of Wine[/B] 

We will configure Wine quickly. To do this, open a terminal and type winecfg. In the tab " Applications" , select the system Windows 98. In the tab "Graphics" _uncheck_ "allow the DirectX applications ....." Check "emulate a virtual desktop" , and give a resolution of 1280 by 1024. At the bottom, check the box “Allow pixel shader” , and select Emulation in the drop-down list. Click now on the Audio tab. Once "Audio" appears (this can take a while), below, select Emulation for hardware acceleration, then check the Driver Emulation box. Validate the whole by clicking on OK. 

[B]
III. Installation of SimCity 4[/B] 

We finally will be able to install SC4 =) You will need 3 things: 
* the game SimCity 4 for Windows (normally 2 CDs). 
* Update UPDATE 2 for SimCity 4 (we will download it)
* A crack No-Cd necessary to launch SC4 (I will give explanations afterwards) 

Insert disc 1 of SimCity 4. In a terminal, type: 

Cd ~ 					##is placed in your /home/yourname ## 
to mkdir sc4setup 			##creates a file sc4setup in your /home/yourname ##
CP - vR /media/cdrom/ * ./sc4setup/ ##copy contents of CD towards sc4setup, on your disc dur.##

 Once the files finish copying, take out disc 1 and insert disc 2. In a terminal, type: 
Cd ~ to mkdir sc4setup2 			##creates a file sc4setup2## 
CP - vR /media/cdrom/ * ./sc4setup2/ 	## copy contents of the CD2, towards sc4setup2## 
Cd sc4setup wine setup.exe 			##starts installation## 

Take out disc 2. If you are offered an online update, refuse, and if it asks you to register, do it later.  If the bar doesn't move during installation, don't panic, that's normal.  Around the middle of installation you'll be asked to insert disc 1. To simulate this action, in a terminal, type: 
Cd ~
 mv sc4setup sc4setup1 
mv sc4setup2 sc4setup 

Then constinue the installation. At the end of  the installation, you will receive an error message regarding a debug. This isn't a problem, just click ok. 

**Installation of the update of SC4 **

Before installing the update of SC4, we must make a all small manip to avoid a problem with Graphic Rules.sgr 
In a terminal (and yes, still :-P) 
Cd ~ 
Cd " .wine/drive_c/Program Files/Maxis/SimCity 4" 
CP " Graphics Rules.sgr" " Graphics Rules.backup" 
Now, let's download this update. 
For Europe: [http://simcity.ea.com/update/exe/R1/UPDATE-SKU2-TO-P2.EXE[]("http://simcity.ea.com/update/exe/R1/UPDATE-SKU2-TO-P2.EXE[")
 For North America:[ http://simcity.ea.com/update/exe/R1/UPDATE-SKU1-TO-P2.EXE]("http://simcity.ea.com/update/exe/R1/UPDATE-SKU1-TO-P2.EXE") * For the others: [http://simcity.ea.com/update/index_update.php?product=R1&x=57&y=12]("http://simcity.ea.com/update/index_update.php?product=R1&x=57&y=12")



 (Download this update in your personal file)

 In a terminal: 
Cd ~ 
wine UPDATE-SKU2-TO-P2.EXE ##for Europe## 
wine UPDATE-SKU1-TO-P2.EXE ##for North America ##  

If it gives you a warning, click on OK to continue =) 

Cd ~ 
Cd " .wine/drive_c/Program Files/Maxis/SimCity 4" 
CP " Graphics Rules.sgr" " Graphics Rules.new"
 CP " Graphics Rules.backup" " Graphics Rules.sgr" 
Cd Apps/ 
mv " SimCity 4.exe" " SimCity 4.backup" 
Cd ~ 
wget " [http://simpage.net/files/SimCity](http://simpage.net/files/SimCity) 4.exe" 
mv " SimCity 4.exe" " .wine/drive_c/Program Files/Maxis/SimCity 4/Apps/SimCity 4.exe"


** IV. Have fun!**

 To play, type in a terminal: 
wine " C:\Program Files\Maxis\SimCity 4 \ Apps \ SimCity 4.exe" 

(click on Ok if the play posts you a warning, and you might need to skip animations.) 

**V. Some adjustments**

 To benefit as well as possible from SC4, you can carry out some adjustments within the game. After having starting, on the top right click on the button with 3 points,(options), then on the screen (graphic adjustments). In the first category, if you have a good graphics card, put all the options at " high". Then select then Clouds/Fog, and Waves. Colors 32 Bits. For the moment keep a resolution of 1024 by 768. Click on Accept, and start again SC4. If you go to a city, should see you waves on the water, and the details (trees, swimming pools) at the houses! To have the full screen  go to the options, select a resolution corresponding to your screen (for example 1280 by 1024 for one 17 inches) Click ok and leave the game. Start winecfg.  In the tab " Graphics" , deselect " To emulate virtual desktop" and " To allow the manager… ". Change Vertex Shader support to Emulation. If full screen doesn't work for you well, choose" To allow to the manager… " in the tab Graphics of winecfg. 

**VI. Solution to problem**. 
The Audio tab in Wine
Does wine close if you click on Audio?  To solve this problem, in a terminal type: 
sudo mv /usr/lib/wine/winearts.drv.so /usr/lib/wine/old_winearts.drv.so 
sudo modprobe snd-seq 


Graphic acceleration
To play SC4 you must have activated graphic acceleration. 
*On graphics cards by ATI:[ [http://doc.ubuntu-fr.org/fglrx]( [URL="http://doc.ubuntu-fr.org/fglrx"]http://doc.ubuntu-fr.org/fglrx)]("http://doc.ubuntu-fr.org/fglrx")
*On the graphics cards by nVidia: [[http://doc.ubuntu-fr.org/nvidia]([URL="http://doc.ubuntu-fr.org/nvidia"]http://doc.ubuntu-fr.org/nvidia)]("http://doc.ubuntu-fr.org/nvidia")

**VII. Conclusion** 
This tutorial meets end =) I hope that you will not have had too much trouble to installing SimCity ;-) Not having the Rush Hour expansion, I could not continue the tutorial for its installation. But if a pleasant Ubuntu user sees this, I hope they will be able to finish it =) 
If you see errors, do not hesitate to correct them =)
 Irony of history, SC4 is much more fluid under Linux than under Windows:!: 

Contributors: FIXME. Source (completely rehabilitated and translated): [url[http://www.simpage.net/simcity4/articles/1054017182.shtml"]]http://www.simpage.net/simcity4/articles/1054017182.shtml](")[/url]
// Addition 12/11/08 by Tgarfr 
Tuto for SimCity Rush Hour: [[http://www.woneb.net/index.php?page=99-Faire-fonctionner-SimCity-4-Deluxe-avec-Rush-Hour-sous-Wine]([URL="http://www.woneb.net/index.php?page=99-Faire-fonctionner-SimCity-4-Deluxe-avec-Rush-Hour-sous-Wine"]http://www.woneb.net/index.php?page=99-Faire-fonctionner-SimCity-4-Deluxe-avec-Rush-Hour-sous-Wine)]("http://www.woneb.net/index.php?page=99-Faire-fonctionner-SimCity-4-Deluxe-avec-Rush-Hour-sous-Wine")

---

### Post by balagosa on 2009-02-27
> **ljkelling said:**
> 
[b]
III. Installation of SimCity 4[/B] 

We finally will be able to install SC4 =) You will need 3 things: 
* the game SimCity 4 for Windows (normally 2 CDs). 
* Update UPDATE 2 for SimCity 4 (we will download it)
* A crack No-Cd necessary to launch SC4 (I will give explanations afterwards) 

Insert disc 1 of SimCity 4. In a terminal, type: 

Cd ~ 					##is placed in your /home/yourname ## 
to mkdir sc4setup 			##creates a file sc4setup in your /home/yourname ##
CP - vR /media/cdrom/ * ./sc4setup/ ##copy contents of CD towards sc4setup, on your disc dur.##

 Once the files finish copying, take out disc 1 and insert disc 2. In a terminal, type: 
Cd ~ to mkdir sc4setup2 			##creates a file sc4setup2## 
CP - vR /media/cdrom/ * ./sc4setup2/ 	## copy contents of the CD2, towards sc4setup2## 
Cd sc4setup wine setup.exe 			##starts installation## 

Take out disc 2. If you are offered an online update, refuse, and if it asks you to register, do it later.  If the bar doesn't move during installation, don't panic, that's normal.  Around the middle of installation you'll be asked to insert disc 1. To simulate this action, in a terminal, type: 
[b]
Cd ~
 mv sc4setup sc4setup1 
mv sc4setup2 sc4setup 
[/b]
```
For some reason that I do not know why, the above code does not work for me
```

Then constinue the installation. At the end of  the installation, you will receive an error message regarding a debug. This isn't a problem, just click ok. 


Need Help. The things that I am having trouble with are in Bold and Code. After doing the above code, I am supposed to click "OK" in Wine. But nothing happens when I click OK.

Info: I am using game Images, not the CD per se.

---

### Post by balagosa on 2009-03-05
bump

---

