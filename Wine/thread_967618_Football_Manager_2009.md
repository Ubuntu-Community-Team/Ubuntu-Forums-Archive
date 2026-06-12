---
title: "Football Manager 2009"
date: 2008-11-02
forum: Wine
---

### Post by AndyCooll on 2008-11-02
Let's post all help, comments, problems etc relating to the latest version of the Football Manager series here.

You can get the demo [here]("http://www.footballmanager.net/"), with the full-version due for release on 14th November.

The following is as far as I've got so far and may prove useful to some people (I've gathered the following hints off this thread, last years thread, wild_oscar's thread on the SI Games forum, and the Wine bug reports):

**Preparation**

1. Disable Compiz effects (System > Preferences > Appearance > Visual effects tab > Select "None")

2. Install Wine:
```
sudo apt-get install wine
```

3. Install Winetricks (information about Winetricks here: [Winetricks]("http://wiki.winehq.org/winetricks") and a number of Microsoft libraries:
```
wget http://www.kegel.com/wine/winetricks

sh winetricks directx9 vcrun2005 vcrun2005sp1
```
(Installation setup boxes will pop-up, accept agreements and defaults)

4. Install Java, the version for Windows (it's required for your Wine environment). You can get it here: [Java]("http://www.java.com/en/download/manual.jsp")

Navigate to where you downloaded to and double-click on it. It should open up in Wine (accept agreements and defaults)

**Installing the game**

5. Download the demo from: [Football Manager 2009 Demo]("http://www.footballmanager.net/")

6. Using Archive Manager (i.e. File Roller), manually unpack the demo, and delete the "jre" folder (located in the unpacked Windows > Resource folder) 

7. Run "Setup FM2009 Demo.exe" from the "Windows" folder. E.g.: 
```
cd ~/Sports\ Interactive/Windows

wine "Setup FM2009 Demo.exe"
```

8. In the installation options choose "Advanced" and then choose "No" when it asks if you want to install "DirectX".

**Playing the game**

9. Once installed, run the game the game itself. E.g.:
```
wine "c:\Program Files\Sports Interactive\Football Manager 2009 Demo\fm.exe"
```

Known bug: [http://bugs.winehq.org/show_bug.cgi?id=15893]("http://bugs.winehq.org/show_bug.cgi?id=15893")

Unfortunately, for me running the game either leaves a blank screen, or still doesn't run ...yet. However I know others have got the game running. As for me ...I'll keep working at it and update as appropriate.

:cool:

---

### Post by AndyCooll on 2008-11-02
And I'll start the ball rolling (so to speak). Has anyone managed to get the demo running yet?

When I tried the install this morning (strawberry demo version) it begins loading the setup process and then crashes right out of my Ubuntu session. Unfortunately I've not yet been able to read the error messages before it crashes, so I'm still trying to find out why it's failing.

:cool:

---

### Post by mabulco on 2008-11-02
well, installing the game starts just fine for me, only problem is direct x. Whenever I trie to install it, I get some kind of error and after that the installation is failed and the whole football manager setup  freezes. I guess that I only need to install direct x in order to install FM succesfully. But How?

---

### Post by Coslany on 2008-11-02
I did this:

Skipped DX installation in FM setup.

Installed directx via winetricks
Installed some other runtimes via winetricks

So far I can play but...

No sound.
Graphics in the 3D view a bit glitchy.
Can't get fullscreen to work.

Keep the tips coming (all you bright people out there!)

---

### Post by mormor on 2008-11-02
Could you be a bit more spesific about those winetricks? : ) Im dloading demo now, to decide if im going to buy the game or not.

---

### Post by Tosh78 on 2008-11-02
Yeah, please, tell us how did you do. I installed the game fine without Direct X, but after I installed two libraries. When I did that I'm still getting an error when I try to play.

---

### Post by Coslany on 2008-11-02
Steps.

I skipped the Direct X installation.

From terminal I used:
sh winetricks directx9
sh winetricks vcrun2005sp1
sh winetricks vcrun2005

Used virtual desktop and run!

Keep 'em coming!

---

### Post by AndyCooll on 2008-11-02
Winetricks was a new one on me too, I hadn't heard of it until Coslany mentioned it. I'll have to investigate further.

Anyway, for those interested there's more information about Winetricks here: [Wine Wiki: winetricks]("http://wiki.winehq.org/winetricks")

:cool:

---

### Post by wild_oscar on 2008-11-02
I tried to install the demo this morning.

However, when running the setup, I get to the first installanywhere screen, it runs to 100% and then just goes to a blank window. The size of the window is the same as probably the 1st installation screen, I can even go "next" by pressing enter, but the window is just blank - only the close "x" on top right corner shows.

Any idea why this is happening? Did none of you have this issue when installing?

---

### Post by wild_oscar on 2008-11-03
A bug was submitted in Wine regarding this issue. 

It would be really good if you could help out with this one - lets make FM 2009 the most compatible with Linux!

For those who have managed to run the installation, could you please tell me:

1) OS version
2) Wine version
3) All other installed things on wine and how you installed them
4) Any non-default configuration in wine
5) Hardware - processor, graphics card...

Moreover, if you backup your .wine folder and start up from the beginning (ie, with a fresh wine config), does the installation work alright?

Thank you for the help!

---

### Post by andelund on 2008-11-03
Hi,

I had the problem with the blank window after the installAnywhere window. 
To me it was solved by killing Compiz, you can do this by doing the following;

Press Alt + F2
In the window that pops up, type: 

metacity --replace

But i still haven't managed to play the demo, since it only starts loading on the window bar, then disapers. I haven't tried winetricks yet. 

Hoping someone will find a solution without winetricks :)

---

### Post by wild_oscar on 2008-11-04
I managed to install it following the instructions at [http://bugs.winehq.org/show_bug.cgi?id=15893](http://bugs.winehq.org/show_bug.cgi?id=15893)


However, I have an issue with the 3D / 2D rendering: a black line all over the pitch:
[IMG]http://farm4.static.flickr.com/3216/3002738872_b4310236c0.jpg[/IMG]

Anyone else with this bug?

---

### Post by Coslany on 2008-11-04
> **wild_oscar said:**
> 
However, I have an issue with the 3D / 2D rendering: a black line all over the pitch:


Anyone else with this bug?

I get the same.
NV8800GT on restricted drivers.

---

### Post by wild_oscar on 2008-11-04
> **Coslany said:**
> I get the same.
NV8800GT on restricted drivers.

Yeah. 8600 GTS here, on restricted drivers (177.80).

---

### Post by Dave_G on 2008-11-06
I've done everything as explained in the first post, but i get the below error when trying to run the setup.exe

Install of vcrun2005sp1 done
winetricks done.
dave@dave-desktop:~$ cd '/home/dave/Desktop/untitled folder/Windows' 
dave@dave-desktop:~/Desktop/untitled folder/Windows$ wine "Setup FM2009 Demo.exe"
cwd: H:\Desktop\untitled folder\Windows
cmd: "C:\windows\system32\javaw.exe" -Xms16777216 -Xmx50331648 -classpath "H:\Desktop\untitled folder\InstallerData\IAClasses.zip;H:\Desktop\untitled folder\Windows\resource\jdglue.zip;H:\Desktop\untitled folder\InstallerData\Execute.zip;H:\Desktop\untitled folder\Windows\InstallerData\Execute.zip;H:\Desktop\untitled folder\InstallerData\Resource1.zip;H:\Desktop\untitled folder\Windows\InstallerData\Resource1.zip;H:\Desktop\untitled folder\InstallerData;H:\Desktop\untitled folder\Windows\InstallerData;" com.zerog.lax.LAX "H:/Desktop/untitled folder/Windows/Setup FM2009 Demo.lax" "C:/windows/temp/lax9e93.tmp" 
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:win:EnumDisplayDevicesW ((null),0,0x7d5d2c08,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x7d5d2c08,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x7d5d2ae0,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:imm:ImmGetOpenStatus (0x1d0190): semi-stub
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  EXCEPTION_ACCESS_VIOLATION (0xc0000005) at pc=0x7d0ebd52, pid=33, tid=50
#
# Java VM: Java HotSpot(TM) Client VM (11.0-b15 mixed mode, sharing windows-x86)
# Problematic frame:
# C  [wined3d.dll+0x6bd52]
#
# An error report file with more information is saved as:
# H:\Desktop\untitled folder\Windows\hs_err_pid33.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
dave@dave-desktop:~/Desktop/untitled folder/Windows$

---

### Post by Flegmatik on 2008-11-07
1) OS version : Ubuntu 9.10
2) Wine version : 1.1.7
3) All other installed things on wine and how you installed them : winetricks
4) Any non-default configuration in wine
5) Hardware - processor, graphics card... : centrino duo, GeForce 7400...

I can't install the game because of the blank window... i tried everything posted here... So i installed the game on a Windows PC and i copied the folder in my ubuntu pc... And it works... but i have black lines in the 3D match...

Can I have help please ?

---

### Post by Dave_G on 2008-11-09
So can anyone tell me about my Java problem above, as by the looks of the error i got its that which is the problem?

---

### Post by thewOndErEr57 on 2008-11-10
> Anyone else with this bug? 

I too am getting the thick black stipe down the middle of the pitch, as shown in the printscreen above.

nvidia 9500gt
177.80
wine 1.1.8

If anyone can get over this, then please post your solution.


Thanks !

---

### Post by Dave_G on 2008-11-10
thewOndErEr57,

Can you tell me step-by-step how you managed to install it?  I am having big problems due to the Java error that i keep getting sa you can see in my post above; i am using Wine 1.1.18.

Many Thanks.

> **thewOndErEr57 said:**
> I too am getting the thick black stipe down the middle of the pitch, as shown in the printscreen above.

nvidia 9500gt
177.80
wine 1.1.8

If anyone can get over this, then please post your solution.


Thanks !

---

### Post by ballas38 on 2008-11-11
Hi, i am new to Ubuntu so there are many things i have to learn, so forgive me for my possibly stupid question:

Does FM2009 run faster in Ubuntu than in Windows???

---

### Post by AndyCooll on 2008-11-12
> **ballas38 said:**
> Hi, i am new to Ubuntu so there are many things i have to learn, so forgive me for my possibly stupid question:

Does FM2009 run faster in Ubuntu than in Windows???
Unlikely. However, equally you are unlikely to notice any significant degradation either. When I've run previous versions of FM the speed at which the game has run has been impressive.

:cool:

---

### Post by tobias-mansson on 2008-11-13
Got my full-game copy today, but it's not working. Almost worked the first time but now it seems like I have the same problem as everyone else, the Java-problem. How do I install Sun's JVM on Wine and will it solve my problems? Really want to play FM2009 and not install Windows again.

---

### Post by AndyCooll on 2008-11-13
> **tobias-mansson said:**
> Got my full-game copy today, but it's not working. Almost worked the first time but now it seems like I have the same problem as everyone else, the Java-problem. How do I install Sun's JVM on Wine and will it solve my problems? Really want to play FM2009 and not install Windows again.
You download it (see point 4 of my original howto) and then double click on the downloaded file.

If you get an error message saying it can't open the file you can always alternatively use the commandline:
```
cd /folder/with/javadownloadfile
wine javedownloadfile
```

:cool:

---

### Post by fatbloke on 2008-11-13
Ok I have it working with sound and no black bar.
I semi followed the instructions in the first post but instead of running the 2009 demo setup from the console , I went to configure wine and selected to run in win98..I clicked the fm2009demo exe and let the first box open up... I quit and then configured wine to run in winxp mode and then clicked the fm2009 demo exe again and then let it install choose advance install and make sure you don't install the directx part of the setup.
I loaded a game played one game..it showed the black strip down the centre of the pitch and I saved and quit.
I then went back to configure wine and chose the vista option.
I ran the game again and the pitch is normal with no strip down the centre.. I hope you guys have as much luck as I did.
My graphics card is a nvidia geoforce 8800gt.
I am using the AC97 onboard sound until my soundblaster x-fi is supported more.
BR,
Peter:)

---

### Post by tobias-mansson on 2008-11-13
Next problem! Thanks to this thread I've been able to install it, but when I run fm2009.exe an activation pop-up shows, and this box only presents text and no buttons, equals dead end. 

In order to reach the advanced option during the installation I had to choose the Uniloc-method which obviously doesn't work for me. Tried to run the installation again without success. Any ideas?

---

### Post by jackietreehorn on 2008-11-13
I installed the program successfully, but when I tried to execute it via the terminal I got this:

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\saAuditMD.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\saAuditMD.dll") not found
err:module:import_dll Library saAuditMD.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\fm.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\fm.exe" failed, status c0000135 
```

---

### Post by Flegmatik on 2008-11-14
My dvd player doesn't want to mount the dvd game... how can i force it ?

---

### Post by Flegmatik on 2008-11-14
so i copied the dvd and it works now but the install anywhere ask me every time to select a folder to extract temp files... where to extract them ?

---

### Post by Flegmatik on 2008-11-14
So after installed in windows xp via virtualbox i copied the folder Football Manager 2009 in ubuntu... But when i run the game i have to activate it... how to do because there is no button to continue...

---

### Post by Flegmatik on 2008-11-14
> **tobias-mansson said:**
> Next problem! Thanks to this thread I've been able to install it, but when I run fm2009.exe an activation pop-up shows, and this box only presents text and no buttons, equals dead end.

I have the same problem... :(

Note i Opened a website for french speaking player of Football Manager for linux : [www.fmtux.net](www.fmtux.net)

---

### Post by wild_oscar on 2008-11-14
> **Flegmatik said:**
> I have the same problem... :(

Note i Opened a website for french speaking player of Football Manager for linux : [www.fmtux.net](www.fmtux.net)

I don't have the full game yet (and won't buy it until I know it works on my system, without any lame 3D with black stripes). Have you tried pressing enter? Sometimes it advances to the next screen...

---

### Post by Flegmatik on 2008-11-14
Just doing enter don't work :(

---

### Post by tobias-mansson on 2008-11-14
Feels like theres something missing in Wine so the activation pop-up can't be read properly. Or maybe in winetricks. Tried to install FM2009 through Steam but the same problem occurs. 

Why have they started with activation codes? Stupid move I'd say. Been reading some forums and a lot of people been having problem with activating their game, not only Linux people.

---

### Post by Flegmatik on 2008-11-14
I tried with the demo to install it with xp in virtualbox and i copied the folder of the game to use it with ubuntu and it worked. So I will try to activate with windows and to copy the folder to paste it in ubuntu...

---

### Post by Kossick on 2008-11-14
was there an exact time when FM09 stopped working?

mine turned up in the post this morning at 10, installed, took quite a while with steam installing patches, but then i was on and away, and am now up to november with Man doing well i may add :)

couple of my mates are unable to install. god bless the old days when we used to just get FM off limewire, download the crack and have a year of free football gaming.

damn my desperation to try this new one so i forked out £20!!

---

### Post by nappy boy on 2008-11-14
hi i have a problem i install football manager 2009 but then afta it says to activate the product online.... so i put in the code for it then it comes up with sorry you have no internet connection.... when i actuali hav =S then it tells me to go on sigames.com but i click on it and it dont work =S need help cause realli wanna play it

---

### Post by Flegmatik on 2008-11-14
> **nappy boy said:**
> hi i have a problem i install football manager 2009 but then afta it says to activate the product online.... so i put in the code for it then it comes up with sorry you have no internet connection.... when i actuali hav =S then it tells me to go on sigames.com but i click on it and it dont work =S need help cause realli wanna play it

how did you do to press "next" ? cause i can't do it there is no button, just the text : Next

---

### Post by nappy boy on 2008-11-14
wat do u mean? uve lost me =S

---

### Post by Flegmatik on 2008-11-14
look at my screen... in the activation window i don't have a button to go next (sorry it's a french version)

---

### Post by nappy boy on 2008-11-14
Hmmmm see thats wat i get but myns in english... but myn has next on it but when i type in the product code and press next it comes up sayins sorry theres no internet connection when i actualli hav an internet connection lol then tells me to go on sigames

---

### Post by Flegmatik on 2008-11-14
in mine i can't press next :(

---

### Post by jackietreehorn on 2008-11-14
ah!!! This is so close to working. I tried to run the demo from the terminal and all I get is a blank/black screen. It looks like it is working, just that nothing is showing up on the screen. 

I'm on Intrepid Ibex, I installed java and winetricks, so I'm not sure where things went wrong. Any advice?

Also, on a sort of related note, the Guardian has an excellent piece about old Championship manager legends if anyone is interested. 

[http://www.guardian.co.uk/sport/blog/2008/nov/14/championship-manager-joyofsix-football](http://www.guardian.co.uk/sport/blog/2008/nov/14/championship-manager-joyofsix-football)

---

### Post by Flegmatik on 2008-11-15
I just need to activate the game but the window to do that is not working like with xp. Sometime a message tells me to install gecko (for mozilla) but nothing changes... I'm desperate to use FM2009 to linux. I'm looking for copying the game from a computer on xp but i don't know how to copy the activation system tu run the game on linux...

---

### Post by Vesuro on 2008-11-15
Has anyone tried installation via Steam as this is already activated?

I've bought the game for Windows so I'll be trying it now, will keep everyone updated.

I'm using Linux Mint 5 (Elyssa) which I believe is based on Hardy.

Note: Wine Version 1.1.8

---

### Post by tobias-mansson on 2008-11-15
> **Vesuro said:**
> Has anyone tried installation via Steam as this is already activated?
I installed via Steam but when you start the game you have to activate it again. So the same screen shows up again, the one with no next button.

---

### Post by WonderStivi on 2008-11-15
I've installed FM 09 via Steam, but can't get it to work. Whenever I start the game, I get the dialogue box that wants me to either copy the cd-key to the clipboard or start the game, and it doesn't get further than that. The dialogue box disappears after launching, but then the process goes zombie on me.
 
I read on Wine's Appdb that some got the demo to work with a DirectX workaround.

---

### Post by Vesuro on 2008-11-15
[http://community.sigames.com/showthread.php?t=62365&page=3](http://community.sigames.com/showthread.php?t=62365&page=3)

Seems like this may not be a Linux problem...

---

### Post by Flegmatik on 2008-11-15
I found a crack and it works now :D

---

### Post by Vesuro on 2008-11-15
Can you PM me a download link?

---

### Post by WonderStivi on 2008-11-15
> **Flegmatik said:**
> I found a crack and it works now :DCould you please describe your solution? Simply exchanging the .exe from retail with a no-cd crack?

---

### Post by Flegmatik on 2008-11-15
> **WonderStivi said:**
> Could you please describe your solution? Simply exchanging the .exe from retail with a no-cd crack?

It's a small program that cracks the fm.exe But you need to install the game and the patch 9.1.0.
after cracked the game it could take a lot of time to run the game...

---

### Post by fogtrin on 2008-11-15
error log form terminal :(

```
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:advapi:CheckTokenMembership ((nil) 0x13dbe0 0x32fc54) stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x7d92614c,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x7d926348,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot

```

---

### Post by Flegmatik on 2008-11-15
Yes i have the same problem when i try by the terminal :( The ativation system is not working correctly with ubuntu...

---

### Post by andrizz on 2008-11-15
thanks for the wiki, but i have the some problem with the black screen......i tried disabling compiz but still don't works.
Any suggestion is welcome!
(sorry for my bad english)

---

### Post by Dave_G on 2008-11-15
I just can't get passed the below Java error when trying to install the demo!!!



# An unexpected error has been detected by Java Runtime Environment:
#
# EXCEPTION_ACCESS_VIOLATION (0xc0000005) at pc=0x7d0ebd52, pid=33, tid=50
#
# Java VM: Java HotSpot(TM) Client VM (11.0-b15 mixed mode, sharing windows-x86)
# Problematic frame:
# C [wined3d.dll+0x6bd52]
#
# An error report file with more information is saved as:
# H:\Desktop\untitled folder\Windows\hs_err_pid33.log
#
# If you would like to submit a bug report, please visit:
# [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
dave@dave-desktop:~/Desktop/untitled folder/Windows$

---

### Post by Novus on 2008-11-16
I coulden't install JRE but I got it working in Virtualbox and that will have to do for now

---

### Post by narcotico on 2008-11-16
```
wine "c:\Programas\Sports Interactive\Football Manager 2009\fm.exe"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programas\\Sports Interactive\\Football Manager 2009\\fm.exe" failed, status c0000142

```

:(

---

### Post by Vesuro on 2008-11-17
The exe crack doesn't work with a Steam install.

We need to work out how the Activator decides whether the game is activated or not, and edit it or manually insert something for it.

---

### Post by wild_oscar on 2008-11-17
So, how many of you have:

1) The full game and patch working?

2) in addition to that, no weird issues like the black line in the 3D pitch or no face regens?

---

### Post by Vesuro on 2008-11-17
No one has the full game working without the patch.

Full game with crack works if you have a non-Steam install, but the ramifications include no network games, no holiday mode and I think auto-sacking at the end of every season.

---

### Post by Wrasko on 2008-11-17
Been trying to get the java in the installer to work.. Can't do it.. I can see it if I run in Win NT 4.0 mode, but it's not possible to install it in NT4.0 mode..

Almost the same with java.. I managed to install it under nt4.0 mode, but not under 2k/xp/vista mode..

Help? can't see the information in the installer....



edit: Wow! Suddenly I can see the installation in vista mode :D

---

### Post by wild_oscar on 2008-11-17
> **Vesuro said:**
> No one has the full game working without the patch.

Full game with crack works if you have a non-Steam install, but the ramifications include no network games, no holiday mode and I think auto-sacking at the end of every season.

I am sorry, is that with a "downloaded" version or the same happens with the original disk? (just trying to understand if buying the game is worth it)

---

### Post by Hairy_Palms on 2008-11-17
Bah 2007 and 2008 worked reasonably well too :(

---

### Post by Vesuro on 2008-11-17
> **wild_oscar said:**
> I am sorry, is that with a "downloaded" version or the same happens with the original disk? (just trying to understand if buying the game is worth it)

Works with both, as long as you don't buy through Steam.

---

### Post by moujik on 2008-11-17
Hi!
Thank you for this thread!
I've managed to install and run full FM 2009 patch 9.1 with crack.

1. Download FM2009.iso, patch 9.1, crack fm9.1_t1 (using torrents)
2. Install from .iso using wine 1.0.1 configured to win2000.
    IMPORTANT: choose VIA PHONE rather than stream, advanced installation without directX 10.
3. Patch 9.1
4. Run crack, specify the map through browse. 4 bytes will be changed.
5. Download directx9 using winetricks
6. Configure wine to winXP
7. Run it!

I run Mandriva 08 and I have Iced Tea java installed. I had a lot of issues with install. I had to reinstall .wine cause I pressed via stream, which messed up the registry and I had the common icon with nothing but x.
I coudn't run it without directx, which thanks to you I saw. 
Default wine 1.0.1 configuration is win2000, I think, and it woudn't run giving me Bad file discriptor mistakes.

In the game I changed the screen settings from default 1268x1024 to 1024x768 with 52Hz, because the font seemed too small. I didn't have any black line or anything like that.

I've only tested the game until the first match to see 3D with Liverpool, Premier only, England only, small database, smart sound cache.
I've not tried to go on Holiday, which supposedly doesn't work, but this is the crack issue.

I hope you have luck with it!

---

### Post by Vesuro on 2008-11-17
> **moujik said:**
> Hi!
Thank you for this thread!
I've managed to install and run full FM 2009 patch 9.1 with crack.

1. Download FM2009.iso, patch 9.1, crack fm9.1_t1 (using torrents)
2. Install from .iso using wine 1.0.1 configured to win2000.
    IMPORTANT: choose VIA PHONE rather than stream, advanced installation without directX 10.
3. Patch 9.1
4. Run crack, specify the map through browse. 4 bytes will be changed.
5. Download directx9 using winetricks
6. Configure wine to winXP
7. Run it!

I run Mandriva 08 and I have Iced Tea java installed. I had a lot of issues with install. I had to reinstall .wine cause I pressed via stream, which messed up the registry and I had the common icon with nothing but x.
I coudn't run it without directx, which thanks to you I saw. 
Default wine 1.0.1 configuration is win2000, I think, and it woudn't run giving me Bad file discriptor mistakes.

In the game I changed the screen settings from default 1268x1024 to 1024x768 with 52Hz, because the font seemed too small. I didn't have any black line or anything like that.

I've only tested the game until the first match to see 3D with Liverpool, Premier only, England only, small database, smart sound cache.
I've not tried to go on Holiday, which supposedly doesn't work, but this is the crack issue.

I hope you have luck with it!

The thing is, if the going on holiday is a crack issue, there may be others. Some have suggested that you get sacked every season.

---

### Post by moujik on 2008-11-17
I tried to install with wine 1.0.8 and it didn't not work for me. Maybe I just didn't try the right configuration.

---

### Post by moujik on 2008-11-17
> **Vesuro said:**
> The thing is, if the going on holiday is a crack issue, there may be others. Some have suggested that you get sacked every season.

I've heard that as well I'll make sure I save frequently in June, I'll let you know

---

### Post by Wrasko on 2008-11-17
Well, I've managed to get the game installed, patched and cracked (patching and cracking was the simple part) anyway, nothing happens when I try to run fm.exe.. And the weirdest thing is that wine did not create a shortcut for it..


edit: Thinking of something.. CS/Gta:SA etc works through Steam, have anyone tried FM 09 over steam yet? Shouldn't it work?

---

### Post by mormor on 2008-11-18
I can run the installer, but it free*es when i get to the install-part of it :P

---

### Post by GavinZac on 2008-11-18
Install works fine through Steam.

Unfortunately the game uses UniLoc DRM also (bizarrely, as if it needed users to go through 2 activations while pirates play happily on) and the UniLoc activation application does not work properly.

---

### Post by wild_oscar on 2008-11-18
Well, I have a "downloaded" version. I couldn't install it in Linux so I dual booted in Windows and installed it there.

It now plays well even on Linux, except I had to use the crack. So go on holiday doesn't work (and I'm afraid it may also have the "get sacked" issue). 

Have any users with an original game been able to play on Linux without installing a crack?

---

### Post by Graeme2804 on 2008-11-18
> **jackietreehorn said:**
> I installed the program successfully, but when I tried to execute it via the terminal I got this:

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\saAuditMD.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\saAuditMD.dll") not found
err:module:import_dll Library saAuditMD.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\fm.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sports Interactive\\Football Manager 2009 Demo\\fm.exe" failed, status c0000135 
```

I get this exact same problem.  Going to do a bit of hacking around and see if I can get it to work.

Will let you know if I manage it, in the mean time, anyone had this problem and fixed it?

---

### Post by GavinZac on 2008-11-18
> **Graeme2804 said:**
> I get this exact same problem.  Going to do a bit of hacking around and see if I can get it to work.

Will let you know if I manage it, in the mean time, anyone had this problem and fixed it?

Is the Demo available via Steam? Try using that.

---

### Post by Graeme2804 on 2008-11-18
> **Graeme2804 said:**
> I get this exact same problem.  Going to do a bit of hacking around and see if I can get it to work.

Will let you know if I manage it, in the mean time, anyone had this problem and fixed it?



Ok, I've fixed that problem, put the missing dlls in ~/.wine/drive_c/windows/system32/
(missing dll's attached)

I have a new problem with C++, as seen in screenshot.  Any insight people?

I'm not bothering with the demo, I've downloaded the full version overnight, I'm determined to get it working!

---

### Post by Graeme2804 on 2008-11-18
when I try installing Microsoft Visual C++ 2008 Redistributable, I get - 

Executing wine /home/'name'/.winetrickscache/vcrun2008/vcredist_x86.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec9c,0) stub!
fixme:advapi:DecryptFileA "c:\\5cb6084de3bf51f2b28aab5156\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:LsaOpenPolicy ((null),0x33f3a8,0x00000001,0x33f3d0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"'name'" (nil) 0x7ddb23e8 (nil) 0x7ddb23ec 0x7ddb23e0 - stub
fixme:advapi:LookupAccountNameW (null) L"'name'" 0x1536e8 0x7ddb23e8 0x160cd0 0x7ddb23ec 0x7ddb23e0 - stub
fixme:advapi:LookupAccountNameW (null) L"'name'" (nil) 0x7ddb23b4 (nil) 0x7ddb23b8 0x7ddb23ac - stub
fixme:advapi:LookupAccountNameW (null) L"'name'" 0x189390 0x7ddb23b4 0x1892d0 0x7ddb23b8 0x7ddb23ac - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:msi_view_get_row Invalid type!
err:msi:msi_view_get_row Invalid type!
err:msi:msi_view_get_row Invalid type!
err:msi:msi_view_get_row Invalid type!
err:msi:msi_view_get_row Invalid type!



Any ideas?

---

### Post by Vesuro on 2008-11-18
You can install vc2005sp1 via Winetricks.

I've got the activator to work, it's activated but doesn't run.

See [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555) for more info.

---

### Post by Graeme2804 on 2008-11-18
woot! that worked!

now i need java.

---

### Post by mormor on 2008-11-18
"Cannot Run game: Failed to set up graphics system."

Error when trying to start game.

Ubuntu 8.10
Wine 1.0.1
Innstalled the game in vista, copied to wine in ubuntu
Acer travelmate 6291

---

### Post by Graeme2804 on 2008-11-18
I get a load of fixme: errors and the attached image for a screen.

Damn it!!

---

### Post by mormor on 2008-11-18
Trying to install DX9 gives this error:

> marius@tobor:~$ sh winetricks
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
Setting Windows version to win2k
Executing wine regedit /home/marius/.wine/drive_c/winetrickstmp/set-winver.reg
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
Executing wine /home/marius/.winetrickscache/directx_jun2008_redist.exe /t:c:\winetrickstmp
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
wine: cannot find '/home/marius/.winetrickscache/directx_jun2008_redist.exe'
Note: command 'wine /home/marius/.winetrickscache/directx_jun2008_redist.exe /t:c:\winetrickstmp' returned status 2.  Aborting.

---

### Post by Underoath on 2008-11-18
when install directx sdk:

11/18/08 18:23:34: dxupdate: C:\WINDOWS\system32\xactengine3_0.dll have been installed already.
11/18/08 18:23:34: dxupdate: DirectXUpdateInstallPlugIn(): Registering: XACT3_0_x86_xp.inf - [DllRegisterServer]
11/18/08 18:23:35: dxupdate: RegisterDLL(): LoadLibraryEx() failed, error = 0xc000001d.
11/18/08 18:23:35: dxupdate: DXSError(): FormatMessage() failed, system cannot find message text for error.
11/18/08 18:23:35: dxupdate: RegisterDLL(): Unable to load C:\WINDOWS\system32\xactengine3_0.dll.
11/18/08 18:23:35: dxupdate: DirectXUpdateInstallPlugIn(): RegisterDllFromSection() failed.
11/18/08 18:23:35: dsetup32: CSetup::InstallPlugIn(): DirectXUpdateInstallPlugIn() failed.
11/18/08 18:23:35: dsetup32: CSetup::SetupForDirectX(): InstallPlugIn() failed.
11/18/08 18:23:35: dsetup32: start finalizing: phase: 125 - 125, total: 0 - 108
11/18/08 18:23:40: dsetup32: Installation ended with value -9 = Internal or unsupported error



why ?? help me =s

---

### Post by fogtrin on 2008-11-18
it's work!

I change configuration wine to emulate windows xp

---

### Post by Wrasko on 2008-11-18
Made it :D

I deleted wine, and the folder .wine.

Then:
sudo apt-get install wine.
sh winetricks directx9
sh winetricks vcrun2005sp1
sh winetricks vcrun2005

Installed java for Xp/Vista
Then I installed the game with wine (2000 conf).
Patched, and cracked. 
Didn't work, then I tried with the original fm.exe, then I suddenly had the code screen. Got excited, then tried with the cracked .exe again, nothing happens.. Then changed winecfg to be in xp config.. Woila..

Me happy !

---

### Post by pluckypigeon on 2008-11-18
here is a list of troubleshooting advice-
[http://community.sigames.com/showthread.php?t=63556](http://community.sigames.com/showthread.php?t=63556)

it may not be wine or ubuntu causing problems

I got the error "ERROR: Cannot run game:Failed to set up graphics system"

It told me to install a different directx, DXSDK or something.

I'm yet to test it because it is currently downloading.

I'll keep you posted!!!!

---

### Post by Nylon Alpaca on 2008-11-19
I have WWSM09 (the US version of FM) working on Intrepid without needing a crack. 

My WINE install has IE (installed from IES4Linux), Winetricks (for directx9 vcrun2005 and vcrun2005sp1 as mentioned earlier in the thread to run the demo), Steam (obviously) and Firefox (for mozplugger).

I bought through Steam. Used the activation fix utility from [http://community.sigames.com/showthread.php?t=65715](http://community.sigames.com/showthread.php?t=65715) to enter the license code that Steam presents you, having got the "trial expired" dialog on initial launch. Couldn't get it to run initially, then I set WINE to XP emulation and off I went.

I don't use facegen or sounds, so I have no idea if they work, but I have flawless 3D (NVIDIA GeForce Go 7900, latest restricted driver) in windowed mode.

I'm using a Dell Inspiron E1705, a fresh install of Intrepid (the upgrade from Hardy borked my system, but it was fine when I did a reinstall), NVIDIA restricted drivers as I mentioned above, Metacity compositing (no Compiz) and the latest version of WINE.

---

### Post by c001os on 2008-11-19
Thx for everybody the game finaly works for me! 

I reinstalled wine, install directx vcrun2005 vcrun2005sp1 through winetricks and finaly installed dxsdk_nov08 and its WORKS!

I have now only one problem (the game is updated to 1.0.1), i can't the game preferences just chose low graphics performance, and in the match i cant choose 3d match engine (or i dont know where i can). 

Have everybody the same problem?

thx

p.s. : fantastic work for the comunity anyway runing this brand new game in ubuntu!!!!! :popcorn:

---

### Post by c001os on 2008-11-19
uodate for my last reply:

The 3d match now working,( but just in low mode. My graphics card is a nvidia 9600GT.

---

### Post by Wrasko on 2008-11-19
> **c001os said:**
> Thx for everybody the game finaly works for me! 

I reinstalled wine, install directx vcrun2005 vcrun2005sp1 through winetricks and finaly installed dxsdk_nov08 and its WORKS!

I have now only one problem (the game is updated to 1.0.1), i can't the game preferences just chose low graphics performance, and in the match i cant choose 3d match engine (or i dont know where i can). 

Have everybody the same problem?

thx

p.s. : fantastic work for the comunity anyway runing this brand new game in ubuntu!!!!! :popcorn:

When I started the game, 3d were as default, and I can choose detail level.

---

### Post by mormor on 2008-11-19
winetricks seems to pull tricks on me.

> marius@tobor:~$ sh winetricks
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
Executing wine /home/marius/.winetrickscache/vcrun2005sp1/vcredist_x86.exe
Warning: could not find DOS drive for current working directory '/home/marius', starting in the Windows directory.
wine: cannot find '/home/marius/.winetrickscache/vcrun2005sp1/vcredist_x86.exe'
Note: command 'wine /home/marius/.winetrickscache/vcrun2005sp1/vcredist_x86.exe' returned status 2.  Aborting.


Any idea how to fix this?

---

### Post by Wrasko on 2008-11-19
> **mormor said:**
> winetricks seems to pull tricks on me.



Any idea how to fix this?

sh winetricks directx9
sh winetricks vcrun2005sp1
sh winetricks vcrun2005

It seems that it can't find the packages with only sh winetricks

---

### Post by tobias-mansson on 2008-11-21
I finally got my original game to work thanks to this thread. Wrasko's reply on the previous page was extra helpful. Hopefully the game will be as good as everyone say. Thank God for not have to install Windows just to play my favorite game!

---

### Post by Flegmatik on 2008-11-21
i create a wiki in the french ubuntu site to install an activate fm2009 : [http://doc.ubuntu-fr.org/football_manager](http://doc.ubuntu-fr.org/football_manager) if you need help in english, contact me ;)

---

### Post by t_da_don on 2008-11-23
im on windows xp
 i was wondring i have installed football manager and it repiles a message stateing:

"cannot run game: failed to se up graphic system." 

how would i be able to over come this message so that i would be able to play the game

---

### Post by andrizz on 2008-11-24
> **t_da_don said:**
> im on windows xp
 i was wondring i have installed football manager and it repiles a message stateing:

"cannot run game: failed to se up graphic system." 

how would i be able to over come this message so that i would be able to play the game

install [DirectX Software Development Kit](http://www.microsoft.com/downloads/details.aspx?familyid=5493F76A-6D37-478D-BA17-28B1CCA4865A&displaylang=en) (needs .net framework installed)

---

### Post by diopter on 2008-11-24
> **Flegmatik said:**
> i create a wiki in the french ubuntu site to install an activate fm2009 : [http://doc.ubuntu-fr.org/football_manager](http://doc.ubuntu-fr.org/football_manager) if you need help in english, contact me ;)

Hi, would be great if you can create a english version wiki for this. :)

---

### Post by Flegmatik on 2008-11-25
I'll try to prepare an english one ;) But you can use google translation ;)

---

### Post by tobias-mansson on 2008-11-25
Has anyone experienced not been able to write in capitalized letters? Haven't found anyone else with that problem yet. I have the original game, patch 9.1 and cracked the fm.exe.

---

### Post by jackietreehorn on 2008-11-26
So I got fm2009 to work, kind of. The game starts, but I'm using a laptop, which I don't think has the processing power to handle the game. Also, when I start the game, and hit Ctrl+Alt+D (show desktop) the intro screen appears. However, when I don't do that all I get is a black screen. The game "works" but it doesn't, if you follow me.

---

### Post by andrizz on 2008-11-27
> **jackietreehorn said:**
> So I got fm2009 to work, kind of. The game starts, but I'm using a laptop, which I don't think has the processing power to handle the game. Also, when I start the game, and hit Ctrl+Alt+D (show desktop) the intro screen appears. However, when I don't do that all I get is a black screen. The game "works" but it doesn't, if you follow me.

I Have the same error with an intel GM965/GL960 video card.

---

### Post by Flegmatik on 2008-11-27
I use 2 or 3 different desktop to not have this problem ;)

---

### Post by jackietreehorn on 2008-11-27
> **andrizz said:**
> I Have the same error with an intel GM965/GL960 video card.

hmm....my graphics card is a ATI Mobility RADEON 9000 AGP 4X video graphics I think. Also, I am on a laptop that is about 4 years old, and probably isn't made for this game.

---

### Post by ajcham on 2008-12-01
> **tobias-mansson said:**
> Has anyone experienced not been able to write in capitalized letters? Haven't found anyone else with that problem yet. I have the original game, patch 9.1 and cracked the fm.exe.

Yeah, I'm having that problem too.  Same patch/crack installation.

I'm currently using a clumsy workaround where I have a folder called ABCDEFGHIJKLMNOPQRSTUVWXYZ - I set this as the user folder, highlight the name, right-click and copy.  Then I quit the prefs without saving and  I can then paste the text into the manager name box (this is the only point at which I really care about the caps), deleting the letters I don't need.

---

### Post by tobias-mansson on 2008-12-03
I've been thinking if it's a keyboard problem, and that it could be solved by changing the keyboard settings. Be I haven't been so successful yet. Had to reinstall the game when I tried one solution.

---

### Post by Tosh78 on 2008-12-05
Please, give me some help. I've installed FM 2009 without problems. I've also installed the patch and the crack. So I tried to run it but I got a message saying "Cannot run game: failed to set up graphics system". So I tried to install SDK using winetricks "sh winetricks DXSDK_Nov08", but it couldn't find it, so I downloaded and installed it using "wine DXSDK_Nov08.exe". It installed perfectly but I'm still getting the same error. Any idea? Please, help me!

---

### Post by diopter on 2008-12-06
> **Tosh78 said:**
> Please, give me some help. I've installed FM 2009 without problems. I've also installed the patch and the crack. So I tried to run it but I got a message saying "Cannot run game: failed to set up graphics system". So I tried to install SDK using winetricks "sh winetricks DXSDK_Nov08", but it couldn't find it, so I downloaded and installed it using "wine DXSDK_Nov08.exe". It installed perfectly but I'm still getting the same error. Any idea? Please, help me!

I'm having the same problem also.

---

### Post by steveydoteu on 2008-12-06
I cannot actually extract the exe file with file roller.

EDIT: Nevermind, helps if the torrent of the demo executable finishes downloading first.

---

### Post by gretsenko on 2008-12-08
>  Originally Posted by andrizz  View Post
I Have the same error with an intel GM965/GL960 video card.

Intel GM965 - Black screen too :(:'(

FM 2008 working well

---

### Post by Tosh78 on 2008-12-09
Please, somebody help me. I installed the game in windows in the same computer and is working fine, so I assume it's not a hardware problem. Does anybody want/can help me?
How did you install DXSDK_Nov08? using winetricks? if so, what did you type? I installed it using "wine DXSDK_Nov08.exe" is that ok?

---

### Post by cmartins on 2008-12-10
Hi you all, first of all i've installed** wine 1.1**, and rebooted the wineserver (for me it was an upgrade)

Then installed some things with winetricks
winetricks **vcrun2005sp1**
winetricks **vcrun2005**
winetricks **allfonts**
winetricks **msxml3**

Then i've donwloaded and installed **JRE 1.5** - jre-1_5_0_17-windows-i586-p

Now the big piece of Directx Crap, you have to download and install **DXSDK_Nov08** (i know it sucks...)

Now we're ready for the FM2009, first time i've runned setup it showed me a blank screen... but i've noticed that the lax installer was running from windows temp, so i've
cd ~/.wine/drive_c/windows/temp/I..../

And there it was the temp folder for the game, delete the jre folder inside windows resources and from the command line, run wine setup.exe (the one inside the temp folder). You'll now see the installation window displayed correctly, and you just have to follow the setup.

Hope it helps, Robinho is scoring a lot for me ;)


One aditional note... For me, the game only works in full screen...

---

### Post by cmartins on 2008-12-10
> **Tosh78 said:**
> Please, somebody help me. I installed the game in windows in the same computer and is working fine, so I assume it's not a hardware problem. Does anybody want/can help me?
How did you install DXSDK_Nov08? using winetricks? if so, what did you type? I installed it using "wine DXSDK_Nov08.exe" is that ok?

Yeah, wine DXSDK_Nov08.exe should work

---

### Post by nenadsuperzmaj on 2008-12-12
I have installed the game and got it working under windoz xp. Can I use Wine to start it under Ubuntu 8.10 directly from the installed folder?

That's the way I used to play FM 2008...

I installed DirectX and when i start fm.exe, I get an "Microsoft Visual C++ Runtime Library" runtime error, and the console output:

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\Aplikacije\\igre\\Football Manager 2009\\fm.exe" failed, status c0000142

```

What do you make of this?

I downloaded this MSVCR80.dll and put in in the windows\system folder on Wine's C disk, but no luck...

Do I have to instal .NET framewort to get C++ part working?

edit: Well, I suppose I answered my own question there... After installing .NET framework (version 2.x) the game works. In full screen mode that is. In windowed mode there is something wronh, possibly with DirectX, but in full screen mode it works no problem, except the 3D match is a bit slower, so I turned the sky and stadiums(which are rubbish anyway) off...

Nice one. Thanks, nenadsuperzmaj :)

---

### Post by Tosh78 on 2008-12-13
Hi guys,
I'm still getting an error when I try to run FM09. I've installed it perfectly, and I also installed the libraries, DXSDK_Nov08, .Net, and everything, but when I try to run the game, a pop up comes saying:

Cannot run game: Failed to set up graphics system.

In the terminal, this is what I get:

```
 fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:advapi:CheckTokenMembership ((nil) 0x13f288 0x32fc54) stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x7d7e314c,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x7d7e3348,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10026 0x00000000
fixme:win:EnumDisplayDevicesW ((null),0,0x7d6d2464,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20028 0x00000000
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x20028
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10026
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub 
```

---

### Post by fedemw on 2008-12-16
Hello all,


1)
Patch to version 9.1.0 (Football Manager 2009 v9.1.0 Patch) downloading here: [http://www.gamershell.com/download_35922.shtml](http://www.gamershell.com/download_35922.shtml)

2)
Here you can get the Activator Crack for patched version (9.1.0). You don't need to activate after use this file (download from here: [http://w18.easy-share.com/1702865470.html](http://w18.easy-share.com/1702865470.html)).

3) Now i need your help ;-)

I installed winetricks, wine 1.1.10, Ubuntu 8.10 and a Intel graphics card on my Toshiba Laptop. I run the game and i get a black screen with a white cursor. I cannot do anything; i changed to winxp system in Wine... but it doesn't solves the issue.

I get this output from console:

```
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3406
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3406
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278

```

I cannot install under Windows and run from Linux because i deleted ALL Windows system from my PC one year ago ;-)

Could you please give me a little helo with this?

Thanks in advance

---

### Post by Flegmatik on 2008-12-23
I opened a website for linux players of Football Manager, come to [www.fmtux.net](www.fmtux.net) or [http://www.fmtux.net/index.php?board=25.0](http://www.fmtux.net/index.php?board=25.0)

For your problems, did you check if your graphical system is up to date ?

---

### Post by __Henke on 2008-12-27
Well!

I installed Ubuntu yesterday as to test if FM09 runs faster in Linux, I know FM07 did so here goes my yesterday evening:

1. Installed Ubuntu and later Wine.

2. Tried to install FM. Well, big fail.

I had to look on the web, and found the winetricks program. Used that with all the programs mentioned in this thread and then it started.

3. Next problem, the installwindow shows nothing at all. FMtux.net has a "good" guide, although, the E TTT S TTTT E didn't work for me, so I read in the thread more, then I came to a post that said when the install is running, try to delete the "jar" folder in ~/.wine/drive_c/windows/temp/I???

somehere in a folder that has windows/resources, then in the I???? folder, run "wine setup.exe", then I got the full install GUI. Fantastic.

I finally got the game installed without any fuss.

4. Now, the activation. SIs v2 of the fix didn't work, but the offline v3 did!

5. Now, the game is activated, but it wont start. The same symptom as the failing installation GUI. I can click things, I see the pointing cursor wehere the "Start new game", "Load game" etc, etc is.

And I'm stuck. 
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) - this is what lspci says, and I'm thinking that is the problem.

Gonna try to install the drivers with wine...

I hope this little post can be to some help for people. I also played around with NT4.0/2K/XP/Vista in winecfg with every step.

6. Upgraded Wine to 1.1.10 - Doesnt work either.

---

### Post by __Henke on 2008-12-27
Well...

7. 

I installed the DirectX SDK, November 08 release and the introscreens appeared. But after the "Lets kick racism out of football" nothing more happened... crap.

I got happy there for a while...

[http://henkee.se/bilder/fm09-fail.png](http://henkee.se/bilder/fm09-fail.png)

---

### Post by __Henke on 2008-12-27
Finally.

But on a different computer...

Tried to install with the CD, fail because Java didn't want to work for some reason.

Used Steam, activationfix 3 and the other stuff with winetricks.

Im happy now.

---

### Post by Flegmatik on 2008-12-28
> **__Henke said:**
> Well!

I installed Ubuntu yesterday as to test if FM09 runs faster in Linux, I know FM07 did so here goes my yesterday evening:

1. Installed Ubuntu and later Wine.

2. Tried to install FM. Well, big fail.

I had to look on the web, and found the winetricks program. Used that with all the programs mentioned in this thread and then it started.

3. Next problem, the installwindow shows nothing at all. FMtux.net has a "good" guide, although, the E TTT S TTTT E didn't work for me, so I read in the thread more, then I came to a post that said when the install is running, try to delete the "jar" folder in ~/.wine/drive_c/windows/temp/I???

somehere in a folder that has windows/resources, then in the I???? folder, run "wine setup.exe", then I got the full install GUI. Fantastic.

I finally got the game installed without any fuss.

4. Now, the activation. SIs v2 of the fix didn't work, but the offline v3 did!

5. Now, the game is activated, but it wont start. The same symptom as the failing installation GUI. I can click things, I see the pointing cursor wehere the "Start new game", "Load game" etc, etc is.

And I'm stuck. 
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) - this is what lspci says, and I'm thinking that is the problem.

Gonna try to install the drivers with wine...

I hope this little post can be to some help for people. I also played around with NT4.0/2K/XP/Vista in winecfg with every step.

6. Upgraded Wine to 1.1.10 - Doesnt work either.

How do you use the V3 ? 

The tutorial of FMTux for english users is up to date on [http://www.fmtux.net/index.php?topic=67.0](http://www.fmtux.net/index.php?topic=67.0) ;)

---

### Post by RichMase on 2008-12-31
Ok, this is where I'm at now.

Downloaded WineTricks and did everything the original how-to guide asked.

Installed java, and the .dll files recommended by FMTux and followed the walk-through on the installation screens.

Now, it's all installed and I've ran the activator, the attached screenshot is the first screen I come to when I run FM2009. None of the buttons are functional. What do I do?

---

### Post by Flegmatik on 2008-12-31
Try to install IE with winetricks (run winetricks and select IE) You would see the good activation window...

---

### Post by RichMase on 2008-12-31
> **Flegmatik said:**
> Try to install IE with winetricks (run winetricks and select IE) You would see the good activation window...

It's saying module not found, even though it is in the options list.

Edit, installing now

---

### Post by Flegmatik on 2008-12-31
when you run

```
winetricks
```

a new window opens with that :

[[IMG]http://img300.imageshack.us/img300/7739/captureselectapackagetory9.th.png[/IMG]](http://img300.imageshack.us/my.php?image=captureselectapackagetory9.png)

---

### Post by RichMase on 2008-12-31
I give up. I really do. I've jumped through every hoop going yet it's now saying, at the product activation screen, that I've keyed in an incorrect code. I bought the game from a shop, I've had less trouble installing cracked editions in the past!

---

### Post by Flegmatik on 2008-12-31
The first time i installed the game i pass successfully the activation... But I had to format my laptop... I re-install the game and try the same thing and it didn't work so i use the crack file for the patch 9.1.0 because i have no found how to do now... i'm working now to create an update with a linux team ;) and after i'll try to find how to activate the game ;) But some peoples in FMTux.net activated their game without problems...

---

### Post by RichMase on 2008-12-31
> **Flegmatik said:**
> The first time i installed the game i pass successfully the activation... But I had to format my laptop... I re-install the game and try the same thing and it didn't work so i use the crack file for the patch 9.1.0 because i have no found how to do now... i'm working now to create an update with a linux team ;) and after i'll try to find how to activate the game ;) But some peoples in FMTux.net activated their game without problems...

Well I've followed everything that has been advised, short of using a crack or a patch, because I don't want to corrupt the game ie being sacked at the end of every season.

I know it was a gamble buying a game not compatible for my setup, but it really is a pain in the **** when after all that, it's saying the code is incorrect, which is clearly ******** because I have the game with me.

---

### Post by Flegmatik on 2008-12-31
I can understand your frustration because i do the same... i'll try quickly to have an answer... I read somewhere the fixv2 didn't work now and that we have to use the fixv3 but it did'nt want to work with wine ! When i'll be back home (after my vacations) i'll try to use it...

---

### Post by Champino on 2009-01-01
i was experiencing the same problem as some of the others with the activation box that pops up with no next button, and I can confirm that installing IE with winetricks fixes the problem.

i am however still having the problem with not having any capital letters in the game, no big thing but yeah, kind of annoying.

---

### Post by Champino on 2009-01-01
ok so now i have hit an even bigger problem, one I really have no idea how to fix.

The game runs fine, match engine, everything. it just locks up after the 3rd match or so, during the "processing" screen. it just grinds to a halt, and becomes totally unresponsive. i have spent about a month getting this game to run, and now it does, it still doesnt work properly. Virtualbox is not a viable option either, as the game runs annoyingly slow and the match engine jerks uncontrollably. 

anyone else having this problem?

---

### Post by Flegmatik on 2009-01-01
I never saw that !

---

### Post by anlag on 2009-01-01
First of all, thanks a million to everyone who's contributed, most of all to the people behind fmtux.net; I spent hours to get the installer window to work trying just about everything in this thread and a few more things... when just following the guide on what buttons to click and when did the job very well.

I'm using a cracked version as I want to know I can run the game before buying it. Patched to 9.1 and it started up well, I didn't even need the DXSDK installation (because I sorted it while downloading.) Could start a game, but had the issue where I could only type in lower case letters. *However, after a while I switched to windowed mode which worked well, and next time I tried I could use upper case letters just fine!*

Wanting to see if this was reproducable, I shut down the game and restarted it... only to realize it doesn't seem to be able to start in windowed mode. The window outlines appear, but there are no contents and it hangs shortly.

I'll try the SDK installation, see if that helps. If not, and there's no way to get it back to starting in fullscreen that doesn't involve any controls inside the same, I suppose I'll need to reinstall and never exit the game in windowed mode again.

---

### Post by anlag on 2009-01-02
Installing the DirectX SDK didn't help being able to start in windowed mode, the problem persists.

**--Trying to force FM to start in fullscreen**
The preference to use windowed mode must of course be saved somewhere that FM finds it during startup... and having a look, I came upon this folder:

~/.wine/drive_c/windows/profiles/anlag/Application Data/Sports Interactive/Football Manager 2009/settings/Version 901

...which contained a file called full_window.xml, containing a boolean variable set to "false." Great, thinks I, changing it to true and thinking that would solve it but no. Then had a look in the install directory under my Windows XP system, and it doesn't even contain that file so I deleted it from the above patch thinking it goes fullscreen by default if it doesn't find that file... and it didn't, it still went windowed.

**--Windowed start works after all, but slow (facegen issue?)**
However, as I went to type this I just left the last startup window open even though it had 'apparently' hung and lo and behold, it hadn't... it just took significantly longer to start up (in windowed mode.) Something like five minutes, to compare with the seconds it normally takes. And upon coming back to life after this wait, a pop-up is displayed saying the face generator couldn't be initialized and so is disabled. Perhaps disabling this altogether will mean the game starts fast again.

**--Lower case issue**
As I got back into the game after that wait, still in windowed mode I checked again and upper case letters work fine. I then tried to switch to fullscreen mode in the preferences menu, which unfortunately crashed the game. :)

--

edited to add:

After another slow start, I disabled player pictures altogether which got rid of the error message with the facegen (logically) however the game still takes five minutes to start up in windowed, and switching to full screen after it has still crashes it.

--

and edited again:

Should've learned the first time... it seems the game didn't crash when switching to full screen, the window just disappeared for another five minutes or so, and when it came back it took the whole screen although the game graphics were restricted to a part of it the same size as the starting window. And the mouse was out of synch, so it only half managed to switch to fullscreen. Think I may reinstall and get back to this later, feels like a bit of a sidetrack.

---

### Post by Flegmatik on 2009-01-02
Hey guys, could you come to fmtux.net and report everything you wrote here for the community please ? it could be interesting to centralize all datas about using this game with Ubuntu ;)

---

### Post by meskel on 2009-01-04
> **anlag said:**
> Installing the DirectX SDK didn't help being able to start in windowed mode, the problem persists.

**--Trying to force FM to start in fullscreen**
The preference to use windowed mode must of course be saved somewhere that FM finds it during startup...


Well, I had the problem when tried to put in windowed mode: it was working good in full screen, black screen in windowed.

**I resolved like this:**
just put in wine conf to emulate a virtual desktop (I used 1024x768) and it worked good. It acts as in window mode, but like that is more slow... So I used this way to put back inpreferences "full screen" and playing in full screen.

---

### Post by Daninho13 on 2009-01-15
Could someone please give me a very detailed description, from top til toe, on how you install FM09 with patch 9.2.0.

I already have the cd, but I'd really like a very detailed description with:
- which commands I need to use.

---

### Post by kopus on 2009-01-15
Is there any solution for the blank screen yet?

I'm running Ubuntu 8.10 with a ATI Mobility Radeon HD 3470 graphics card. xorg if configured with the fglrx driver and has worked fine.

I got the latest version of wine from the Wine HQ and installed java, directx, etc. I have even checked the dxdiag just to see if directx is ok. Everything seems ok.

The error log is too big, so I will add it as an attachment. And hope it can do some help.

I can run the game on another computer that has an nvidia graphics card. So I suspect that the problem is with wine/directx/ATI.

---

### Post by anarchoal on 2009-01-16
I thought I'd add a note here - it seems that everyone with an Intel GMA card (including me :( ) is getting a black screen when running the game, with the pointer turning to a hand over the (invisible) buttons.

The console gives the following, repeated indefinitely:

fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3568
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 521
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278

Unfortunately, if you turn shaders off the game won't even run.

If anyone finds a solution, scream it from the rooftops! :)

---

### Post by anarchoal on 2009-01-16
Oh, I should add- the 2.5.x intel drivers don't help either.

---

### Post by jkapsi on 2009-01-18
I had the same problem with windowed mode. My solution was to copy the Sports Intractive folder from Application data in windows and paste it to application data in wine ubuntu. The full screen came back and the game is ok now!

---

### Post by jkapsi on 2009-01-18
> **meskel said:**
> Well, I had the problem when tried to put in windowed mode: it was working good in full screen, black screen in windowed.

**I resolved like this:**
just put in wine conf to emulate a virtual desktop (I used 1024x768) and it worked good. It acts as in window mode, but like that is more slow... So I used this way to put back inpreferences "full screen" and playing in full screen.

Meskel, Thank you!
I just tried your advice and worked like a charm!

---

### Post by tekne on 2009-01-25
looks like almost every problem as been solved except for mine and many that i've seen on this thread: when i run the game, i came ahead with:
```
me:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3480
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3480
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  11 (X_GLXSwapBuffers)
  Serial number of failed request:  1666
  Current serial number in output stream:  1666
```



anyone?

---

### Post by johnlyu on 2009-02-13
i've installed fm09 and got it working through steam on my thinkpad t61
but the thing is that when i launch the game it self it doesn't always work
majority of the time when i launch it, nothing happenes(both through steam and fm.exe in the file)
then i go to system monitor to see that it's status is sleeping
any suggestions to my problem
when it works everything works fine sound and stuff

---

### Post by bmitov on 2009-02-15
I downloaded FM09 and I've installed wine and all the winetricks. First off I'm not completely sure whether java is installed. I downloaded both the java files (one is 7mb and other is 15mb) and tried them both. The first one told me that it couldn't uncompress, and when I tried the second file it said that java was already on the system and asked if it wanted to reinstall. So to be sure, I said yes to the reinstall, and what happens... the thing doesn't do anything...

Anyways I thought that what the hell, I might as well try installing the game. So I extracted all the files from the iso and ran the setup by double clicking on it. It goes through the part where InstallAnywhere is preparing for installation, yet when it gets to 100% I get this blank window. The first time I waited it out... and nothing happened. I tried again and the same thing happened, except this time I pressed Enter a couple of times and another window popped up saying that "the installer can't run on this system........ fuckoff." So what am I to do? I'm running Ubuntu 8.10 which I installed just yesterday for the first time.

Anyways if you guys can help me out, I'll be a realllly happy!!! :D

---

### Post by linkman1337 on 2009-02-15
I'm having a similar problem to you, it's all installed, activated, everything, I think i've installed DirectX, etc, yet I just get a black screen when I load it.

---

### Post by bmitov on 2009-02-16
Alright so now I'm getting the "failed to set up graphics system." How do I get past this? I installed the Direct X SD from the microsoft website but I still get the same message...

---

### Post by goughs on 2009-02-20
> **tekne said:**
> looks like almost every problem as been solved except for mine and many that i've seen on this thread: when i run the game, i came ahead with:
```
me:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3480
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3480
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawArrays @ drawprim.c / 278
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  11 (X_GLXSwapBuffers)
  Serial number of failed request:  1666
  Current serial number in output stream:  1666
```



anyone?

I get the same as this, running with an ATI HD4850 1GB card, using the drivers from the ATI website.  Compiz disabled.

Blank screen, cursor with a white box around it, changing to a pointer presumably on the buttons, but unable to see them.

Hit a brick wall myself, and it seems everyone else has too.  Anyone have any ideas on a fix for this?

Or has anyone been able to get FM2009 running on VirtualBox?

---

### Post by tunni on 2009-02-23
i dont know if this error has been reported before but im knew to this and wasnt sure how to search etc, but when i play a match it shuts down and says something about a line not being formed, i managed to get around ten seasons with no problems, now it doesnt matter if its a new game or old game, it comes upwith this error everytime, any idea how i get rid?

---

### Post by pablitoneal on 2009-02-25
Hi all,

This thread has helped me a lot but now I'm stuck.  When I run fm.exe with wine, a window comes up and the circular Sports Interactive logo is displayed.  It spins off the screen to the right and then I just have a black screen.

I have ...
wine
winetricks
java
directx
fm patch 9.2

---

### Post by johnlyu on 2009-02-27
i just got the 9.3.0 patch and the game does not work at all
i run it through steam and now when i launch it nothing happens
it worked fine before just sometimes it wouldn't launch and i'd go to system monitor and end process and retry
but now it doesn't even register on system monitor

---

### Post by Nylon Alpaca on 2009-02-27
I had to add two windows native .dlls to the wine /windows/system32 folder after I patched up to 9.3.0 in order to get the game to run again.

pdh.dll was one and I forget the other. Run wine fm.exe from a terminal in the application folder and the output will tell you what .dll is missing.

---

### Post by PaulM1985 on 2009-02-28
Hi all

My fm was running for a while and now it doesn't start anymore.  I was running it through Steam and now it doesn't start when I try to run it.  It doesn't even appear in the System Monitor.  I have added those dlls mentioned in the previous post.  I think the other was odbcbcp.dll if anyone needed it.

When I try running from terminal, I get the following output:

[email]paul@paul-desktop:~/.wine[/email]/drive_c/Program Files/Steam/steamapps/common/football manager 2009$ wine fm.exe
fixme:advapi:RegisterEventSourceW ((null),L"PDH"): stub
fixme:powrprof:DllMain (0x7d670000, 1, (nil)) not fully implemented
fixme:powrprof:GetActivePwrScheme (0x32fbac) stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
Invalid CSIDL token name.
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:advapi:CheckTokenMembership ((nil) 0x1446a8 0x32fc54) stub!
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
err:seh:setup_exception_record stack overflow 852 bytes in thread 0009 eip f7d7f5ae esp 00230fdc stack 0x230000-0x231000-0x330000


Any idea what is happening with it? Any help would be greatly appreciated.

Paul

---

### Post by PaulM1985 on 2009-02-28
That output again in code tags to remove those annoying faces:

```
paul@paul-desktop:~/.wine/drive_c/Program Files/Steam/steamapps/common/football manager 2009$ wine fm.exe
fixme:advapi:RegisterEventSourceW ((null),L"PDH"): stub
fixme:powrprof:DllMain (0x7d670000, 1, (nil)) not fully implemented
fixme:powrprof:GetActivePwrScheme (0x32fbac) stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
Invalid CSIDL token name.
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:advapi:CheckTokenMembership ((nil) 0x1446a8 0x32fc54) stub!
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
err:seh:setup_exception_record stack overflow 852 bytes in thread 0009 eip f7d7f5ae esp 00230fdc stack 0x230000-0x231000-0x330000

```

Paul

---

### Post by doruktayfun on 2009-02-28
I got ubuntu 8.10 (64bit) 
I've been trying since last night but only managed to run the activation window on the game. 
I got the game through Steam (so it's patch 9.3.0)  

*installed with winetricks : directx9 ,  msxml3  ,  pdh ,  dotnet20 ,  vcrun2005 , vcrun2005sp1 .
*Downloaded some dlls (obcd32 , obcd*.dll)
*made the dlls window native . 
*downloaded&installed java for windows

Anyway I got this far but after this I'm stuck. I installed the fix(v3) to activate the game. Managed to run it and got an "activation successful" message (or something similar) . After running fm.exe I still get an activation window which is very corrupted 
[IMG]http://img22.imageshack.us/img22/7108/screenshotf.jpg[/IMG]
[IMG]http://img88.imageshack.us/img88/1222/screen2uxc.jpg[/IMG]

And I'm unable to click / tab to next button. 

(I'm running wine as WindowsXP)

Anyone having the same problem ?

---

### Post by Nylon Alpaca on 2009-02-28
Have you tried deleting the activation cache and re-running the SI activation fix utility?  (details at [http://community.sigames.com/showthread.php?t=63556](http://community.sigames.com/showthread.php?t=63556)).




@Paul; have you verified the game files through steam?  Before I added the .dll files I discovered the patch didn't properly download and Steam updated the files again.

---

### Post by doruktayfun on 2009-02-28
I tried deleting those and doing it again but failed. Guess linux still isn't good for playing games :/

It's been 24 hours since I started trying to play this game.

---

### Post by PaulM1985 on 2009-02-28
> **Nylon Alpaca said:**
> Have you tried deleting the activation cache and re-running the SI activation fix utility?  (details at [http://community.sigames.com/showthread.php?t=63556](http://community.sigames.com/showthread.php?t=63556)).




@Paul; have you verified the game files through steam?  Before I added the .dll files I discovered the patch didn't properly download and Steam updated the files again.

Hi

Thanks for the reply.  Steam updated the files itself and I added the .dlls after this and unfortunately it still doesn't seem to work.  It seems strange that it was running fine and all of a sudden it stopped.

I am using Ubuntu 8.10 on 64 bit if that makes any difference.

Any ideas?

Thanks again

---

### Post by Nylon Alpaca on 2009-02-28
It looks like the key difference I have to you guys is that I'm running 32-bit, but I don't know how much of a difference it is for Wine. 

SI have had reports of games not running under Windows after this patch, so it isn't necessarily a Wine issue.  One of the fixes that has worked in those cases appears to be to have Steam uninstall and then re-download the whole game.

---

### Post by PaulM1985 on 2009-03-01
Thanks for the advice.  I will try that today.

Paul

---

### Post by womble1690 on 2009-03-01
> **doruktayfun said:**
> I got ubuntu 8.10 (64bit) 
I've been trying since last night but only managed to run the activation window on the game. 
I got the game through Steam (so it's patch 9.3.0)  

*installed with winetricks : directx9 ,  msxml3  ,  pdh ,  dotnet20 ,  vcrun2005 , vcrun2005sp1 .
*Downloaded some dlls (obcd32 , obcd*.dll)
*made the dlls window native . 
*downloaded&installed java for windows

Anyway I got this far but after this I'm stuck. I installed the fix(v3) to activate the game. Managed to run it and got an "activation successful" message (or something similar) . After running fm.exe I still get an activation window which is very corrupted 

And I'm unable to click / tab to next button. 

(I'm running wine as WindowsXP)

Anyone having the same problem ?

Hi 

To get the activation window to show correctly install ie6 via winetricks

You should then be able to activate and run game

---

### Post by PaulM1985 on 2009-03-01
Hi

I have just checked before uninstalling reinstalling that my wine version is 1.1.16.  I think it was version 1.1.10 when it was working originally.  Is there a way that I can get wine back to version 1.1.10 or 1.1.11?

Paul

I have installed Wine 1.1.10 and still not working.  Unsure what to do now.

---

### Post by Nylon Alpaca on 2009-03-01
I'm running wine 1.1.16.  I'd guess that given that there have been issues on Windows too, deleting and reinstalling through Steam is more likely to help than changing Wine version.

Are you running FM using Windows XP compatibility in Wine?  I found that worked better than Vista from initial release.

---

### Post by doruktayfun on 2009-03-02
Well FM2008 works beautifully. So I just downloaded a midseason database update and playing fm2008 :D Thanks for the help .

---

### Post by Raistlin82 on 2009-03-07
Hi all, I dual boot win vista and intrepid, when using fm08 i just copied the exe over from vista and was able play the game, I've just copied the entire folder over but cant seem to get it to run, anyone know a quick fix? Really want to play in ubuntu!

---

### Post by bennyevs on 2009-03-09
hi, 

im reasonably new to ubuntu but not to software and os's e.t.c.

have installed wine, wine tricks and the needed directx, went through installation of football manager 2009 and now have the launcher shortcut on my desktop, and a location in the c: drive. but when i try to launch the game through application-wine-programs-sports interactive..... i get nothing. a tab opens on the tab bar saying 'starting football manager 2009' but then dissapears and my laptop stops accessing my hard drive. 

any ideas? its really frustrating to get this far and not be able to play!

---

### Post by wild_oscar on 2009-03-11
Has anyone managed to have 9.3.0 working?

---

### Post by PaulM1985 on 2009-03-14
I still haven't.  I am trying to reinstall and I can't install from disc anymore because the windows that open for the installation are all blank.

Paul

---

### Post by marks04 on 2009-04-20
Once i have downloaded the graphics package off microsoft do i just launch football manager and it will work???

---

### Post by stwschool on 2009-05-02
For those struggling:
I'm running FM09 (legit, not pirate) through the latest wine. It works ok on 8.10 or 9.04. not tested on anything older. I basically followed the tutorial on the fmtux website and was fine. I also ran the command in terminal to see what errors came up. Where a dll file was mentioned, I found that dll and put it in the windows/system32 folder. It's straightforward if you're willing to do a little bit of detective work.

---

### Post by Aidan James on 2009-05-02
hi all,

i purchased the game today, and am having issues getting past the install loading. after i run setup.exe, i get the following:

[IMG]http://img186.imageshack.us/img186/4164/capturesn3.jpg[/IMG]

i'm running wine 1.18, i've installed winetricks, along with directx9, vcrun2005sp1, vcrun2005, msxml3, ie6, and even java. also, i was reading a tutorial, and have done this: download the dll xinput1_3.dll and d3dx9_38.dll to place in the folder  /.wine/drive_c/windows/system32.

can anyone tell me where i'm going wrong? thanks in advance. i'm running intrepid, by the way.

---

### Post by wild_oscar on 2009-05-12
> **Aidan James said:**
> hi all,

i purchased the game today, and am having issues getting past the install loading. after i run setup.exe, i get the following:

[IMG]http://img186.imageshack.us/img186/4164/capturesn3.jpg[/IMG]

i'm running wine 1.18, i've installed winetricks, along with directx9, vcrun2005sp1, vcrun2005, msxml3, ie6, and even java. also, i was reading a tutorial, and have done this: download the dll xinput1_3.dll and d3dx9_38.dll to place in the folder  /.wine/drive_c/windows/system32.

can anyone tell me where i'm going wrong? thanks in advance. i'm running intrepid, by the way.

That's what always happens to me....

---

### Post by rcayea on 2009-05-12
I get that same screen...

As someone stated in a previous post in this thread, is there a workaround to copy/paste fm09 from my windows HD to my linux HD and play it that way? Maybe to get around the installation issues?

R.

---

### Post by mckay077 on 2009-05-13
my fooball manager isnt working it says
 
not well formed invalid token at line 1 of channel- FAVEGEN_CHANNEL.xml
 
wat does that mean
 
REPLY ASAP

---

### Post by kubu88 on 2009-05-21
Hi guys,

i can't really run my football manager. The installation works fine and I fixed the activator problem. When I start fm.exe a warning appears: Failed to setup graphic system. This is a know problem so I find out I gotta use DirectX SDK to get my game working. I installed this software but the problem isn't solve yet. So? What does it mean? What have to do for not throw out of my window this ******* ****?
Thank you...

---

### Post by kubu88 on 2009-05-21
> **Aidan James said:**
> hi all,

i purchased the game today, and am having issues getting past the install loading. after i run setup.exe, i get the following:

[IMG]http://img186.imageshack.us/img186/4164/capturesn3.jpg[/IMG]

i'm running wine 1.18, i've installed winetricks, along with directx9, vcrun2005sp1, vcrun2005, msxml3, ie6, and even java. also, i was reading a tutorial, and have done this: download the dll xinput1_3.dll and d3dx9_38.dll to place in the folder  /.wine/drive_c/windows/system32.

can anyone tell me where i'm going wrong? thanks in advance. i'm running intrepid, by the way.

This is a java problem. Couldn't be a problem install the game if you follow the instruction of fmtux.net . I hope this could help you.

---

### Post by Mokou on 2009-05-30
> **kubu88 said:**
> This is a java problem. Couldn't be a problem install the game if you follow the instruction of fmtux.net . I hope this could help you.


I have the same problem,i tried with the help of fmtux.net but nothing,wine sees only the first enter end then nothing,is there anything to fix java
?

---

### Post by proevofanatik on 2009-06-05
> **kubu88 said:**
> This is a java problem. Couldn't be a problem install the game if you follow the instruction of fmtux.net . I hope this could help you.


i get this problem too but i get that black window and a loading bar. when it gets to 100% it just closes and then nothing. it wont even go as far as installing. as far as i know i have all my wine tricks files loaded in. 

im using the full game of fm09 too.

---

### Post by proevofanatik on 2009-06-05
ok i managed to get the full game to install and load up. but the main menu screen of the game is black. you can move the cursor around and the curson even changes to a hand when the cursor is hovering on new game or something. 

this is what i did and what im using.

i have linux mint 7 gloria dual booted with windows xp. i installed wine and wine tricks. the winetricks packages installed are dotnet11, dotnet20, pdh, directx9, vcrun2005, vcrun2005sp1 and i changed windows version to windows 2000.

what i then did was install football manager 2009 on xp. install the update 9.0.3 then play the game. then closed the game then reboot into linux mint 7. i opened the xp partition, went into my aplication folder and copied the sports interactive folder into my wine application folder and did the same in program files.

now when i click on the fm.exe in progam files the activator loaded up. the actual one you get in xp. not the one everyone is complaining about. i put in my cd key and everything activated just fine. the game then loaded up but very slow. all of the kick racism out of football load screens loaded up again very slow. 

now when i look in my hardware drivers i cant see a graphics driver and im guessing that is whats causing itto be slow. if i can get the graphics issue sorted then i think it will be playable. im also guessing the graphics issue is causing the black main menu screen. does anyone know if there are drivers for ati cards in linux mint 7? i have a ati radion x1800.

---

### Post by Hairy_Palms on 2009-06-06
if its the same as fm07 and fm08 you must install java for windows under wine to speed it up
get it from [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

download the XP/Vista version. also it needs to be run in its own wine desktop, run winecfg and check emulate virtual desktop in the graphics tab, 

also the driver to install in synaptic is xorg-driver-fglrx and fglrx-modaliases for ATI cards iirc if you want it working in jockey too.
hope that fixes some issues at least.

---

### Post by goughs on 2009-06-18
Guys, the Virtualbox 3 Beta has experimental DirectX9 support.  I have Football Manager 2009 running OK on Windows XP SP2 in this version.

You must download and install Virtualbox 3 Beta from here:

[URL="http://forums.virtualbox.org/viewtopic.php?f=1&t=18820"]
http://forums.virtualbox.org/viewtopic.php?f=1&t=18820[/URL]

Then you MUST install Guest Additions for this version, and make sure you tick the box to enable DirectX support.

I downloaded and installed the DirectX SDK from Microsoft.  Run dxdiag and do the Display tests, DX 7 & 8 failed for me, but the DX 9 one worked perfectly fine.

I copied my FM folder from my Windows install, and did telephone activation, although I see no reason why Steam/the DVD version wouldn't work.

Then run fm.exe.  It didn't work in windowed mode for me, and occasionally crashes out on loading.  If it does crash, reboot the VM, and load again, this seems to work.

Issues are that you can't view the match in 3D, I just get a black field with the player names, the 2D view works fine however.

---

### Post by andreimr on 2009-06-24
I managed to install the game with the blank screen. 

I enter the folder where the game is installed, run the fm.exe and i get this :
wine fm.exe
err:service:validate_service_config Service L"Macsvmgbbsbs" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Macsvmgbbsbs" - skipping
fixme:actctx****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\saAuditMD.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\saAuditMD.dll") not found
err:module:import_dll Library saAuditMD.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\fm.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\fm.exe" failed, status c0000135

---

### Post by beswar on 2009-06-27
Hello,

I have a problem, I installed the game, patched and cracked, but when I try to run fm.exe, nothing happens. 
I use wine, and downloaded winetricks.

I get:

wine fm.exe
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:advapi:CheckTokenMembership ((nil) 0x1406b0 0x32fc54) stub!
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:advapi:CheckTokenMembership ((nil) 0x1406b0 0x32fc58) stub!
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 27/09/2009, dlt (d/m/y): 27/03/2009
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!

---

### Post by beswar on 2009-06-27
help....?

---

### Post by andreimr on 2009-06-28
FM09 is working now, but it/s very very slow.

---

### Post by toninho_77 on 2009-07-17
Hello people, this is my first post, sorry about my English! :-D
Well, I have a problem with my virtualbox and football manager 2009, I have in virtualbox 3 windows xp sp3 and fm 2009 installed, the problem is, when I run the fm.exe, is open, but in 5/6 seconds later, close again, in this time i can't play the game, is something wierd because not show a message error or something like that.
Someone help me in this?
Thanks, and sorry again about my english, it's very bad I know!
By the way, I'm portuguese and a newbie in the forum! :-({|=
Thanks for the patience!

---

### Post by realmagnum on 2009-08-11
> **toninho_77 said:**
>  when I run the fm.exe, is open, but in 5/6 seconds later, close again,

toninho_77,

I have the same problem with VirtualBox 3.0.4, WinXP SP3 and FM 2009.

I don't know what to do.

Anyway, the problem is probably caused by video driver. Virtual machines doesn't have a good 3D support.

In this topic ([http://ubuntuforums.org/showthread.php?t=1190989]("http://ubuntuforums.org/showthread.php?t=1190989")) the same problem was mentioned:

> **goughs said:**
> It didn't work in windowed mode for me, and occasionally crashes out on loading. If it does crash, reboot the VM, and load again, this seems to work.

However, nothing worked for me.

It's good remember that wine is the best way to run games and any other 3D applications.

---

### Post by bresdog on 2009-08-12
I've gotten everything going ok, just cant get past the activation screen where you submit the product key? I dont think its a DirectX or Java problem as i've got both them installed, along with all the winetricks stuff mentioned in this thread. Also been through the fmtux site and did everything there. Any ideas because im stumped?
Thanks

---

### Post by TehPea on 2009-08-13
I bought FM09 and installed it and updated it to 9.0.3 (all of this was done in Windows Vista x86 and put on a NTFS partition). I have Ubuntu 9.04 x64, if I installed Wine would I be able to run FM09 from the NTFS partition? I can run FM09 from Vista x86. My graphics card is an ATi Mobility Radeon HD3470 and I have AMD/ATI drivers installed in Ubuntu.

edit: I installed Wine and Ubuntu yesterday on a 10gb ext3 partition and I know absolutely nothing about Linux or the like.

---

### Post by rcayea on 2009-09-25
> **bresdog said:**
> I've gotten everything going ok, just cant get past the activation screen where you submit the product key? I dont think its a DirectX or Java problem as i've got both them installed, along with all the winetricks stuff mentioned in this thread. Also been through the fmtux site and did everything there. Any ideas because im stumped?
Thanks

I get that same box. I am wondering if we can run a command from command line to activate that box and then insert our activation codes through terminal???

---

### Post by Djises on 2009-10-02
Ok..here goes. 

I'm a complete noob when it comes to Ubuntu, just installed it a couple of days ago. 
But so far i love it..beats the crap out of windowns  \o/

but theres only 1 problem..when i try to get fm09 up and running, i get to the point where is says preparing to launch fm..and then it just vanishes! :(
Ive tried to read the forum, but quite frankly, i dont know what to look after. 
so I'm hoping that one of you can give me a hand and tell me whats wrong..?
and if you say it in a way that a complete noob like me can understand it, that would be nice :)

>Djises<

btw, got 9.04    amd 64...

---

### Post by bresdog on 2009-10-07
> **rcayea said:**
> I get that same box. I am wondering if we can run a command from command line to activate that box and then insert our activation codes through terminal???

Im not sure to be honest. Thats a bit out of my scope unfortunately. Im going to try and install it again this weekend, gave up last time.

---

### Post by rcayea on 2009-10-08
Well,

I gave up kind of. I had the opportunity to obtain an XP disk. I installed it in virtualbox as a VM. I then was able to install FM09 right into the VM. I kept hearing how this wasn't possible. So, now I can play FM at just about the same speed as "normal". Now, the only problem is my games are shown in 2D and I am working on making the 3D players show up. 

Randy

---

### Post by WombleKiller on 2010-08-23
I know this is probably a dead thread now, but I'd really appreciate it if someone could help me!

I've managed to install the game (after two days of trying!) thanks to this brilliant thread, but when I click on FM.exe I get the box 'Football Manager 2009 is already running'. I've tried shutting down and making sure it isn't running, but I keep getting this box popping up and it won't allow me to continue.

The only reason I have to use Windows is Football Manager. I love Ubuntu and want to stay on it!

---

### Post by WombleKiller on 2010-08-23
I managed to get round that problem by running wine taskmgr and manually ending FM.exe which was running (put doing/showing nothing). I now get 'the program fm.exe has encountered a serious problem...' and it then closes.

Ack, it feels like I'm so close too.

---

### Post by WombleKiller on 2010-08-23
Sorry for spamming this thread now...

I've managed to get rid of the previous two problems, and to my knowledge did everything that everyone has mentioned here, but when I click on the FM.exe file the virtual window appears for a few seconds and then disappears with no error messages, and nothing happens!

---

