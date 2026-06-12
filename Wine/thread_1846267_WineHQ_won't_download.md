---
title: "WineHQ won't download"
date: 2011-09-18
forum: Wine
---

### Post by only1pj on 2011-09-18
Hi there

first day with ubuntu and i am struggling already. Whilst searching for how to ope exe files in Ubuntu i found the answer would be to download winehq, but when i try to do this i get the following:

Failed to download package files
Check your Internet connection.

I OK that then get

Requires installation of untrusted packages
The action would require the installation of packages from unauthenticated sources.
ttf-symbol-replacement-wine1.3 wine1.3 wine1.3-gecko winetricks

from googling i can see solutions to similar problems but they all seem program specific and i have not seen an answer for my problem so hope someone can help here

Cheers

---

### Post by ron999 on 2011-09-18
No need to "download" anything.
Use the **PPA** for wine.

Enter these three commands (copy and paste) in the terminal and 'enter', one at a time :-

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install wine1.3 winetricks
```

---

### Post by only1pj on 2011-09-18
That was looking like excellent advice until:

Configuring ttf-mscorefonts-installer 

TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                  <Ok>

I can't click th <OK> and if i try to close the terminal it tell me :
There is still a process running in this terminal. Closing the terminal will kill it.

Help????

---

### Post by ron999 on 2011-09-18
Use 'Tab' key to move to **<OK>** then enter.

---

### Post by only1pj on 2011-09-18
Nice one, all sorted, thanks a million

:)

---

### Post by lisati on 2011-09-18
*Thread moved to **Wine**.*

---

### Post by madjr on 2011-09-18
if you're new this should help:

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal)

[http://www.noobslab.com/2011/06/install-wine-on-ubuntu-1104.html](http://www.noobslab.com/2011/06/install-wine-on-ubuntu-1104.html)

[http://www.youtube.com/watch?v=FkS_Zo4owXU](http://www.youtube.com/watch?v=FkS_Zo4owXU)
[http://www.youtube.com/watch?v=aSQt9qXduqU&feature=related](http://www.youtube.com/watch?v=aSQt9qXduqU&feature=related)

---

