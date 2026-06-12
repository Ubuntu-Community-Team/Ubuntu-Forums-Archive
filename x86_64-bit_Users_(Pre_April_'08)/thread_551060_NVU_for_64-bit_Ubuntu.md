---
title: "NVU for 64-bit Ubuntu"
date: 2007-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by master_kernel on 2007-09-14
[COLOR="Blue"][CENTER][SIZE="5"]**_Project NVU 64_**[/SIZE][/COLOR][COLOR="Gray"]*[SIZE="2"]Straight up AMD64 NVU[/SIZE]*[/CENTER][/COLOR]

[This is NVU 1.0 Final]("http://two.xthost.info/nvu/nvu_1.0final-2ubuntu2_amd64.deb") **for AMD64 processors**. It was compiled from [edgy] source straight from the [Ubuntu Package Site]("http://packages.ubuntu.com/edgy/web/nvu").

My question is: **Does it work for you?**

I followed the Debian Package Management System to compile this deb file for Ubuntu.

If you didn't see the download link above, here it is again: [http://two.xthost.info/nvu/nvu_1.0final-2ubuntu2_amd64.deb](http://two.xthost.info/nvu/nvu_1.0final-2ubuntu2_amd64.deb)

The [devel package]("http://two.xthost.info/nvu/nvu-dev_1.0final-2ubuntu2_all.deb") is also available.

Please post your results, questions, and comments here.

---

### Post by speedbuggy on 2007-09-17
Works like a charm for me on Kubuntu64 Feisty. Thanks for the download link. Everything seems to work as it should. I can grab a random site or connect to my ftp with site manager. It sure is nice to still be running 64 bit clean ..

Cheers
Speedbuggy

---

### Post by master_kernel on 2007-09-24
> **speedbuggy said:**
> Works like a charm for me on Kubuntu64 Feisty. Thanks for the download link. Everything seems to work as it should. I can grab a random site or connect to my ftp with site manager. It sure is nice to still be running 64 bit clean ..

Cheers
Speedbuggy
Sure, thanks for your support.

---

### Post by master_kernel on 2007-09-24
I have confirmed that this works on my computer running Ubuntu Gutsy and Feisty.

---

### Post by thenewrhapsody on 2007-10-10
works for me

---

### Post by steveneddy on 2007-10-10
I will try this after I upgrade to Gutsy 64 bit.

:popcorn:

---

### Post by FredB on 2007-10-13
So do I. But I think it will be a better idea to work on Kompozer, the official "fork" of Nvu.

[http://kompozer.sf.net/](http://kompozer.sf.net/)

---

### Post by Kilz on 2007-10-13
> **FredB said:**
> So do I. But I think it will be a better idea to work on Kompozer, the **official** "fork" of Nvu.

[http://kompozer.sf.net/](http://kompozer.sf.net/)

If you look at the link you provide, at the top it says "Kompozer, NVU's _Unofficial_ Bug-fix Release".

---

### Post by FredB on 2007-10-14
[http://en.wikipedia.org/wiki/Daniel_Glazman](http://en.wikipedia.org/wiki/Daniel_Glazman)

"Daniel Glazman announced on September 15, 2006 that he has stopped official development on [Nvu]("http://en.wikipedia.org/wiki/Nvu") and he is developing a successor to it, tentatively called [Composer]("http://en.wikipedia.org/wiki/Mozilla_Composer") (or Mozilla Composer 2.0), as a Mozilla.org project. It is written from scratch and based on Mozilla trunk [Gecko 1.9]("http://en.wikipedia.org/wiki/Gecko_%28layout_engine%29") and [XULRunner]("http://en.wikipedia.org/wiki/XULRunner"). [PHP]("http://en.wikipedia.org/wiki/PHP") and [CSS]("http://en.wikipedia.org/wiki/Cascading_Style_Sheets") will be supported. A community-driven fork, [KompoZer]("http://en.wikipedia.org/wiki/KompoZer"), maintains Nvu codebase and fixes bugs until a successor to Nvu is released."

I used it and it is safe. Even if Daniel Glazmann, daddy of Nvu thinks it is not a good idea to spent time on Kompozer.

I think there is a bug on launchpad to replace nvu by kompozer.

---

### Post by Kilz on 2007-10-14
I was just pointing out its unofficial is all. I have both Nvu (Edgy deb) and kompozer installed on Feisty. They both work fine.

---

### Post by FredB on 2007-10-15
Ok. But I prefer a slightly less bugged version (Kompozer) than the official one (Nvu).

And you can build it to see if it is ok or not ;)

---

### Post by michael37 on 2007-10-17
.debs are available for Kompozer for 32-bit and 64-bit Feisty.  I tested 64-bit binary on both Feisty and Gutsy-RC and they work fine.
[http://www.getdeb.net/app.php?name=Kompozer](http://www.getdeb.net/app.php?name=Kompozer)

About Composer vs Kompozer:  I do not see new Composer even in nightly builds from mozilla.org, which pretty much tells me it doesn't exist.
[http://ftp.mozilla.org/pub/mozilla.org/](http://ftp.mozilla.org/pub/mozilla.org/)

---

### Post by FredB on 2007-10-17
> **michael37 said:**
> .debs are available for Kompozer for 32-bit and 64-bit Feisty.  I tested 64-bit binary on both Feisty and Gutsy-RC and they work fine.
[http://www.getdeb.net/app.php?name=Kompozer](http://www.getdeb.net/app.php?name=Kompozer)

About Composer vs Kompozer:  I do not see new Composer even in nightly builds from mozilla.org, which pretty much tells me it doesn't exist.
[http://ftp.mozilla.org/pub/mozilla.org/](http://ftp.mozilla.org/pub/mozilla.org/)

Thanks for the info about getdeb.

Composer ? Still a work in progress. See Daniel Glazmann blog for more info :

[http://glazman.org/weblog/](http://glazman.org/weblog/)

Buglist for composer (nvu next generation) :

[http://tinylink.com/?9UfPuIganx](http://tinylink.com/?9UfPuIganx)

Checkins (not a lot !)

[http://tinylink.com/?7oq4Qylefn](http://tinylink.com/?7oq4Qylefn)

---

### Post by master_kernel on 2007-10-22
Looks like KompoZer is in the Gutsy repos.

---

### Post by Jouke74 on 2007-10-22
Yes it is, and it is working ok woo hoo..

---

### Post by junnuh on 2007-10-26
Hello!

Good work, I am interested but will it work also in 64-bit Dapper!:)

with warm regards junnuh:guitar:

---

### Post by michael37 on 2007-10-26
> **junnuh said:**
> Hello!

Good work, I am interested but will it work also in 64-bit Dapper!:)

with warm regards junnuh:guitar:

The 64-bit package works only for Feisty and newer. Sorry.

---

### Post by junnuh on 2007-10-27
:popcorn: Thanks!

That's ok, I'll wate to get the next LTS-version of Ubuntu, maybe it will work there!:)

wirth warm regards and thanks junnuh:guitar:

---

### Post by FredB on 2007-10-28
> **master_kernel said:**
> Looks like KompoZer is in the Gutsy repos.

Really ? Didn't noticed them !

:rolleyes:

Just installed it. Thanks for the info ;)

---

