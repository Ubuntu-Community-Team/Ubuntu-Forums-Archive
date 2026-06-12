---
title: "Old Story, new touch: Broadcom wireless! :("
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by leche on 2006-04-07
Hey guys,

before anybody starts screaming "RTFM": 
I _have_ read the (very good) tutorial in this forum on the installation of the chip (and quite a few more) but to no avail!
Okay, now to the problem. :)

I own a HP nx6125 laptop and am using Ubuntu 5.10 (Breezy) - quite a nice distro I think. 
The laptop uses the Broadcom 4318 chipset for wireless LAN and I did not manage to get the windows drivers installed and working so far.
I have tried loads of different drivers:
- the ones from hp
- linuxant 64 bit
- acer ferrari 4000 64 bit
and some more.

What I usually get is the following (no matter which driver):
> ndiswrapper -l
No drivers installed
> rmmod ndiswrapper
> ndiswrapper -i bcmwl5.inf 
> for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile; done
> modprobe ndiswrapper
> ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
>tail /var/log/messages
[..]
ndiswrapper version 1.1 loaded (preempt=no,smp=no)
> cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 19

So apparently ndiswrapper is being loaded, the driver however being ignored. Thus no wireless /proc.
The driver is the one used in the other Ubuntu-forum questions (with the same laptop) so it _should_ be working. 
(Jeez, how much I love to say that sentence... :)

Any ideas? 
Anybody?

Cheers
Che

---

### Post by skylark on 2006-04-07
Looks complex. One extra reason for me to avoid going wireless for awhile!

Anyway, it might help if you post some links to what guides you have been following up to now.

Also - maybe this is a dumb question, but I'll ask it anyway - are the driver's you are using 32-bit? Or do they come precompiled in 64-bit (or are you compiling them youself... I really don't know anything about these drivers as you can tell). If they are 32bit they probably won't work in a 64bit environment. If this is the case, it might honestly be easier just installing the i686 (32-bit) version of Breezy on your machine and running with that. Otherwise you will have to jump through all kinds of hoops getting the drivers working.

---

### Post by leche on 2006-04-11
Hey Skylark,

well, I've been trying 32 and 64 bit drivers - neither are working. :(
Guidewise, I don't have all the links anymore, but there is a nice guide in this forum:
[http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan](http://ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+wlan)

I also used the drivers from this post:
[http://www.ubuntuforums.org/showthread.php?t=129647&highlight=nx6125+wireless](http://www.ubuntuforums.org/showthread.php?t=129647&highlight=nx6125+wireless)

Both got me nowehere though. Strange since the guy in the second post seems to have the same laptop and everything...

Btw: just giving up on wlan due to some problems seems a little harshto me. How else could you get up in the morning, go to your favourite coffee shop in amsterdam and sit there - working all day - while having a nice cup of coffee and a bagle? *g*

Anyway, I think I'll give up on this chip and just plug in my good old netgear pcmcia wireless card. This stupid redundancy hurts, though...

Thanks again, skylark.

Che

---

### Post by skylark on 2006-04-11
Have you tried the drivers at
[ftp://ftp.support.acer-euro.com/notebook/aspire_3010_5010/driver/xp64/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3010_5010/driver/xp64/80211g.zip)
?

They seemed to work for this German guy with your model [http://de.gentoo-wiki.com/Compaq_HP_nx6125](http://de.gentoo-wiki.com/Compaq_HP_nx6125) (despite the drivers being on an acer web site).
edit: (you can try [http://www.google.com/translate_t](http://www.google.com/translate_t) to translate the page to English, it kind of works).

Otherwise I'm out of ideas (although this forum post seems to suggest sticking with ndiswrapper version 1.1, but that is the version that ships with Breezy anyway).
[http://forums.suselinuxsupport.de/index.php?showtopic=22694&pid=152626&st=0&#entry152626](http://forums.suselinuxsupport.de/index.php?showtopic=22694&pid=152626&st=0&#entry152626)

---

### Post by Disabled20240622 on 2006-04-11
that's for gentoo only. I just tryed on ubuntu and none of the commands are recognised in the terminal.

---

### Post by leche on 2006-04-12
Hey Skylarc,

well, that´s fortunate: I AM german, so no problem with the site. And *lol* that I did not search on any german websites.

I´ll give the stuff you pointed out a try since that´s a driver I haven´t tried yet.
Thanks alot, I´ll let you know... :)

@bigglespip:
That should not matter at all - Gentoo, Ubuntu, Debian: it´s all the same.

Cheers
Che

---

### Post by TriZz on 2006-04-12
I had the same problem.  Make sure that you have the .sys file also.  It's also VERY important that the .sys and .inf have the same filename.

The first time I tried, the .sys had an extra character in the name and it didn't work out.

I hope this helps.

---

### Post by leche on 2006-04-13
Hey guys,

wow, thanks alot for all the help - I am getting there it seems. :)

I tried the driver and again, ndiswrapper says hardware and driver are there.
However, if I modprobe ndiswrapper I get (for the first time with a driver) a message, that it could not load the driver:

localhost loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwl5

That is not good. *g*

Any ideas on why I get this message now?
Btw: I renamed the sys as you, trizz, suggested but then ndiswrapper cannot even install the driver.

Thnaks again for your help, it is much appreciated. :)

Cheers
Che

---

### Post by leche on 2006-04-15
It should be the correct driver since the german dude got it running with the very same driver... *scratch head*

Any other ideas? I am lost... :(


Cheers
Che

---

### Post by skylark on 2006-04-15
I think we are all out of ideas on this one! Maybe write to Braodcom and demand Linux drivers ;-)

There's a thread here: [http://www.fedoraforum.org/forum/showthread.php?t=55276](http://www.fedoraforum.org/forum/showthread.php?t=55276)
that might help you *maybe* (basically the bit about unloading old drivers... near the end).

---

### Post by leche on 2006-04-17
Okay, thanks alot for your help.

As soon as I find a solution I'll post it here... :)

Cheers
Che

---

### Post by Adler on 2006-04-18
leche,

This is a real shot in the dark to try to help you. Have you tried the commands "ifdown wlan0" then "ifup wlan0"? Or "iwlist" or "ipwlist"?

I've just come to UBUNTU from SuSE and I have the Linuxant DriverLoader that was the only way that I could get wireless going. Eventually, as SuSE developed it seemed that the later versions recognized my Centrino chipset. 

I now run UBUNTU Dapper 64-Bit and rather than torture myself until Dapper goes final and Linuxant can catch up with my kernel I use a PCMCIA wireless card. You may want to try that idea out until things further develop. If the first card that you try doesn't work, return it, and try another. I have a D-Link Air Plus Xtreme G PCMCIA card. Dapper picked it up right away.

---

### Post by cat on 2006-04-19
I had the same problem. Try using the latest version of ndiswrapper and follow the tutorial in the wiki and your wlan should work.

---

### Post by Jefim on 2006-04-19
Ok, I know that there is problem in Dapper (at least x64) with ndiswrapper and broadcom. I don't really know if this problem is in breezy too.
My broadcom wireless wasn't working because of the bcm43xx module. And after I removed it with "rmmod bcm43xx" and inserted "modprobe ndiswrapper" my wireless actually started working. Look for this module in your loaded modules (lsmod) - maybe this is your problem? Also check if you laptop need any extra actions (my acer needs acer_acpi module loaded) for wireless to work...

---

### Post by leche on 2006-04-22
Hey guys,

thanks alot for all your replies - I was afraid this was the end. :)

@Adler: Nope, I cannot up the if cause it's not recognized. iwconfig shows me nada wireless ifs... *sigh*

@cat: Hmmm, I followed the tutorial with loads of drivers alot of times. Prob is they say you should not use the newest ndiswrapper but version 1.1. That's the one I use (well, the Ubuntu-version anyway).
I'll go ahead and make a newer ndiswrapper myself and try it again...

@jefim: Nope, if I probe ndiswrapper it gets loaded properly but the driver does not - although ndiswrapper lists it as proper driver for the device(see above posts).

Jeez, this is getting really complicated... :)

Cheerio
Che

---

### Post by leche on 2006-04-22
Guys, it has been done!! *cheers*

I had a ndiswrapper 1.13 version somewhere, compiled that one and tried the tutorial once more - nothing.

I 'just to have a look' surfed to ndiswrapper on sourceforge and yes, there is a new 1.14 version out!
Compiled and debbed for amd64, installed - it works!!!

Jeeeeeez, it was a hard one, thanks alot to all of you for all the effort and the great hints. You rule... *smile*

See you in the next post ;)
Che

---

### Post by Adler on 2006-04-22
leche,

Sorry that my offering didn't help. I was thinking that you might have found that your card just needed to be "activated". But, you now have it working.

Where did you find the 64-Bit .deb version? Can you post the link? Thanks in advance.

---

### Post by leche on 2006-04-23
Hey Adler,

no worries - any help is appreciated and it might have been the hint I needed. :)
Creating the debs for ndiswrapper is pretty straight forward. I actually wrote a little howto on how I setup my wireless card for people to refer to. It also dfescribes how to get the debs.
It's  [here]("http://www.ubuntuforums.org/showthread.php?t=164634").

Enjoy
Che

---

### Post by skylark on 2006-04-23
Glad you eventually got things working.

Slightly OT but I came across this article [http://kerneltrap.org/node/6497]("http://kerneltrap.org/node/6497") about the effort needed to create free drivers without any specs (maybe one of these guys will eventually reverse engineer a Broadcom wireless device...). Anyway, I found it to be a really interesting read.

---

### Post by Adler on 2006-04-23
leche,

Thanks for the information. I **did** actually go nuts trying to install ndiswrapper at one time. LOL!

---

### Post by leche on 2006-04-23
Hey Skylarc,

yeah, quite interesting ... I'd like to write a driver once. Like, having a permanent thing to be remembered by.
"Yep son, the module you are using at the moment was written by me." *g*

Would be probably be more like this, though:
"What the $#%@#% is this 1024bit quantum network thingy that Windows XXXXXP is complaining about all the time?" :)

@Adler: Glad I could help. :)

Cheers
Che

---

