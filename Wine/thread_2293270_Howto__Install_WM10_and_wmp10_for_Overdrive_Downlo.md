---
title: "Howto : Install WM10 and wmp10 for Overdrive Downloader"
date: 2015-09-03
forum: Wine
---

### Post by Tim_Johnson on 2015-09-03
I'm using ubuntu 14.04 and have installed wine 1.6.2
My goal is to enable the Overdrive Downloader.
I'm referencing the following URL : [https://appdb.winehq.org/objectManager.php?sClass=version&iId=27541](https://appdb.winehq.org/objectManager.php?sClass=version&iId=27541)
I have not used wine in 10 or 12 years. I do not find the following instructions to be sufficient ```

1. Install winetricks
2. With winetricks install WM10
winetricks wmp10
3. Now you will be able to install ODM console:
wine msiexec /i ODMediaConsoleSetup.msi
```
1. winetricks **is** installed
2. I do not find **WM10** in the winetricks database
3. I do not find **wmp10 **in the winetricks database
4. I **have** downloaded ODMediaConsoleSetup.msi
Question : 
1. How do I add WM10 and wmp10 to the winetricks database
or can I bypass winetricks?
2. What version should I set wine to?
Added :
Downloaded MP10Setup.exe from [https://www.microsoft.com/en-US/download/confirmation.aspx?id=20426](https://www.microsoft.com/en-US/download/confirmation.aspx?id=20426)
I'm on a dual-boot system and can't get into the ubuntu partition 'til tomorrow. I will try installing both tomorrow and see what happens.
In the meantime, I'd still welcome comments and advice.

thanks
Tim

---

