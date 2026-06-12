---
title: "Jaunty 64 bit and Atheros Wireless"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by TheLastTimTam on 2009-05-03
I've tried everything I can find. I upgraded to Jaunty last night, after beating my head against a brick wall trying to get Intrepid to find my wireless networks -- nothing has worked so far. Apparently it's recognizing that I have a wireless card, but nothing comes up in wicd when I look for wireless networks.

I've tried going through the madwifi tutorial, I had ndiswrapper installed from when I was trying to work it out in intrepid, I've probably done something incredibly wrong and the answer is staring me in the face - I'm trying to dump Vista, this is my first attempt at using Linux. Not going very well...

I have an Atheros AR5007EG wireless card, in a Toshiba Satellite A210, running Jaunty 64bit. Any help?

---

### Post by Fir3chi3f on 2009-05-03
I've got the same wireless card on the Toshiba Satellite A215-S4747

Jaunty actually worked out of the box for me, make sure ath5k_pci is installed. 

in a terminal copy and past this in: 
```

modprobe -l | grep ath5k
```

Output should read:

```
kernel/drivers/net/wireless/ath5k/ath5k.ko
```

edit: I did a clean install of Jaunty. If you did the upgrade method it may have left previous settings as they were (ie left ath5k out)

---

### Post by Mark69 on 2009-05-03
Hi TimTam....i had the same issues with a different laptop and had read alot of forums regarding he same wi-fi card my only sollution was to replace the card for an Intel 3945ABG Mini PCI Wireless Adaptor and after that all is working perfect. Maybe find one on ebay there very cheap but it may invalidate your warranty.
Hope this may point you into the right direction

---

### Post by TheLastTimTam on 2009-05-04
Hey! I'm baaaaaaaaack.. and posting from my wireless!

Solution: Clean install of Jaunty... worked right out of the box. I am.. incredibly happy. Fantastic signal and everything. Cheers!

---

### Post by Atrophy on 2009-05-06
I'm having the same problem... although after upgrading to 9.04 there are many things that work much better than in 8.10. I'm sceptical though of doing a clean install because of this. Can anyone shed some light on what exactly may have changed on TimTams computer that caused the wireless to work? Theoretically there has to be something that can be done with out having to reinstall. I do have all the same files and (hopefully) components of an operating system as anyone else that has upgraded, no?

---

### Post by Fir3chi3f on 2009-05-06
This is just what I was thinking-

When upgrading to 9.04 it tries to use your old settings and your old ndiswrapper with windows driver setup. Were clean install wouldn't take your old settings and just install ath5k

You might be able to try to remove your old madwifi/ndiswrapper and then install/reinstall ath5k

---

