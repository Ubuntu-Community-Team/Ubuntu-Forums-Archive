---
title: "how to add photoshop repository in ubuntu"
date: 2017-01-19
forum: Wine
---

### Post by rcrahul60 on 2017-01-19
i have installed wine and trying to add photoshop repository but its failing all the time and i have 64 bit ubuntu.what should i do help me

---

### Post by ian-weisser on 2017-01-19
What did you try?
How did it fail?

Please provide as much detail as possible. We do not know what instructions you are following, We cannot see what you see...until you show us.

---

### Post by rcrahul60 on 2017-01-19
okey i have done these steps:
sudo add-apt-repository ppa:ubuntu-wine/ppa     
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install wine1.8 winetricks

it all work but this failed:-
winetricks atmlib gdiplus msxml3 msxml6 vcrun2005 vcrun2005sp1 vcrun2008 ie6 fontsmooth-rgb gecko

---

### Post by ian-weisser on 2017-01-19
Are you following some online instructions?
Most users choose wine from the Ubuntu repos instead of the PPAs. Does the PPA provide some feature you need?
PPAs are not supported by this forum. PPAs are supported only by the PPA author. If you feel it's a Wine problem, you must contact them.

Was the failure totally silent? Was there an error message?

---

### Post by vasa1 on 2017-01-19
> **rcrahul60 said:**
> ...
it all work but this failed:-
winetricks atmlib gdiplus msxml3 msxml6 vcrun2005 vcrun2005sp1 vcrun2008 ie6 fontsmooth-rgb gecko
Please copy/paste the exact message you get. Use code tags like this:
[noparse]
```

text you want to paste

```[/noparse]

---

### Post by rcrahul60 on 2017-01-19
gamer@gamer-550P5C-550P7C:~$ winetricks atmlib gdiplus msxml3 msxml6 vcrun2005 vcrun2005sp1 vcrun2008 ie6 fontsmooth-rgb gecko
------------------------------------------------------
You are using a 64-bit WINEPREFIX. If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.
------------------------------------------------------
Executing w_do_call atmlib
Executing load_atmlib
Downloading [http://download.microsoft.com/download/E/6/A/E6A04295-D2A8-40D0-A0C5-241BFECD095E/W2KSP4_EN.EXE](http://download.microsoft.com/download/E/6/A/E6A04295-D2A8-40D0-A0C5-241BFECD095E/W2KSP4_EN.EXE) to /home/gamer/.cache/winetricks/win2ksp4
--2017-01-20 01:01:13--  [http://download.microsoft.com/download/E/6/A/E6A04295-D2A8-40D0-A0C5-241BFECD095E/W2KSP4_EN.EXE](http://download.microsoft.com/download/E/6/A/E6A04295-D2A8-40D0-A0C5-241BFECD095E/W2KSP4_EN.EXE)
Resolving download.microsoft.com (download.microsoft.com)... 104.113.220.41
Connecting to download.microsoft.com (download.microsoft.com)|104.113.220.41|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-01-20 01:01:13 ERROR 404: Not Found.

------------------------------------------------------
Downloading [http://download.microsoft.com/download/E/6/A/E6A04295-D2A8-40D0-A0C5-241BFECD095E/W2KSP4_EN.EXE](http://download.microsoft.com/download/E/6/A/E6A04295-D2A8-40D0-A0C5-241BFECD095E/W2KSP4_EN.EXE) failed

---

### Post by ian-weisser on 2017-01-19
404 is universal. The URL does not exist on that server.
Please contact the PPA author and notify them of the bug in atmlib.

---

### Post by rcrahul60 on 2017-01-21
Is there any other way to install photoshop in ubuntu?

---

### Post by wildmanne39 on 2017-01-21
You can install virtualbox then install windows in it and run photoshop that way.
[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by mörgæs on 2017-01-21
Have you tried Gimp? I don't think there is much that Photoshop can do that Gimp can't.

---

### Post by rcrahul60 on 2017-01-24
Is there any other way using wine

---

### Post by ian-weisser on 2017-01-24
Depends upon the version of Photoshop.
Some versions work quite well under Wine, some won't even start.
See [https://appdb.winehq.org/objectManager.php?sClass=application&iId=17](https://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

---

### Post by rcrahul60 on 2017-01-25
thax

---

