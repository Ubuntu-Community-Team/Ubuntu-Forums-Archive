---
title: "Command Line Problem: AOM"
date: 2011-09-02
forum: Wine
---

### Post by laagamer on 2011-09-02
Hey what's up fellas! Wondering if you could help me out with what I think is a command line problem while trying to run Age of Mythology on my laptop. I'm really new to Ubuntu but I'm trying to learn as best I can. I already had a couple of DLL file problems and a problem with the disk-check that I was able to solve but I seem to have hit a brick wall. :(  


I'm currently trying to run AOM on my laptop with "Ubuntu 9.10" through "Wine 1.3.15".

My "winecfg" is set to Windows XP, OSS Sound Driver, Hardware Acceleration = Emulation, Virtual Desktop (800x600), with a "pidgen (native,builtin)" overide in the library for the the PidGen.DLL and MFC42.DLL file replacements, as those files where originally missing and causing errors. I also got a NoCD-Crack version of AOM, so that I can run it without the disk and placed it in AOM's directory (NoCD-Crack file named "aom2.exe") to replace the original "aom.exe" game file. I already owned an original hard copy of AOM with a CD-key so I'm able to play it. When I placed the new "aom2.exe" game file in the AOM directory, I left the original "aom.exe" game file where it was, as I didn't think it would cause any conflicting problems.

I got the directions for winecfg and NoCD-Crack version off the Age of Mythology WineHQ Version 1.0 page:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2711](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2711)

Currently when I try to run AOM through the desktop icon's default command prompt I get an "Insert CD1" popup. The default command for the icon is:

> env WINEPREFIX="/home/nick/.wine" wine C:\\windows\\command\\start.exe /Unix /home/nick/.wine/dosdevices/c:/users/Public/Desktop/Age\ of\ Mythology.lnk

My next attempt was to try and run the game through the terminal. I cd to the correct directory ("cd AOMD1/aom") and run the game using "wine aom2.exe", to which I get a frozen splash screen and crash which forces me to terminate the process and comes up with these errors (I get the exact same errors when trying to run the original "aom.exe" file with the disk in as well):


> nick@nick-laptop:~/AOMD1/aom$ fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB: (0x134fe8 )
fixme:msctf:LangBarMgr_ShowFloating STUB: (0x134fe8 )
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x2004a, 0x133c70): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x133c70): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec58,0x00000000), stub!


The directions from the previously mentioned WineHQ page say the crash happens because movieplayer.exe cannot find the play list. If I understand correctly, that means that the intro video is causing the crash. WineHQ's solution to this problem is to skip the intro video entirely by changing the desktop icons command line prompt and adding a "+noIntroCinematics" command to it, which they have an example of how to do on their page and is the 1st command line. Changing what I think is the appropriate information (username, directory names, drives, ect.) I came up with the bottom command line:

Their Example:
> env WINEPREFIX="/home/myusername/.wine" wine "C:\Programme\Microsoft Games\Age of Mythology\aom.exe" xres=1024 +noSound +noIntroCinematics bpp=16 +window +lowend +terrainHalfDensity +lowPoly -waterbump skipMipMapLevels=1 graphicDetail=2

My Version:
> env WINEPREFIX="/home/nick/.wine" wine C:\\windows\\command\\start.exe /Unix /home/nick/.wine/dosdevices/f:/users/Public/Desktop/Age\ of\ Mythology.lnk +noIntroCinematics

I added a drive in winecfg lettered "F" with the command line "/home/AOMD1/aom/aom2.exe" so that Wine would know to start up the NoCD-Crack version of AOM through the desktop icon, which is why I replaced "c:" with "f:" for the drive letter in my version of the command prompt. They also said the only command you actually needed was the "+noIntroCinematics" which is why I left the rest out. 

When I click on the desktop icon I get Wine's virtual desktop screen which then proceeds to crash without the splash screen ever even appearing. When I run my command through the terminal I get the same virtual desktop screen crash, along with these errors:

> fixme:exec:SHELL_execute flags ignored: 0x00000100
err:exec:shellex_load_object_and_run failed to get data object

So unsurprisingly my command line prompt is right enough to run, but wrong enough to crash without even loading the game. I'm trying my best to learn about this kind of stuff but so far I'm not having any luck. I've given you guy's all the relevant information I can think of (probably to much :???:  ) and if any of you are still reading at this point, whatever help or advice you can give would be greatly appreciated.

I'll continue to work on and change up that command line to see if I can fix it and if I get any results I'll be sure to post an update, as it might help someone else in the future.

Thanks! ;)

---

### Post by laagamer on 2011-09-04
Hey anyone? :confused:

---

### Post by cwwilson721 on 2011-09-04
> **laagamer said:**
> ... [COLOR="Red"]I also got a NoCD-Crack version of AOM, so that I can run it without the disk[/COLOR] ...
Sorry. We are NOT going to help.

Cracked is not allowed on these forums.

Read the stickies.

---

### Post by kyletstrand on 2011-09-04
It also would be suggested to upgrade to 10.04.  It's the most recent LTS OS.  9.10 is no longer supported.

---

