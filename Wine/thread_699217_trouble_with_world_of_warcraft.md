---
title: "trouble with world of warcraft"
date: 2008-02-17
forum: Wine
---

### Post by devin0 on 2008-02-17
Hello, i followed this toutorial to try to install world of warcraft on my machine.[http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraftwh](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraftwh)
[http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft)

everything seemed to be going ok, but when it comes time to play wow, the two intro movies play,then wow exits. i couldn't find anything on how to fix this problem, could someone please tell me how to fi this problem?

---

### Post by Sandlst on 2008-02-17
Hello, could you try running wow from a terminal and see if an error message pops up?  If one pops up, please post it here.  Also, what video card are you using?

---

### Post by devin0 on 2008-02-17
ok, I type in wine "C:\Program Files\World of Warcraft\Launcher.exe"
 the launcher starts, i click play. the intro movie plays,then exits. this is what the terminal says:

llyokoboy0@lyokobox:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw:WebBrowser_QueryInterface (0x12eb08)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x33e780) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x12eb08)->(0x33e74c)
fixme:shdocvw:OleControl_FreezeEvents (0x12eb08)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x12eb08)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x130420): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130828): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130828): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d2969f8, overlapped 0x7d2969dc): stub
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12eb9c)->((null) 1 0x33ded4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 25 2 0x33dee8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 26 2 0x33dee8 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12eb9c)->(0x33df24)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33dfe0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x144d58)->(L"" L"" 0 0x33e014)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x144d58)->(0x33e018 0x33e028)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 29 2 0x33ecc0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12eb9c)
fixme:shdocvw:ClientSite_GetContainer (0x12eb9c)->(0x33ece0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12eb9c)->(0xb7e27109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 25 2 0x33ec14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 26 2 0x33ec14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 28 2 0x33ec6c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 26 2 0x33eca0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 29 2 0x33ecb0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12eb9c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12eb9c)->(0x7bc9e5b1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12eb08)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x145268)->((nil))
fixme:shdocvw:OleObject_Close (0x12eb08)->(1)
fixme:shell:DllCanUnloadNow stub
lyokoboy0@lyokobox:~$ fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d550000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d550000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f724,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x12cdc8) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x130da8) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x34f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:state_psizemin WINED3DRS_POINTSIZE_MIN not supported on this opengl, value is 0.000000
fixme:d3d:state_psizemax WINED3DRS_POINTSIZE_MAX not supported on this opengl, value is 1.000000

lyokoboy0@lyokobox:~$ 


You asked for what my video card is, i dont know and dont know how to find out....

---

### Post by dtgolder on 2008-02-17
Same thing here...have loaded WOW following the tutorials...after playing the intro movie, it cuts out and drops me to the desktop.

Same thing whether I run launcher.exe or wow.exe

Any ideas?

(Dell B120 laptop, Gutsy)

---

### Post by Sandlst on 2008-02-17
Ok, all the messages preceded by "fixme" are messages intended for developers, so they aren't really relavent; I would say the problem is with these lines: > **devin0 said:**
>  err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
A quick search on google, ubuntuforums, and winehq doesn't show any helpful information for this specific error message, but I did notice on winehq's app database some users had the same problem with the intro video, and fixed it by unchecking "allow pixel shader if hardware allows" in winecfg, so maybe you could try that.

Also, are you running the latest version of wine?  If not, or you're not sure, follow the guide here: [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")
> **devin0 said:**
> 
You asked for what my video card is, i dont know and dont know how to find out....
Ah, I just meant a general vendor, i.e. Nvidia, Ati, Intel, etc.

One last thing, you can run the command ```
WINEDEBUG=fixme-all wine "C:\Program Files\World of Warcraft\Launcher.exe"
```if you want to avoid printing out the "fixme" messages, to make the actual error messages easier to read.

Good luck!

---

### Post by devin0 on 2008-02-18
I did everything you said, but just asbefore- the intro movie plays then returns me to the desktop.

---

### Post by devin0 on 2008-02-18
actually after the last movie i  ran don't get the movie anymore. i get a blank screen with an echoing sound. also there is now alot of stuff in my config.wtf file that wasn't there before.

---

### Post by rickggreen on 2008-02-18
I had WOW running under Wine 54, with the last update to 55 stopped working, how do I get 54 back?

---

### Post by Sandlst on 2008-02-18
> **devin0 said:**
> actually after the last movie i  ran don't get the movie anymore. i get a blank screen with an echoing sound. also there is now alot of stuff in my config.wtf file that wasn't there before.
Alright, try launching the game with this command: ```
WINEDEBUG=fixme-all wine "C:\Program Files\World of Warcraft\Launcher.exe" -d3d
```
This will try to start the game in direct 3d mode, which tends to be worse than opengl, but I've heard of a few cases where direct 3d is the only way for some graphics cards to run it.  By the way, could you list your graphics card?  You can look it up with this command: ```
cat /etc/X11/xorg.conf | grep Device

```The last device listed should be your graphics card, I think.  If you have an intel graphics card, wine may never be able to play wow.  If you have an ati graphics card, you might be able to get it working with some work.  With an Nvidia card, the chances wow will run easily are much higher.

> **rickggreen said:**
> I had WOW running under Wine 54, with the last update to 55 stopped working, how do I get 54 back?
Try looking here: [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

---

### Post by devin0 on 2008-02-19
ok, I typed in  WINEDEBUG=fixme-all wine "C:\Program Files\World of Warcraft\Launcher.exe" -d3d

the launcher opened and i clicked play. My screen turned black for about 1 minute, then i was returned to the desktop. this is what was in the terminal:

lyokoboy0@lyokobox:~$ WINEDEBUG=fixme-all wine "C:\Program Files\World of Warcraft\Launcher.exe" -d3d
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1


you also asked me to run  cat /etc/X11/xorg.conf | grep Device ,
this is what i got:
lyokoboy0@lyokobox:~$ cat /etc/X11/xorg.conf | grep Device
Section "InputDevice"
Section "InputDevice"
        Option          "Device"                "/dev/input/mice"
Section "InputDevice"
        Option          "Device"                "/dev/psaux"
Section "InputDevice"
        Option          "Device"        "/dev/input/wacom"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
Section "InputDevice"
        Option          "Device"        "/dev/input/wacom"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
Section "InputDevice"
        Option          "Device"        "/dev/input/wacom"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
Section "Device"
        Device          "ATI Technologies Inc Radeon Mobility U1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
lyokoboy0@lyokobox:~$

---

### Post by Sandlst on 2008-02-19
Having an ati card makes things more difficult, unfortunately.  The fact that the same error messages occurred under opengl and direct3d makes me think that the problem is with your graphics card drivers, so my next question is which drivers are you using?  If you don't know, try looking under 'System/Administration/Restricted Drivers' and see if the box is checked for the graphics driver.  I use an nvidia card myself, but I believe the driver you want to be using is known as the "fglrx" driver.

---

### Post by Sammi on 2008-02-19
Have you tried looking over the community WoW/Wine howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ?

And especially it troubleshooting section?

---

### Post by devin0 on 2008-02-20
I went to system/administration/restricted drivers manager. When i click on restricted drivers manager i get a message saying
"Your hardware does not need any restricted drivers."

Is this a problem?

---

### Post by Zypher on 2008-02-21
SET movie "0"
SET expansionMovie "0"

in Config.wtf plz.

and run in OpenGL

---

### Post by Sammi on 2008-02-21
> **devin0 said:**
> I went to system/administration/restricted drivers manager. When i click on restricted drivers manager i get a message saying
"Your hardware does not need any restricted drivers."

Is this a problem?It should be right if you have a Intel graphics card.

Only Nvidia and ATI require restricted drivers for advanced 3D.

---

### Post by Sandlst on 2008-02-21
> **Sammi said:**
> It should be right if you have a Intel graphics card.

Only Nvidia and ATI require restricted drivers for advanced 3D.
I think he has an ati card, since I asked him in the first page to do a ```
cat /etc/X11/xorg.conf | grep Device
```and a device showed up as 
> **devin0 said:**
> 
Section "Device"
        Device          "ATI Technologies Inc Radeon Mobility U1"

I've done some digging on that specific card, and it appears the fglrx drivers do not support it, but some people have had success getting direct rendering with the open-source radeon driver.

devin0, could you run this command for us please: ```
glxinfo | grep direct
```and post the result?

---

### Post by devin0 on 2008-02-21
ok, i ran that code in terminal and this is what i got:

lyokoboy0@lyokobox:~$ glxinfo | grep direct
direct rendering: Yes
lyokoboy0@lyokobox:~$

---

### Post by Sammi on 2008-02-21
> **Sandlst said:**
> I think he has an ati card...Sry, I only skimmed the tread very quickly ;)

---

### Post by Sandlst on 2008-02-24
The fact that you have direct rendering is good; you've done everything right, that guide is solid,  but since it still is not working I'm going to have to assume your graphics card just does not work well with wine.  

I would test it out on other graphics-intensive windows games known to work with wine if you have any (demos would be fine too), and also to try native linux games that require 3d-acceleration (like planet penguin racer) to test out your graphics card.  Depending on the results, dual-booting might be your only chance at playing wow.  I tried searching for people using your specific card on linux, and haven't managed to find any information.  

Hopefully someone more knowledgeable than me can help you, I've tried everything I can think of, good luck!

You might also want to try the irc ubuntu channels, if you haven't already.
> Server:
irc.freenode.org
Channel:
#ubuntuforums

---

### Post by kindofabuzz on 2008-02-25
my Wow is working perfectly now thanks to the newest wine version.  0.9.56.  no more opengl!

---

### Post by Sammi on 2008-02-26
Even if you set WoW to use DirectX you're still using OpenGL, because Wine translates all the DirectX calls that WoW makes into OpenGL :D

---

