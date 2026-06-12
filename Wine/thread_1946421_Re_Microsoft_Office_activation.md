---
title: "Re: Microsoft Office activation"
date: 2012-03-24
forum: Wine
---

### Post by Rocketman4God on 2012-03-24
I need some help activating my Microsoft Office 2007 on Ubuntu 11.10. I have installed it using Wine and even entered the key as part of the installation process. When I run one of the programs, such as Word, the activation wizard opens and asks how to activate your product. The online option does not work even though my WiFi connection is fine, and the phone option window will not let me type in the code. Any suggestions as to how I can activate it? I do have the CD with the activation code.
Thanks a bunch!

---

### Post by howefield on 2012-03-24
Post moved to the "*Wine*" forum.

---

### Post by forrestcupp on 2012-03-24
Open up Winetricks and choose 'Select the default wineprefix'. In the next screen, choose to 'Install a Windows DLL or component'. In that list, install these components:
```
msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```You'll have to insall msxml3 separately from the others because it will take you to a download link where you can download it to a certain folder, then you have to run the installation again.

When you're done installing those things, go back and choose 'Install a font' and select 'allfonts'. It's takes a while to install that.

After installing all of these things, you can open Word again and try to activate it. If it still doesn't work, you'll have to uninstall it and install it again after having done all of that with Winetricks.

After installing Office 2007 this way, I was even able to activate over the internet. I couldn't get Office 2007 to install with the new Wine 1.4 in Precise, though.

---

