---
title: "How to install Tahoma font"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-09
is this possible ?

thanks in advance

I have just found and downloaded tahoma.ttf and I have it on my desktop, but do not know how to install it

---

### Post by jamesford on 2008-05-09
create a folder called .fonts in your homedir (if there isnt one already) and put the font there and then paste 
sudo ln -s ~/.fonts /root/.fonts
in a terminal and press enter. thats one way of doing it at least

---

### Post by Murz on 2009-11-05
You can use the automated script:
```
#!/bin/bash
[ ! -f /usr/share/fonts/truetype/msttcorefonts/tahoma.ttf -o ! -f /usr/share/fonts/truetype/msttcorefonts/tahomabd.ttf ] &&
wget http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB &&
cabextract -F 'tahoma*ttf' IELPKTH.CAB &&
mkdir -p /usr/share/fonts/truetype/msttcorefonts/ &&
mv -f tahoma*ttf /usr/share/fonts/truetype/msttcorefonts/ &&
chmod 644 /usr/share/fonts/truetype/msttcorefonts/tahoma* &&
fc-cache -v &&
rm -f IELPKTH.CAB &&
echo "Installed Tahoma"

```

---

### Post by Ginsu543 on 2009-11-07
As jamesford said, all you need to do is create a .fonts file in your Home directory and copy the TrueType file into it. I copied all the TrueType fonts in my Windows XP Fonts folder into ~/.fonts and I can access all of them, including in OpenOffice and Appearance.

---

