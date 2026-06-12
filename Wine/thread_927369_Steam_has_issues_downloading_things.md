---
title: "Steam has issues downloading things"
date: 2008-09-22
forum: Wine
---

### Post by Nybb on 2008-09-22
So I've been trying to get the Orange Box to work in Hardy. I saw that all of the games had good ratings in the App DB and decided to give it a go yesterday. I set up Steam alright and began installing the games. It took a suspiciously long time, but I suppose there was a lot of content to install.

Once everything was installed, the My Games page listed all five of the games as 100% Complete - Ready to play or whatever. But when I tried to play any of them, it lingered on the Preparing to Launch Portal/TF2/etc and eventually said that the games were unavailable and to try again later.

After trying this again and giving it some more time, eventually it started updating Portal. It said that the update would take a few hours, so I left and came back. Upon my return, it once again said the game was unavailable.

I repeated the same process with a different game and the exact same thing happened -- the download started to work, but eventually gave the same error message.

So I decided to come back for round two today. But now I can't even get into Steam. I run the .exe and it says it is updating Steam, but it lingers at that window for a long time, and while it is open it seems to severely slow down everything else I try to do on this computer.

I checked the system monitor, and this is where my computer noobishness becomes apparent. I am on a wireless connection, and whenever I am not doing anything that requires the internet the connection drops pretty much to zero, and then goes up when I do something like browse websites in firefox. 

However, when I open Steam and it tries to update, the connection stays at around zero. So it seems to me that Steam is having trouble "requesting internet power" from the computer, if that makes any sense.


I believe I'm using the latest version of wine. I won't bother giving video card specs and stuff like that because that is obviously not the issue here.

Help would be greatly appreciated.

---

### Post by kostkon on 2008-09-22
> **Nybb said:**
> So I've been trying to get the Orange Box to work in Hardy. I saw that all of the games had good ratings in the App DB and decided to give it a go yesterday. I set up Steam alright and began installing the games. It took a suspiciously long time, but I suppose there was a lot of content to install.

Once everything was installed, the My Games page listed all five of the games as 100% Complete - Ready to play or whatever. But when I tried to play any of them, it lingered on the Preparing to Launch Portal/TF2/etc and eventually said that the games were unavailable and to try again later.

After trying this again and giving it some more time, eventually it started updating Portal. It said that the update would take a few hours, so I left and came back. Upon my return, it once again said the game was unavailable.

I repeated the same process with a different game and the exact same thing happened -- the download started to work, but eventually gave the same error message.

So I decided to come back for round two today. But now I can't even get into Steam. I run the .exe and it says it is updating Steam, but it lingers at that window for a long time, and while it is open it seems to severely slow down everything else I try to do on this computer.

I checked the system monitor, and this is where my computer noobishness becomes apparent. I am on a wireless connection, and whenever I am not doing anything that requires the internet the connection drops pretty much to zero, and then goes up when I do something like browse websites in firefox. 

However, when I open Steam and it tries to update, the connection stays at around zero. So it seems to me that Steam is having trouble "requesting internet power" from the computer, if that makes any sense.


I believe I'm using the latest version of wine. I won't bother giving video card specs and stuff like that because that is obviously not the issue here.

Help would be greatly appreciated.
Have you installed the wine IE replacement browser prior to using *Steam*? If not, the open a terminal and give
```
iexplore http://www.winehq.org/
```
If it is not installed, it will be installed after doing the above. If it is, it will just open the Wine website in a browser window.

---

### Post by Bios Element on 2008-09-22
This is a common Steam bug even on windows. Try it again in a few hours after restarting Wine and it should fix itself.

---

### Post by Nybb on 2008-09-23
Bios Element, I can see the "game not available" thing being a bug, but what about where Steam won't even open because it can't update? If that is a common bug, then Steam is an intensely bad platform -- I haven't been able to get into a game successfully for the better part of two days now.

And kostkon, I tried running that command (well, it didn't work exactly as you typed it, but it worked with a wine command in front) and it did indeed open a browser window. However, it did spew out a bunch of lines in the termninal. Here it is, if it matters:

```
xxx@xxxxx:~$ wine iexplore http://appdb.winehq.com/
fixme:ole:CoResumeClassObjects stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7db74a08, overlapped 0x7db749ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x101ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12a7ac)->((null) 1 0x33e69c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->((null) 25 2 0x33e6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->((null) 26 2 0x33e6b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12a7ac)->(0x33e6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33e7b0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12b388)->(L"" L"" 0 0x33e7e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->((null) 29 2 0x33fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12a7ac)
fixme:shdocvw:ClientSite_GetContainer (0x12a7ac)->(0x33fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12a7ac)->(0xb7e476d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->((null) 25 2 0x33fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->((null) 26 2 0x33fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7ac)->((null) 28 2 0x33fb18 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
jon@jon-laptop:~$ wine iexplore http://www.winehq.org/
fixme:ole:CoResumeClassObjects stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7db6da08, overlapped 0x7db6d9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x101ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12a7a4)->((null) 1 0x33e69c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->((null) 25 2 0x33e6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->((null) 26 2 0x33e6b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12a7a4)->(0x33e6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33e7b0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12b380)->(L"" L"" 0 0x33e7e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->((null) 29 2 0x33fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12a7a4)
fixme:shdocvw:ClientSite_GetContainer (0x12a7a4)->(0x33fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12a7a4)->(0xb7e806d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->((null) 25 2 0x33fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->((null) 26 2 0x33fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12a7a4)->((null) 28 2 0x33fb18 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented

```

---

### Post by Bios Element on 2008-09-23
Yes, Steam is an intensely bad platform sometimes. This bug shouldn't have anything to do with iexplore not working. You may have a firewall or the like blocking it in which case Steam will act bonkers. Also, you could try re-installing steam if that is not the case.

---

### Post by Nybb on 2008-09-23
Will reinstalling Steam force me to reinstall/reactivate the games as well? Or is there a way to keep the local game files and just uninstall Steam itself?

And I've never had any firewall problems with networked games or anything before, so unless Steam is actually as terrible as it's beginning to sound, I don't think that would be an issue.

---

### Post by Bios Element on 2008-09-23
> **Nybb said:**
> Will reinstalling Steam force me to reinstall/reactivate the games as well? Or is there a way to keep the local game files and just uninstall Steam itself?

And I've never had any firewall problems with networked games or anything before, so unless Steam is actually as terrible as it's beginning to sound, I don't think that would be an issue.

You can move the .gcf files out of the Steam/steamapps folder so you won't have to re-download them ASSUMING they're at 100% You don't want to mess with them if they're not. Then after re-installing copy em back in and load steam up.

And your running through Wine. Meaning Steam can't really tell if there's a firewall or not. Obviousally, It wasn't designed for Linux so there will be tons of little bugs.

---

