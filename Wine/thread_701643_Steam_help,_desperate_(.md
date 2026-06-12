---
title: "Steam help, desperate :("
date: 2008-02-19
forum: Wine
---

### Post by boblettoj99 on 2008-02-19
right, i finally bit the bullet last night and made the switch from windows...hoorah!

problem is it means i had to say goodbye to all my lovely games, or so i thought. I stumbled across wine and downloaded it straight away hoping i could play cs:s through steam.

i installed wine and steam and it was all going fine but when i run steam it gets to the part where it logs in to my account then suddenly disappears. when i did it through the console i got a huge pile of errors:

```

fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure th
at ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of y
our distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ntdll:RtlpWaitForCriticalSection section 0x70c11b0 "?" wait timed out in thr                                                                                                   ead 0021, blocked by 0014, retrying (60 sec)
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:ViewObject_SetAdvise (0x139bc8c0)->(1 00000002 0x14cdf40)
fixme:shdocvw:PersistStreamInit_InitNew (0x139bc8c0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x139bc8c0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x139bc8c0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x139bcc90)->(1 00000002 0x14cdfa8)
fixme:shdocvw:PersistStreamInit_InitNew (0x139bcc90)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x139bcc90)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x139bcc90)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x10096,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
err:module:map_image Could not map section .text, file probably truncated
err:module:map_image Could not map section .text, file probably truncated
err:mshtml:init_nsio Could not get factory: 80040154
err:mshtml:set_profile Could not get profile service: 80040154
err:mshtml:NSContainer_Create Creating WebBrowser failed: 80040154
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb

```



pleeease someone help me, iv read numerous how to's but none of them seem to work, i just need some proper one to one advice!

thanks, ed

wine verion = 0.9.46

---

### Post by Roryking on 2008-02-19
It seems like you don't have the Gecko libraries installed. The Gecko libs are what Wine uses to simulate Internet Explorer libraries being available. Try going to a terminal, and running this command:

```
wine iexplore http://www.winehq.net
```

and it should prompt you to install the Gecko libraries. Go ahead and do it. When the page loads correctly, close the browser, and try loading Steam again.

---

