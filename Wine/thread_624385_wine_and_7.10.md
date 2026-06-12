---
title: "wine and 7.10"
date: 2007-11-26
forum: Wine
---

### Post by M0rThden on 2007-11-26
Anyone else having trouble with wine? i tried to configure it and it wont let me. utorrent barley runs and when i try to browse for a file all it gives me is a blank box.

I tried to use it but i dont think it removed it completly from my system so when i tried to reinstall it i think it made it worse. any ideas on how to fix it.

Oh i want to use mp3 tag editor program and it gives me this. ```
Error writing temporary file. Make sure your temp folder is valid.
``` which it is. i dunno...ive never had much luck with wine.

---

### Post by Sammi on 2007-11-27
Are you able to run winecfg?

Just write "winecfg" in a terminal and press enter to try. It is the Wine configuration utility.

---

### Post by prab97 on 2007-11-27
I installed WINE 0.9.46 yesterday on  my GUTSY GIBBON through Synaptic Package Manager. When I access anything related to wine, for example when I click the Wine Notepad in Wine menu or Browse C:\, my PC hangs totally, and I have to press the restart button on the System Unit.

Earlier I had Feisty Fawn, and Wine 0.9.41 worked perfectly on it. I tried installing 0.9.41 on Gutsy from the .deb file but that too hanged my system totally, So I have completely removed Wine.

Can anyone help me in running Wine on my Gutsy?

---

### Post by roger_1960 on 2007-11-27
I have exactly the same problem with wine 9.49  on 7.10 Have tried re installing with terminal.  After installation with no reprted errors, any wine command completely hangs the PC.  (AMD XP-M 2400)  Any help welcome!

---

### Post by M0rThden on 2007-11-27
I can open the winecfg file but other than that wine doesnt work. ha now its doing even less, it now cant open the .exe i want it to run.

---

### Post by cogadh on 2007-11-27
Do a complete uninstal/purge of Wine, delete your .wine directory, then reinstall and create a new .wine:
```
sudo apt-get remove --purge wine
rm -r ~/.wine
sudo apt-get install wine
winecfg
```

---

### Post by roger_1960 on 2007-11-28
Hi

Thanks for that.  Wine uninstalls and reinstalls fine, but when I type winecfg in terminal and press return it shows one line - something like "configuring folders in /home/roger/.wine and then locks the PC so nothing works except the off button (hence I cant paste the last line!)

I suspect this may be a hardware compatibility issue?

---

### Post by prab97 on 2007-11-28
I too have an AMD system. Its an AMD Sempron 2200+ and has 1GB DDR 333MHz. Same problem- i.e. I completely removed wine and reinstalled it from scratch, then typing winecfg showed a ... then in next line it wrote "creating wine configuration directory .wine..." and then the system hanged completely again. I had to press the power button on UPS.

---

### Post by M0rThden on 2007-11-29
Hey thanks that worked...for now atleast haha.

Thanks!

---

### Post by prab97 on 2008-04-07
Yahoo!!!!!!!!!!!!!!!!!!! Finally I found the solution to my problem!!!!! :guitar:
:guitar:

**_What did I do???_**

My problem was that whenever I typed winecfg and pressed enter, it showed the message:

*creating wine configuration directory .wine*

and then completely hanged my system, leaving only the power button on the system unit to work.
I once restarted my PC after such an event and navigated to my home folder through nautilus with "Show hidden files" enabled. I noticed there many wine configuration directories existinng with the name .wine-<garble> where <garble> refers to a combination of random alphabets(both upper & lower case).

I just renamed such a directory to .wine and deleted the other ones. And voila!!!!! Wine worked when I tried to run it afterwards! :guitar: :guitar:

---

