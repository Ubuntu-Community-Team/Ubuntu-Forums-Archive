---
title: "Installing Lego Mindstorm EV3 Software"
date: 2017-10-08
forum: Wine
---

### Post by dmmatei on 2017-10-08
Hi,

I need to install and run lego mindstorm on ubuntu via wine 

When running /home/xxx/.wine/drive_c/LMS EV3/MindstormsEV3.exe, I get the error below:

fixme:mscoree****_supported_runtime sku=L".NETFramework,Version=v4.0" not implemented
Unhandled Exception:
System.IO.FileNotFoundException: Could not load file or assembly 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
File name: 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'

Ubuntu version: 16.04
Wine version: 1.3.0
Lego mindstorm: 1.2.1 but the error reproduces also on 1.3 

Can anybody please help me fix the error ?
Thank you so much

---

### Post by ajgreeny on 2017-10-08
> Ubuntu version: 16.04
Wine version: 1.3.0
Lego mindstorm: 1.2.1 but the error reproduces also on 1.3 
Wine 1.3.0?  Really that version?
The only info I can find at the Wine apps database is at [https://appdb.winehq.org/objectManager.php?sClass=application&iId=15648](https://appdb.winehq.org/objectManager.php?sClass=application&iId=15648) and if Silver or Bronze is the best it can do, I suspect you will not get it running as you want it to; from my memory of wine, which I admit I have not used for several years and it may have become better, things needed to be listed as Gold or Platinum to be worth using in wine.

---

