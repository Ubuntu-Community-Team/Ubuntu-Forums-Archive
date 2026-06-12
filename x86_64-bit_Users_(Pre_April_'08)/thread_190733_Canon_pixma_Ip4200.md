---
title: "Canon pixma Ip4200"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mschievano on 2006-06-06
Hello to everybody.
I finally upgrade to beta form stable of 64 bit dapper, and I have an unresolved question (till march 06): how can i made the pixma ip4200 canon Work?

On Canon and internet there are the source for the x86 not for the 64 bit.

thanks

---

### Post by IbeeX on 2006-06-07
On flight 3 I installed driver for Pixima 4000 and it worked.

---

### Post by mschievano on 2006-06-13
[QUOTE=IbeeX]On flight 3 I installed driver for Pixima 4000 and it worked.[/QUOTE]

I have the 64 bit version

---

### Post by IbeeX on 2006-06-13
[QUOTE=mschievano]I have the 64 bit version[/QUOTE]

Me to ;) Administration -- Printing Add new printer next and then I got Pixima IP4000

only thing is that it dont't work as it should do.

Note:

there is offical Canon driver, I still did't tried it but will one off this days

[http://software.canon-europe.com/software/canon_print_filter_for_linuxs24302.asp](http://software.canon-europe.com/software/canon_print_filter_for_linuxs24302.asp)

Well driver is in rpm :(
so I guess I should try with alien :)

---

### Post by mschievano on 2006-06-18
> **IbeeX]Me to  said:**
> http://software.canon-europe.com/software/canon_print_filter_for_linuxs24302.asp[/url]

Well driver is in rpm :(
so I guess I should try with alien :)

hope canon release in ftp the amd64 driver. This won't work well.
Bye!

---

### Post by michaeljt on 2006-09-03
I added some experimental code to Gutenprint to support the iP4200.  It is currently in CVS but not yet released.  Please feel free to try it out - and comment if anything doesn't work!

---

### Post by angelago on 2006-09-06
Hi 

I have a Canon pixma IP 3000 which has not been printing well under Dapper except to A5 size. However Today (yeaa) I happened across a driver that works for it. It is the one in the printer driver list  BJC 8200. I get full size A4 pages with it. I guess it  might work for the IP 4000 as well. In my list there are two called BJC 8200 - the one I am  using is the first one High Quality image (Gutenbprint) (en).

---

### Post by michaeljt on 2006-09-08
How well does it work?  Perfectly?  Most or some functions?  You might want to report it on the Gutenprint bugtracker ([http://sourceforge.net/tracker/?group_id=1537&atid=101537)](http://sourceforge.net/tracker/?group_id=1537&atid=101537)).  The thing is that Canon actually only seem to use three or four different command sets for their printers, so that when they release a new printer they use an old command set and add a few functions.  So often you can find another driver that more or less works.

The iP4000 does have a working driver, and hopefully my iP4200 will be OK too.

---

### Post by michaeljt on 2006-09-08
Sorry, don't bother.  Gutenprint (at least the CVS version) already has a driver for the iP3000.

---

