---
title: "Wireless in 64 bit Linux"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by velocity303 on 2006-06-01
Hey everyone,

Ive been itching to use 64 bit linux, but since I depend on wireless internet I havent been able to go through with the transition to 64 bit. I'm willing to buy a wireless adapter with 64bit drivers, but the problem is I dont know where to start looking for one that has 64 bit drivers, since they seem to be quite rare at this point. If anyone is using 64 bit and wireless internet can they recommend any pci adapters for a desktop. Thanks for your help!

---

### Post by praxxus on 2006-06-01
I'm using a Linksys WMP54G (v.4) that uses the Ralink RT2500 chipset. Haven't tried getting WPA to work but using 128bit WEP encryption it connects just fine to my wireless home network. Never could get it to work in Suse but Dapper 64bit picked it up automatically.

---

### Post by Jason_25 on 2006-06-01
Pretty much all the cards that work in 32-bit work on 64-bit with the native driver.  I don't know about ndiswrapper.

I have a Netgear WG311T wireless G that works fine and so does a Netgear MA311 wireless B card.  Both PCI.

---

### Post by Jonathan987 on 2006-06-01
do they work with WPA(WiFi Protected Access)?

---

### Post by Jason_25 on 2006-06-01
The WG311T works fine and is fast with WPA with no dropouts.  I haven't tried the MA311 with WPA, just WEP.

---

### Post by velocity303 on 2006-06-03
Thanks a ton guys, im glad to hear success stories with wireless in 64 bit, they seem rare these days. :)

---

### Post by ikin on 2006-06-03
is there a problem with the 64 bit version of ndiswrapper?

because my wifi ain't working (check other topic, SMC2802 v2 probs...)
but if there are problems, i might consider putting a 32 bit distro on my system... if that would help out the problems ofcourse...

---

### Post by danshirah on 2006-06-03
If one needs another suggestion I too had difficulty using Ubuntu Breezy x64 because of my dependency on wireless.  I have a WG111v2 adapter from netgear.  At the time there was a 64 bit driver for windows but I could not for the life of me get it working under ndiswrapper, something about a reference to an .exe file.  I downloaded the new 64 bit version with a hope and a prayer, and much to my surprise, my adapter worked "out of the box", although it did involve a little network configuration under ubuntu (no big deal).  Seems to be working perfectly, although now I'm fighting a whole other battle (the bittorrent thread).  Hope this helps. :)

---

### Post by cemptor on 2006-08-10
Would any wireless adapter with the Ralink RT2500 chipset work under Dapper 64 with native Linux drivers? I see a bunch of devices with that chipset that are more reasonable than the Linksys or Netgear

---

### Post by AIysandra on 2006-08-11
i'm using a gigabyte wpkg wireless pci card.. works juz fine.. however my netgear card n my d-link cards both dont work..

i believe it may have to do with ur system as well, coz i'm using a AMD64 gigabyte mainboard...
:KS

---

### Post by henrismail on 2006-10-03
> **danshirah said:**
> If one needs another suggestion I too had difficulty using Ubuntu Breezy x64 because of my dependency on wireless.  I have a WG111v2 adapter from netgear.  At the time there was a 64 bit driver for windows but I could not for the life of me get it working under ndiswrapper, something about a reference to an .exe file.  I downloaded the new 64 bit version with a hope and a prayer, and much to my surprise, my adapter worked "out of the box", although it did involve a little network configuration under ubuntu (no big deal).  Seems to be working perfectly, although now I'm fighting a whole other battle (the bittorrent thread).  Hope this helps. :)

Realy on my amd64x2 it works then crashes the kernel or
slows down to a crawl.

---

### Post by noeldescallar on 2006-10-04
Try DLINK DWL-G510 or G520+ with 128bit WEP key set in your router.
What we are using is G510, it's working fine, just plug and play with our 64bith sempron using ubuntu 64bit.

---

### Post by vgrisham on 2006-11-14
> **praxxus said:**
> I'm using a Linksys WMP54G (v.4) that uses the Ralink RT2500 chipset. Haven't tried getting WPA to work but using 128bit WEP encryption it connects just fine to my wireless home network. Never could get it to work in Suse but Dapper 64bit picked it up automatically.

Do you happen to have access to the full model number for your WMP54G? I have the broadcom version, and it won't work in 64 bit XP (so I'm assuming that eliminates it in Ubu 64 as well). I'm trying to find the Ralink chipset version, but that stuff isn't exactly advertised.

Thanks!

---

### Post by RAOF on 2006-11-14
> **vgrisham said:**
> ...I have the broadcom version, and it won't work in 64 bit XP (so I'm assuming that eliminates it in Ubu 64 as well). ...

Actually, no.  That just means Broadcom haven't bothered releasing 64bit drivers for windows.  The linux drivers are exactly the same, 32bit or 64bit, so if it works out of the box in 32bit Ubuntu it should work out of the box in 64bit Ubuntu.  If it uses the same chipset as the other guy's, it should work just the same.

---

### Post by John Jason Jordan on 2006-11-15
> **RAOF said:**
> Actually, no.  That just means Broadcom haven't bothered releasing 64bit drivers for windows.  The linux drivers are exactly the same, 32bit or 64bit, so if it works out of the box in 32bit Ubuntu it should work out of the box in 64bit Ubuntu.  If it uses the same chipset as the other guy's, it should work just the same.
I have a Broadcom 4306 in my Compaq laptop and I use a 64-bit Windows driver with ndiswrapper. Got the 64-bit Windows driver from Linuxant, but it is available on other sites as well. I don't know who created the 64-bit Windows driver, but it does exist. Also don't know about 64-bit drivers for other models.

---

