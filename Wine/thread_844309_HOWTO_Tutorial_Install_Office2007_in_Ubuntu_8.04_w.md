---
title: "HOWTO Tutorial: Install Office2007 in Ubuntu 8.04 with Wine 1.1"
date: 2008-06-29
forum: Wine
---

### Post by rdiaztushman on 2008-06-29
Hello!

I have found that all of the HowTo tutorials out there for this process are missing steps.  To get Office 2007 to work on my system with:

Wine 1.1
Ubuntu 8.04

I needed to pull various commands from various tutorials and execute them in a specific order.  I thought I'd put them all together here.  Hope this helps!

------------------------------------------

Step 1. Install Wine:
[LIST]
[*]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[*]	sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
[*]	sudo apt-get update
[*]	sudo aptitude install wine
[/LIST]

Step 2. Download Winetricks

[LIST]
[*]wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
[/LIST]
Step 3. Install Cabextract to run the Winetricks smoothly

    	[LIST]
[*]sudo aptitude install cabextract
[/LIST]

Step 4. Run Winetricks

	[LIST]
[*]sh winetricks
[/LIST]

[INDENT]
In the Winetricks window, install each of the following *individually*, which means check & install one, then re-run Winetricks and do the next:

	* dotnet11
	* dotnet20
	* vb3run
	* vb4run
	* vb5run
	* vb6run[/INDENT]


Step 5. Configure Wine. 

	[LIST]
[*]winefcg
[/LIST]

[INDENT]In the "Applications" tab, set "Version to Imitate" to *Windows Vista* 
	In the "Libraries" tab, define "rpcrt4.dll" and "msxml3.dll" as *Native (Windows)*[/INDENT]


Step 6. Rename files.


[INDENT]In ~/.wine/windows/system32, rename "rpcrt4.dll" to "rpcrt4.dll_bak" (you will need this later) 
	In ~/.wine/windows/system32, rename "msxml3.dll" to "msxml3.dll_bak" (you may need this later)
	Download a replacement for "rpcrt4.dll" here: [http://www.mediafire.com/?njtut9aswdk](http://www.mediafire.com/?njtut9aswdk)
	Copy the downloaded "rpcrt4.dll" to ~/.wine/windows/system32.
[/INDENT]

Step 7. Run Winetricks again.

	[LIST]
[*]sh winetricks
[/LIST]

	[INDENT]In the Winetricks window, install each of the following *individually*, which means check & install one, then re-run Winetricks and do the next:

	* msxml3
	* msxml4
	* msxml6
	* riched20
	* riched30
	* vcrun6
	* vcrun2003
	* vcrun2005
	* vcrun2005sp1
	* vcrun2008[/INDENT]

Step 8. Install MS Office 2007.

	[INDENT]From your MS Office Installer CD or Directory, run:[/INDENT]

	[LIST]
[*]wine setup.exe
[/LIST]

Step 9. Revert to original dll file.

[INDENT]
In ~/.wine/windows/system32, rename "rpcrt4.dll" to "rpcrt4.dll_dl"
	In ~/.wine/windows/system32, rename "rpcrt4.dll_bak" to "rpcrt4.dll"[/INDENT]


Step 10. Set Wine to emulate WindowsXP

	[LIST]
[*]winecfg
[/LIST]

[INDENT]	In the "Applications" tab, set "Version to Imitate" to *Windows XP* 
	In the "Libraries" tab, define "rpcrt4.dll" as *Native then Builtin*[/INDENT]


Step 11. Run Office 2007 to confirm it works!

I really hope this helps you all!

Thanks!

---

### Post by FatalChaos on 2008-06-30
I just tried this from a clean wine install, and it didn't work for me. Everything installed correctly, but nothing would load up. The closest I got was word would load up and them immediately crash. I might have done a step wrong, so I'll try again some other time. But still, could you post anything else on wine that might help your ms office 2007? especially b/c ur one of hte only ppl who seems to have gotten a stable office going.

---

### Post by cbuckbee on 2008-07-02
I was able to get Office 2007 installed and running following these steps with a fresh install of Ubuntu 8.04 and Wine 1.1.  All the programs work except for Outlook 2007 which exits with a generic popup box that reads, "Cannot start Microsoft Office Outlook".  I haven't been able to find anything else online about this error yet but will keep looking.

---

### Post by snowball1288 on 2008-07-02
I had a similar problem to FatalChaos.  Word 2007 crashed on startup, along with most of the other programs.  i also found that i couldnt re-launch winecfg after Step 9.  

So heres what i did:
I did Step 10 (setting wine to emulate XP and changing the settings on rpcrt4.dll) _*before*_ Step 9.  Then I went back and did Step 9.  

And it works!  Word, Excel, Powerpoint, and OneNote 2007 all seem to launch and respond normally.  And my compiz effects all work on them.  :)  hats off to Wine and to rdiaztushman for the HowTo.

---

### Post by RustyTrowel on 2008-07-04
Thanks rdiaztushman.

Using your install method I got everything to work except Access.  

Unfortunately,  my attempts at fixing that issue completely messed things up.  I reinstalled wine and winetricks and tried to go through the steps again.  The result of that decision was that winecfg refused to open.  I'm starting a new thread to see if folks can't help me get that going.

I'm definetly going to try to use this tutorial again once I get wine running properly.

---

### Post by daerko on 2008-07-05
The install was sucessful but I had same problem as snowball with not being able to launch wine config. I did the same thing as him to change it to run as WINXP and it crashes using the downloaded dll and starts with an errors from services.exe of missing rpcrt4.dll and then doesn't see the dlls like ole32.dll, oart.dll, urlmon.dll, ole32.dll and wwlib.dll (which are all suprisingly in their correct directories) while using the default rpcrt4.dll. 

I find it funny that wine config runs with the downloaded rpcrt4.dll but doesn't run with the default one (it gives the rpcrt4.dll missing message and is required by services.exe). 

I don't know where I should proceed from here.

---

### Post by d4ng3r on 2008-07-05
So I followed the tutorial but for some reason office still wont install.  Has anyone tried this with Enterprise, every time I run the installer it crashes (and wants me to send an error report) at the point right after you click the "Install" button and the status bar comes up.  I think it MAY have something to do with some of the things Winetricks installed not working exactly correctly...but I wouldn't know how to fix that.

---

### Post by elmaster84 on 2008-07-05
Hi...
I did every step until No. 10
I cant get winecfg to work...
This is the problem Im getting. so If any one could help me!!!...
I urgently need Office 2007. I have a presentation on Monday 7th and my Windows Vista ](*,) partition stopped working for no reason at all!!...cant load my user profile, so I cant acces my documets...something like that!!....

PLEASE HELP!!!

```
jach@jach-laptop:~$ winecfg
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

```

---

### Post by Twitch6000 on 2008-07-05
I must suggest also trying out wine doors due to it making some of the windows instillation alot easier.

---

### Post by lilkidz on 2008-07-15
> **d4ng3r said:**
> So I followed the tutorial but for some reason office still wont install.  Has anyone tried this with Enterprise, every time I run the installer it crashes (and wants me to send an error report) at the point right after you click the "Install" button and the status bar comes up.  I think it MAY have something to do with some of the things Winetricks installed not working exactly correctly...but I wouldn't know how to fix that.

I have the same problem as you = =; Using Enterprise too; always asking my to send a error report =/

---

### Post by mrx17 on 2008-07-16
> **lilkidz said:**
> I have the same problem as you = =; Using Enterprise too; always asking my to send a error report =/


Same here... I've tried a lot possible tutorials.. but every time the installer crashes :( 

I get the following error:
fixme:xrender:x11drv_alphaBlend not a dibsection

And this goes on and on... I hope some knows the answer to get around that problem...

---

### Post by _DD_ on 2008-07-16
I went through all these problems (with Enterprise version) including the one mentioned above and spent days trying to get it working - after mushing together the instructions of several tutorials I finally got it installed and the apps I wanted working perfectly (Word, Excel, Powerpoint and Publisher).

It worked fine for one or two months, but then I didn't use Office for about 2 weeks, by which time I had run updates several times. Went to fire up Word yesterday and it loaded but then crashed. Tried to roll back Wine versions and tried different dlls which were being complained about, but no luck.

Arrrgggghhhh

So now I'm back to square one, and I can't remember what I did to get it working in the first place.

---

### Post by sjcrss on 2008-07-16
how do i find this.....Im stuck at this point...
Step 8. Install MS Office 2007.

    From your MS Office Installer CD or Directory, run:

    * wine setup.exe
i can't seem to figure it out.....sorry for the noobie question

---

### Post by mrx17 on 2008-07-18
I don't know how I did it, but I've got Office 2007 Working on my Ubuntu 8.04! Yes!:)

I was desperate... after installing the latest Wine version (1.1.1) and installing a lot of packages with Winetricks I somehow managed to get the installer running. After setting the windows version back to XP. The application (i only tested Word) works, for I can see perfectly.

Hopefully it would stay this way :)

---

### Post by Gokudan on 2008-07-26
Hi there!

I'm really stuck here, when i start winetricks and start running this installations i always get errors...for example, on the .doc attached file it's what i get when i install dotnet11..



Any ideas? I'm a linux newbie.


BR's
GD

---

### Post by ernstblaauw on 2008-07-28
I also have the Enterprise edition and it won't install. The first time I ran the installer of Office 2007, I got an error message that looks like this (at about a quarter of the progress bar): 
> R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application’s support team for more information.
Now, if I run the installer again, it quits very quickly and says only: > Microsoft Office 2007 Enterprise encountered an error during setup.
I can only click 'Close' then.
I'm running Wine version 1.1.2. Does someone know a solution to this problem?

---

### Post by ethos101 on 2008-07-31
So after a looooong time it finally finished...

But now nothing works.  Just crashes.

---

### Post by Xero121690 on 2008-08-16
So did any ones MS enterprise work with this guide?
I want to install MS enterprise but it seems like every one has problems with it..
Does any body have a solution to this?.

---

### Post by Beanmonster on 2008-08-18
Thank you rdiaztushman. 

The HowTo worked perfectly on my laptop, but on my desktop I get the following error when running setup.exe

> err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"F:\\Office 2007 Enterprise\\setup.exe") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\oleaut32.dll") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\oleaut32.dll") not found
err:module:import_dll Library OLEAUT32.dll (which is needed by L"F:\\Office 2007 Enterprise\\setup.exe") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\urlmon.dll") not found
err:module:import_dll Library urlmon.dll (which is needed by L"C:\\windows\\system32\\msi.dll") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\oleaut32.dll") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\oleaut32.dll") not found
err:module:import_dll Library oleaut32.dll (which is needed by L"C:\\windows\\system32\\msi.dll") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\msi.dll") not found
err:module:import_dll Library msi.dll (which is needed by L"F:\\Office 2007 Enterprise\\setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"F:\\Office 2007 Enterprise\\setup.exe" failed, status c0000135

I tried copying these dlls drom my windows partition, I downloaded different versions, I even used the same dlls on the laptop... but to no avail. Anybody know why?

---

### Post by Dihi Doctor on 2008-09-06
Does anyone else find that in Powerpoint 2007, when dragging a floating object (e.g. a textbox) that the whole slide turns black? This is actually quite a problem, since you cannot see where you are placing the object.

Is this just me? :confused:

---

### Post by jjwoznia on 2008-09-07
Is anyone using onenote to do hand drawn notes? It won't do pen stuff for me. Everyonce in a while it complains that it isn't the tablet pc version of xp and then it grays out all the pen tools. After this happens, wine starts using 50% of my cpu. 

Does anyone have a fix for this?

---

### Post by Lesterchakyn on 2008-09-24
> **Dihi Doctor said:**
> Does anyone else find that in Powerpoint 2007, when dragging a floating object (e.g. a textbox) that the whole slide turns black? This is actually quite a problem, since you cannot see where you are placing the object.

Is this just me? :confused:

This was somewhat fixed in Wine 1.1.5, have you tried it yet?  It still doesn't work properly tho.

Also try disabling Desktop Effects, it helped me a bit.

---

### Post by dontcopymusic on 2008-09-30
awesome! finally a COMPLETE howto that WORKS! thank you very very much!

One thing, I had to do step 10 before step 9.. I couldn't run winecfg otherwise.

---

### Post by elmaster84 on 2008-09-30
FINALLY
Thanx to the one who said that steps 9 and 10 were backwords!!!...
Im using office enterprise 2007!!...
The last thing that kept me going back to vista!!!
No more...free at last!!...
I hate to double boot.
Just one thing...I cant get MS Word to work, 
something about an error loading the dotx file necesary to open

C:\windows\...\3082\$ilding Blocks.dotx

If any one has any idea on how to make it work!!!...Ill be very VERY thankful!!:D:guitar:

---

### Post by smautf on 2008-09-30
I use Enterprise Edition, and it works because of this:
> **dontcopymusic said:**
> **[COLOR="Red"]I had to do step 10 before step 9.. I couldn't run winecfg otherwise.[/COLOR]**

Thanks to dontcopymusic and the person who started the thread!

---

### Post by ukblacknight on 2008-10-02
I've got this kinda working!

Word: Have to open it twice for it to work properly.  The first attempt, it closes instantly after opening it.  Other than that, Works fine.
Excel: Works fine
Access: Doesn't open due to a C++ Runtime error
Publisher: Works fine
Powerpoint: Doesn't open - no error message.
InfoPath: Works fine
Outlook: I get the same generic error as someone above me got.  Doesn't work.

Cheers to the OP and dontcopymusic for making us aware to swap steps 9 and 10!

If has any answers to the Word/Powerpoint problems, I'd be greatful for your help!

---

### Post by bwell on 2008-10-09
It worked!  Thanks rdiaztushman!  

I also reversed steps #9 & #10 and currently able to use Office 2007 (Word, Excel, PowerPoint, & Publisher.  I also received generic pop up error when trying to launch Outlook 2007.

---

### Post by killer_d76 on 2008-10-19
very nice tutorial!, i have created a "How to" in installing MS Office 2007 as well but using latest Wine version.. click here [http://ubuntuforums.org/showthread.php?t=922963]("http://ubuntuforums.org/showthread.php?t=922963")

here are some pics..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85611&d=1221715679[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85585&d=1221701314[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85586&d=1221701314[/IMG]

---

### Post by Kinst on 2008-10-19
> **jjwoznia]Is anyone using onenote to do hand drawn notes? It won't do pen stuff for me. Everyonce in a while it complains that it isn't the tablet pc version of xp and then it grays out all the pen tools. After this happens, wine starts using 50% of my cpu.

Does anyone have a fix for this?[/QUOTE]

I was trying to figure that out a long while ago. This is all I got:

[LIST]
[*]# Put a native copy of MSVP60.DLL and GDIPLUS.DLL in your fake windows/system32 folder. Then set GDIPLUS to native.[/LIST]

Then you'll be able to use the arrow tool, and any drawings show up properly, and it shouldn't crash as much.

You can't draw though.

[QUOTE=ukblacknight said:**
> I've got this kinda working!

Word: Have to open it twice for it to work properly.  The first attempt, it closes instantly after opening it.  Other than that, Works fine.
Excel: Works fine
Access: Doesn't open due to a C++ Runtime error
Publisher: Works fine
Powerpoint: Doesn't open - no error message.
InfoPath: Works fine
Outlook: I get the same generic error as someone above me got.  Doesn't work.

Cheers to the OP and dontcopymusic for making us aware to swap steps 9 and 10!

If has any answers to the Word/Powerpoint problems, I'd be greatful for your help!

Um...what I can tell you is that I had the exact same word-powerpoint problem. This was a long time ago though. I can't quite remember the fix. I thought it was 'winetricks riched20'. Did any of the winetricks fail or complain or something?

---

### Post by tC_Crazy on 2008-11-16
You are AMAZING. I have tried countless office 07 tutorials from the web, installed and uninstalled wine about 40 times in the last 3 days, and now FINALLY I got it to work. Before, everything installed properly, and Word and Excel worked properly. However, I could not get OneNote to open any notebooks, or even create a notebook. I have the problem with drawings/ink not showing up, but that's beyond the scope of this tutorial. Thanks a LOT.

---

### Post by d3phoenix on 2008-11-25
I got this working (with some modification) on **Ubuntu 8.10 Intrepid amd64**. (Intel C2D, 4GB RAM)

Here's what I did:

**Step 1 -- Install Wine:**
Since Wine 1.0* is now in the repos, I figured I'd just use the version already exposed through the default apt-sources. Run this in a terminal to install it:
```
sudo aptitude -y install wine wine-gecko
```

**Steps 2 through 8:**
Follow rdiaztushman's original guide EXACTLY. (Don't forget setting the imitation mode to Vista in step 5! It didn't work for me when I forgot that!)

**Steps 9 and 10:**
Do step 10 first, then step 9, or winecfg won't start properly.

---

### Post by Anbin89 on 2008-12-07
Hey guys... i have tried everything... i have this one problem... when the installation starts.. it keeps saying that it cannot find "Office.en-us/OfficeMUIset.xml"

can someone help me out here.. i would really appreciate it... Thanks in advance..
yeah..one more thing.. I am using ubuntu 8.10 intrepid amd64 as well... that is all guys

---

### Post by Anbin89 on 2008-12-10
It is ok. I have solved the problem. When you install, you have to choose cutomize and at the last tab, make sure you fill in name and organization. Weirdly, that solves all the problems and the tutorial works flawlessly.. Except for powerpoint

---

### Post by legoals on 2008-12-23
It works perfectly for me. Thanks your tutorial, it's very very useful.
P/S I think you should change the order of step 9 and 10 , so everybody can have the problem solved.

---

### Post by philrev on 2008-12-27
Good day to all! to people sucessfully installed MS office 2007 please give me a feedback if you were able to install Publisher and can create and save publisher files without errors. Thanks.

---

### Post by trentmc on 2009-01-01
thanks! seems to work like a charm with steps 9 and 10 swapped.

---

### Post by complete n00b on 2009-01-01
Thanks a MILLION for this post. I thought I'd never get it working but this turned out like magic!!

---

### Post by argail1980 on 2009-01-21
Hi,

great tutorial, thanx a lot. 

Did anyone have problems with powerpoint? I cannot open existing presentations without crashing powerpoint (that's what I installed this bloody M$-Office for in the first place) 
I could however save and reopen a basic presentation I made with that installation of PPT. I also could open the crashing presentation with OOo and save it again as *.ppt. Then it would open, but most of the formulas were gone (only funny characters left).

---

### Post by Surfer07 on 2009-01-31
Very nice howto.
In ubuntu 8.10 it works fine here. Only Outlook doesn't work, but that no problem because i only need word and powerpoint.

Tnx :D

---

### Post by ooboyle on 2009-02-01
Hi,

I'm on 8.10 x86 with a clean install of Wine 1.1.14. I've followed the OP with and tried any hints from other posters, but I can't even get it to install. It hangs at about 65-70% and the terminal window gives me these errors:

wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcFreePipeBuffer, aborting
wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcGetBufferWithObject, aborting

Any ideas? What am I missing here?

Oliver

---

### Post by supersrbin2000 on 2009-02-04
> **ooboyle said:**
> Hi,

I'm on 8.10 x86 with a clean install of Wine 1.1.14. I've followed the OP with and tried any hints from other posters, but I can't even get it to install. It hangs at about 65-70% and the terminal window gives me these errors:

wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcFreePipeBuffer, aborting
wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcGetBufferWithObject, aborting

Any ideas? What am I missing here?

Oliver

same problem, but @ x64...i'm running out of ideas and help would be highly appreciated :)

---

### Post by NightMKoder on 2009-02-04
I actually don't know about this tutorial, but on wine 1.1.14 the initial setup works without any changes (although it hangs a little when verifying the serial number). This is on wine 1.1.14 (probably 1.1.12 when I just installed it) and Kubuntu Intrepid x86 .

The only thing that didn't work for me (and I really needed) were equations in Word, but I found a fix for it and posted it: [http://ubuntuforums.org/showthread.php?p=6673381](http://ubuntuforums.org/showthread.php?p=6673381) .

---

### Post by ooboyle on 2009-02-06
@NightMKoder

When testing this, I installed on 1.1.12, .13, and .14. I got different results with each sub version. I did not use Kubuntu.

There's some minor change between sub versions that causes this to break, and it's specific to 8.10.

I've successfully installed 2007 using CrossoverLinux, but even then I had to mess around with things. 

On Crossover, I had to install Explorer 6 in it's default bottle (win98). I then then installed 2007 up until the actual 2007 installer,at which point I canceled the 2007 install and installed dotnet 1.1. I then resumed the 2007 install. After the 2007 install, all apps threw errors every time they opened. I then installed dotnet 2.0 which failed. However, after that, Word, Excel, Powerpoint, Publisher, OneNote, and Outlook worked. However... again... Outlook to Exchange via RPC/HTTP didn't work, I also got an error the first time I opened any one of these apps, but only on the first time running any of these apps.

Oliver

---

### Post by Denis Clijsters on 2009-02-06
Does someone knows how to open MS excel/word documents directly instead of opening first ms office and then open -> etc..

always when I open a document with ms office I get an empty page.

I tried making a executable link with folowing code

```
#!/bin/sh
env WINEPREFIX="/home/dclijste/.wine" wine "C:\Programma Bestanden\Microsoft Office\Office12\WINWORD.EXE" "$@
```"

I remember it was working a year ago (last time I used office, on previeous computer) with crossover so I looked into my backups where I discovered the $@ but that didn't do the trick..

---

### Post by Denis Clijsters on 2009-02-06
Mission accomplished!

create following files and make them executable:

```
excel
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\EXCEL.EXE" "`winepath -w "$@"`"

onenote
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\ONENOTE.EXE" "`winepath -w "$@"`"

powerpoint
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\POWERPNT.EXE" "`winepath -w "$@"`"

pptviewer
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\PPTVIEW.EXE" "`winepath -w "$@"`"

publisher
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\MSPUB.EXE" "`winepath -w "$@"`"

winword
#!/bin/bash
wine "C:\Program Files\Microsoft Office\Office12\WINWORD.EXE" "`winepath -w "$@"`"
```

---

### Post by chambersc on 2009-02-08
> **ooboyle said:**
> Hi,

I'm on 8.10 x86 with a clean install of Wine 1.1.14. I've followed the OP with and tried any hints from other posters, but I can't even get it to install. It hangs at about 65-70% and the terminal window gives me these errors:

wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcFreePipeBuffer, aborting
wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcGetBufferWithObject, aborting

Any ideas? What am I missing here?

Oliver
This is my problem exactly.

I did steps 1-7 exactly. I downloaded the enterprise.exe from Microsoft website. I did 'wine enterprise.exe' and it'll load through the serial screen and freeze while installing. In the terminal window, it will give me the same error message.

I tried to replace my rpcrt4.dll.bak to the rpcrt4.dll and it wouldn't even open up wine. So, any help?

---

### Post by NightMKoder on 2009-02-09
> **ooboyle said:**
> @NightMKoder

When testing this, I installed on 1.1.12, .13, and .14. I got different results with each sub version. I did not use Kubuntu.

There's some minor change between sub versions that causes this to break, and it's specific to 8.10.

I've successfully installed 2007 using CrossoverLinux, but even then I had to mess around with things. 

On Crossover, I had to install Explorer 6 in it's default bottle (win98). I then then installed 2007 up until the actual 2007 installer,at which point I canceled the 2007 install and installed dotnet 1.1. I then resumed the 2007 install. After the 2007 install, all apps threw errors every time they opened. I then installed dotnet 2.0 which failed. However, after that, Word, Excel, Powerpoint, Publisher, OneNote, and Outlook worked. However... again... Outlook to Exchange via RPC/HTTP didn't work, I also got an error the first time I opened any one of these apps, but only on the first time running any of these apps.

Oliver

I don't think me running Kubuntu makes a difference - I'm pretty sure wine is toolkit independent. The only thing that might matter is x86 or not. Also as a note I have Office Enterprise, but the wine appdb says the student edition also works. You may also want to check if you have office sp1 pre-built into your cd - it does not work (either slipstreamed or installed).

Office 2007 was the first thing that I installed on wine. I followed the instructions from wine's appdb [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992) (scroll down to how to install). I did not use winetricks or any DLL overrides for the installation. I actually think the installation won't work with rpcrt4.dll set to native. (For those that don't know: this means removing the entry in the wine config - not just deleting the file).

Also, the official instructions for getting the latest wine are at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) (scroll to the bottom for the console commands).

---

### Post by djsephiroth on 2009-02-12
> **ooboyle said:**
> Hi,

I'm on 8.10 x86 with a clean install of Wine 1.1.14. I've followed the OP with and tried any hints from other posters, but I can't even get it to install. It hangs at about 65-70% and the terminal window gives me these errors:

wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcFreePipeBuffer, aborting
wine: Call from 0x7b8458a0 to unimplemented function rpcrt4.dll.I_RpcGetBufferWithObject, aborting

Any ideas? What am I missing here?

Oliver
Same release version and arch, same problem here. Using the student edition of Office 2007 Professional.

Figured it out. First, change step #1: just install 1.1.4 using Synaptic. Skip step #5 completely, except for setting the emulation version to "Vista". Skip step #6 completely: with 1.1.4, there's no need to replace the rpcrt4.dll file. Also, you need "gdiplus" and "allfonts" installed via Winetricks:

sh winetricks gdiplus allfonts

Skip step #9 completely.

So far everything is working perfectly. Using Office 2007 student edition with 8.10 x86, Wine 1.1.4, and winetricks.

---

### Post by Molenman on 2009-02-18
The last couple of days I have been trying to get Office 2007 Student, installed on my HP 8530w elitebook, with Ubuntu 8.10. (since open office 3, consumes over 90% of my cpus)

Firstly I have followed the steps mentioned by the TS, this however did not work out. This returned the following error (wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found), since google did not find useful results on this error. I decided to follow NightMkoder suggestion, and tried to install office07 on an unmodified WINE.
So i removed wine completely and reinstalled. Still no luck, so i removed it again, when i typed:  locate wine in the console a lot of entries where found.. so i tried to uninstall wine by following the steps described in ([http://ubuntuforums.org/showthread.php?t=265480](http://ubuntuforums.org/showthread.php?t=265480)). 

After reinstalling wine 1.1.14, more errors were produced:
wine: created the configuration directory '/home/arno/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf94
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x33c960 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cd12898, overlapped 0x7cd128a0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x33ca50 (nil)
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/arno/.wine' has been updated.
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found


-----------
I am only using Ubuntu for two weeks now, i really hope you guys can help me.


Ps. after the latest reinstall of wine, wine didn't show up in my applications menu. However running winecfg from the console works fine.

---

### Post by BDNiner on 2009-02-18
I will definitely give this a try when i get home. Hopefully it works.

---

### Post by NightMKoder on 2009-02-20
> **Molenman said:**
> The last couple of days I have been trying to get Office 2007 Student, installed on my HP 8530w elitebook, with Ubuntu 8.10. (since open office 3, consumes over 90% of my cpus)

Firstly I have followed the steps mentioned by the TS, this however did not work out. This returned the following error (wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found), since google did not find useful results on this error. I decided to follow NightMkoder suggestion, and tried to install office07 on an unmodified WINE.
So i removed wine completely and reinstalled. Still no luck, so i removed it again, when i typed:  locate wine in the console a lot of entries where found.. so i tried to uninstall wine by following the steps described in ([http://ubuntuforums.org/showthread.php?t=265480](http://ubuntuforums.org/showthread.php?t=265480)). 

After reinstalling wine 1.1.14, more errors were produced:
wine: created the configuration directory '/home/arno/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf94
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x33c960 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cd12898, overlapped 0x7cd128a0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x33ca50 (nil)
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1d4158]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/arno/.wine' has been updated.
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found


-----------
I am only using Ubuntu for two weeks now, i really hope you guys can help me.


Ps. after the latest reinstall of wine, wine didn't show up in my applications menu. However running winecfg from the console works fine.

Most of that stuff is wine starting for the first time. If you look on the last line: `wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found`, it simply couldn't find the file you were trying to start.

My guess is you typed "wine setup.exe" in your terminal. That won't work unless you're in the same directory as the setup.exe file; ie in the cdrom folder. Also - I'm not sure, but it may be case sensitive (run "wine Setup.exe" if the file is called Setup.exe). The easy solution would be to just open up the CD as you would normally in your file browser and double-click Setup.exe . Otherwise you need to type "cd /media/cdrom0" before running "wine setup.exe"

---

### Post by Molenman on 2009-02-23
Thanks for your quick reply, I did indeed run the installer from the console, however I had navigated in to the right folder, only mounting a windows-based ISO image on ubuntu didn't work ( ;1 was added to each file name) so I burned the image and then everything worked perfectly!

---

### Post by swagner on 2009-02-27
I just wanted to say that these were great directions!  Thank you for helping me potentially be rid of Windows once and for all!

---

### Post by zorgh on 2009-03-04
Thx great tuto.

I have a problem with Powerpoint :

```

wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\POWERPNT.EXE"
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0

```

How to fix it ?

Thx so much.

---

### Post by NightMKoder on 2009-03-04
> **zorgh said:**
> Thx great tuto.

I have a problem with Powerpoint :

```

wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\POWERPNT.EXE"
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0

```

How to fix it ?

Thx so much.

That's not really an error, those are fairly benevolent fixme's.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813)

Did you set riched20 to native?

If you did follow that howto, I'm assuming you installed riched20 from winetricks. I don't know whether that works but debugging with winetricks is nearly impossible. At least more of a log would be nice (if there is nothing else, can't help you).

YOU SHOULDN'T NEED THIS TUTORIAL TO INSTALL OFFICE 2007 (on latest beta wine, intrepid)!
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

---

### Post by zorgh on 2009-03-05
Thx for your answer but it don't work.
I have set riched20 to native.
Sorry for my english language. I'm french.
I followed this howto (I had to do step 10 before step 9):

[http://ubuntuforums.org/showthread.php?t=844309](http://ubuntuforums.org/showthread.php?t=844309)

or this :

[http://forum.ubuntu-fr.org/viewtopic.php?pid=2472154](http://forum.ubuntu-fr.org/viewtopic.php?pid=2472154)

Same result.

Wine : 1.0.0
Ubuntu : Hardy

---

### Post by NightMKoder on 2009-03-05
Wine 1.0.0 is old and will probably not work. Download Wine 1.1.16
[http://winehq.org/download/deb](http://winehq.org/download/deb)

---

### Post by zorgh on 2009-03-05
With the last version (1.1.16), the install don't progress.

[IMG]http://cjoint.com/data/dhuvuMEBfX_screencap.jpg[/IMG]

I get this message :

```

wine: Call from 0x7b8447e0 to unimplemented function rpcrt4.dll.I_RpcGetBufferWithObject, aborting

```

"rpcrt4.dll" come frome here: [http://www.mediafire.com/?njtut9aswdk](http://www.mediafire.com/?njtut9aswdk)

---

### Post by zorgh on 2009-03-05
I used another file "rpcrt4.dll".

Now, I get this message starting POWERPOINT :

```

fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!

```

---

### Post by NightMKoder on 2009-03-05
When installing Office 2007, you need to remove any native dlls you may have installed. It installs out of the box - ie, don't use any native rpcrt4.dll.

If you still get errors after removing it from the overrides list, I suggest deleting your .wine directory and try installing from there.

Check Wine's Appdb: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992) and [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813)

---

### Post by zorgh on 2009-03-05
Thx so much for your help.

Before installing Office 2007, I use these commands :

```

aptitude remove --purge wine
rm -fR /home/user/.wine
rm -fR /home/user/.local/share/applications/wine/Programmes/*
rm -fR /home/user/.winetrickscache
rm -fR /home/user/.windows-label
rm -fR /usr/lib/wine
apt-get install wine

```

The folder .wine is always deleted before a fresh installation.

Then, I followed this howto (I had to do step 10 before step 9):

[http://ubuntuforums.org/showthread.php?t=844309](http://ubuntuforums.org/showthread.php?t=844309)

Where is my error ?

Maybe I don't have to install riched20 with wintricks ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)).

When you say :"*you need to remove any native dlls you may have installed. It installs out of the box - ie, don't use any native rpcrt4.dll*" ---> It corresponds to step 6 (howto) / remove or move is similar.

---

### Post by NightMKoder on 2009-03-05
> 
YOU SHOULDN'T NEED THIS TUTORIAL TO INSTALL OFFICE 2007 (on latest beta wine, intrepid)!


I.e. Don't follow this HOWTO! Just install office by launching setup.exe . After installation set riched20 and usp10 to native and that's it.

---

### Post by zorgh on 2009-03-05
> **NightMKoder said:**
> I.e. Don't follow this HOWTO! Just install office by launching setup.exe . After installation set riched20 and usp10 to native and that's it.

Ok, Office 2007 comes with its own version of riched20. I did not follow a Howto. In current (1.1.16) Wine, I simply installed Office 2007. After installation, I just set riched20.dll to (native) in winecfg.

[IMG]http://cjoint.com/data/dhxpgjlW5p_screencap.jpg[/IMG]

Nevertheless I got the same message in starting POWERPOINT :

```

fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!

```

Do I have to compile the 1.1.3 version wine ? Many persons succeeded without needing to make it. I begin to lose hope to be able to one day install Office 2007.

---

### Post by NightMKoder on 2009-03-05
Since you have a clean wine install, it should be working. Make sure that the windows version is set to xp. With vista it hangs at the open screen for me.

---

### Post by zorgh on 2009-03-06
Thx NightMKoder but it hangs at the open screen.
I'm disappointed. There are many howto but each is different.
I read "It works for me" _but not for me_. I resign not to use Office 2007.

---

### Post by halovivek on 2009-03-06
Hi 
i have installed in ubuntu 8.10 and it is doing great.

---

### Post by zorgh on 2009-03-06
> **halovivek said:**
> hi 
i have installed in ubuntu 8.10 and it is doing great.

+1

---

### Post by zorgh on 2009-03-08
Hi,

So that it works, I have to start twice the application from Gnome menu.

Starting in command line, no problem to start the application.

An idea to fix it ?

Thx so much

*(Ubuntu 8.10 Intrepid Ibex 64 bits)*

---

### Post by amylase on 2009-03-09
Hi everyone

I installed Office Enterprise 2007 using CodeWeaver 7.1.0 (CrossOver Linux) which to me is just a little tool that sets up WINE correctly for me to run certain Microsoft products. So far I've used Word and OneNote in Ubuntu without major problems. If anyone wants any configuration files or see how which file is set up, just let me know what file you want and I can post it up here. Hope this makes things easier for some.

---

### Post by NightMKoder on 2009-03-09
> **zorgh said:**
> Hi,

So that it works, I have to start twice the application from Gnome menu.

Starting in command line, no problem to start the application.

An idea to fix it ?

Thx so much

*(Ubuntu 8.10 Intrepid Ibex 64 bits)*

I don't know about you, but I know it takes a while to start the first time (wine starts wineserver, which apparently takes a while). Considering you're on 64 bit, the initialization will take longer (wine has to load 32-bit versions of libraries), so the first time you start it, it will take a while.

If it's REALLY not starting, then try copying the command line for the shortcut and see what the console output is.

---

### Post by zorgh on 2009-03-11
NightMKoder, thank you very much for these explanations and this precision.

---

### Post by tydell on 2009-03-13
Do you have Access 2007 working ? 
I ask because I installed Office 2007 Enterprise, everything works except Access, it's problem with msvcpr80.dll, but other Office 2007 apps need this dll for work too and they run, Access 2007 won't

---

### Post by jburman01 on 2009-03-14
Im followed all of the directions in order and installed office 2007 but I dont see it under applications/wine/programs. Am I looking in the wrong place for the office executables? Do they need to be added manually to the applications tab?

---

### Post by NightMKoder on 2009-03-14
> **tydell said:**
> Do you have Access 2007 working ? 
I ask because I installed Office 2007 Enterprise, everything works except Access, it's problem with msvcpr80.dll, but other Office 2007 apps need this dll for work too and they run, Access 2007 won't

The appdb entry for office 2007 (installer) says to install MS  Visual C++ 2005 Libraries. I'm guessing that `winetricks vcrun2005` will do it. But I'm not sure about stability - never tried (and the appdb is missing the entry for access 2007?)

> **jburman01 said:**
> Im followed all of the directions in order and installed office 2007 but I dont see it under applications/wine/programs. Am I looking in the wrong place for the office executables? Do they need to be added manually to the applications tab?

Which directions? (this howto is outdated) And try restarting, they should appear there automatically.

---

### Post by mattfry on 2009-03-17
I'm trying to install MS Office Home and Student 2007 onto Ubuntu 8.10 with Wine 1.1.17. I followed [these instructions ]("http://http://ubuntuforums.org/showthread.php?t=844309&") I get all the way to the install progress bar, but then it freezes. The last couple of lines in the terminal are as follows. 

```
wine: Call from 0x7b844430 to unimplemented function rpcrt4.dll.I_RpcFreePipeBuffer, aborting
wine: Call from 0x7b844430 to unimplemented function rpcrt4.dll.I_RpcGetBufferWithObject, aborting

```

Any help would be greatly appreciated. Thanks.

---

### Post by illmatic on 2009-03-17
> **mattfry said:**
> I'm trying to install MS Office Home and Student 2007 onto Ubuntu 8.10 with Wine 1.1.17. I followed [these instructions ]("http://http://ubuntuforums.org/showthread.php?t=844309&") I get all the way to the install progress bar, but then it freezes. The last couple of lines in the terminal are as follows. 

```
wine: Call from 0x7b844430 to unimplemented function rpcrt4.dll.I_RpcFreePipeBuffer, aborting
wine: Call from 0x7b844430 to unimplemented function rpcrt4.dll.I_RpcGetBufferWithObject, aborting

```

Any help would be greatly appreciated. Thanks.
actually you don't have to install anything in addition.
Just run the office 07 installation out of box (you can't install some Programs e.g. acess (i don't know them by heart)).
If you'hve installed office you just need to go into winecfg
-> library tab 
get riched20 from the list and set it to "native"
after do the same with
usp10 but set it to "native,builtin"
And that's how it works for me @ wine 1.17

you can also find some help here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

---

### Post by mattfry on 2009-03-18
Thanks so for the help! Sadly, it's still not working. [Appdb.winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992") is saying that 1.1.17 won't install MSOffice. If you got it to work, I'm impressed. I did a fresh install of wine and followed your instructions and it got further than I have before, but when the install progress bar in the Office installer gets to about 2/3, the window just disappears. Winehq says that 1.1.14 works so I'm going to try to install that version, but I don't know how. It seems all they have is 1.0.1 or 1.1.17, which is the most recent. I could download the source code and try to compile it myself, but I don't have or know where to get the proper .dlls. 

Plus I don't really know what I'm doing in Linux at all, so that doesn't help.

I'm gonna start a new thread about installing older versions of wine, esp since people seem to be having problems with the current one.

---

### Post by amylase on 2009-03-18
Thanks a lot for the steps. I can see some people found it to work some not. Can somebody make a script or something to simplify things? A script that I can just double click and sets up everything right, ready to go for Office 2007 in WINE. That'll be fabulous.

---

### Post by illmatic on 2009-03-18
I installed it with wine 1.16 and have it working now with 1.17
And 1.17 is also the newest wine release ( as far as I'm conserned).

EDIT

:) I just read here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)
"A regression in 1.1.17 breaks the Office 2003 & 2007 installers.Install in an earlier version*."

I guess the installatoin just doenst work with 1.1.17
Just try any version later than 1.1.3 and earlier than 1.1.17
and it'll work.

And after you installed office you can just upgrade wine because once installed office works even with 1.1.17 (I'm at 1.1.17 too)

If 1.1.16 doesnt work, too
Try to install only the following packets
powerpoint
word
excel
One Note
Outlook
Publisher
Picture manager

That should work i think :)
Just give it a try

---

### Post by kiprit on 2009-04-19
Thanks for the great tutorial... 

I used this among others and failed several times. Finally I understood where I went wrong and basically sticking to the info provided here I managed to install Office 2007 on intrepid.

Basically I will not recommend to follow step 1:
Instead of getting the latest wine, download Wine 1.1.10 from [here]("http://wine.budgetdedicated.com/archive/index.html"). I tried with several versions. And finally this is the one that worked the best. In different trials I managed to install the office but powerpoint was constantly crashing. Or in other trials I came until step4 and something went wrong in the midway.
But I can confirm that the instructions work perfectly with wine 1.1.10

Another point is on step 9:
> Step 9. Revert to original dll file.
    In ~/.wine/windows/system32, rename "rpcrt4.dll" to "rpcrt4.dll_dl"
    In ~/.wine/windows/system32, rename "rpcrt4.dll_bak" to "rpcrt4.dll"
When I did this, winecfg  and wine kept crashing. So in my case step 10 had to come before step 9.
Meaning I ran winecfg before reverting to original rpcrt4.dll, changed libraries option and windows version. 

Now everything seems to be running perfectly...

thanks again!

---

### Post by NightMKoder on 2009-04-19
This tutorial is really, really outdated. Installing office is relatively painless under wine now - just downgrade to 1.1.16, install it, upgrade to latest. If you get errors it is because you probably don't have a clean wine prefix.

[http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

---

### Post by kiprit on 2009-04-20
In my case wine 1.1.16 did install correctly, but powerpoint was keeping on crashing. (and PP is the reason I had to have MS office. In my job i have to use it and some of the stuff i do with impress won't display properly with pp).

And this is the funniest: when I use the repository, whether i make a clean installation or an upgrade, wine congiguration tool is not allowing me to choose windows version to mimic!

OK I just read your thread...and saw the powerpoint fix... I don't know how I did not find it, I've been reading whatever I can for about one week!

---

### Post by Salamancero on 2009-04-26
Hi, I have Wine 1.1.9.  How do I get back to Wine 1.1 for so that i can use the tutorial properly? 

Thanks!

---

### Post by jhoeijao on 2009-05-30
> **lilkidz said:**
> I have the same problem as you = =; Using Enterprise too; always asking my to send a error report =/

I'm using Enterprise too but works well with this guide. [http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft](http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft)

---

### Post by jhoeijao on 2009-05-30
> **Salamancero said:**
> Hi, I have Wine 1.1.9.  How do I get back to Wine 1.1 for so that i can use the tutorial properly? 

Thanks!

You have to uninstall your wine using synaptic or use terminal try this guide [http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft](http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft)

---

### Post by jhoeijao on 2009-05-30
> **kiprit said:**
> In my case wine 1.1.16 did install correctly, but powerpoint was keeping on crashing. (and PP is the reason I had to have MS office. In my job i have to use it and some of the stuff i do with impress won't display properly with pp).

And this is the funniest: when I use the repository, whether i make a clean installation or an upgrade, wine congiguration tool is not allowing me to choose windows version to mimic!

OK I just read your thread...and saw the powerpoint fix... I don't know how I did not find it, I've been reading whatever I can for about one week!

My powerpoint works well with this guide [http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft](http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft)

---

