---
title: "New 64-Bit Developer Machine Specification (Virtualization)"
date: 2008-06-11
forum: x86 64-bit Users
---

### Post by probin51 on 2008-06-11
Hi All,

Every 10 years or so, I give up trying to upgrade my old PC, grab some cash from under the matress and relunctantly head to the next PC store in search of hardware enlightment. Alas, this time has come again.

NO MORE MICROSOFT

I successfully ditched ALL my Microsoft machines this year (format c: REDMOND!!!), having firstly switch to SUSE 10.x, which is already history. I'm now on debian (server) and UBUNTU 8.0.4 on the laptops and on my desktop. 

But I still have a problem, I MUST work in a MS environment for my customers (banks etc.), so I need a virtualization developer machine. One with lots of RAM (min 4GB) and CPU. One that will do it's job for the next 5 years or so. 

I need help specifying my machine and would appreciate any help from you expert LINUX guys. I've put together the following machine and would like to know what you think. 

I'm planning to run UBUNTU 8.0.4. Desktop on a wireless lan setup, starting MS Windows 200* Server as a virtual machine. I'm not too sure which one to use yet (xen, qemu, vmware)? Any advice about which one can use multiple cores would be gratefully appreciated.

Here's the specification I've arrived at:

CASE         ATX Big Coolermaster Cosmos RC-1000-KSN1-GP silver/black***     188.15

Motherboard  Gigabyte EP35-DS4 P35+ICH9R S775 FSB 1333MHz ATX***               113.62

CPU          Intel Core 2 Quad Q6600 2.40GHz 1066MHz S775 8MB 65nm 95W(G0) Box 146.69

Memory       Kit 2x2048MB OCZ DDR2 1066MHz CL5 XTC Platinum***                 106.29

Fan          Zalman 9700 LED (AMD, Intel)                                       52.05

Power        Netzteil ATX be quiet! Dark Power Pro P7 650W ATX 2.2             139.20

Graphics     512MB XFX Geforce 8800GT GDDR3 2xDVI TVOut PCIe                   135.47

DVD          LG GH20NS10-AUAR10B SDSATA Kit***                                  43.74

HDD (x2)     300GB Western Digital WD3000GLFS VelociRaptor 16MB***             226.54 (453.08)
                                                                 TOTAL 1,378.19 EUROS

Here's the reasoning...

CASE. I wanted a decent, quiet case with easy access. My current one rattles like hell. Also, it offers a panel on top, where I can quickly plug in up to 4 USB devices without having to get on my knees.

Motherboard. The EP35-DS4 one is supposed to be energy efficient and superior to the ASUS PK5E? Sounded really good in the write-ups.

CPU. I'm not gaming and compared to the P4 2.5Ghz, this 2.4Ghz Quad processor should suffice shouldn't it? Also with G0 stepping offering reduced power consumption.

Memory. OCZ is a good name and by bying 2GB sticks, I still have room for a few more GB if I need to add them later. Also, same speed as FSB.

Fan. Zalman has a good, solid reputation. Also looks good?

Power. I upgraded my machine because it was too loud and put in a be quiet! unit. When you look at the unit, it is so well finished (cabling etc.) that it's a shame to hide it in a box. I'm well impressed and decided to stick with this brand with my new PC.

Graphics. NVIDIA seems to be the favoured card. I don't play games really, but sometimes I like to watch a movie. I currently have DUAL screen and this has dual DVI output that I can attach my Samsung 940* VGA monitors to I guess. Also, I don't want to EMPTY the matress is one go!

DVD. I like LG drives, I have a LG 55H (IDE) or something like that in both my VIA C7 1.3Ghz DEBIAN Server (38Watts 24x7) and my Desktop. Their simply fast and reliable. I plan to put two into this machine (SATA).

HDD. Not too sure here. I didn't want to pay so much, but don't want to slow things down. I'm actually very happy with Samsung Spinpoint technology. What do you think?



The PC will replace my Desktop and I'll be playing around with Virtualization (Microsoft servers) a fair bit (due to my work). 

ALL ADVICE would be gratefully appreciated.

Thanks!
Pete

---

### Post by Cappy on 2008-06-11
Memory - It's a common mistake thinking you need memory matching the FSB. You can't use that memory to its potential (unless you are overclocking REALLY high, past say, 3GHz!). That 1066 FSB actually only requires 667MHz. Get a 800MHz memory instead. They are cheap.

Motherboard - I don't know which Intel MoBos (motherboards) do, but it would be definitely worthwhile to get a MoBo that supports linux's acpi and apic. Otherwise you would need to disable the cores "talking" to each other. Someone else would have to suggest one because I run AMD. If you want to try AMD instead, my M3A-H is fully linux compatible. I got it this week after my Gigabyte motherboard died [after a year].
**Edit: The M3A-H has a clock drift of 4 minutes a day. There is a fix here: [http://ubuntuforums.org/showthread.php?t=835288](http://ubuntuforums.org/showthread.php?t=835288)**

Power - I prefer the Corsair HX620. It's completely silent and cheaper than the one you selected. Just a suggestion, I don't know much about the Dark Power Pro so it may be better.

Graphics - The Nvidia 9600 is much better for the price. You may need to install beta drivers on Hardy (not running Hardy myself) but that's not hard when you use a program called Envy. Do know that if you only want to watch videos you can go for a very cheap nvidia card at the $100 or lower price (7900, 8600, etc) and still be able to play most any game [except Crysis], but not at the higher qualities with AA and AF and whatever else.

Hard Drive - I wish I could afford one of those VelociRaptors =( From what I've heard though, they are definitely worth the money.

---

### Post by probin51 on 2008-06-11
Hi Cappy,

I'm not a hardware guy, so MANY thanks for the information!!!

Memory. 800Mhz it is. I wasn't sure if I could do that! I got told that the 800Mhz will slow the 1033Mhz FSB down.

Motherboard. Do you now of a "green" quad motherboard from Intel? Something that is able to "save energy" during idle phases? Are you maybe talking of something like the ASUS P5K (Intel P35)?

Power. HX620 looks impressive and around 40% cheaper. What's all this "NVIDIA SLI Ready" stuff about?

Graphics. Basically I want to retain the DUAL setup. 7900 Will do this I think. Thanks for the ENVY tip.

HDD. I had two on my list (wanted to do 300GB raid-1). But too costly I think for 500 EUR. Out of my price range. Will have to check the matress. And ask my wife for permission!!!

Thanks.


PS: Just found this...

GIGABYTE vs. ABIT vs. ASUS
[http://www.linuxhardware.org/forums/viewtopic.php?t=8](http://www.linuxhardware.org/forums/viewtopic.php?t=8)

---

### Post by Yellow Pasque on 2008-06-11
I don't think memory prices on your side of the pond are quite as good as this side. My suggestion would be 8GB of DDR2-667, running the system clock 1:1 with the FSB, and raising the system clock to 333MHz (a very reasonable OC). Or, if DDR2-800 is about the same price, try finding a 1333MHz FSB CPU, and running 1:1 with system clock at 400MHz.

PSU - Unless you're planning on running multiple video cards, 650W is overkill. A 450W will handle that hardware nicely, or a 500 - 550W unit if you're uncomfortable with that. I can provide links to SPCR articles if you'd like.

---

### Post by Jouke74 on 2008-06-11
If you are planning on going for multiple virtual machines at the same time i.e. with using Xen, then I would opt for 8 Gb of internal memory. It is currently very cheap and it would improve running two VM's at once a lot, also because a lot gets cached into memory.

The samsung F1 spinpoint series might be a cheaper and good alternative for the very expensive WD raptor disks.

VMware for sure supports dual core CPU's.

---

### Post by probin51 on 2008-06-11
Thanks Temüjin. This is the kind of solid feedback I was hoping to get. I'm now looking at a yorkfield (?) Q9*00.

I guess I can still use the motherboard - I saw a number of good reviews.

My initial idea was to put 8GB in. So reducing the rate to 667 or 800 halves the price on that item, e.g. Around 45 EUROS.

[http://www.mindfactory.de/search_result.php?Query=800+mhz+2+GB](http://www.mindfactory.de/search_result.php?Query=800+mhz+2+GB)

The money saved could pay for a Q9300.

[http://www.mindfactory.de/product_info.php/info/p413804_Intel-Core-2-Quad-Q9300-2-50GHz-1333MHz-S775-6MB-45nm-tray.html](http://www.mindfactory.de/product_info.php/info/p413804_Intel-Core-2-Quad-Q9300-2-50GHz-1333MHz-S775-6MB-45nm-tray.html)

And a 500W (I'd like to be a little on the safe side) be Quiet! Titan BQT Straight unit lands at around 90 EUR.

[http://www.mindfactory.de/product_info.php/info/p133547_Geh-Netzteil-ATX-be-quiet--Titan-BQT-Straight-Power-500W-ATX-2-2.html](http://www.mindfactory.de/product_info.php/info/p133547_Geh-Netzteil-ATX-be-quiet--Titan-BQT-Straight-Power-500W-ATX-2-2.html)

---

### Post by probin51 on 2008-06-11
Hi Jouke74,

I'm going to be running the machine only when I'm sat in front of it. I may have to run multiple MS machines, not too sure yet. 

I'm basically developing software for an MS MOSS (portal) and so I need to have Windows 2003 server + MOSS etc. running only in a development (programming) environment. Single user etc.

The main reason I'm upgrading to a quad is because I can. And also because I only do this every 5-8 years. The machine I'm typing on now if a P4 1.5Ghz that I've upgraded to 2.8Ghz last year. 

Yet, with virtualisation, I just need that extra RAM. e.g. evil old MS needs minimum 4GB to run smoothly. I'm experimenting a little, so the guidance you gives kindly give will save me time, mistakes and a little money too.

Thanks for the advice re: VMWARE. My brother uses this too, but he's at a fully MS shop.

I think I'll settle for the Spinpoint and maybe put the raptor disks on my christmas wish list! :o)

Thanks!

---

### Post by mad_max0204 on 2008-06-11
I'll try to help you with some advices if I can. I run my own pc store so I have some experience.

Motherboard is a good one and you dont have to think about it.
Case rocks but there are some minuses with positions of certain components. There can be a better solution. Look for other CM or TT cases.
CPU is a good one and u cant be wrong with new Intel C2Q series.
Memory sounds nice but u wont get anything with 1066 as someone mentioned. Get 800 sticks and put in 2x4GB or 4x2GB so you can run MS Win Server in virtual box with ease.
PSU is not such a good choice. Get something stronger. Something like 650 atleast. And look for brands (CM, TT, Chieftech, Tagan,...), You have a power efficient Mobo and cpu but theres never enough power.
Get some Noctua fans. 12cm if you can find them. Ugly color but silent and really good. You get a nice guarantee on them too.
DVD is nothing to worry about. it costs 10-15e. LG has done a nice job for me so only plus for that.
GPU is another story. If you want to run virtual box you dont need any expensive graphics but for that money you can get a nice 9600. Thats up to you. You dont get benefits from either since you dont game. I have a 7900GTX still and no need for a better one.
HDD is actually the most personal choice. Lots of people prefer WD, other prefer Seagate, etc. I have 4x 500GB WD from AAKS series for storage and a fast 74GB hdd for system. Some would say seagate is better esp. with its new series with 32mb but you wont notice any difference. It still stays personal choice.

Hope I helped you some. Maybe I didnt help you or even made it worse for you but good luck. Post your new configuration when you get it and enjoy in assembly.

---

### Post by Cappy on 2008-06-11
> **probin51 said:**
> Hi Cappy,
Power. HX620 looks impressive and around 40% cheaper. What's all this "NVIDIA SLI Ready" stuff about?

Support for two video cards for hardcore gamers.

> 
Graphics. Basically I want to retain the DUAL setup. 7900 Will do this I think. Thanks for the ENVY tip.


So will the 8600 and you will want the 8600 over the 7900 if the price is the same (or lower) near you. The reason being that the Nvidia 8600 has some more features like DX10.

> 
GIGABYTE vs. ABIT vs. ASUS
[http://www.linuxhardware.org/forums/viewtopic.php?t=8](http://www.linuxhardware.org/forums/viewtopic.php?t=8)

That's not a good comparison. My Gigabyte that burned out wasn't fully linux compatible but my new Asus is. It's more of just a case-by-case basis on if the motherboard supports linux fully.

> **Temüjin said:**
> 
PSU - Unless you're planning on running multiple video cards, 650W is overkill. A 450W will handle that hardware nicely, or a 500 - 550W unit if you're uncomfortable with that. I can provide links to SPCR articles if you'd like.

It's true, a 500W power supply would be fine but you get advantages from a high grade power supply such as power savings and extended warranties (The Corsair 620W has a 5 year). It's more about quality than the wattage imo. 

> **Jouke74 said:**
> 
The samsung F1 spinpoint series might be a cheaper and good alternative for the very expensive WD raptor disks.


Actually, I didn't know the Samsung F1 Spinpoints were so good. I looked up a benchmark: [http://www.tomshardware.com/reviews/HDD-SATA-VelociRaptor,1914-11.html](http://www.tomshardware.com/reviews/HDD-SATA-VelociRaptor,1914-11.html)
and while the Spinpoints are a bit slower on read speed (which you will be doing mostly, honestly) they match in write speed. I'm pretty impressed; I thought the VelociRaptor would be much better considering its price.

---

### Post by probin51 on 2008-06-12
Hi mad_max0204

> Case rocks but there are some minuses with positions of certain components. There can be a better solution. Look for other CM or TT cases.

I was looking around for one, e.g. the CM Stacker. I like the fact the panel is up on top (it will stand on the floor and is real easy to reach, turn-on, turn-off) and the 4 USBs allow me to quickly plug stuff in without getting dirty on the floor (no carpet + fat hairy black cat hairs everywhere). I don't know why the manufacturers all put just 2 on the front and not 8 or 12. I have all sorts of goodies like USB sticks, camera, external 320GB hdd (needs 2 usb for power), keyboard dongle (Cherry Barracuda - GREAT [LINUX] KEYBOARD).

I'd never heard of Noctua fans, and you're right about the colour. It looks like they've been recycled from prosthetic limbs. Jeeeeezzz.

In Germany, PaPst has always been traditionally a sign of good quality and their very quiet too (17db). They're also easy to get hold of here. Price is about the same.

Za Germanz don't just build great carz, take a look at this stuff too:

	[http://www.be-quiet.net/be-quiet.net/index.php?StoryID=1](http://www.be-quiet.net/be-quiet.net/index.php?StoryID=1)

	[http://www.be-quiet.net/be-quiet.net/index.php?StoryID=13](http://www.be-quiet.net/be-quiet.net/index.php?StoryID=13)
	
I bought one of these for an older PC (waste really). It's a work of art and shouldn't be inside a machine but on your desk somewhere where you can see it.

They also have a click and select tool for calculating which power supply best suits your needs.

	[http://www.be-quiet.net/calculator.php?websiteLang=en](http://www.be-quiet.net/calculator.php?websiteLang=en)

> You dont get benefits from either since you dont game. I have a 7900GTX still and no need for a better one.

I absolutely agree, but I might install a game? Maybe? But, Cappy's got a point. I'll go for either the 8600/8800 GT anyway because of DX10 support and similar price - I really don't want to upgrade this machine for a while.

> HDD is actually the most personal choice.

All my machines run Samsung Spinpoint. Dollar for dollar their a real bargain, quick and very quiet - also Samsung 1000GB costs 125 whereas Raptor 300GB costs 250. 

I'm going to order everything at the weekend, then I'm off on holiday to Reykyavik (Iceland). 

Cooler Master :)

Thanks for your help!!!

---

### Post by mad_max0204 on 2008-06-12
Cheers

---

