---
title: "IE7 on Wine"
date: 2008-01-31
forum: Wine
---

### Post by Hoom@n on 2008-01-31
Hello! I used "sudo apt-get install wine" and installed wine. Now When I wanna install IE7 which I downloaded from Microsoft site I get this: (attached)
+++
(In the picture you can also see the IE7 .exe file)
___
Thank you.

---

### Post by pissedoffdude on 2008-01-31
It doesn't seem like IE7 would run very well under wine [URL="http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195"]http:
//appdb.winehq.org/objectManager.php?sClass=version&iId=4195[/URL]
However, it is possible to run IE6 [http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by Hoom@n on 2008-01-31
Thanks. I gonna install IE6.

---

### Post by Hoom@n on 2008-01-31
Hello again!
I installed IE6 from the site in two posts before. Now please see the attachments:
(First is the homepage, and in second I drown a line which shows a place that in that place I pressed end then shift+home and wrote [http://www.google.com](http://www.google.com) and pressed enter.)
What can I do?
Thanks.

---

### Post by fethio on 2008-02-01
same problem here. check out picture of the broken gui. I had no problems with this package in its previous release (ies4linux-2.0.5.tar.gz). when i installed version 2.99.0, the gui got screwed up... (i tried installing older version back again, but didn't work out)
[IMG]http://me.yeditepe.edu.tr/staff/okyar/ies4linux_brokengui.jpg[/IMG]

---

### Post by Hoom@n on 2008-02-01
Isn't here any help?

---

### Post by Nash Li on 2008-02-01
I have the same problem.
It's really annoying.

---

### Post by Hoom@n on 2008-02-01
I try to download the 6th version directly from microsoft and install it by wine, without ie4linux. I'll tell the result very soon.

---

### Post by wizkey on 2008-02-01
For those experiencing problems with ies4linux and versions of wine since 0.9.53:

[http://ubuntuforums.org/showpost.php?p=4171872&postcount=23](http://ubuntuforums.org/showpost.php?p=4171872&postcount=23)

The problem with ies4linux is with the theme it is using. wine made some recent changes to themes, and this appears to be causing some issues with ies4linux's theme.

---

### Post by wizkey on 2008-02-01
Better link of instructions:

[http://ubuntuforums.org/showpost.php?p=4158076&postcount=17](http://ubuntuforums.org/showpost.php?p=4158076&postcount=17)

---

### Post by Hoom@n on 2008-02-02
Thanks. I gonna test.

---

### Post by promodus on 2008-07-01
```
 apt-get install cabextract
 wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux
```

Done.

---

### Post by spud.dups on 2008-07-02
I know this is way after the fact, but here is something I learned.  Using winetricks ([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)) in the terminal type "sh winetricks volnum".  This give the change that you will need for the files to extract.

Though don't get to excited, because there is another problem that I haven't figured out.  Now it comes up with the error message "Setup could not verify the integrity of the files needed for the installation.  Make sure the Cryptograp"... and it ends there.  I'm guessing it's talking about one of the Windows services that needs to be running.  I'll take a deeper look into this one, but at least the files now extract.

Cheers

---

### Post by karthik.velugoori on 2008-09-04
hey that's where i m stranded :(

---

### Post by karthik.velugoori on 2008-09-04
> **promodus said:**
> ```
 apt-get install cabextract
 wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux
```

Done.

this code works for me .... but the ie7 i installed after going to advanced options doesn't work properly ...
i can't modify internet options

---

### Post by bleedingpowers on 2009-10-20
Same problem when trying to install IE7,

I'm getting the "Setup could not verify the integrity of the files needed for the installation. Make sure the Cryptograp"

Did anyone find the workaround for this?

---

### Post by alexthunder on 2010-05-26
I installed IE7 using the following instructions
[http://stream-recorder.com/forum/install-internet-explorer-7-ie7-ubuntu-10-t6721.html](http://stream-recorder.com/forum/install-internet-explorer-7-ie7-ubuntu-10-t6721.html)

I can access HTTP pages, but I need HTTPS and ActiveX. Any idea how to make it work in Ubuntu?

p.s. Please do not suggest a virtual machine or dual boot.

---

### Post by SteamInc on 2010-05-27
Why would a person want to use IE. Its a piece of crap which is so slow. Firefox or Chrome is way better.

---

### Post by alexthunder on 2010-05-28
> **SteamInc said:**
> Why would a person want to use IE. Its a piece of crap which is so slow. Firefox or Chrome is way better.
Isn't it obvious? Web-designers need to see how their web-sites look like in IE. And some web-sites are compatible with IE only (for example, the ones with ActiveX), you can't just change a user agent.

---

