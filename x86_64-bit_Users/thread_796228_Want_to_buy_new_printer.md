---
title: "Want to buy new printer"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by captainzott on 2008-05-16
Hi
would appreciate comments on the choice of a new printer
I am running 64 bit Hardy and so far have managed to get everything working, with a bit of messing around,(sound, screen 1650 x 1250 wide screen, wireless, wireless keyboard/mouse etc) and am grateful to this forum for all advice. 
The one thing I just cannot get working is my Cannon i250 printer - but as it is getting on a bit, I thought I'd buy a new one.
I'm looking for one of those 'all in one' types, (print and scanner),and I thought I'd go for a HP, as they seem to have the best Linux support.
Comments/recommendations will be gratefully considered, (I don't do loads of printing so I'm looking sub £100).
Thanks

---

### Post by Sef on 2008-05-16
HP is about the best printer you can buy that will work with GNU/Linux.  Click [here]("http://hplip.sourceforge.net/supported_devices/index.html") to see if the printer you want will work with Ubuntu.  (They almost all will.)

---

### Post by darco on 2008-05-16
The HP OJ5610 should fit the bill. I purchased it recently and it works great. The scanner option is very important to me and it works like a champ. The only negative is it seems so rough when it shuts down.
good luck
darco

---

### Post by Kilz on 2008-05-16
I agree that HP probably has the best support, I have never had a problem with HP. But a close second would be an Epson, my brother has a CX-3800 that was real easy to setup. [You might also want to look here]("http://www.sane-project.org/sane-mfgs.html") to make sure there is a sane backend for the scanner part of the all in one.

---

### Post by Kilz on 2008-05-16
I agree that HP probably has the best support, I have never had a problem with HP. But a close second would be an Epson, my brother has a CX-3800 that was real easy to setup. [You might also want to look here]("http://www.sane-project.org/sane-mfgs.html") to make sure there is a sane backend for the scanner part of the all in one.
A good rule of thumb to remember is run away from lexmark!

---

### Post by cjazz on 2008-05-16
> **Kilz said:**
> 
A good rule of thumb to remember is run away from lexmark!


Amen to that. You may also want to look [here]("http://www.linux-foundation.org/en/OpenPrinting") for a broad look at how printers across all brands work with Linux.

---

### Post by fjgaude on 2008-05-16
HP or Epson seem to have full support from my experience... Most Canon models are not on the CUPS list.

---

### Post by Sef on 2008-05-17
> HP or Epson seem to have full support from my experience

HP or Epson?

From [OpenPrinting's Suggested Printers]("http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters"):

>  Which to buy?

By way of comparison, the Gutenprint Epson driver uses better dithering techniques and produces very good color quality on printers for which it has mature support. Basic color tuning adjustments are fairly flexible in Gimp-Print, and an improved color model with full-blown profile support is being planned. HP's driver offers less advanced dithering techniques and fewer adjustments, but with fairly uniform color quality across all the printers it supports.
HP devices generally use integrated ink-and-printhead cartridges; these are a clear plus if you print in clog-inducing ways (ie very infrequently, or in dusty environments). OTOH, if you do clog, with the HPs you had to use awkward button presses to run a clean or test cycle, currently you can initiate the cleaning cycles by simple mouse clicks in the HP Toolbox of HPLIP. On HP's multi-function devices with alpha-numeric display you can also use front panel menues to clean and check the nozzles.
Epson printers has permanent piezo nozzles. As you cannot change them the printer will get unusable if it is so heavily clogged that the printer-internal cleaning mechanisms do not work any more. To initiate the nozzle cleaning Gimp-Print includes command-line-based cleaning/loading/testing software and an alternative software with graphical user interface is available: MTink. Furthermore, for many Epsons alternative special-purpose inks are available (archival, greyscale, altered gamuts, etc), as well as more options for refilling and continuous-feed systems. In most cases, the Epson arrangement is better; at the cost of some simple regular maintenance you get a more flexible and capable device.
Epson devices generally produce better photo output; this is especially true when using the Gimp-Print driver. HP devices are generally held to produce better text output, although with the latest models, Epson has caught up to HP's text abilities. 

---

### Post by cotcot on 2008-05-17
I bought an Epson after having compared the ink cartridge cost of HP and Epson. HP ink cartridges are expensive (not only because of the included print head).
After some 10 changes you will have spent much more money with HP compared to EPSON than the value of the printer itself. 
I run the epson in 64 bit with gutenprint. The printer worked out of the box, but not with correct colors. Hardy chosed the 'simplified' driver of my printer type. I changed it to the full driver (easy to do with cups) and adjusted the color settings (with cups as well). It is working fine.
The EPSON native drivers (see [[COLOR="Red"]here[/COLOR]]("http://avasys.jp/hp/menu000000500/hpg000000442.htm")) are 32 bit only. If you use one of these then choose a printer type for wich the website has a pips-driver. The pipslite-driver is poor in features. (it was a mistake I made).

---

### Post by inphektion on 2008-05-17
I got a huge corp Canon ImagePass H1 printer working by providing it with the windows .ppd file from the windows driver.  Works flawlessly.  why can't you do this with any printer?

---

### Post by Sef on 2008-05-17
> The EPSON native drivers (see here) are 32 bit only.

Some of us run 64-bit systems.  HPLIP works out-of-the-box on 64-bit systems.

---

### Post by Kilz on 2008-05-17
> **Sef said:**
> Some of us run 64-bit systems.  HPLIP works out-of-the-box on 64-bit systems.

Yes, most drivers from manufacturers are only 32bit. But the drivers that come with cups will be 64bit.

---

### Post by badrunner on 2008-05-18
> **inphektion said:**
> I got a huge corp Canon ImagePass H1 printer working by providing it with the windows .ppd file from the windows driver.  Works flawlessly.  why can't you do this with any printer?

You often can, but not all printers have ppd drivers. High end printers almost all do, but there are quite a few dirt cheap printers with terrible quality windows only drivers.

Like said previously, at the prices being talked about here, HP is definately the way to go.

---

### Post by Sef on 2008-05-19
>  Originally Posted by inphektion  View Post
I got a huge corp Canon ImagePass H1 printer working by providing it with the windows .ppd file from the windows driver. Works flawlessly. why can't you do this with any printer?

Often corporate printers can run on GNU/Linux, e.g., Lexmark consumer printers do not usually work with GNU/Linux, while the corporate ones (Opterons) will work with it.

---

### Post by pixel :-) on 2008-05-21
I'll just add that HP is ok.Don't see just the price of the printer but also the price of the cardriges,they can get preaty expensive.Just in case maybe you will prefer a USB printer,in the worst case, it will work with windows inside virtuallbox.

---

### Post by wdaniels on 2008-05-21
+1 for HP

---

### Post by insane_alien on 2008-05-21
epson printers have always treated me well when used with linux.

---

### Post by mudlogger on 2008-05-21
We just bought a Brother HL-5240 laser and it is recongnized instantly and works great.

---

### Post by JoshLukas on 2008-05-21
My Brother HL-2070N works out of the box with ubuntu 7.04/7.10 and 8.04 in its 64bit version. Connected via ethernet using hl1250 pxlmono. For color printing the HP D1460 works fine for me.


Josh

---

### Post by aikishugyo on 2008-05-22
I've spent the better part of my time in Japan fighting to get inkjet printers to work with linux. The best support I ever got was from the gutenprint team (inkjet support primary), helping me get my Epson and Canon inkjet printers supported to the best of the open-source capability; and, of course, lest it not be obvious, a massive ZERO help from printer companies in Japan. The results:
[LIST]
[*] open-source drivers for Canon only give 600dpi, making them useless for the photo applications that most people seem to use inkjets for. Thus, Canon inkjets are a dead end for linux use;
[*]Epson open source drivers seem to be excellent, and my PM670C from around 1998 or so does wonderful photo printing at 1440x720dpi (just showing off!). Epson drivers give full support to the highest resolutions (see latest gutenprint documentation and the gimp-print/gutenprint ML), as well as to edgeless printing. Thumbs up to Epson!
[*]HP gives support to its own range, although I don't see the quality approaching what Epson (or Canon, with Win and Mac drivers) can do, and in Japan HP only has like three models for sale, none top of the range and therefore all far less capable than the current Epsons and Canons (quel surprise...);
[*]lately, I have looked at low-end lasers. I have remarkably good experience with Brother: not only does this company provide excellent drivers for linux from its website, it also has a great range of low-end (even network-capable) monochrome laser printers, far better than anything that Canon or other companies I have looked at can provide.
[/LIST]
Conclusion: for inkjet, go Epson (or HP if you can find a good one); for monochrome laser, go Brother. 

For color lasers I have no recommendations.

HTH,
Gernot

---

### Post by FrankVdb on 2008-06-01
That's nice! 

I love my five year-old Canon S9000 large format photo printer but there are no Linux drivers for it. There is something like TurboPrint but I refuse to fork out 30 euros for a driver... My cameras are Canon but I won't be buying any of their printers anymore.

Would you mind explaining what you did with the ppd file?

---

### Post by jazzman65 on 2008-06-01
I use an HP Photosmart C5280 All-in-One and it works just fine.

---

