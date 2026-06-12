---
title: "Wireless! Can It Happen on An Apple G3"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by gconn77 on 2005-12-19
Ok... today I pickup up a Belkin wireless desktop card. I couldn't find anything that specifically said would work with an Apple computer... so I decided to then get the Belkin instead of DLink or Linksys for price... its experimental, so why pay more... UNLESS someone here tells me differently.

Here is what I have:

- [Apple G3 B&W running Ubuntu 5.10]("http://ubuntuforums.org/search.php?searchid=3010783")
- [Belkin Wireless G Router]("http://web.belkin.com/support/download/download.asp?download=F5D7230-4&lang=1&mode=")
- [Belkin Wireless Desktop Card]("http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201522&pcount=&Product_Id=136479")

No support from what I can find for Apple computers or Linux for that matter. Can anyone offer any suggestions? Perhaps there is a card that is proven to work? This is an 802.11g set up here... 

I did attempt to search this forum and had about 2 pages of results... however, there was really nothing that covered the Belkin product or anything specific to my situation. Any help would be totally appreciated. :D

This seems to be very informative:

[B]
[LIST]
[*][Hardware Support Components Wireless Network Cards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")
[*][What Wireless Device Is Right For Me?]("http://ubuntuforums.org/showpost.php?p=542946&postcount=7")
[*][Belkin F5D7000 Info. Source, LinuxQuestions.org]("http://www.linuxquestions.org/hcl/showproduct.php/product/1870/sort/2/cat/128/page/1")
[/LIST]
[/B]

---

### Post by gconn77 on 2005-12-19
Bump :D 

I purchased a Belkin Wireless G Desktop Card #F5D7000 version 4000.

I have actually found some information regarding that... and from what I can tell, at one time the card worked... but they changed chips and the new chip is not compatitable. 

I have searched around for a few hours here... and it appears that this is a very complicated thing to do for a newbie linux user.... even worse for a newbie linux user that installed linux on an Apple computer! LOL!!!

So, I guess what I would like to know is which desktop wireless G card should I purchase that will be the easiest to get functioning on my Apple G3 computer. 

Local purchases can include Wal-mart, Radio Shack, Best Buy, Circuit City.... these are all stores here in town.... I need to get this purchased and installed before Christmas for my daughter....

Sorry for the bump... but I am sure that you can understand that time is a definate factor here! LOL!!!

---

### Post by lubod on 2006-01-04
Sorry I never saw your post before the New Year, I don't browse the forums very frequently. Hence why my posts have an email address at the bottom so people can contact me more directly if need be.

The Belkin F5D7000 is big drama IMHO. 5 different revisions, at least 3 chipsets, pretty sad really. The early ones (so called v1000 and v2000) used Broadcom chips, which in most cases work with OS X, but not Linux, except on Intel/AMD PCs with NDIS Wrapper, software to allow the use of windows drivers in Linux (sadly x86 only!)

Then some later ones (v3000 and v4000) used Ralink chips, if you can verify that yours is one of these then your chances of getting it working are good, the manufacturer has downloadable Linux drivers, but you might well get it working directly with what's installed by Breezy (aka 5.10).

The latest batch (v5000) use Atheros chips, which are also usable in Linux too, I managed to make mine work on a PC (my Ubuntu Mac is a Cube which has no PCI or PC card slots), at least with no encryption in 802.11b mode.  Next up 802.11g with WPA.

The v number is printed on the box and card. So as the Belkin F5D7000 goes, your best bet for Linux is the middle series (v3000 and v4000). In theory the newest one is supposed to be easy too, with the madwifi package from synaptic. The old ones may work in OS X or on a PC using NDIS Wrapper, but so far as I know NDIS Wrapper does not work on PowerPC Linux (something about what it does is specific to x86 code).

---

### Post by deathshadow on 2006-01-05
I've got a F5D7050 that works with the ralink drivers on one of the 333mhz G3 "Blueberry Toilet Seat" iBooks, but I had to use a vanilla kernel (I forget which version) to get it to work.

Big word of warning to most everyone when it comes to certain ralink based cards - they WILL NOT function through an external USB hub on ANY OS. This little detail was driving me nuts as I was unable to get it to work through ANY of the five hubs at my disposal, but it works fine in XP, Linux and OS X if it's directly connected.

*Which is semi-annoying since the original 333mhz iBook only HAS one USB port and I like my logitech trackman marble.*

---

