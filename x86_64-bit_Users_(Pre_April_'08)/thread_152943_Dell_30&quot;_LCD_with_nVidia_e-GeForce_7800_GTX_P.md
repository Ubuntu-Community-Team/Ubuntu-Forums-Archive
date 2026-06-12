---
title: "Dell 30&quot; LCD with nVidia e-GeForce 7800 GTX PCIe under 64-bit Ubuntu?"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-03-30
Can it be done?

Starting to work on building myself a new desktop, but I'm still a pretty big n00b at Linux. I have Ubuntu-64 Breezy on my AMD-64 laptop and I love it. I use the nVidia driver for the 15.4" widescreen display at 1680 x 1050 and it is awesome. I want to replace my Windows 2000 desktop with a new Linux desktop, which will be used for serious DTP work, and I want an even more impressive display. This sytem will be used for no gaming at all. I will use mostly Scribus and Adobe InDesign under Crossover Office, plus the usual additional stuff -- OpenOffice.org, the GIMP, etc.

The Dell 3007 WFP 30" widescreen monitor does natively 2560 x 1600 resolution, and that is what I want. According to Dell the input is DVI-D TMDS, whatever that means. I think it requires a dual video card. However, on the same page where Dell lists the monitor for sale they also offer three video cards which (presumably) will drive the monitor to 2560 x 1600, all of which are the 7800 series. The most expensive is the e-GeForce 7800 GTX 256 MB GDDR3 PCIe Evga card. 

It's hard to find information on the net about the possibility of setting this up under Linux because there are practically no Linux users willing to spend $2,000 on a monitor, let alone Linux users who do DTP work. However, there should be some gamers out there who are running this setup. I don't need 3D, but the rest of the capabilities of this card and monitor should be documented someplace. I can't find any clear statements on nVidia's site. Also, part of the problem is that I haven't put together a new computer for several years and I don't understand current terminology. Like, I have little idea what "DVI-D" means, or "TMDS" or what PCIe is.

So is there anyone using the Dell 30" widescreen monitor at 2560 x 1600 under Ubuntu-64? Can it be done? If so, how well does it work? TIA for any pointers.

---

### Post by skylark on 2006-03-31
Yeah, it is hard to find info on stuff like this and the landscape changes very quickly.

I've got a 24" Dell but the 30" is another beast because of it's very high resolution.

Basically you can use a single card, but you need to make sure it has "dual-link DVI" or else you won't be able to drive the panel at it's full resolution. Dual-link DVI simply refers to the type of DVI connection - only reasonably high-end/new cards support it properly (although this is probably changing).

See [http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface) for definitions of the terms you mentioned. And PCIe stands for PCI-express ([http://en.wikipedia.org/wiki/PCI_Express](http://en.wikipedia.org/wiki/PCI_Express)) which is the new high-speed PCI. Basically new video cards plug into PCIe slots instead of AGP slots.

Overall I expect Ubuntu on AMD64 + suitable Nvidia video card + 30" panel should work fine. Just make sure dual-link DVI output (2560 x 1600 @ 60Hz) is supported by the Linux video drivers for whatever card you choose. Hopefully someone here is running with such a setup and can verify all this.

---

### Post by 5hundy on 2006-04-27
My plan is to get a 3007WFP in a couple of months so I don't have any personal experiences to share but I can point you to a couple of sites I found:

The gentoo wiki has an [article on the apple cinema display]("http://gentoo-wiki.com/HARDWARE_Apple_30%22_Cinema_Display") which explains a few things.

It looks like [this dude]("http://xusia.net/") got the 3007wfp working in fedora.

I personally don't care much about gaming (all I play is warcraft TFT), I just want to have a freakin huge desktop. My plan is to get a 7600GT or something a little less new that still supports dual-link DVI. I've been looking at manuf. websites and reading through the tech specs to make sure the cards I'm looking at actually have dual-link and say they do 2560x1600. So far it looks like some of the xfx 7600GT cards do. Some specs are confusing though because they say the max resolution is <2560x1600 and yet the support dual-link... if anyone can shed some light on this or say "I have it working", that would be great.

---

### Post by John Jason Jordan on 2006-04-27
[QUOTE=5hundy]My plan is to get a 3007WFP in a couple of months so I don't have any personal experiences to share but I can point you to a couple of sites I found ... <snip>[/QUOTE]
Since posting my original question I found someone on a local Linux e-list who has the 3007 running under 64-bit Linux. Here is what he said [note the number of >s, the first part is from him (>>>), then my response (>>), then his final response (>)]:

```
>>>I have a Dell 30" 2560x1600 attached to an eVGA 7800GT
>>>(one dual-link DVI, one single-link DVI) and it is a joy to behold.

>>Dude!! I love you!!
>>
>>Wait ... maybe not.
>>
>>OK, what you have is what I am dreaming of. 
>>
>>So tell me more about the dual Opteron motherboard and stuff. I was
>>thinking of going with a single dual-core AMD-64, probably a couple
>>steps below cutting edge, as CPU speed is probably not that big a
>>deal to me. At the same time, I want a pretty fast hard disk. Plus I
>>want the rest of the goodies -- a couple DVD+_RW drives, and maybe
>>even a TV tuner. Standard 10/100 ethernet is all I need and
>>otherrwise nothing special. Do you recommend the Suptermicro
>>motherboard, and if so, which one?
>>
>>Also, which distro are you using, and is it the 64-bit version?
>>
>>And do you have any other words of advice?

>System under discussion:
>
>Supermicro AW4020C composed of Supermicro H8DCE dual Opteron
>motherboard and Supermicro 645 rack/tower case with temp controlled
>case/mb/PS fans and 8-SATA hot-swap bays. Areca 1220 PCIe 8-port SATA
>HW RAID controller eVGA 7800 GT KO video card Pioneer 110D DVD DL/RW
>Hauppgauge PVR550 dual TV tuner Creative Audigy 2Z (includes firewire
>port "missing" from MB)

>Getting this system up and running has been a real PITA.  Mostly due
>to bad vendor experience exacerbated by bad or misleading
>compatibility/driver information.

>I purchased the Supermicro AW4020C barebones system (which contains
>Supermicro H8DCE motherboard), (2) 246 Opterons, and (4) 1G OCZ ECC
>PC3200 RAM  from Monarch Computers.  I purchased as "parts" because
>Monarch could not build the system with the parts I wanted.  I
>purchased the rest of the components from TigerDirect, Newegg,
>Directron, and QuietPC.  I prefer to keep the vendor count down but,
>in this case, no one could provide all the components.  For example, I
>wanted the eVGA 7800 GT (to get dual-link DVI) but only TigerDirect
>had them in stock.  I purchased my fanless CPU coolers from QuietPC
>because they were, and always have been, very helpful in determining
>what would or would not work in the system.

>I now, personally, consider Monarch Computer my "vendor of last 
>resort".  There service and support was so bad I would only purchase
>something from them if I could not get it ANY PLACE else.  They are
>supposedly OEM for the Supermicro products but were totally unable to
>provide support.  I had a problem which turned out to be a bad
>motherboard; I sent the system back; after waiting the alloted time
>for it's return it took me days just to get someone to answer the
>phone where upon they just shipped the system back without fixing it
>(not sure they even looked at it).
>
>Once I contacted Supermicro and pleaded for direct support (which they
>readily granted) things were diagnosed and fixed very quickly.  They
>cross-shipped a new motherboard FedEx and things were moving on.
>
>Which got things working enough to discover the (5) Samsung 2504C 250G
>SATA drives I purchased have a bug in their implementation of SATA-II
>features and can not be detected by the Areca RAID.  This is a
>known/fixed problem but requires drives with newer/upgraded firmware. 
>It took me weeks, and several calls to the Samsung national sales
>manager to receive firware upgrade software which immediately rendered
>the drive dead.  More calls to the national sales manager and I
>received (5) new drives ALL with the outdated firware.  I gave up on
>the Samsung drives.
>
>The Seagate 7200.9 500G drives now in the machine work just great.
>
>Unfortunately, they only work attached directly to the mother board
>nForce SATA ports.  I could install onto the Areca based RAID array
>using SuSE 10.0 or Ubuntu 5.10 BUT both exhibited such instability (I
>think related to, then current, AMD64/nvidia problems) that I could
>not use the system.  I switched to Debian (which I use on a couple
>other systems) and now have a very stable system.  Unfortunately, the
>Areca driver is not included in the Debian kernels (not even the
>newest ones).  There are sarge install variants available which
>include the Areca driver but as soon as you upgrade your kernel you
>loose the Areca.  Bottom line -- Areca and Debian only work if you are
>into building you own kernel/drivers.
>
>TigerDirect, Newegg, Directron, Dell, and especially QuietPC were all
>very, very good to deal with.
>
>Now, having listened to my home movie, let me say my plans for the
>next system.
>
>1) I will not buy another RAID card unless I KNOW it is supported in
>the standard kernel.  It is just too much ongoing pain and hassle if
>you're just trying to maintain/use the machine.  Every time I have
>been swayed to buy the newer/better/shinier SCSI, RAID, whatever it
>has not been cost-effective to get the thing working and maintain it.
>The safest is 3ware which is well supported in most distributions and
>has been for some time. 
>
>2) I will probably buy the Tyan motherboard next time (eg. 2895).  The
>Supermicro people have been very good when I have a bad component but
>there are very few forums or other resources available to get help. 
>Supermicro's Opteron products are kind of their quiet secret and just
>not nearly as widely/publically supported as the Tyan boards are.
>
>3) I would highly recommend the Hauppgauge PVR 150/250/350/550 cards. 
>Not only are they good products but they seem to be the best supported
>(eg. in MythTV project, etc.).
>
>4) For desktop/workstation system I would probably, at this point, go
>with a AMD64 X2 solution using a DFI, MSI, or Tyan motherboard.  The
>system above needed to include a large disk array and will eventually
>migrate into primarily server role so I went with the more expensive
>"server" hardware.  Probably overkill the desktop/workstation use.
>
>5) Get the Apple or Dell 30"; it is "sell a body part" worth it (at
>least for the development / graphics work I do).  At least make sure
>you get a dual-link DVI card so you can support a 30" (2560x1600) or
>24" (1920x1200) when you finally get paid for all those blood
>donations :)
>
>6) If you install AMD64 version (esp of Debian) you will need to set
>up a 32-bit chroot environment;  it turned out to be a lot simpler to
>set up than it appeared at first blush and works quite well.
>
>Hope that is not too longwinded...
```
I hope that helps some.

I plan to wait until early July. My reason is because I want Dapper Final on it, plus I am in classes until mid-June and don't need another project right now. But I'm taking the summer off from school, so I will have time to fiddle with it and get it all perfect by the time fall term starts. OK, that's the plan anyway. :)

---

### Post by mcglothi on 2006-06-22
I just wanted to add my experience to the thread...

I'm fairly new to Ubuntu, but not to Linux.  I recently installed Ubuntu on my personal workstation.  I have an Nvidia 7800GT running an Apple 30" cinema display (same rez as your Dell 3007).  

Note:  I used the 32-bit version of Ubuntu, but this should work with the 64-bit version as well (not sure about that though with the nvidia drivers) Here is how I got mine working (it was very easy):

1. Install ubuntu (6.06 in my case)

2. Get and install Automatix 
        - I followed this guide: [http://ubuntuforums.org/showthread.php?t=190025&highlight=automatix]("http://ubuntuforums.org/showthread.php?t=190025&highlight=automatix")

3. Get Nvidia drivers from the Automatix package manager

4. Open a terminal window

5. Backup your xorg.conf file
        [HTML]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup[/HTML]

6. Edit xorg.conf to add 2560x1600 resolution
        [HTML]sudo nano -w /etx/X11/xorg.conf[/HTML]
- search for 'Section "Screen" '
- edit the lines that say 
                  [HTML] Modes     "1280x800" [/HTML] 
   to read:
                  [HTML] Modes      "2560x1600" "1280x800"[/HTML]

(you could probably just omit the 1280x800 modes but I left them in just in case)

7. Save the xorg.conf file (ctrl-o if your using nano)

8. Log off

9. Restart the X server (ctrl-alt-backspace)

10. Done!

It worked for me just like that, but this is the only machine I have put linux on with this monitor so YMMV.

Hope this helps!!

-Tim

---

