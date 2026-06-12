---
title: "How do I uninstall Microsoft Office 2000?"
date: 2008-08-02
forum: Wine
---

### Post by FrancesL on 2008-08-02
Hello,
I have tried to install MS Office 2000 in the hope to use it with WINE. My desktop using WosXP crashed (no surprise) but I need to run MS Office on something for my at home part time work. Due to a need to meet a work commitment that required using Office Word, I attempted to install it on my laptop which has Hardy Heron.
I followed a tutorial [https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office) but I still couldn't get Word to run. In the end I spent the night 'fixing' the XP machine. 
That said, I cannot now remove the Ms Office that is still showing as installed in WINE. 
I have followed all the information and instructions I have found. Any further ideas?
Many thanks.

Although I have found workaround using OpenOffice I am still unable to remove all of MS office 2000

---

### Post by tamoneya on 2008-08-03
do you have anything else installed with wine.  If you dont just do this:```
sudo apt-get remove --purge wine
sudo apt-get install wine
```

---

### Post by FrancesL on 2008-08-22
Sorry to take so long to get back..BUT that didnt remove office 2000 which doesnt work wont remember the license number, wont run correctly, freezes the laptop and is just a plain pest.
As my desktop is flakely ( the very reason for getting the laptop) I am barely getting my partime at home work done. I am thinking I may have to install XP onto laptop instead of Ubuntu, at least for now. That would be a pity, but I cant afford to lose my income.
Open Office works beautifully until my employer tries to open the work I complete for them, using Office 2007. OO and Office 2007 dont talk to each other. Pity.

---

### Post by EnGorDiaz on 2008-08-22
you save it as a .doc it works fine it supports all formats including microsoft format in open office

---

### Post by EnGorDiaz on 2008-08-22
i run everything on open office no problems

---

### Post by Kinst on 2008-08-22
Go to home and delete the hidden folder called ".wine"

You'll have to enable hidden folders to see it.

---

### Post by FrancesL on 2008-08-22
> **EnGorDiaz said:**
> you save it as a .doc it works fine it supports all formats including microsoft format in open office
Thanks for response..
I found another answer that works and works well. Save me having to resort to MS! Thankfully!
I went to Synaptic and installed the latest Office from there. One of the options in OoCalc is to Export as <choices> among which is Export as Excel. I used this and it works perfectly, emailed to employer, they can open with MS Office 2007, same applies to OoWord Processor.

---

