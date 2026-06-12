---
title: "FlashGet alternative"
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-06-19
I need something like flashget on xubuntu 8.04.
I have tried Downloader for X, Kget and Gwget, and none is working what I need.
I need to download from rapidshare and I have premium account, I tested Downloader for X, because it has site manager, and I type in correct username and password, but it only downloads a 8 kb file...

any help ?

---

### Post by pixel :-) on 2008-06-20
i don't know if it going to work with registration.In Firefox install DownThemAll! plugging.Hopefully since it's a Firefox plugging, there will be no problem with logging and to have acceleration.

If it doesn't work,try flashget with wine.

Download accelerators work, by starting multiple downloads of different sections of the file.Are you sure that flashget can do this,with a registration?i would expect that rapidshare takes proactive measures to block accelerators.This is just my guess.

---

### Post by DachaArh on 2008-06-20
I do not need acceleration, I just need site manager that works, to type my user name and pass to be used for every file from rapidshare, and I do not wan't to download more files at once, that is the whole point, I wan't to paste 20 links and to have max one job at time, so when one download is completed, another starts ;)

thanks

---

### Post by mike16889 on 2008-07-04
you could install kget, konqueror and then use konqueror to loginto rapidshare then hust paste your links into my script:[Kget Link Maker](http://kgetlinkmaker.flashplace.net/)
then all you have to do is go into kget and og to: File > Import Transfers. and import the file my script gives you...

---

### Post by Archmage on 2008-07-04
My guess is that you need provide the username and password.

AFAIK you should have the option in Flashget. If all gets wrong you could use wget with comando line options.

```
--http-user=user

       --http-passwd=password
           Specify the username user and password password on an
           HTTP server.  According to the type of the challenge,
           Wget will encode them using either the `basic' (inse-
           cure) or the `digest' authentication scheme.

           Another way to specify username and password is in the
           URL itself.  For more information about security
           issues with Wget,
```

---

### Post by Artemis3 on 2008-07-05
[DownThemAll!](https://addons.mozilla.org/en-US/firefox/addon/201) needs no external programs and does what you want and more...

---

### Post by kuja on 2008-07-06
The KDE4 version of KGet should be able to handle it. With some googling I saw some bugs about downloading from rapidshare, marked resolved. It is also accelerated :)

---

### Post by jonian_g on 2008-07-12
The best solution is to go and get jDownloader.

"JDownloader is open source, platform independent and written completely in Java. It simplifies downloading files from One-Click-Hosters like Rapidshare.com or Megaupload.com - not only for users with a premium account but also for users who don't pay. It offers downloading in multiple paralell streams, captcha recognition, automatical file extraction and much more. Of course, JDownloader is absolutely free of charge. Additionally, many "link encryption" sites are supported - so you just paste the "encrypted" links and JD does the rest. JDownloader can import CCF, RSDF and the new DLC files."

You can store your login info. Massive links import and it even works with no premium acounts. The only bad thing is that it works only with one-Click-Hosters like Rapidshare.com. You can't use it as a download manager for any file (as far as I know).

---

### Post by bren21 on 2008-07-13
Install konqueror and kget. Mark kget as default download manager for konqueror. In konqueror go to rapidshare.com and do your premium login. Make sure you accept the cookie. Then in firefox install the flashgot plugin. Choose kget as the default download manager for flashgot, and now you have a manager that accepts downloads from firefox. You can also use flashgot to download the links at once using firefox's built in download manager.

---

