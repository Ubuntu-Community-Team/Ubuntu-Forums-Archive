---
title: "[SOLVED] Wine Gecko Installer"
date: 2007-12-07
forum: Wine
---

### Post by BattleGnome on 2007-12-07
Hi,

Whenever I send the command;

> "c:\program files\world of warcraft\launcher.exe"

I always get a popup with 'Wine Gecko Installer' in the title bar asking me to install the gecko engine. So I click install and eventually the launcher app for Wow will appear. If I try to start the launcher through Wine again I keep getting asked to install Wine Gecko again? 

Is there someway that I can install Wine Gecko for good without being prompted all the time?

---

### Post by cogadh on 2007-12-07
Once installed, it should never ask you to install it again. The normal way to install is to just run "wine iexplore http://www.winehq.org" in the terminal and then follow the prompts.

---

### Post by BattleGnome on 2007-12-07
Hi,

I done that and once its finished downloading a big white window pops up with the title 'Wine Internet Explorer' In the middle it just says HTML Rending is currently disabled.

I then tried running the launcher again, and I was prompted to install gecko again?

This is what the console is filled with, I don't understand why it  can't find mozilla?

> ash@ash-desktop:~$ wine iexplore [http://www.winehq.org](http://www.winehq.org)
fixme:shdocvw:IEWinMain "http://www.winehq.org" 1
fixme:ole:CoResumeClassObjects stub
err:mshtml:check_version Could not open VERSION file
err:ole:CoGetClassObject apartment not initialised
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7d3662b7, 0x7d3662b0): stub
fixme:urlmon:ObtainUserAgentString (0, 0x12b348, 0x7d3662b0): stub
fixme:wininet:InternetLockRequestFile STUB
err:mshtml:check_version Could not open VERSION file
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x126204)->((null) 1 0x33fa9c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->((null) 25 2 0x33fab0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->((null) 26 2 0x33fab0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x126204)->(0x33faec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33fba8 (nil))
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x128ac0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x128540)
fixme:mshtml:InternetBindInfo_GetBindString (0x128ac0)->(10 0x33e4c8 1 0x33e4dc)
fixme:urlmon:ObtainUserAgentString (0, 0x33e4e7, 0x33e4e0): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1283f0, 0x33e4e0): stub
fixme:mshtml:BSCServiceProvider_QueryService (0x128ac0)->({79eac9d2-baf9-11ce-8c82-00aa004ba90b} {79eac9d2-baf9-11ce-8c82-00aa004ba90b} 0x127b88)
fixme:mshtml:BSCServiceProvider_QueryService (0x128ac0)->({4f9f9fcb-e0f4-48eb-b7ab-fa2ea9365cb4} {4f9f9fcb-e0f4-48eb-b7ab-fa2ea9365cb4} 0x33e4d4)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x128ac0)->(0x33e4e8 0x33e4e0 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->((null) 29 2 0x33fcb0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x126204)
fixme:shdocvw:ClientSite_GetContainer (0x126204)->(0x33fb9c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x126204)->(0xb7e7f109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->((null) 25 2 0x33fad0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->((null) 26 2 0x33fad0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x126204)->((null) 28 2 0x33fb28 (nil))
fixme:mshtml:HttpNegotiate_OnResponse (0x128ac0)->(200 L"HTTP/1.1 200 OK\r\nDate: Fri, 07 Dec 2007 22:56:15 GMT\r\nServer: Apache/2.2.3 (Debian) PHP/5.2.0-8+etch7\r\nX-Powered-By: PHP/5.2.0-8+etch7\r\nExpires: Mon, 26 Jul 1997 05:00:00 GMT\r\nLast-Modified: Fri, 07 Dec 2007 22:56:15 GMT\r\nCache-Control: no-store, no-cache, must-revalidate\r\nCache-Control"... (null) 0x33fc18)

---

### Post by cogadh on 2007-12-07
It didn't install properly, so that is why it keeps trying to reinstall it. What should have happened is after the install the Wine website should have displayed.

You can manually install the engine:
[list=1]
[*]Open a terminal and manually download/extract the Gecko package by running the following:
NOTE - You will need to install the cabextract package from the repositories to do this
```
wget http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab && cabextract wine_gecko-0.1.0.cab
```
[*]Next, run the following to create the directories needed for Gecko:
```
mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Place the extracted Gecko files into the newly created directory:
```
mv wine_gecko ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Run regedit in the terminal. Go to HKEY_Current_User/Software/Wine/MSHTML and create a new key labeled &#8220;0.1.0&#8221;
[*]In the new &#8220;0.1.0&#8221; key, create a new string value labeled &#8220;GeckoPath&#8221; and set the string value to &#8220;c:\windows\gecko\0.1.0\wine_gecko&#8221;
[/list]
Gecko should be installed correctly now.

---

### Post by BattleGnome on 2007-12-07
Thanks, all working now

---

### Post by DesolationUSA on 2008-01-13
mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/

^ that didnt work for me.  it just starts a whole new line waiting for a new command.  Doesn't do or say anything.  Please note that I'm brand new to Linux of any kind.  I'm assuming I'm supposed to replace the "~" with my user name.  I did and still got nothing.

---

### Post by jennergruhle on 2008-02-28
> **DesolationUSA said:**
> mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/

^ that didnt work for me.  it just starts a whole new line waiting for a new command.  Doesn't do or say anything.  Please note that I'm brand new to Linux of any kind.  I'm assuming I'm supposed to replace the "~" with my user name.  I did and still got nothing.

~ is a placeholder for the user's home directory, so if your user name is johndoe your ~ is /home/johndoe.

If you are getting new lines with > in the beginning you probably used backslashes \ instead of slashes / for the path. Backslashes as path delimiters are only valid inside wine (in a cmd.exe or similar).

---

### Post by Deathbeholdsyou on 2008-04-25
> **cogadh said:**
> Once installed, it should never ask you to install it again. The normal way to install is to just run "wine iexplore http://www.winehq.org" in the terminal and then follow the prompts.


Thanks!

---

### Post by @xi0m on 2008-04-25
I've tried the above and gecko still will not work for me.

> $ wine iexplore [http://www.winehq.org](http://www.winehq.org)
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
fixme:ole:CoResumeClassObjects stub
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dd2da08, overlapped 0x7dd2d9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x101ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12d494)->((null) 1 0x32e69c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->((null) 25 2 0x32e6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->((null) 26 2 0x32e6b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12d494)->(0x32e6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e7b0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12e158)->(L"" L"" 0 0x32e7e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->((null) 29 2 0x32fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12d494)
fixme:shdocvw:ClientSite_GetContainer (0x12d494)->(0x32fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12d494)->(0xf7e217c9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->((null) 25 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->((null) 26 2 0x32fa60 (nil))
err:mshtml:before_async_open GetWineURL returned NULL
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12d494)->((null) 28 2 0x32fb18 (nil))
$ 

---

### Post by frootloop on 2008-05-01
HI, I get the same issue - followed the manual install instructions as posted above with no problems - afterwords, when I run wine iexplore [http://www.winehq.org](http://www.winehq.org) I get a blank wine window opening and the following in the terminal:

fixme:ole:CoResumeClassObjects stub
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8e4a08, overlapped 0x7d8e49ec): stub
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0xc3ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12ddbc)->((null) 1 0x32e69c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->((null) 25 2 0x32e6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->((null) 26 2 0x32e6b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12ddbc)->(0x32e6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e7b0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12ea80)->(L"" L"" 0 0x32e7e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->((null) 29 2 0x32fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12ddbc)
fixme:shdocvw:ClientSite_GetContainer (0x12ddbc)->(0x32fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12ddbc)->(0xf7e317c9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->((null) 25 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->((null) 26 2 0x32fa60 (nil))
err:mshtml:before_async_open GetWineURL returned NULL
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12ddbc)->((null) 28 2 0x32fb18 (nil))


Any ideas?

I'm running Hardy AMD64, wine 0.9.60 installed via apt get after adding the wine repository
Previously I did the sysctl fix for the reserve range errors

---

### Post by PoopyTheJ on 2008-05-27
I hate to jump in someone else's thread with my problem but I got gecko to install correctly, however when loading pirates I get a black window with a bunch of garbage, so obviously it's not rendering correctly. Any ideas?

---

### Post by cogadh on 2008-05-27
What is Pirates?

---

### Post by atowell on 2008-07-03
> **cogadh said:**
> It didn't install properly, so that is why it keeps trying to reinstall it. What should have happened is after the install the Wine website should have displayed.

You can manually install the engine:
[list=1]
[*]Open a terminal and manually download/extract the Gecko package by running the following:
NOTE - You will need to install the cabextract package from the repositories to do this
```
wget http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab && cabextract wine_gecko-0.1.0.cab
```
[*]Next, run the following to create the directories needed for Gecko:
```
mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Place the extracted Gecko files into the newly created directory:
```
mv wine_gecko ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Run regedit in the terminal. Go to HKEY_Current_User/Software/Wine/MSHTML and create a new key labeled “0.1.0”
[*]In the new “0.1.0” key, create a new string value labeled “GeckoPath” and set the string value to “c:\windows\gecko\0.1.0\wine_gecko”
[/list]
Gecko should be installed correctly now.

Thanks for posting this! I was getting the same problem. I went through the steps you posted, but the key and string were already created. After I looked at the regedit the html appeared in the WoW startup screen though, so something got fixed. Thanks again!

---

### Post by itchanddino on 2008-07-03
This worked for me.  It's a slightly modified version of what is on the Wine page for steam:

Download this [wine_gecko]("http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab") file to your /tmp directory

Make a file /tmp/file.reg, and in this file put:

[HKEY_CURRENT_USER\Software\Wine\MSHTML]
"GeckoUrl"="z:\\tmp\\wine_gecko-0.1.0.cab"

Now do 'regedit /tmp/file.reg'
After this, do 'wine iexplore [http://winehq.org](http://winehq.org)'

All done!

---

### Post by stwert on 2008-07-07
Thanks so much, got it working!

---

### Post by mickbuntu on 2009-01-14
Thank You you all rock but this post was the shortest and just as good!:)

> **itchanddino said:**
> This worked for me.  It's a slightly modified version of what is on the Wine page for steam:

Download this [wine_gecko]("http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab") file to your /tmp directory

Make a file /tmp/file.reg, and in this file put:

[HKEY_CURRENT_USER\Software\Wine\MSHTML]
"GeckoUrl"="z:\\tmp\\wine_gecko-0.1.0.cab"

Now do 'regedit /tmp/file.reg'
After this, do 'wine iexplore [http://winehq.org](http://winehq.org)'

All done!

---

### Post by cpxondo on 2010-02-03
Thanks a lot! It work just fine!

---

### Post by killer64 on 2010-03-07
> **cogadh said:**
> It didn't install properly, so that is why it keeps trying to reinstall it. What should have happened is after the install the Wine website should have displayed.

You can manually install the engine:
[list=1]
[*]Open a terminal and manually download/extract the Gecko package by running the following:
NOTE - You will need to install the cabextract package from the repositories to do this
```
wget http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab && cabextract wine_gecko-0.1.0.cab
```
[*]Next, run the following to create the directories needed for Gecko:
```
mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Place the extracted Gecko files into the newly created directory:
```
mv wine_gecko ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Run regedit in the terminal. Go to HKEY_Current_User/Software/Wine/MSHTML and create a new key labeled “0.1.0”
[*]In the new “0.1.0” key, create a new string value labeled “GeckoPath” and set the string value to “c:\windows\gecko\0.1.0\wine_gecko”
[/list]
Gecko should be installed correctly now.

uhh i get an error after the first code is says [CODE]mv: cannot move `wine_gecko' to `/home/*****/.wine/drive_c/windows/gecko/0.1.0/wine_gecko': Directory not empty
/CODE]

---

