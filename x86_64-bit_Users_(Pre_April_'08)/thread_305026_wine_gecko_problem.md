---
title: "wine gecko problem"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-11-22
everytime a application tries to access the internet or a webpage in wine, i get a wine gecko screen, but i cant click the install button, then i get a visual c++ runtime error, anyway i can manually install wine gecko?

---

### Post by xstaticxgpx on 2006-11-22
bump... anything would help

---

### Post by ghepardo on 2007-01-05
I have same problem. How to manual install wine gecko?

---

### Post by cmon on 2007-05-14
> **ghepardo said:**
> I have same problem. How to manual install wine gecko?

Hi.
I'm getting exactly the same error with wine gecko when I start my WoW launcher. Did you ever solve the issue?

---

### Post by navaburo on 2007-10-12
bump

(using hl2, Ubuntu Feisty)

---

### Post by navaburo on 2007-10-12
To resolve this issue manually install wine-gecko using winetricks:

download and save the winetricks shell script from here:
[http://www.kegel.com/wine/winetricks]("http://www.kegel.com/wine/winetricks")

then run it with:
```
sh winetricks gecko
```

Your apps should now work.

---

### Post by Kilz on 2007-10-13
what exactly is wine gecko?

---

### Post by coldguy on 2007-10-21
Ok, I'm a total noob, but I figured it out. I'll bet there are others out there like me who need things spelled out for them, too. So here's my noob's guide.

1. Go to the link -
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

2. Copy all the text on the whole page and paste it into a text editor.

3. Save as "winetricks", not "winetricks.sh" like I did the first time.

4. Open terminal, cd to directory where you saved "winetricks" (you should already be there) and run it with -
"sh winetricks gecko"

I didn't have to go through this with feisty. It just told me I needed gecko for steam, asked to dl and install it, and it worked. It must be a gutsy thing.

---

### Post by coldguy on 2007-10-21
I spoke too soon
I thought it worked, but in the end, it can't seem to get it done.
What is cabextract and status 127.

-edit-
I tried the last line again-
cabextract /home/justin/winetrickscache/wine_gecko-0.1.0.cab
and bash was nice enough to tell me I needed to install cabextract, and even told me what to type to do it! Who says Linux isn't user friendly?
I then typed-
sh winetricks gecko
it did it's thing, I started Steam, and it worked

justin@blackbox:~$ sh winetricks gecko
--01:42:43--  [http://source.winehq.org/winegecko.php?v=0.1.0](http://source.winehq.org/winegecko.php?v=0.1.0)
           => `winegecko.php?v=0.1.0'
Resolving source.winehq.org... 209.46.25.134
Connecting to source.winehq.org|209.46.25.134|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab](http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab) [following]
--01:42:43--  [http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab](http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab)
           => `wine_gecko-0.1.0.cab'
Resolving nchc.dl.sourceforge.net... 211.79.61.10, 2001:e10:5c00:1::10
Connecting to nchc.dl.sourceforge.net|211.79.61.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,746,895 (5.5M) [text/plain]

100%[====================================>] 5,746,895    161.02K/s    ETA 00:00

01:43:20 (156.72 KB/s) - `wine_gecko-0.1.0.cab' saved [5746895/5746895]

Executing cabextract /home/justin/winetrickscache/wine_gecko-0.1.0.cab
winetricks: 689: cabextract: not found
Note: command 'cabextract /home/justin/winetrickscache/wine_gecko-0.1.0.cab' returned status 127.  Aborting.
justin@blackbox:~$

---

### Post by Cappy on 2007-10-21
As per the guide at [http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)
I used ```
wine iexplore http://winehq.org
```

---

### Post by Malkor on 2007-11-24
> :~$ wine iexplore [http://winehq.org](http://winehq.org)
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000001-0000-0000-c000-000000000046}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {00000001-0000-0000-c000-000000000046}, 80040155
fixme:ole:CoRegisterClassObject CoMarshalInterface failed, 80040155!
err:shdocvw:register_class_object failed to register object 80040155
err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
 I tried using that, am I missing something?

---

### Post by prosper927 on 2007-12-06
can someone repeat that for me please.. newbie here and i am not familiar with cd etc instructions.. it would be best if you could post a snapshot on how to install wine gecko.. i am using wine to be able to run Crossloop in my machine.. million thanks to those who could help! :):guitar:

---

### Post by N1ckmeat on 2007-12-11
> **Cappy said:**
> As per the guide at [http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)
I used ```
wine iexplore http://winehq.org
```



This fixed mine!


:guitar:

---

### Post by sonar_un on 2008-04-28
> **coldguy said:**
> I spoke too soon
I thought it worked, but in the end, it can't seem to get it done.
What is cabextract and status 127.

-edit-
I tried the last line again-
cabextract /home/justin/winetrickscache/wine_gecko-0.1.0.cab
and bash was nice enough to tell me I needed to install cabextract, and even told me what to type to do it! Who says Linux isn't user friendly?
I then typed-
sh winetricks gecko
it did it's thing, I started Steam, and it worked

justin@blackbox:~$ sh winetricks gecko
--01:42:43--  [http://source.winehq.org/winegecko.php?v=0.1.0](http://source.winehq.org/winegecko.php?v=0.1.0)
           => `winegecko.php?v=0.1.0'
Resolving source.winehq.org... 209.46.25.134
Connecting to source.winehq.org|209.46.25.134|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab](http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab) [following]
--01:42:43--  [http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab](http://nchc.dl.sourceforge.net/sourceforge/wine/wine_gecko-0.1.0.cab)
           => `wine_gecko-0.1.0.cab'
Resolving nchc.dl.sourceforge.net... 211.79.61.10, 2001:e10:5c00:1::10
Connecting to nchc.dl.sourceforge.net|211.79.61.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,746,895 (5.5M) [text/plain]

100%[====================================>] 5,746,895    161.02K/s    ETA 00:00

01:43:20 (156.72 KB/s) - `wine_gecko-0.1.0.cab' saved [5746895/5746895]

Executing cabextract /home/justin/winetrickscache/wine_gecko-0.1.0.cab
winetricks: 689: cabextract: not found
Note: command 'cabextract /home/justin/winetrickscache/wine_gecko-0.1.0.cab' returned status 127.  Aborting.
justin@blackbox:~$




I have got to say. I have read posts and posts of Ubuntu problems and fixes while I install this OS on all kinds of hardware. I have never had the opportunity to troubleshoot Ubuntu beyond just reading step by step instructions on how to fix things, never learning new methods to fix things on my own. You sir, have opened my eyes to a new troubleshooting method. Thanks!:KS:KS:KS:KS:KS

---

### Post by jackusage on 2008-06-01
> **Cappy said:**
> As per the guide at [http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)
I used ```
wine iexplore http://winehq.org
```

Worked great for me.

---

### Post by thetechguyz on 2008-06-19
It told me I needed gecko for a Windows based Web Editor for the HTML. The way this is acting I may have to file a bug report. I will wait until I can get Wine 1.0 installed. But I am having a problem installing gecko and now the program is crashing when I try to open a blank page to edit. I tried winetricks but had no luck...

---

