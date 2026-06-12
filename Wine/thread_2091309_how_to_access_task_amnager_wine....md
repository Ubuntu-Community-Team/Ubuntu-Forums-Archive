---
title: "how to access task amnager wine..."
date: 2012-12-04
forum: Wine
---

### Post by helen2 on 2012-12-04
I'm useing an old wine version 1.0.1 on ubuntu on a server.I'm running different programms under wine and one of this program is utorrent.Everything is ok but sometimes the icon utorrent disappered snd olso if i forced to stop utorrent closeing wine i cant see aagain the utorrent icon olso if i restart it the only way to seee it agin is restarting the server (i rest this server with ubuntu on).Who can help me tellimg me if there is a way to enter in a sort of task manager under ubuntu so taht i can kill all programms inside on wine infact i think that olso if i close wine somehow there is a programm that dont stp to run instead if i get in the task manager maybe i ill be able to kill everything so that i can restart utorrent getting back icon without restarting the server 
Thank's in advance for your help
Helen
:KS

---

### Post by Tweak42 on 2012-12-04
I'm having trouble understanding what you are asking, but I think this what you are looking for.

[http://wiki.winehq.org/FAQ#head-9d93db2588a3de850b0d42b1944431ac24534caa](http://wiki.winehq.org/FAQ#head-9d93db2588a3de850b0d42b1944431ac24534caa)

Quick way to kill all wine programs -
```
wineserver -k
```

and if you want to just pick one.
```
wine taskmgr
```

---

### Post by helen2 on 2012-12-05
> **Tweak42 said:**
> I'm having trouble understanding what you are asking, but I think this what you are looking for.
 
[http://wiki.winehq.org/FAQ#head-9d93db2588a3de850b0d42b1944431ac24534caa](http://wiki.winehq.org/FAQ#head-9d93db2588a3de850b0d42b1944431ac24534caa)
 
Quick way to kill all wine programs -
```
wineserver -k
```
 
and if you want to just pick one.
```
wine taskmgr
```
 
Thank's!!!I neade to wait tahat the utorrent icon will disapeared again the i will try "wine taskmgr" but by the way i have tryied and is all ok 100% i can view all programms that are running under wine.I understand that my English is hard to understand but understand th i'm Italin and I live in Austria and my English is good only soeaking it but writeng it is just the few thing taht they teache in Italian schools.
By the way,thank's again "wiatin that utorrent will disapppeared again" and so hopening that the way u post me will be usefull ( hope and i am sure :) )
Take care
Helen
:KS

---

