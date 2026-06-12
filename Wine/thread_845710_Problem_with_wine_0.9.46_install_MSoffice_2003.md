---
title: "Problem with wine 0.9.46 install MSoffice 2003"
date: 2008-06-30
forum: Wine
---

### Post by shougang on 2008-06-30
Hi, all:
I installed MSoffice according to this link

[http://wine-review.blogspot.com/2007/09/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2007/09/running-ms-office-2003-under-linux-with.html)

when I execute

$ wine winword.exe

I got the following error.

****************************************************************
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:x11drv:X11DRV_CreateWindow invalid window width -2122799244
err:x11drv:X11DRV_CreateWindow invalid window width -2122799244
err:x11drv:X11DRV_CreateWindow invalid window width -2122799244
err:x11drv:X11DRV_CreateWindow invalid window width -2122799244
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  2901
  Current serial number in output stream:  2915

*****************************************************************

If I run winword in the GUI menu, it shows an error message after load the word interface and then shut off.

_______________________
Microsoft Office Word has encountered a problem and needs to close. We are sorry for the inconvenience.
____________________________-

---

