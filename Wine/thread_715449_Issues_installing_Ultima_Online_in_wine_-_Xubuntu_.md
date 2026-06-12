---
title: "Issues installing Ultima Online in wine - Xubuntu 6.06"
date: 2008-03-04
forum: Wine
---

### Post by doojsdad on 2008-03-04
Hello all, I'm on a fresh install of Xubuntu 6.06 on an old machine. I thought I'd put it to work and see if I could install Ultima Online so I installed wine: ```
sudo apt-get install wine
```
I downloaded the UOML installer from [download.com]("http://www.download.com/Ultima-Online-Mondain-s-Legacy-client/3000-7541_4-10432237.html") Then I am trying to install it via ```
doojsdad@doojsdad-desktop:~/.wine/drive_c/Program Files$ sudo wine UOML_setup.exe
``` This is what I get. It shows some splash screens and the install progress bar but it freezes near 100%. Any ideas here?
```
doojsdad@doojsdad-desktop:~/.wine/drive_c/Program Files$ sudo wine UOML_setup.exe
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7993e5f4,0x7993e5f8), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7993e5f0,0x7993e5f4), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9cedc,0x7fb9cee0), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9cd9c,0x7fb9cda0), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9ce60,0x7fb9ce64), stub!
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Ultima Online: Mondain's Legacy - Install Shield Wizard" of other process window (nil) should not use SendMessage
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9cd38,0x7fb9cd3c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9cbf8,0x7fb9cbfc), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9ccbc,0x7fb9ccc0), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d638,0x7fb9d63c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d4f8,0x7fb9d4fc), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d5bc,0x7fb9d5c0), stub!
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Ultima Online: Mondain's Legacy - Install Shield Wizard" of other process window (nil) should not use SendMessage
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d494,0x7fb9d498), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d354,0x7fb9d358), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d418,0x7fb9d41c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d980,0x7fb9d984), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d840,0x7fb9d844), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d904,0x7fb9d908), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d808,0x7fb9d80c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d6c8,0x7fb9d6cc), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d78c,0x7fb9d790), stub!
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Ultima Online: Mondain's Legacy - Install Shield Wizard" of other process window (nil) should not use SendMessage
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d664,0x7fb9d668), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d524,0x7fb9d528), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d5e8,0x7fb9d5ec), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb91398,0x7fb9139c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb91258,0x7fb9125c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9131c,0x7fb91320), stub!
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x2002a
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d980,0x7fb9d984), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d840,0x7fb9d844), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d904,0x7fb9d908), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d808,0x7fb9d80c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d6c8,0x7fb9d6cc), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d78c,0x7fb9d790), stub!
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Ultima Online: Mondain's Legacy - Install Shield Wizard" of other process window (nil) should not use SendMessage
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d664,0x7fb9d668), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d524,0x7fb9d528), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9d5e8,0x7fb9d5ec), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb91398,0x7fb9139c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb91258,0x7fb9125c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9131c,0x7fb91320), stub!
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x2002a
```

---

### Post by doojsdad on 2008-03-07
I just had one more quick, related, question. Because this is 6.06, the stable wine install was only 0.9.9. Perhaps upgrading wine would fix the issue? 

I don't have the backported repositories enabled, if I enabled them would that allow a later wine to install? If not then how do I install a later version of wine (and is that even recommended) ?

EDIT: After reading the sticky on how to install the latest version, and doing so, it works. I think it turned out to be 0.9.53

---

### Post by isaidthebigstump on 2008-05-12
[For Ultima Online Cheats Ultima Online Exploits and UO Gold dupes click here.](http://www.exploitsrus.com/uo.html)

---

