---
title: "AMD 64 Motherboard for Ubuntu"
date: 2005-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by engklw0 on 2005-04-28
Hi ! 

I wanted to build a Ubuntu Linux system using the AMD 64 power. Can any one tell me which motherboard that suits for Ubuntu ? 

K.L.

---

### Post by makis on 2005-04-29
hi my friend,

I use Asus A8V Deluxe and everything works perfect: the 8 UsBs, sound, everything I have tried. I do not know yet about WiFi  and RAID, I haven't test them. 

My motherboard has an AGP slot for video card, but there is the same edition with RCIe (I think A8K or something like that)

 Of cource, this is just an advice from me.

Cheers!

---

### Post by psoulocybe on 2005-04-29
I'm on an Epox 9nda3+

Great board.  Overclocker friendly.  Comes w/ 8chanel on board sound, GigE lan, firewire, usbs gallore....   and a friendly led for hardware trouble shooting.

---

### Post by engklw0 on 2005-04-29
Thanks , guys.

Your info is very useful. How about the heat generate from the mainboard ? Did it be heater than AMD Xp version ?  I know there has feature to slow the speed of CPU. Did it be work in Ubuntu Linux ?

I will try but I have little money for my build.

K.L.

---

### Post by DutchLau on 2005-04-29
@ Makis, 

Sounds good, I also bought a new PC from scratch recently (which includes an Asus A8V Deluxe 939-pin Mobo), I just haven't had time to install anything on it yet. Does the onboard sound and the 8 USB 2.0 slots work ok with Ubuntu? What about the extra features? Does the Asus driver CD that came with the A8V have any Linux drivers? (Knowing we're in a winblows world, probably not) 

Thanks already,

DutchLau

---

### Post by psoulocybe on 2005-04-29
You are talking about cool and quiet.

it's controlled by the motherboard, it should work find in ubuntu.  havn't personally tried it since i'm an overclocking fiend.

as far as MB temps.... the board doesn't generate any head.  The processor is running with a 600mhz overclock w/ +.1 V at around 40C.  50C under 100% load for a couple hours.  Thats with stock heatsink and fan.  

The A64 windhesters are rated up to 70C, so anything under 60 at full load is pretty safe.  though lower is always better for chip longevity.  

It's also nice that I can install most HSF and not lose any slots of any problems like that.  The only HSF w/ a problem fitting is the XP120, but that doesn't fit on any board.

---

### Post by makis on 2005-04-30
[QUOTE=engklw0]Thanks , guys.

Your info is very useful. How about the heat generate from the mainboard ? Did it be heater than AMD Xp version ? I know there has feature to slow the speed of CPU. Did it be work in Ubuntu Linux ?

I will try but I have little money for my build.

K.L.[/QUOTE]

My friend, **psoulocybe** was very clear. Let me add on his words that Cool & Quiet feature is set up in BIOS so it works automaticaly in Ubuntu.

You have also to know that the processors with 939 pins produce less heating than the old ones; e.g. amd64 3000+ for socket754 produce 89TDP (temperature in watts), amd64 3000+ for socket939 produce 67TDP. This is because the processors for 939pins are built with 0.09&#956;m architecture in the core, while the old ones with 0.13&#956;m.

The interesting thing is that all intel processors, regardless the architecture of the core, have TDP above 73 (between 73 for some celerons and 110 for P4 extreme editions).

In conclusion, heating is the last thing that you have to have in your mind...

---

### Post by makis on 2005-04-30
[QUOTE=DutchLau]@ Makis, 

Sounds good, I also bought a new PC from scratch recently (which includes an Asus A8V Deluxe 939-pin Mobo), I just haven't had time to install anything on it yet. Does the onboard sound and the 8 USB 2.0 slots work ok with Ubuntu? What about the extra features? Does the Asus driver CD that came with the A8V have any Linux drivers? (Knowing we're in a winblows world, probably not) 

Thanks already,

DutchLau[/QUOTE]

Well, USBs worked automaticaly; I really didn't do anything. The same with the sound card of the motherboard. I heard the nice Ubuntu drums from the splash menu directly from the very beginning, at the installation reboot of the OS.Additionally, all the outputs of the soundcard work perfect.

As I said I havent tested the ethernet and wifi yet. But in System->Administration->Device Manager I can see what the OS can recognise. Thus I see:

all the usbs
all main ports: PS/2 mouse & keybord, Parallel,Serial,RJ-45.
the K8 northbridge of the motherboard
the PDC20378 (is the fast track 378 SATA controller if you want to build RAID)
the IEEE 1394 host controller
the VT8233/A/8235/8237 audio controller
the VIA VT6420 SATA RAID controller
the VT 8237 ISA bridge (the south bridge chipset of the motherboard)
the VT 82C586A PIPC Bus master (IDE controllers)
the Yukon Gigabit Ethernet 10/100/1000 base-T adapter (so we must have working ethernet), and
the Ralink RT2500 802.11 Carbus reference card (so we must have working wifi) 

as regards the Asus CD, we have asolutely nothing for Linux inside there.But you also need absolutely nothing from what is in there! Ok, maybe some add-on sofware screening the temp of the CPU and the speed of the funs or the wifi connections, but none is important and additionally you can find linux soft out there doing this. The rest in this CD are all these garbagges make windoze trash bin...

---

### Post by IndieRockSteve on 2005-05-03
I've got an ECS KN1 Extreme

works fine, is my second ECS mobo in this "server". my K7S5A worked flawlessly with linux and will become a secondary server now. so far the KN1 has worked great. I really like this mobo too, great layout and very thoughfully designed. I dunno how it is for overclocking and the such, but I've heard it does a decent job if your not a super-tweaker type person.

---

### Post by dewey on 2005-05-03
I've got a DFI Lanparty NF3 250gb (Socket 754) and it works fantastically, is pretty to look at (UV Reactive), overclocker friendly, and affordable too.
[http://www2.newegg.com/Product/Product.asp?Item=N82E16813136147](http://www2.newegg.com/Product/Product.asp?Item=N82E16813136147)

---

### Post by WirelessMike on 2005-05-03
DFI LanParty does rock.  Everything just works.  Overclocking appears limitless.

That's to be expected, though--  Oskar Wu, the reknowned overclocking engineer from Abit, moved to DFI just last year.  His talent is evident in the bios of the 64-bit architecture LanParty boards.

---

### Post by DutchLau on 2005-05-03
Hi again, I just got my computer (the amd 64 with the A8V motherboard, but I can't get sound working. 

Does anyone have any ideas

EDIT: I'm running i386 Ubuntu on it

---

### Post by DutchLau on 2005-05-03
@Makis, or @anyone else with an Asus A8V Deluxe.

How did you get your sound working? Did it work right out the box? Or did you have to do something special? I'm dumbfounded, I can't seem to get sound working AT ALL! :(

Please help,

DutchLau

---

### Post by makis on 2005-05-04
[QUOTE=DutchLau]@Makis, or @anyone else with an Asus A8V Deluxe.

How did you get your sound working? Did it work right out the box? Or did you have to do something special? I'm dumbfounded, I can't seem to get sound working AT ALL! :(

Please help,

DutchLau[/QUOTE]

Hi my friend,

Yes, in my case it worked right out of the box (I am running ubuntu amd64, but I do not think that this has something to do with your problem). But I will try to help you as much as I can.

Let me know first something stupit: have u plugged the speakers in the green output?? there are many outputs there, try the light green one. Also, try to c somehow if your speakers work.

I am saying these because it is quite strange not to have sound.

Also, go in System->Administration->device manager  and c if you can find the VT8233/A/8235/8237 AC97 Audio Controller

Tell me your news.

In my opinion it must be software and not hardware problem.

M.

---

### Post by Terracotta on 2005-05-04
I have an A8V motherboard as well, and sound worked out of the box, but surround does NOT work, nor does the subwoofer give any sound :-), maybe this problem is related to the one described above, I use the onboard soundcard.

---

### Post by makis on 2005-05-04
if a part of the sound cart works, all the card must work. So, must be software problem. There is an excellent guide for sound problems in Ubuntu, try [here]("http://ubuntuforums.org/showthread.php?t=26567")

---

### Post by DutchLau on 2005-05-04
@Makis,

I've checked the device manager and there *is* a section called "VT8233/A/8235/8237 AC97 Audio" but no "audio controller" as you said. My speakers work just fine. They're speakers attached to my monitor and I used them on my other PC just before putting together this one. The sound jack is also in the light green one, and I even attached the frontal speakers jacks and those aren't working either. Do you need anything else? lsmod or something like that? I'm dumbfounded, Hoary sound worked out of the box for my two other PC's, why not this one?  :-| 

Thanks already for your help,

DutchLau 

(I use Hoary i386 - not 64 btw)

---

### Post by DutchLau on 2005-05-04
Okay!

I got my sound working! I had to configure Alsa and change the configuration of my front panel audio outs on my motherboards and now sound works perfectly! On the reboot I heard the beautiful sounds of the Ubuntu startup, I've never been so happy in my entire life

Thanks Ubuntu community,

DutchLau

---

### Post by makis on 2005-05-04
[QUOTE=DutchLau]Okay!

I got my sound working! I had to configure Alsa and change the configuration of my front panel audio outs on my motherboards and now sound works perfectly! On the reboot I heard the beautiful sounds of the Ubuntu startup, I've never been so happy in my entire life

Thanks Ubuntu community,

DutchLau[/QUOTE]

Happy for you my friend!:):razz:
I told you it must be software problem. Enjoy your perfect new box!!

---

### Post by DutchLau on 2005-05-04
@ Makis thanks, 

I don't think I've ever been so happy to hear sounds when I heard those nice "Ubuntu" sounds when logging in  :razz: 

Now I can go about life normally again :grin: 

Catch you another time and I'll help out w/ anything if nessasary.

DutchLau

Oh yeah, one last question. I have a 160 Gb SATA drive installed, no IDE masters and an LG DVDRAM drive as my secondary IDE Master (wow that was wordy). Do you also have that FastTrack 378 searches for IDE devices at the system bootup and then says BIOS not installed or something? (It's not critical, but it's well annoying) 

Thanks already

---

### Post by coolmike890 on 2005-05-05
The BIOS not installed message is normal. It will report this if no drives are detected on the controller. You are evidently not using any drives on this controller. If it annoys you (it does delay boot times) go into the BIOS and disable  the onboard controller until you need it.

---

### Post by makis on 2005-05-07
[QUOTE=DutchLau]

Oh yeah, one last question. I have a 160 Gb SATA drive installed, no IDE masters and an LG DVDRAM drive as my secondary IDE Master (wow that was wordy). Do you also have that FastTrack 378 searches for IDE devices at the system bootup and then says BIOS not installed or something? (It's not critical, but it's well annoying) 

Thanks already[/QUOTE]

my friend,

coolmike 890 is right. Fast Track is a controller for RAID devices. You can disable it from BIOS, just follow the motherboards book instructions.The message that the BIOS is not installed is normal, because there is an automatic installation of the controllers when there is a RAID HDDs detection. So, no prob! Do not worry!! The motherboard is ok, it is perfect!

Makis

---

### Post by nettlez on 2005-05-08
Is the VIA K8T800 chipset well supported?  I'm currently running on an Nforce 3 250 with no problems.  but, I'm planning to build a cheap computer for my friend and have found the VIA chipset boards to be less expensive.  Though, I am afraid to get it because I can't find any linux drivers on the VIA website.  Does any one have a K8T800 Board?

---

### Post by CospeFogo on 2005-05-09
[QUOTE=nettlez]Is the VIA K8T800 chipset well supported?  I'm currently running on an Nforce 3 250 with no problems.  but, I'm planning to build a cheap computer for my friend and have found the VIA chipset boards to be less expensive.  Though, I am afraid to get it because I can't find any linux drivers on the VIA website.  Does any one have a K8T800 Board?[/QUOTE]
 I have an Abit KV8 Pro, whose chipset is VIA K8T800 Pro.  Everything worked out of the box.

Since the audio and network are the same on K8T800 and K8T800 Pro, I think you'll have no problems. Look: [http://www.via.com.tw/en/products/chipsets/k8-series/comparison_k8-series.jsp](http://www.via.com.tw/en/products/chipsets/k8-series/comparison_k8-series.jsp)

Try looking for the drivers in here: [http://www.viaarena.com/default.aspx?PageID=2](http://www.viaarena.com/default.aspx?PageID=2)

---

### Post by booster on 2005-05-12
I have an MSI K8 Neo platinum, that is an nforce 4 chipset MOBO (Video PCI express x16, dual channel RAM, 8 USB)
everything works,
the Raid I can't say cause I still don't have it. nor having tested firewire

for video card I would go definetly for nvidia. using XFX6600 dual DVI (have not tested dual monitors)

---

### Post by Chareos on 2005-05-13
I'm VERY HAPPY with this mobo and Ubuntu. Even with sound... this is an nForce4 mobo, and was expecting any kind of problems... naah. 5.1 audio worked out of the box, after 2 minutes thinkering in mixer volumes.

Going to love Ubuntu.


(Now, IF ONLY I could get Alsa sound from Cedega...)

---

### Post by crane on 2005-10-07
I know this is an old thread but just wanted to add my 2 cents. 
I recently built a 64bit system using a gigabyte k8ns ultra 939 MoBo. I had nothing but problems. Random ren=boots and freezes. No sound. :( 

I tried every trick I could find with no luck. I finally bought an asus a8v deluxe. I have had it runnning for about 3 hours now and all seems well. Very nice board.

---

### Post by tseliot on 2005-10-08
[QUOTE=crane]I finally bought an asus a8v deluxe. I have had it runnning for about 3 hours now and all seems well. Very nice board.[/QUOTE]
I did the same thing. This mobo rocks

---

### Post by tux21 on 2007-02-24
i think disabling cool n quiet solved freezes for me in m2n-mx

amd 3600+

---

### Post by tooCanad on 2007-02-24
I built one with  the Biostar GeForce 6100-M9 with an AMD 3700. Runs cool and quiet. Needed to wire up the Nvidia drivers but other than that runs fine on edgy.

---

### Post by j0eb0b on 2007-02-24
I built a machine around a DFI nF4 Ultra which works well with one exception.  The onboard sound (Karajan 8 Ch) is not supported and does not work under Ubuntu 6.0.6.  I'm not sure whether it works under 6.10.  I had to buy and install an Audigy card to get sound. The Phoronix forum is a good reference for Linux Hardware compatibility.

---

### Post by flapane on 2007-02-25
I've the same MoBo, and no problems with karajan from breezy to feisty

---

### Post by j0eb0b on 2007-02-25
From the Phoronix forum review of the DFI nF4 Ultra.

"Furthermore, the DFI Infinity has its foot in the door with proper LM_Sensors detection thanks to the ITE Super I/O controller. However, some of these values were reporting inaccurate numbers and the DFI Linux compatibility wasn't complete due to the integrated audio not being properly recognized with Fedora Core 4."

Your system correctly identified the onboard audio controller and you are using it?  Did you have to do anything to make this work.

---

### Post by flapane on 2007-02-25
btw Infinity!=Ultra-D and FC4!=Ubuntu :), if I open Kmix or alsamixer I can read AC97 Nvidia blah blah blah and I can hear form all the speakers of my 5.1 system (analogic)

---

### Post by freemart on 2007-02-25
I recently finished installing a Asus A8VM CSM/NBP MOBO with AMD Athlon 64 3000+ Cool & Quiet. It is a 35W processor and the throttling Ubuntu provides results in two speeds, the lower being 1000 mhz. Total power consumption is 100 W at lower speed including monitor, printer idle, amplifier for sound, UPS and power supply for DSL modem. Performance is good, maybe not for gaming addicts, but for general purpose and engineering work that I do. The low processor speed runs about 98% of the time. There is almost no fan noise, and the cpu fan hardly ever speeds up. This is wonderful where power costs 4 times as much as in the US. The lower heat should also result in a long life for all components.

---

