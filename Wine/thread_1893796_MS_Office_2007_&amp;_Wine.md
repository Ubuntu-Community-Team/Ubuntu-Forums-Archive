---
title: "MS Office 2007 &amp; Wine"
date: 2011-12-11
forum: Wine
---

### Post by Condor Cluster on 2011-12-11
Hi,

I've never used Wine before, but need to ditch LibreOffice for MS Office 2007 as I need the better compatibility.

If I install Office 2007 under Wine, will it still print documents like normal if I click the print button in Word? (ie can an emulated Windows app still see the printer/scanner?)

Also, if I double click on a document file, will it automatically launch Office 2007 Word to open it?

Thanks.

---

### Post by BC59 on 2011-12-11
I answer yes to your questions.

In any case one of the best installation guides for MSOffice 2007 is here:

[http://www.webupd8.org/2011/01/how-to-install-microsoft-office-2007-in.html](http://www.webupd8.org/2011/01/how-to-install-microsoft-office-2007-in.html)

You can do the same with MSOffice 2010 as I explain here:

[http://ubuntuforums.org/showthread.php?t=1885051](http://ubuntuforums.org/showthread.php?t=1885051)

---

### Post by Elfy on 2011-12-11
Thread moved to Wine.

---

### Post by Condor Cluster on 2011-12-11
Cool, thanks for the guides.

Now have Office 2007 successfully installed and working. (Had to add component 'proofing tools' afterwards to get spell checker to work though)

EDIT: managed to remove libreoffice using *sudo apt-get remove libreoffice*.**

PS- can you install Service Packs for Office under Wine? I don't even know how to display the version number of Office 2007 yet, stupid ribbon thingy :S

---

### Post by BC59 on 2011-12-11
> managed to remove libreoffice using [I]sudo apt-get remove libreoffice*.*

The problem is that now you deleted the dictionaries, included to the packages. If you are affected better reinstall them through the app Synaptic.

> PS- can you install Service Packs for Office under Wine? I don't even know how to display the version number of Office 2007 yet, stupid ribbon thingy.


I never manage to do it. The simpler way is to find an MS Office with the Service Packs included. I don't know if someone from the forum can help on that.

---

### Post by Condor Cluster on 2011-12-11
The spell checker in Word, and Firefox still seems to work, so I guess all is well :)

I guess I don't really need to put any Service Packs on, all it would add is PDF and ODT functions, but I can live without.

---

