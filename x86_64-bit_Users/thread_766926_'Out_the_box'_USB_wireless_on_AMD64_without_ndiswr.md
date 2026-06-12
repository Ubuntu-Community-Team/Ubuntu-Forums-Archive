---
title: "'Out the box' USB wireless on AMD64 without ndiswrapper/tweaked drivers"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by usernamed on 2008-04-25
Hi All,

I have a Belkin USB 54g Wireless Adapter that, needless to say, has proven to be Ubuntu proof.

However, I've decided I'm going to find a USB 54g adapter that really works (supporting WPA/WPA2 and not needing ndiswrapper or tweaked drivers) out of the box.

Looking at the hardware compatibility list, it seems that the following should fit my needs:

3CRUSB10075


However, I've been burnt before by manufacturers changing the chipset inside the device and not changing the model number, or worse seeing 'works fine' on the Hardware Compatibility list and not mentioning that they didn't test with WPA or WPA2.

As I've mentioned, my requirements are:

Must be USB (no spare PCI slots)
Must work on **AMD64** Hardy 'out the box' with WPA/WPA2
My definition of 'out the box' means, no ndiswrapper and no tweaked drivers from external sources.  
Preferably it should work with the standard Gnome Network Manager.
Must be available for sale in the UK

Ideally, I'd like a recommendation from somebody who's running Hardy-AMD64 and just had their wireless network kick in when they started Hardy for the first time.

Could anybody out there running the 3COM 3CRUSB10075 let me know if this is as good as the Ubuntu Compatibility List suggests, or give me some other suggestions that will run with the standard kernel drivers and have full WPA2/WPA2 functionality on AMD64 Hardy.

Thanks,

Mark

---

### Post by knaveman on 2008-04-25
I can confirm that the Netgear WG111 works under Hardy AMD64. However I cannot speak to the WPA/WPA2 as I use open network.

---

### Post by usernamed on 2008-04-28
Thanks knaveman,

Is anyone else (who is using WPA2) able to provide any recommendations?

---

### Post by usernamed on 2008-05-01
If I could gently *bump* this, just because I don't want to spend money on the wrong product and I do want to be able to use Ubuntu as soon as possible.

Hardy AMD64 USB wireless with WPA/WPA2?  Anyone?

---

### Post by kutjara on 2008-05-01
> **usernamed said:**
> If I could gently *bump* this, just because I don't want to spend money on the wrong product and I do want to be able to use Ubuntu as soon as possible.

Hardy AMD64 USB wireless with WPA/WPA2?  Anyone?

I know you're looking for an out of the box solution, but I faced a similar problem when the internal card in my HP laptop (Pavilion tx1420us, 2.2GHz Turion CPU) simply refused to connect to my network using WPA under Hardy 64. I researched a bit and finally settled on the Belkin F5D7050 card, principally because it contains a Ralink chipset that works well with Linux.

I still needed to download and install Serialmonkey's rt73 driver to get the card to work, however. That said, it was a pretty painless process and the card now works beautifully.

I mention this just in case you get nowhere with the "out of the box" route.

---

### Post by usernamed on 2008-05-01
Oh, the delicious irony.  I have a Belkin F5D7050 card and have got precisely nowhere with it, hence my looking for another solution.  It seems that there are 5 different versions of the F5D7050 card, and each revision has a different chipset.  The FCC ID on mine ends with an E (showing it's revision E)

I'd tried the rt73 driver and hadn't got Ubuntu to even recognise it (although lsusb recognised a Belkin adapter) despite there being no 'wlan0' interface and no light on the card itself.

Can you point me at the how-to you used to get the rt73 driver working?

> **kutjara said:**
> I know you're looking for an out of the box solution, but I faced a similar problem when the internal card in my HP laptop (Pavilion tx1420us, 2.2GHz Turion CPU) simply refused to connect to my network using WPA under Hardy 64. I researched a bit and finally settled on the Belkin F5D7050 card, principally because it contains a Ralink chipset that works well with Linux.

I still needed to download and install Serialmonkey's rt73 driver to get the card to work, however. That said, it was a pretty painless process and the card now works beautifully.

I mention this just in case you get nowhere with the "out of the box" route.

---

### Post by kutjara on 2008-05-01
> **usernamed said:**
> Oh, the delicious irony.  I have a Belkin F5D7050 card and have got precisely nowhere with it, hence my looking for another solution.  It seems that there are 5 different versions of the F5D7050 card, and each revision has a different chipset.  The FCC ID on mine ends with an E (showing it's revision E)

I'd tried the rt73 driver and hadn't got Ubuntu to even recognise it (although lsusb recognised a Belkin adapter) despite there being no 'wlan0' interface and no light on the card itself.

Can you point me at the how-to you used to get the rt73 driver working?

Isn't that always the way: just when you think you have the perfect solution, you find out you just got lucky. It's particularly true with wireless, where they seem to just grab random parts from the "Big Bag 'O Chips" and stick 'em on a card.

I used the following HOWTO to get my card set up:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

I didn't want to "hardwire" my network setup into the config file, though, so I also installed the RutilT network manager utility from 

[http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

and installed it by typing:

```

tar -xvzf RutilTv0.16.tar.gz
cd  RutilTv0.16/
./configure.sh  --launcher=external
make
sudo make  install

```RutilT makes the whole network setup process much easier. The only problem I've had with it is, every time I boot, RutilT connects to my network fine, but then just keeps disconnecting and reconnecting every few seconds, until I open the RutilT panel and manually click the name of my network. Then it works perfectly. Why these extra two clicks are necessary, I've yet to discover.

---

### Post by usernamed on 2008-05-02
Thanks Kutjara,

I'll go through the process again (though I'm sure I have followed the steps within) and let you know if I make any progress.  Though that won't be until tonight at the earliest (damn day job)

---

### Post by usernamed on 2008-05-02
Rats.  I didn't think it could be that easy.  I've followed the steps in the how-to you'd linked (as I did previously) and the device still isn't recognised, even after a reboot.  A quick 'lsusb -v' gives the following output:

```
Bus 007 Device 003: ID 050d:705e Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705e 
  bcdDevice            2.00
  iManufacturer           1 Manufacturer_Realtek
  iProduct                2 Belkin Wireless G USB Adapter
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           81
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Wireless Network Card
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           9
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 Belkin Wireless G USB Adapter
 
```

Thanks for all your help Kutjara, and if anyone else can either identify what driver I should be using from the output above, or suggest a USB alternative that fulfills the criteria in my original post then I'd be very much obliged.  

It mentions Realtek up there, but not which chipset (and there's more than one...)

---

### Post by kutjara on 2008-05-02
> **usernamed said:**
> Rats.  I didn't think it could be that easy.  I've followed the steps in the how-to you'd linked (as I did previously) and the device still isn't recognised, even after a reboot.  A quick 'lsusb -v' gives the following output:

Here's my lsusb -v output, for comparison:

```

Bus 002 Device 002: ID 050d:705a Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705a 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 

```

Interestingly, your card appears to give more information about itself than mine does. The only important difference I can see is that my card reports itself as 050d:705a, whereas yours is 050d:705e. It looks like that final letter is making all the difference. I suppose I should be grateful that my local Fry's carries old stock. :)

It looks like the "e" version of the card uses a Realtek chipset, while my "a" version uses the Ralink rt73. I think, therefore, you'll have to find a solution that works with Realtek chipsets (which are, I believe, not all that Linux-friendly).

This sort of underlines my earlier point. Short of opening every wifi card box on the shelves of your local electronics store and directly inspecting the card inside, I can't imagine how anyone is supposed to know what chipsets are being used.

Sorry my solution didn't work. I hope someone comes along with a definitive answer to your original question. I'd be interested in knowing, myself.

---

### Post by usernamed on 2008-05-03
Right, I've given up on my dream of out of the box wireless on Ubuntu, and I've also given up any hope of getting my current Belkin card to work (I thought I'd finally had some success with ndiswrapper but 64-bit Hardy, ndiswrapper and the drivers for this realtek based card seem to have issues in working together)

If you're reading this thread and have the Belkin F5D7050 Revision 'E' but are running 32-bit Ubuntu you might get the thread below to work for you:

[http://ubuntuforums.org/showthread.php?t=745655&highlight=050d%3A705e]("http://ubuntuforums.org/showthread.php?t=745655&highlight=050d%3A705e")


Personally I've ordered a 'Linksys Compact Wireless-G USB Adapter WUSB54GC' that can either use the Ralink official drivers from here:  [http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

Or the serialmonkey drivers which are under constant development and don't yet have an official release, but have a main page here:  [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page")

Applause for Ralink who seem to offer proprietary linux drivers (supported by themselves) and also appear to assist with the serialmonkey project to provide open source drivers.

---

### Post by arpanet on 2008-07-05
so...it's 2 months later. did you find something that worked?

i started using ubuntu (and linux) with feisty and have always had wireless trouble, but i was always able to get any of the 3 adapters we have to work. but once i went to 64 with hardy, no luck. i decided i needed to buy a known, working adapter (even if it required some messing). so, i'm anxious to hear if you found a working adapter.

---

### Post by usernamed on 2008-07-07
Hi Arpanet,

The device I ended up with is the Linksys Compact Wireless-G USB Adapter WUSB54GC (this card is for the UK market and was ordered via dabs.com at the time of my last post) that didn't quite work out of the box but worked fine after installing the serialmonkey drivers that I provided a link to in one of the earlier posts in this thread.

This has worked with WPA and seems (touch wood) to be reliable and effective.

However, things to note are:

1.  Once you've compiled and installed your wireless module do not under any circumstances allow Ubuntu's auto-update system to install any kernel updates.  It will stop your fresh compiled kernel module from working and worst of all any attempt at a 'make clean' and recompiling/reinstalling the serialmonkey driver still resulted in no wireless until I reverted to using the pre-updated kernel (which thankfully was still present on the boot menu, but after the update was no longer the default option)  

It seems that some genius at Ubuntu has decided that what you want in an LTS 'day to day use' release of an operating system is to keep having to recompile core components of your system for it to work.  The kernel updates come through just like an innocuous application patch but will immediately after reboot cause any third-party kernel modules such as the wireless driver to stop working.

2.  I had to insert a brief script into my rc.local folder to bring the wireless connection up after each fresh boot into the system.  There are a hundred examples of this script already available on the forums but let me know if you need one and I'll paste mine up.  (It may be a while though, I'm kind of lazy)


Good luck with it, I've found Ubuntu a pleasure when it's working and if you could just stop the kernel updates from occurring it would work all the time!

---

### Post by kenfeyl on 2008-07-08
Thanks to username for the informative post. I just wanted to add my own experience. After reading username's advice I bought the WUSB54GC today. IT WORKED OUT OF THE BOX IN AMD64 HARDY. Wow. Just wow. I literally wept when I saw the green circles. This is my third USB stick, and I plan to return the other two to Office Depot tomorrow. I didn't even have to install any drivers or anything (unlike username). Get this stick now!

---

### Post by ptn107 on 2008-07-08
Belkin Wireless G USB Network Adapter (serial:F5D7050, version:4.xx, FCCID:RAXWN4501H)

Works on hardy 8.04.1 amd46 out-of-box, wpa/wpa2 with my Belkin Wireless G Router (F5D7230-4) with the 802.11 compliant upgrade.

---

### Post by usernamed on 2008-07-08
> **ptn107 said:**
> Belkin Wireless G USB Network Adapter (serial#: F5D7050)

Works on hardy 8.04.1 amd46 out-of-box, wep/wpa/wpa2

If only it was that simple.  There are at least 5 different revisions of the Belkin F5D7050, each of which has a different chipset despite being labelled as F5D7050 on the box.  If you look at the extremely tiny writing on the label of your USB dongle you'll see it has a revision letter (from F5D7050A to F5D7050E and possibly beyond)

Some revisions of the Belkin dongle have chipsets that are linux compatible and some aren't, I had a Belkin F5D7050**E** and it didn't work with 64-bit Ubuntu Hardy at all, even after following a variety of different how-to's.  The hardware definitely worked because I could use the card with Windows, but it wouldn't play ball with Hardy.

By comparison, the Linksys card worked fine after installing the SerialMonkey drivers for it (and it appears kenfeyl didn't even have to do that)

So, if you have a Belkin FD7050 with a chipset that's working then congratulations, you struck lucky.  However, I couldn't recommend purchasing one for use with Ubuntu for the same reason that I couldn't recommend placing your life savings on a horse at the Grand National.

---

### Post by arpanet on 2008-09-20
After 2 DOA Linksys WUSB54GCs, I got one that worked and it worked out of the box using WPA!

Unfortunately network manager is unable to bring the connection up at startup. It remembers the network SSID and password, but it doesn't connect. I have to switch to roaming mode, then switch back to non-roaming and type in the SSID and password. So, I guess I need one of these scripts you mentioned to bring the connection up each time. I'll have a look around for one.

Thanks for the advice. It's nice to not have to snake the ethernet cable into the office everytime I want to get on Ubuntu,

---

