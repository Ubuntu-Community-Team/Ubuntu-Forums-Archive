---
title: "[SOLVED] Acroread RealPlay 64bit Gusty How To"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by be4truth on 2007-10-01
I spent quite some time now to figure out a clean way how to install Arobat Reader 7 or 8 and RealPlayer 10 on a 64bit Gusty system but without much success. Lot's of posts around this to applications. Did anybody figure that out?
Thx in advance

---

### Post by Kilz on 2007-10-01
> **be4truth said:**
> I spent quite some time now to figure out a clean way how to install Arobat Reader 7 or 8 and RealPlayer 10 on a 64bit Gusty system but without much success. Lot's of posts around this to applications. Did anybody figure that out?
Thx in advance

Are you asking just to install the reader, and realplayer, or the browser plugins?

---

### Post by be4truth on 2007-10-02
I think both might be good. I had this running like a charm on Feisty 32 bit. The reader is very useful when working with inkscape.

---

### Post by Kilz on 2007-10-02
The acrobat plugin is going to be the difficult one. Its still only 32bit. [You could use a 32bit browser and install the plugin.]("http://ubuntuforums.org/showthread.php?t=202537") That howto will also install the mplayer plugins which can open up imbeded real content. There should be a realplayer deb in the repositories if you want to use it as a media player.

---

### Post by John.Michael.Kane on 2007-10-02
For acroread under gutsy 64.

Run:
```
echo "deb http://packages.medibuntu.org/ gutsy free non-free" | sudo tee -a /etc/apt/sources.list
```

Followed by
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Then.
```
gksudo aptitude install acroread acroread-plugins acroread-escript
```

Regarding realplayer. You can try the method below.

Download RealPlayer10 from [www.real.com/linux](www.real.com/linux)

To install realplayer save the file to your home folder

mark the file executable: 

Inside your terminal type:
```
chmod a+x RealPlayer10GOLD.bin
```
Next:
```
sudo ./RealPlayer10GOLD.bin
```
enter password

To complete the path where you want to install realplayer type:
/opt/RealPlayer

You should now begin copying files accept the default, and allow the installer to configure system wide symbolic links, If asked to specify the prefix for symbolic links just press enter.


Hope this helps..

---

### Post by be4truth on 2007-10-02
For the time being I get this from medibuntu:
Failed to fetch [http://packages.medibuntu.org/dists/gutsty/free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/gutsty/free/binary-amd64/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]
Failed to fetch [http://packages.medibuntu.org/dists/gutsty/non-free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/gutsty/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]

Maybe this changes.

The Real player I installed the way you decribed but the firefox plugin doesn't work; BBC all the recorded shows for example

---

### Post by serendib on 2007-10-02
There appears to be a typo in the previous post by SD-Plissken to add medibuntu to the sources.list:
	
"echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsty free non-free" | sudo tee -a /etc/apt/sources.list"

This should be gusty not "gutsty" ?

---

### Post by John.Michael.Kane on 2007-10-02
> **be4truth said:**
> For the time being I get this from medibuntu:
Failed to fetch [http://packages.medibuntu.org/dists/gutsty/free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/gutsty/free/binary-amd64/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]
Failed to fetch [http://packages.medibuntu.org/dists/gutsty/non-free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/gutsty/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]

Maybe this changes.

The Real player I installed the way you decribed but the firefox plugin doesn't work; BBC all the recorded shows for example

I'm not sure why real player is not working. Have you tried other sites?

> **serendib said:**
> There appears to be a typo in the previous post by SD-Plissken to add medibuntu to the sources.list:
	
"echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsty free non-free" | sudo tee -a /etc/apt/sources.list"

This should be gusty not "gutsty" ?

Thanks for the heads up I corrected the issue.

---

### Post by be4truth on 2007-10-03
> **SD-Plissken said:**
> I'm not sure why real player is not working. Have you tried other sites?



Thanks for the heads up I corrected the issue.

That corrects the issue. Adobe will install fine. Load with an error:

... error loading plug-in PPKLite.api .

I did this and now it works:

```
cd /usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins
```
```
sudo chmod -x PPKLite.api
```

Firefox plugin will happen soon I guess. It is not so urgent for me. 
Thx for all the help so far! I love community:)

Next problem RealPlayer - soon.

Didn't do anything for 2 weeks but now realplayer works. Fixed itself! That's why I like Ubuntu ...

---

### Post by JAwuku on 2007-10-31
> **serendib said:**
> There appears to be a typo in the previous post by SD-Plissken to add medibuntu to the sources.list:
	
"echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsty free non-free" | sudo tee -a /etc/apt/sources.list"

This should be gusty not "gutsty" ?

It's not gusty, but ***gutsy***

so it should read ```
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) **gutsy** free non-free" | sudo tee -a /etc/apt/sources.list
```

---

