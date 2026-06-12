---
title: "A modest proposal for Ux64"
date: 2007-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by nss0000 on 2007-09-08
BigK:

Having recently saved $20 when an overly flush galpal paid for lunch I propose the following solution to UBUNTUx64 development woes. 

Each of the 5000 Ux64 lusrs on this n.g. each contribute $20 to BUY one of Shuttleworths' programmers for a year. (S)he to work strictly on Ux64 code. Set up an account -- mail in the checks. Among us there must be one accountant and one lawyer to handle the details.  

That $20 will be a business tax-deduction for most of us.

---

### Post by David A Knight on 2007-09-08
What woes?  The only things that don't work are closed source such as flash, which can be made to work with a simple 32bit firefox or the hack nspluginwrapper if you can't live without it.  Other non plugin 32bit apps work fine so long as you have the necessary 32bit libraries installed.

---

### Post by kansei on 2007-09-08
"the only things that don't work" is such a definitive claim, don't make one of those unless you're absolutely sure (and in a complicated world such as ubuntu packages and such, no one is absolutely sure).

here's some things that don't work in 64-bit yet:

--i8k kernel module and utils --needed for sensors and FAN CONTROL with Dell laptops (old ones as well as all current models). This is pretty critical seeing as how popular dell laptops are. Dells are infernos running 64-bit, even just at idle with the cores at their lowest speed. The fan just sits at the lowest fan speed (inaudible). Run 'stress' for less than a minute and BAM core temps hit 72C, fan still barely doing anything.

--config_no_hz in the ubuntu 64-bit kernel. I know is is in the gutsy kernel for 32-bit, but I'm on 64-bit and it seems as though it isn't. Yet another very useful thing for laptop users as it allows decent sleep times.

---

### Post by John.Michael.Kane on 2007-09-08
> **kansei said:**
> "the only things that don't work" is such a definitive claim, don't make one of those unless you're absolutely sure (and in a complicated world such as ubuntu packages and such, no one is absolutely sure).

here's some things that don't work in 64-bit yet:

--i8k kernel module and utils --needed for sensors and FAN CONTROL with Dell laptops (old ones as well as all current models). This is pretty critical seeing as how popular dell laptops are. Dells are infernos running 64-bit, even just at idle with the cores at their lowest speed. The fan just sits at the lowest fan speed (inaudible). Run 'stress' for less than a minute and BAM core temps hit 72C, fan still barely doing anything.

--config_no_hz in the ubuntu 64-bit kernel. I know is is in the gutsy kernel for 32-bit, but I'm on 64-bit and it seems as though it isn't. Yet another very useful thing for laptop users as it allows decent sleep times.

And you have filed bug reports on both problems correct. 


Also when posting stating something does not work. You should include the respective bug reports on the issues, As that would allow anyone else who has those issues to add  info to it or to validate the issue can be replicated.

---

### Post by David A Knight on 2007-09-08
> **kansei said:**
> "the only things that don't work" is such a definitive claim, don't make one of those unless you're absolutely sure (and in a complicated world such as ubuntu packages and such, no one is absolutely sure).

here's some things that don't work in 64-bit yet:

--i8k kernel module and utils --needed for sensors and FAN CONTROL with Dell laptops (old ones as well as all current models). This is pretty critical seeing as how popular dell laptops are. Dells are infernos running 64-bit, even just at idle with the cores at their lowest speed. The fan just sits at the lowest fan speed (inaudible). Run 'stress' for less than a minute and BAM core temps hit 72C, fan still barely doing anything.

--config_no_hz in the ubuntu 64-bit kernel. I know is is in the gutsy kernel for 32-bit, but I'm on 64-bit and it seems as though it isn't. Yet another very useful thing for laptop users as it allows decent sleep times.

config_no_hz isn't even in the mainline x64 kernel (from linus or in ubuntu), the patches are there and seem to work fine for most people.  From my experience it didn't improve battery life very much, although the number of wake ups did drop significantly when the machine was idle.  Either way it isn't present so isn't something that isn't workng.

As for i8k module, for old dells 64bit is irrelevant anyway.  72C isn't that hot, my non dell laptop can hit 70C when both cores are being worked hard which surely 'stress' is doing.   This isn't really a generic x64 problem, but a dell problem.

Other non 64bit systems suffer a similar problem due to lack of specs for hardware, for instance the very large thread for vaio laptops.

---

### Post by kansei on 2007-09-08
> **SD-Plissken said:**
> And you have filed bug reports on both problems correct.

no, but I am subscribed to both of the respective bug reports (were already made long ago) and added my comments where applicable.

72C with 0 gpu stress (GDM not even running) is a little ridiculous. But yeah, I guess since the laptop didn't self destruct (people *have* had this model die from extreme temps when taxing the quadro card and cpu at the same time), it's not an issue that there is 0 fan control >_<

and yes I do hate dell for doing none of this crap in hardware. I only use it because it was given to me and should be a decent bit faster than my thinkpad T42 (2.0ghz dothan 2gb ram vs 2.0ghz core2 2gb faster ram 64-bit)

---

### Post by Em-Buntu on 2007-09-08
> **nss0000 said:**
> BigK:

Having recently saved $20 when an overly flush galpal paid for lunch I propose the following solution to UBUNTUx64 development woes. 

Each of the 5000 Ux64 lusrs on this n.g. each contribute $20 to BUY one of Shuttleworths' programmers for a year. (S)he to work strictly on Ux64 code. Set up an account -- mail in the checks. Among us there must be one accountant and one lawyer to handle the details.  

That $20 will be a business tax-deduction for most of us.

[COLOR="Blue"][SIZE="2"]Sign me up!

First project is to hack ATI's proprietary All-In-Wonder drivers to work in Ubuntu/GPL Media Centers. This would bring millions of the tens of million of ATI all-In-Wonder users over to Ubuntu since they will get no support from AMD/Microsoft in 64-bit land.
[/SIZE][/COLOR]

---

### Post by kansei on 2007-09-08
> **Em-Buntu said:**
> [COLOR="Blue"][SIZE="2"]Sign me up!

First project is to hack ATI's proprietary All-In-Wonder drivers to work in Ubuntu/GPL Media Centers. This would bring millions of the tens of million of ATI all-In-Wonder users over to Ubuntu since they will get no support from AMD/Microsoft in 64-bit land.
[/SIZE][/COLOR]

I've heard reports (but haven't read into them) that AMD/ATI is going to open source their drivers :)

---

### Post by Jouke74 on 2007-09-08
ATI is indeed catching u slowly. See my last post about it...

[http://ubuntuforums.org/showthread.php?t=544267](http://ubuntuforums.org/showthread.php?t=544267)

---

### Post by Em-Buntu on 2007-09-08
> **kansei said:**
> I've heard reports (but haven't read into them) that AMD/ATI is going to open source their drivers :)

This is true. Unfortunately, it doesn't include the proprietary All-In-Wonder Multimedia Center which as you recall, was never Windows Media Center compliant. It appears AMD/ATI has decided to obsolete the All-In-Wonder line and replace it with something new in 2008,  based on their upcoming Fusion line.  It'll have to be really awesome to entice me to buy it. I have $600 worth of All-In-Wonders with no 64-bit support. Neither Windows64 Media Center, VISTA, Sage or Myth TV will see an All-In-Wonder's Tuner and Theater components.  I'll stick with Nvidia or standalone TV tuners in the future.
Great example of how closed proprietary driver hurt consumers.

---

### Post by kansei on 2007-09-08
I used the ATI software back when I had an all-in-wonder, and god I hated that crap. I'm *glad* they aren't open sourcing that crap haha. Drivers so that the tuner and such can be used with Linux are just absolutely necessary.

---

