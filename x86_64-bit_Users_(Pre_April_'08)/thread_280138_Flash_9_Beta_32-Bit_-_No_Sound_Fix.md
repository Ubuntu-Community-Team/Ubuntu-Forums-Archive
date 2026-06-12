---
title: "Flash 9 Beta 32-Bit - No Sound Fix"
date: 2006-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by warp99 on 2006-10-19
Flash 9 Beta for Linux has just been released for testing and is available here:

[http://labs.adobe.com/technologies/flashplayer9/]("http://labs.adobe.com/technologies/flashplayer9/")

but the sound will not work unless you install the 32-bit ALSA sound library:

sudo apt-get install lib32asound2

You can now run the Flash 9 beta plugin or stand alone player with sound under a 32-bit Firefox install. :cool:

---

### Post by russianpirate on 2006-10-19
Wow awesome :D

Unfortunately, my 64-bit install has borked before i could install this and I'm planning to install a 32-bit version of ubuntu soon just to make it more compatible and run nicer.

---

### Post by fabertawe on 2006-10-19
It works! I've just tried a couple of sites that didn't work previously and they now do... even better, audio is in sync :D 

Paul

---

### Post by honeric01 on 2006-10-19
hi,
i am having a problem with my dell PP08l,when i shut it down, it doesn't come up again,except it showing green and orange light,and again, i am also having a problem with the sound device,i think the sound card software is dead or bad, and i need to instal one asap.
can anyone help me..?
eric

---

### Post by doood81 on 2006-10-19
> **warp99 said:**
> Flash 9 Beta for Linux has just been released for testing and is available here:

[http://labs.adobe.com/technologies/flashplayer9/]("http://labs.adobe.com/technologies/flashplayer9/")

but the sound will not work unless you install the 32-bit ALSA sound library:

sudo apt-get install lib32asound2

You can now run the Flash 9 beta plugin or stand alone player with sound under a 32-bit Firefox install. :cool:
What browser are you using, because the stock 64bit firefox that ships with Dapper doesn't work with this new FP9. In fact it behaves the same as the previous version, a black filled window where the video should be.

I was able to run the previous flash player with flock but there was no sound.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7

---

### Post by RafRaf on 2006-10-19
Couldn't find package lib32asound2

---

### Post by xboxer21 on 2006-10-19
> **RafRaf said:**
> Couldn't find package lib32asound2

it is in the main repositories.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lib32asound2&searchon=names&subword=1&version=dapper&release=main](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lib32asound2&searchon=names&subword=1&version=dapper&release=main)

---

### Post by Kilz on 2006-10-19
If anyone has installed the 32bit firefox with my howto, the files  should already be installed. Install instructions for those that have installed my howto/script are on the howto now.

---

### Post by Kilz on 2006-10-19
> **doood81 said:**
> What browser are you using, because the stock 64bit firefox that ships with Dapper doesn't work with this new FP9. In fact it behaves the same as the previous version, a black filled window where the video should be.

I was able to run the previous flash player with flock but there was no sound.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7

Its possible to installl the 32bit version of firefox so that all plugins work. See the link in my signature, or the "Sticky: How to get specific programs to run under Dapper Drake 64-bit edition" post for a link.

---

### Post by JAPrufrock on 2006-10-20
Thank you Adobe.  Thank you Kilz.

---

### Post by incubus on 2006-10-20
Not surprising, but my firefox crashes randomly with flash 9.  It mostly happens when there's sound involved, but not always.   Everything stops with a Segmentation Fault.

But I welcome flash 9.  I hope they come up with the 64bit version soon.

incubus

---

