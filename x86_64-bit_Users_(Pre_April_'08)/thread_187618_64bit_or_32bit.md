---
title: "64bit or 32bit?"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Scorpuk on 2006-06-03
Been playing with breezy badger for a month now for gaming servers and such.

Now looking to go for a remotely controlled video recorder using MythTV, so my question is pretty straight forward:


Will MythTV work on a 64bit version of linux or do I need to install a 32bit version?


Possible spec:

Gigabyte VIA K8M800M MATX
AMD Sempron 2800+ (64bit)
2 x 512Mb 184Pin DIMM PC3200
3 x Maxtor DiamondMax Plus10 300Gb U133
Linksys Wireless-G PCI card (WMP54G-UK)
Still to work out compatability for TV card :-k 
All inside an Aspire X-QPack :)

---

### Post by GrammatonCleric on 2006-06-03
In my opinion?  Unless you *need* the extra registers available to 64bit, say for High Definition encoding, I'd stay with 32bit.


But you know what people say about opinions? =P


Here are the spec's of my MythTV box running  Breezy.

AMD 64 3700+ 
ABIT NF4ST Mainboard
2gig Ram
1 320gig WD HD SATA
1 400gig WD HD SATA
NEC DVDRW 3550A
GeForce 6800 GS 256MB PCI-Express
2 WinTV-PVR-250
Creative Audigy2
Ahanix MCE601 Home Theater PC Case

---

### Post by Scorpuk on 2006-06-03
Tnx for the help.

Also nice specs. 

Making me redecide on small portable case to under the TV case. Just need to make sure my wireless conenction reaches that far. Mainly need that soz I can call into the server and tell it to record something when I'm working away from home. :-D 

:-k

---

### Post by GrammatonCleric on 2006-06-03
I did have an issue with my wireless reaching my Myth box.  What I did to improve the signal was setup a seperate wireless network with directional antennas on both the Myth box and access point. 

Since you mention that you are going to schedule recordings remotely...be sure to install mythweb.  It's a browser based frontend for Mythtv.  Also another hand little app is Hamachi ([http://www.hamachi.cc]("http://www.hamachi.cc")) .  I use it  to schedule shows when I'm at work or away from my house.

Lastly in case you have not found  them  here are a couple of nice how to's for installing MythTV  on Ubuntu....

[http://www.quietglow.com/docs/ubuntumythtv.html]("http://www.quietglow.com/docs/ubuntumythtv.html")

and

[http://www.abarbaccia.com/content/view/13/27/]("http://www.abarbaccia.com/content/view/13/27/")

---

### Post by meng on 2006-06-03
I also have a 64bit processor but prefer to install a 32bit system. I tried 64bit breezy, and other distros too, but it needed too much fiddling. One day 64bit will be easy enough for folks like me, but not today I think.

---

### Post by JoWilly on 2006-06-03
64bit is relatively easy and trouble free if you know your way arround.

But if you're new or if you just want flash/java/wmv to work "out of the" box stay with 32bit.

---

### Post by meng on 2006-06-03
Fingers crossed then that it won't be too long before 64bit is a viable option for me.

---

### Post by JoWilly on 2006-06-03
[QUOTE=meng]Fingers crossed then that it won't be too long before 64bit is a viable option for me.[/QUOTE]

It will for sure.

Actually it only needs a deb with the needed 32bit libs (wmv also needs 32 bit player as libs are in 32, for java and flash there is a wrapper that allows them with a 64bit browser).

If someone would have the time to make such a deb available it would be game for everyone :)

---

### Post by henriquemaia on 2006-06-03
[quote=JoWilly]It will for sure.

Actually it only needs a deb with the needed 32bit libs (wmv also needs 32 bit player as libs are in 32, for java and flash there is a wrapper that allows them with a 64bit browser).

If someone would have the time to make such a deb available it would be game for everyone :)[/quote]

Automatix for 64bit. It will come soon, I hope.

---

### Post by JoWilly on 2006-06-03
[QUOTE=henriquemaia]Automatix for 64bit. It will come soon, I hope.[/QUOTE]

Looking forward to it ;)

---

### Post by Teroedni on 2006-06-03
Ive just tested it out 
Works great

Get it here
[http://www.ubuntuforums.org/showthread.php?t=185604](http://www.ubuntuforums.org/showthread.php?t=185604)

---

### Post by JoWilly on 2006-06-03
[QUOTE=Teroedni]Ive just tested it out 
Works great

Get it here
[http://www.ubuntuforums.org/showthread.php?t=185604](http://www.ubuntuforums.org/showthread.php?t=185604)[/QUOTE]

WOOOOHHOOOWW :mrgreen: :mrgreen: :mrgreen:

---

### Post by Scorpuk on 2006-06-03
Ok so if I'm going for 32 bit version what exactly do I install as it looks as though the 32 bit version is for i386 only.


Anywho looking to change my spec to:

Silverstone SST-LC11
Gigabyte VIA K8M800M Socket 754 MATX Audio / LAN / RAID 
AMD Sempron 2800+ S754 256KB Box Inc Fan 
Crucial 2x512MB 184Pin DIMM PC3200 Unbuffered Non-ECC
Linksys Wireless-G PCI Card 
3 x Maxtor DiamondMax Plus10 300Gb U133 (maybe SATA hmmmm)

:-k

EDIT: heh whats automatix?

---

### Post by JoWilly on 2006-06-03
[QUOTE=Scorpuk]Ok so if I'm going for 32 bit version what exactly do I install as it looks as though the 32 bit version is for i386 only.


Anywho looking to change my spec to:

Silverstone SST-LC11
Gigabyte VIA K8M800M Socket 754 MATX Audio / LAN / RAID 
AMD Sempron 2800+ S754 256KB Box Inc Fan 
Crucial 2x512MB 184Pin DIMM PC3200 Unbuffered Non-ECC
Linksys Wireless-G PCI Card 
3 x Maxtor DiamondMax Plus10 300Gb U133 (maybe SATA hmmmm)

:-k

EDIT: heh whats automatix?[/QUOTE]

for 32 bit, just click on a flash link when it asks you to install the plugin, it will download it automatically.

automatix is an installer for commonly needed apps like dvd,audio,video codecs,players, etc...

---

### Post by Teroedni on 2006-06-03
[QUOTE=Scorpuk]Ok so if I'm going for 32 bit version what exactly do I install as it looks as though the 32 bit version is for i386 only.


Anywho looking to change my spec to:

Silverstone SST-LC11
Gigabyte VIA K8M800M Socket 754 MATX Audio / LAN / RAID 
AMD Sempron 2800+ S754 256KB Box Inc Fan 
Crucial 2x512MB 184Pin DIMM PC3200 Unbuffered Non-ECC
Linksys Wireless-G PCI Card 
3 x Maxtor DiamondMax Plus10 300Gb U133 (maybe SATA hmmmm)

:-k

EDIT: heh whats automatix?[/QUOTE]


I strongly reccomend you to not buy the Via motherboard
The VIA K8M800M is very poor in 3d 



Buy A Nforce 410 Geforce 6100  Motherboard instead
Its not that big Price differenze and the performance differance is Huge;)

I also recomend you too buy a Sata hardrive, since they tend to be faster than Ata:)

---

### Post by Anthem on 2006-06-03
[http://www.ubuntuforums.org/showthread.php?t=185524](http://www.ubuntuforums.org/showthread.php?t=185524)

---

### Post by Scorpuk on 2006-06-04
Ok looking at new specs again: :-k 


[COLOR="Red"]Case[/COLOR]
SilverStone "LASCALA" LC11SM-300 + RC (Silver) Aluminum Front & SECC Body Desktop case + 300W PSU 
 
[COLOR="red"]Motherboard[/COLOR]
Asrock K8NF4G-SATA2 NF 410 MCP, S754, PCI-E (x16), DDR 400, SATA II, SATA RAID, uATX, On Board VGA

[COLOR="red"]Processor[/COLOR]
AMD Sempron 64 2800+ Socket754 , Palermo Core, 1.6GHz , 256KB Cache, Retail  
 
[COLOR="red"]Memory[/COLOR]
1GB (2X512MB) Corsair Value Select, DDR PC3200 (400), 184 Pin, Non-ECC Unbuffered, CAS 2.5

[COLOR="red"]HDD's[/COLOR]
3 x 320 Gb Western Digital WD3200JS Caviar SE, SATA300, 7200 rpm, 8MB Cache, 8.9 ms


So the new problem thrown into the ring is the VFD in the case. Is it easy to set up with 64 bit linux, heck any bit linux, as it comes with windows software only. ](*,)  Something called iMON.


I am also leaning more and more towards 64bit as it should surely be able to cope with mpeg encodeing far better than 32bit? 

As I might want to re-encode the saved data from the DVB card. On that matter does anyone know compatability for the follwing DVB card:

 KWorld 100SS DVB-T PCI Digital TV/HDTV Tuner inc Remote 
 

tnx for all your help so far. :)

---

### Post by GrammatonCleric on 2006-06-04
I'm guessing but I'd bet your are also going to have a CD/DVD/DVDRW in your mythtv box?  Add to your specs a capture card and you might be pushing that 300 PSU a little too hard.

Next, the VFD is pretty easy to get running.  I think I followed this how to to get mine working.

[http://knoppmythwiki.org/index.php?page=ParallelVFDHowTo]("http://knoppmythwiki.org/index.php?page=ParallelVFDHowTo")

If you purchase a capture card that has built-in hardware MPEG encoder, which I believe the   KWorld 100SS does,  you don't need to worry about the cpu encoding the video.  But you may want to go with a better supported capture card.  Pay a little more and save yourself a ton of time trying to get the KWorld working.  I would recommend that you look at a PVR-250, PVR-150, or PVR-350. If you want to convert the mpeg video to say xvid take a look at nuvexport.

[http://www.mythtv.org/wiki/index.php/Nuvexport](http://www.mythtv.org/wiki/index.php/Nuvexport)
 

Now the iMON, it's a universal ir remote control device and I believe that there is a lirc driver for iMON.

---

### Post by Scorpuk on 2006-06-04
doh. Forgot about that. Yeah would be looking at a dvd rewriter too.

I might even add a wireless network card, but still pondering about going for dLAN duo Starter Kit only 14Mbps, but thats guranteed. LAN on mains. :eek: 


Would reducing the number of hard drives reduce the load on the PSU?

As i could probably get away with 500Gb for video storage (prob about 250 hours at 2Gb per hour) using 2 x 320Gb sata drives. 


Really, really think the SST-LC11M is a nice case though. :-D 


Futurewise I could even be looking at 2 capture cards in the machine.


Still not set on which DVB card to go for. :-k

---

### Post by RAOF on 2006-06-04
Video encoding is one of the uses for which x86_64 **is** usefully faster.  Even if you're capture card already has a MPEG encoder on it, it won't do newer codecs like h264 (aka: mpeg4-AVC).  Or Dirac, or...

For DVB compatibility, try [www.linuxtv.org](www.linuxtv.org) :)

---

### Post by GrammatonCleric on 2006-06-05
Scorpuk... you might find the following helpful for figuring out your power supply needs.

[http://www.jscustompcs.com/power_supply/]("http://www.jscustompcs.com/power_supply/")

Yes, reducing the amount of hard drives will help but run thru the calculator above and see for sure.

   Another thing to think about is heat, cooling, and think about where you're going to put your mtytv HTPC.  I know I had to do a little modification to my entertainment center to allow the heat from my HTPC to vent out the back.   I noticed that the SST-LC11M vents to the side and rear.  Make sure that the heat fromt the HTPC has space to dissipate.

---

### Post by Scorpuk on 2006-06-06
Nice website 8) 


Went for the following options:
AMD Athlon Palomino 1500 - 1800
32Mb or less Basic Video card (Will be using onboard video card)
2 x sticks DDR SDRAM
3 x HDD
2 x additional PCI cards
1 x DVD -+RW
2 x USB (just in case)
2 x IEEE-1394 (just in case)
3 x system fans

Max wattage: 289 =D> 


Since I already have a gaming PC I don't see the need for any higher spec on the graphics card front. Mind you its still running XP Pro. :-\" 


As for placing the box it would be in an open TV cabinet/stand with more than adequate venting to rear and I think adequate venting to side.

---

### Post by scifan on 2006-06-16
is there actually a pre-rolled set of mythtv for dapper-64?

or are you basically stuck building your own?

(I'm having seg-fault issue's with the last frontend that I built by hand...)

my media box that I've been running i386 on is:

AMD Venice 3200 (939)
MSI RS482-ILD (ATI X200 chipset)
1gb ddr400
sony dvdrw dual layer
200gb maxtor pata
160gb seagate sata
pvr 500
FX7600 GS w/ 256mb PCI Xpress
nmediapc 200BA w/ 450W kingwin power supply

---

### Post by GrammatonCleric on 2006-06-17
Not that I'm aware of but if you find one please post where you do?

---

### Post by buggzero on 2006-06-17
Just out of curiosity, I'm running an amd64, but for the sake of not knowing what I would need an x64 linux OS just yet, and since I don't use mythtv... Is running i386 Dapper somewhat redundant or getting less out of my system?

---

### Post by Lil_Eagle on 2006-06-17
You could run the i686 kernel.  It would perform better than the 386 build, but there isn't a great gain.  As for the 64 bit, you get the gains in number crunching apps (like ripping CDs and manipulating video).  If you're just surfing the net and doing basic office work, then the 32 bit version would probably be better as there is no flash for 64 bit yet and a lot of websites use that.

Personally I hate flash.  

The only thing I miss by running 64 bit is wine (which I don't really need since my killer windows app won't run in wine) and the ability to play Windows Media 9 files.  Since most of my movies are xVid, it doesn't effect me heavily.  Sometimes people mail me funny videos using that codec and I am forced to forward that to another machine, or reboot into Windows.

The main point is that I bought a 64 bit CPU and I want a 64bit OS.  When I run mp32ogg to convert all my mp3 files to ogg, I'll be thankful.

---

### Post by Timokl on 2006-06-18
I tried the 64 Bit Breezy but changed to 32 Bit. After it's my first real attempt on Linux, this was the right decision for me. However, I keep me informed on 64 Bit -- and when I know my way around Linux better, I will definitely give it another try. 

Timo

---

### Post by RAOF on 2006-06-18
[QUOTE=scifan]is there actually a pre-rolled set of mythtv for dapper-64?
[/QUOTE]
Yes!  My repository: [raof.dyndns.org/falcon](raof.dyndns.org/falcon).  I've been using those packages; they work fine (apart from killing XGL when mythfrontend tries to use XV :()

---

### Post by steabert on 2006-06-18
[QUOTE=Lil_Eagle]When I run mp32ogg to convert all my mp3 files to ogg[/QUOTE]

why would you wan't to do that? can't you play the mp3's?

---

### Post by Lil_Eagle on 2006-06-21
I'm not a big fan of propriatary formats, and while mp3 is sort of open source (ie lame) it's still not free, because the author has patented it and requests royalties.  That is the reason ubuntu doesn't provide support for mp3 files with the distro, although it is quite simple to install the necessary codecs.

I am listening to mp3 files as I type this.  There is no real reason to convert my 18000 mp3 files to ogg.  It all depends on my next car.  If my car stereo can play ogg files, then I will probably re-rip most of my CDs into ogg (ogg is better).  I may or may not convert the files I downloaded.

---

### Post by steabert on 2006-06-22
Well, I have the same issues ( no car though )

Luckily I have enough hard disk space to spare to keep all ripped cd's as flac.
So If my next audio system supports ogg, I don't have to rerip the bunch :D

---

