---
title: "Printing issue with the postage app, Endicia Dazzle"
date: 2013-08-15
forum: Wine
---

### Post by dyers2 on 2013-08-15
I'm only a week into using Ubuntu. I have several business applications, and one or another version of Photoshop that I aim to install in Wine. The first to tackle is Endicia Dazzle which prints postage. It was a snap to install. While I haven't gotten Dazzle to do a test print yet, it prints fine from Gedit. I'm running Ubuntu Studio v.13.04 w/ Xfce desktop environment, and my printer is a Samsung CLX3185FW.

When I try to do a test print, I get this message: "Printer 'Samsung-CLX-3180': 'marker-supply-missing'". 3185 was not an available choice. 3180 & 3190 both were. I selected 3180 because it was recommended.

A Google search led me to do this:

> [COLOR=#696969]#[/COLOR][COLOR=#b22222] ls -l[/COLOR][COLOR=#696969]
total 1544[/COLOR]
[COLOR=#696969]-rwxr-xr-x 1 root root  22256 May  9 17:54 [/COLOR][COLOR=#008000]bannertopdf[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  34488 Nov 22  2012 [/COLOR][COLOR=#008000]c2esp[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  26216 Nov 22  2012 [/COLOR][COLOR=#008000]c2espC[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  13856 Nov 22  2012 [/COLOR][COLOR=#008000]command2esp[/COLOR]
lrwxrwxrwx 1 root root     33 Mar  9 03:10 [COLOR=#0000ff]command2foo2lava-pjl[/COLOR] [COLOR=#008000]-> ../../../bin/command2foo2lava-pjl[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   5544 Jul 11  2012 [/COLOR][COLOR=#008000]commandtocanon[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   9648 Jul 11  2012 [/COLOR][COLOR=#008000]commandtoepson[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   9704 May  9 17:54 [/COLOR][COLOR=#008000]commandtoescpx[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   5596 May  9 17:54 [/COLOR][COLOR=#008000]commandtopclx[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  13672 Apr 16 02:57 [/COLOR][COLOR=#008000]commandtops[/COLOR]
lrwxrwxrwx 1 root root     12 Mar  8 13:56 [COLOR=#0000ff]cupsomatic[/COLOR][COLOR=#008000] -> foomatic-rip[/COLOR]
lrwxrwxrwx 1 root root     25 Mar  8 13:56 [COLOR=#0000ff]foomatic-rip[/COLOR] [COLOR=#008000]-> ../../../bin/foomatic-rip[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   6985 Jul 30 18:20 [/COLOR][COLOR=#008000]gstopxl[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  26264 Jul 30 18:21 [/COLOR][COLOR=#008000]gstoraster[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   5480 Apr 16 02:57 [/COLOR][COLOR=#008000]gziptoany[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  14354 Mar  9 02:47 [/COLOR][COLOR=#008000]hpcac[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root 385776 Mar  9 02:48 [/COLOR][COLOR=#008000]hpcups[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  26232 Mar  9 02:48 [/COLOR][COLOR=#008000]hpcupsfax[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   9708 Mar  9 02:48 [/COLOR][COLOR=#008000]hplipjs[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  10483 Mar  9 02:47 [/COLOR][COLOR=#008000]hpps[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  30408 May  9 17:54 [/COLOR][COLOR=#008000]imagetopdf[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root    989 May  9 17:53 [/COLOR][COLOR=#008000]imagetops[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  52244 May  9 17:54 [/COLOR][COLOR=#008000]imagetoraster[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  22292 May  9 17:54 [/COLOR][COLOR=#008000]pdftoijs[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root 129488 May  9 17:54 [/COLOR][COLOR=#008000]pdftoopvp[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root 120884 May  9 17:54 [/COLOR][COLOR=#008000]pdftopdf[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  26480 May  9 17:54 [/COLOR][COLOR=#008000]pdftops[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  30492 May  9 17:54  [/COLOR][COLOR=#008000]pdftoraster[/COLOR][COLOR=#696969] 
-rwxr-xr-x 1 root root   6479 May  9 17:53  [/COLOR][COLOR=#008000]pstopdf[/COLOR][COLOR=#696969] 
-rwxr-xr-x 1 root root  50568 Apr 16 02:57  [/COLOR][COLOR=#008000]pstops[/COLOR][COLOR=#696969] 
-rwxr-xr-x 1 root root  18036 Apr  8 17:52  [/COLOR][COLOR=#008000]pstoqpdl[/COLOR][COLOR=#696969] 
-rwxr-xr-x 1 root root    974 Mar  9 02:47  [/COLOR][COLOR=#008000]pstotiff[/COLOR] 
lrwxrwxrwx 1 root root     13 Apr 16 02:57[COLOR=#0000ff] rastertodymo[/COLOR][COLOR=#008000]  -> rastertolabel[/COLOR] [COLOR=#696969]
 -rwxr-xr-x 1 root root  17768 Apr 16 02:57 [/COLOR] [COLOR=#008000]rastertoepson[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  30344 May  9 17:54[/COLOR][COLOR=#008000]  rastertoescp x[/COLOR][COLOR=#696969] 
-rwxr-xr-x 1 root root  42904 Jul 11  2012 [/COLOR][COLOR=#008000]rastertogutenprint.5.2[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  17768 Apr 16 02:57 [/COLOR][COLOR=#008000]rastertohp[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  21864 Apr 16 02:57 [/COLOR][COLOR=#008000]rastertolabel[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  30352 May  9 17:54 [/COLOR][COLOR=#008000]rastertopclx[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  34324 Sep 11  2012[/COLOR][COLOR=#008000] rastertoptch[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  13672 Apr 16 02:57 [/COLOR][COLOR=#008000]rastertopwg[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  59080 Apr  8 17:52 [/COLOR][COLOR=#008000]rastertoqpdl[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  15942 Feb 15  2012[/COLOR][COLOR=#008000] rastertosag-gdi[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root   3560 May  9 17:53[/COLOR][COLOR=#008000] textonly[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  40356 May  9 17:54[/COLOR][COLOR=#008000] texttopdf[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root    983 May  9 17:53 [/COLOR][COLOR=#008000]texttops[/COLOR][COLOR=#696969]
-rwxr-xr-x 1 root root  38648 May  9 17:54 [/COLOR][COLOR=#008000]urftopdf[/COLOR]


In addition to the suggestion to "[COLOR=#008080]go to /usr/lib/cups/filter and do[/COLOR] an[COLOR=#b22222] ls -l[/COLOR]", the original responder also said, "[COLOR=#008080]perhaps you will see what  ownership or permissions are wrong, then fix  them[/COLOR]". I kinda don't know what to make of this. If you do, and/or if you see something wrong in the output I quoted above, and/or have a suggestion for how to resolve my printing issue, I'll be very appreciative to hear it.

---

