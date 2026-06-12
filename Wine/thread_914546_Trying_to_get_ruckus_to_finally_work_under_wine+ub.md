---
title: "Trying to get ruckus to finally work under wine+ubuntu."
date: 2008-09-08
forum: Wine
---

### Post by tomd123 on 2008-09-08
Well there are currently two programs that are currently keeping my laptop in dual boot mode. The first one is steam (counterstrike/condition zero) the other is ruckus. I came here to finally get ruckus to work and hopefully get my unnecessarily necessary programs working under Ubuntu :D
I will quickly re-edit this post once I boot into Ubuntu :( see what I mean.

First, I do sudo aptitude install wine on a fresh install. The wine version is 1.1.4.
Next, I installed the ruckus player from the ruckus website.
 The ruckus install, installed wmp 10, with banjour and flash.
 During the install, I get a fatal error "Installation ended prematurely because of an error".
It was currently on C:\windows\temp\bonjourcorewrapper.msi
 This pops up with Ruckus Player Setup
"Apple Bonjour did not install successfullly.
 The neighborhood features of the Ruckus Player will not work without Bonjour installed."

This error is fine by me, since I don't want to use that feature.

Next, when I start ruckus, I get the error: ruckus
"Ruckus detected a problem with the Windows DRM store.
 Please clear the DRM store as described on our help site."
And pointed me to [http://ruckus.custhelp.com/cgi-bin/ruckus.cfg/php/enduser/std_adp.php?p_faqid=111](http://ruckus.custhelp.com/cgi-bin/ruckus.cfg/php/enduser/std_adp.php?p_faqid=111)
I don't have a documents and settings folder in wine, so this probably does not relate to me.

Now when I sign in, I type in user and password. Then click sign in. I get the following error: ruckus player
"Cannot connect to the ruckus server:
 Error: a security error occurred (12175).
 Please check your firewall settings to verify that Ruckus is allowed to make outgoing connections."
But my Ubuntu install does not have a firewall and it works on windows so I don't know what the problem could be ?:(. Thanks for your help, I'm sure this will help a lot of people (most of them being university students)

---

### Post by tomd123 on 2008-09-09
Here is the exact console output that I get, starting with "wine Ruckus.exe" clicking ok on the error message, the trying to login, confirming another error message, and exiting.

[http://pastebin.com/f25aab7df](http://pastebin.com/f25aab7df)

Hopefully we can get somewhere :D

The error all the way at the end could have resulted from me clicking on the x button on the top right corner, but I'm not certain. -Thanks

---

### Post by birddog165 on 2009-01-23
I wish I knew how to code, cause seriously, I'd be all over this... and I'd be like a billionaire cause everyone wants to know how to do this.

---

### Post by hikaricore on 2009-01-23
I seriously doubt Ruckus will ever run under WINE:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3601](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3601)

---

### Post by Tomatz on 2009-01-23
> **tomd123 said:**
> Well there are currently two programs that are currently keeping my laptop in dual boot mode. The first one is steam (counterstrike/condition zero) the other is ruckus. I came here to finally get ruckus to work and hopefully get my unnecessarily necessary programs working under Ubuntu :D
I will quickly re-edit this post once I boot into Ubuntu :( see what I mean.

First, I do sudo aptitude install wine on a fresh install. The wine version is 1.1.4.
Next, I installed the ruckus player from the ruckus website.
 The ruckus install, installed wmp 10, with banjour and flash.
 During the install, I get a fatal error "Installation ended prematurely because of an error".
It was currently on C:\windows\temp\bonjourcorewrapper.msi
 This pops up with Ruckus Player Setup
"Apple Bonjour did not install successfullly.
 The neighborhood features of the Ruckus Player will not work without Bonjour installed."

This error is fine by me, since I don't want to use that feature.

Next, when I start ruckus, I get the error: ruckus
"Ruckus detected a problem with the Windows DRM store.
 Please clear the DRM store as described on our help site."
And pointed me to [http://ruckus.custhelp.com/cgi-bin/ruckus.cfg/php/enduser/std_adp.php?p_faqid=111](http://ruckus.custhelp.com/cgi-bin/ruckus.cfg/php/enduser/std_adp.php?p_faqid=111)
I don't have a documents and settings folder in wine, so this probably does not relate to me.

Now when I sign in, I type in user and password. Then click sign in. I get the following error: ruckus player
"Cannot connect to the ruckus server:
 Error: a security error occurred (12175).
 Please check your firewall settings to verify that Ruckus is allowed to make outgoing connections."
But my Ubuntu install does not have a firewall and it works on windows so I don't know what the problem could be ?:(. Thanks for your help, I'm sure this will help a lot of people (most of them being university students)

Use virtualbox (in repos) to install windows in a vm. Then install ruckus in the vm. I think that will be your only option.

---

### Post by birddog165 on 2009-01-23
I think so too, I was just hoping that I could avoid the whole windows thing. lol

---

### Post by Tomatz on 2009-01-23
> **birddog165 said:**
> I think so too, I was just hoping that I could avoid the whole windows thing. lol

Maybe you should petition for a linux port? Ruckus player is aimed at students so you should get some interest.

---

### Post by birddog165 on 2009-01-23
You know, they've got poor service, however, I just may do that right now :)

I'm startin a revolution

---

### Post by birddog165 on 2009-01-23
Hey, good news!?

So Ruckus is basically like "We want to be helpful, but it's not our fault." lolz

Anyways, [they say that the issue lies in the DRM.]("http://ruckus.custhelp.com/cgi-bin/ruckus.cfg/php/enduser/std_adp.php?p_faqid=109&p_created=1123182259&p_sid=AcSx3Eoj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSw1JnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1saW51eA**&p_li=&p_topview=1")

---

### Post by Tomatz on 2009-01-23
> **birddog165 said:**
> Hey, good news!?

So Ruckus is basically like "We want to be helpful, but it's not our fault." lolz

Anyways, [they say that the issue lies in the DRM.]("http://ruckus.custhelp.com/cgi-bin/ruckus.cfg/php/enduser/std_adp.php?p_faqid=109&p_created=1123182259&p_sid=AcSx3Eoj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSw1JnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1saW51eA**&p_li=&p_topview=1")

Same old chestnut lol. Basically what the bbc say :(

---

### Post by Tomatz on 2009-01-23
Doubt it would work but maybe if you install wmp10 in wine you may be able to get ruckus to work:

[http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html)

Worth a try?

---

### Post by birddog165 on 2009-01-24
oh boy, I've got to do some work today, but I will have to try this

---

