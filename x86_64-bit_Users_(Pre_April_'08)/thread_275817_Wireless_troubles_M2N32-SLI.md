---
title: "Wireless troubles M2N32-SLI"
date: 2006-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by ThndrShk2k on 2006-10-11
I recently bought and installed a M2N32-SLI Deluxe Wireless motherboard with an Athlong 64 4200 X2, and I am having troubles. I got through the install no problem (with noapic), but the wireless driver in the kernel of the latest downloadable DVD, 6.06 i think, detects the device; however, it does not use it at all. I get no signal other than the one parsing for the SSID, which it finds.

Any help on this subject would be most appreciated.

---

### Post by ashram on 2006-10-14
Try to search in the forum about this MoBo (chip rtl8187).

I have this MoBo too and having problem.

In order to solve noapic issue you need update firmware to latest from asus (make backup before).

Linux drivers didn't worked. 
I got it working only after installing ndiswrapper + win98/me drivers but I have it disconnecting all the time, hope you will have more luck.

---

### Post by MightyMouse on 2006-10-21
Hi,
same motherboard, same wireless problems.
Any particular reason why you didn't use the windows xp driver with ndiswrapper?

Anja

---

### Post by ashram on 2006-10-23
for me XP driver did't worked. I tried XP drivers that come with CD and new XP drivers from realtek site.

---

### Post by jck on 2006-10-30
I can relate.  I just built a new AMD64x2 system w/M2N32-SLi Deluxe Wireless Edition m/b.  Upgraded the BIOS to 0704 or 0706.  Can't remember for sure.

I can get ndiswrapper to wrap the drivers for the Realtek 8187 (tried x64, 2kXP, and 98Me versions), but nothing seemed to want to work on my setup.

I'm slowly re-learning all my Linux stuff in hopes that I can figure this out myself.  Just hoped that someone here could help me save time and get me onto more important things in Linux.

If I figure anything out, I'll try to remember to post something for you guys here.

---

### Post by ashram on 2006-10-30
Just take win98 or WinME drivers with ndiswrapper and it should work.

Before that blacklist linux driver that comes with kernel: r8187 and rtl8187
in /etc/modprobe.d/blacklist

I would recommend install generic/i386 rather than 64bit... (my opinion)

---

### Post by jck on 2006-10-31
Thanks.  I will try that this evening.

Are you configuring your WLAN with WEP or WPA?

I currently use WPA-PSK for my WLAN.  I installed WPASupplicant and loaded the KNetworkManager modules from the Kubuntu 6.10 CD, but KNetworkManager doesn't seem to be able to configure and use my wireless card properly.

I'll try re-blacklisting the r8187 driver, and I'll wrap the ME and 98 drivers tonight with reboots to make sure the drivers are reset fresh each time.

Funny thing is...I installed Linux on older hardware and it seemed to have no problem (cheap motherboard, cheap PCI WLAN card, etc).

That will teach me to build a new, top-line PC!! :D 

Thanks again.

---

### Post by ashram on 2006-10-31
For me only WEP worked... As I remember, this limitation comes from ndiswrapper or from driver... but I am not sure

---

### Post by Gizim on 2006-11-11
Hiddy do any update on this problem?
I have the same issue. Did the issue get resolved?

---

### Post by Big00wig on 2006-11-19
:???: aI just got this MoBo also. I have had nothing but troubles. When I first setup windows it connected to my wireless network no problem.. Then the next day I try to get on... Nothing. it says the wireless adapter is disabled or removed. I reload drivers, nothing. So I break down and reload Windows. Start it up. install the driver. Its working again. Everything good. I install the rest of the drivers and go on with my day. Well. then I'm playing a online game and it cuts out. Back to the same old problem. I can't seem to figure out what is wrong and I can't reformat my computer everyday. Does anyone have any advice? Thanks in advance.

Also. When I go to network connections it doesn't show a wireless adapter and it doesn't show one in Device Manager. :???:

---

### Post by jck on 2007-01-19
Big00wig...If you haven't already...go and update your BIOS.  I have heard the older BIOSes (no telling when your supplier got the board) had some issues.

I'm running Windows XP Professional x64 with Kubuntu and I have had no issues after the BIOS update, with the exception of the wireless card not talking to my router.

As I posted in the Networking and Wireless forum, I am about to spend the weekend getting an Encore 802.11 Super-g card installed and configured in Windows...will disable the on-board WiFi...then will reboot to the latest Kubuntu release and re-install and see if it will detect, configure, and utilize the new PCI card.

I will let you all know...in one forum or another...how it goes.

I really am dedicated (after seeing Vista Ultimate priced at $399 MSRP) to moving all of my boxes to Linux.  I would rather take and get Ubuntu or Kubuntu and send a $100 donation to them for a quality product...than pay for the execs at Microsoft $399 for Vista so that they can build 10,000xn square foot houses in Redmond.

I will let you all know about the Encore card.  If it works, you're only looking at about $30 to get the card in 3 days and installing it in place of the Realtek-based on-board wifi on the M2N32-SLI Deluxe

---

### Post by Zer0Nin3r on 2007-01-23
JCK, Been following your posts.  Any luck?  It just seems like wired would be the way to go with LInux.  I wouldn't mind the security with going wired, or making an attempt to utilize the Gb ethernet within the M2N32-SLI Deluxe motherboard.  Unfortneatly we share the internet connection with the neighbor...

---

### Post by goofeyfoot on 2007-03-19
Gents:

I have the same Asus motherboard with the same issues.

On writing to Realtek they referenced this fairly new Linux driver.  Here is what it is called.

rtl8187_linux_26.1024.0209.2007.tar.gz.  The guy from Realtek sent me this.

I tried this driver without success.  But I am real new to this Linux stuff so it could very well be that I screwed something up.

Would be curious to know whether you guys tried this new driver and whether I should pursue it further or whether this "new" driver is just another dead letter.

Look at what the realtek guy said about this driver:

"Dear Sir,

Thanks for your e-mail.

Attached file please find 8187 latest linux package which able to support Ubuntu 6.06.

If you have any questions, please let us know.

Regards,

Fred"

Sounds from the email like this driver works.  Am wondering what other peoples' experience is.


Thanks.

Michael

---

### Post by jck on 2007-03-21
Just an update:

I have been working with someone who (at least, compared to me) is a Linux guru.

I did download just last week the latest driver from Realtek for the 8187B (which seemed to be the one for USB WNICs, instead of the 8187L...please anyone correct me if I am wrong), as well as got the latest ndiswrapper and wpa_supplicant.

I had no luck with the newest ndiswrapper, so I fell back to 1.28 (I think).

I used the newest wpa_supplicant though.

Apparently things seem to install okay, but then when **iwconfig wlan0** (wlan0 is my wireless card), the ESSID still shows "off/any".

I ran **dmesg** to see what is going on, and I am getting all sorts of "atomic" errors in evidently what is wpa_supplicant trying to do things with my WNIC.

Has anyone else run into this problem?  Any solution?  Any thoughts?

The Linux guru I'm working with is stumped.  I just think that it being such a new piece of hardware, it's going to be time before "kinks" get worked out in getting it to work with external software to the *ubuntu core product, such as wpa_supplicant and/or ndiswrapper.

I am also going to try loading the 32-bit driver for Windows from my Asus CD.  I remember reading somewhere someone said to use that instead of the latest driver for Windows from the Realtek site.

My apologies for being so long in getting back to everyone, but I am working on so many things at work that my time has been limited and when I get home I am beat and want to just vegetate.

I will try to give more updates as I progress in figuring out how to resolve this issue with the Realtek 8187 chipset on the Asus M2N32-SLi Deluxe Wireless edition motherboard.

jck

---

### Post by goofeyfoot on 2007-03-21
Thanks for that update.  I will also post here if I ever get this thing worked out.

Another thread talks about using ndiswrapper to install the Win 98 drivers. A couple people reported success.  I tried that on mine, though and that didn't work.

What is aggravating is that when I load either the Win 98 driver or the newest Linux driver, I can always "see" the card but it seems to be inactive, IE it won't scan connect, or otherwise do anything useful.

Errrr!  Hopefully this will all get sorted out.

Michael

---

### Post by jck on 2007-03-21
I have had the same issue as well.

I have tried the Windows 98 driver with no luck either.

I have I also have the issue where it sees the proper channel...and even sees 54 MB/s...but, it for some reason won't see my wireless router even though I've configured the ESSID and key and protocol and all other settings ahs Wieman has said in another thread.

I will try to update as soon as possible.  I have another meeting in 15 minutes.  Have to go.

jck

---

### Post by jck on 2007-03-30
I just wanted to update.

I tried installing the 7.04 beta x64 desktop distro of Kubuntu with the following drivers:

Realtek for Windows-
    Win98SE/ME
    WinXP/2K
    x64

Asus for Windows-
    Win98
    WinME
    WinXP
    Win2K
    x64

I was trying to use the ndiswrapper that is default for 7.04 Beta x64 desktop distro.

All of the drivers from Realtek would not work.  I downloaded the latest 8187L drivers.

As for the drivers from Asus's motherboard CD:
Win98 would load, but not work
WinME would load into the wrong USB address
WinXP would load into the wrong USB address
Win2K would load into the wrong USB address
x64 would load into ndiswrapper, but once loaded give status "Netrtuw_x64         invalid driver!"

I would be curious to find out if it is an issue with the drivers themselves...or, the release of ndiswrapper with the distro being unable to wrap a 64 bit driver.

I'm back on the 7.04 Beta 32-bit desktop distro again.  Works like a champ.

thought I'd keep peeps up-to-date, and hope the development team looks into this issue.  Would love to be fully x64 by June.

thanks

jck

---

### Post by rodofilo on 2007-06-01
I have the same problem with my M2N32-SLI Deluxe/Wireless Edition the usb port is always busy with some drivers in tha moment is with Rialtek drivers, some one can help me

---

### Post by goofeyfoot on 2007-09-09
Wondering whether, after all this time anyone has found any fixes for this problems with the motherboard and its idiosyncratic wireless card.

Would love to hear from somebody if there's a fix.

Best regards.

Michael

---

### Post by goofeyfoot on 2007-09-09
I don't know for sure but I may have solved the wireless problem with the Asus board and Realtek wireless.

I will tell you what I did and we can all maybe get this thing worked out.

Basically I followed the technique shown on linuxquestions.org.

If you search on "NdisWrapper: The Ultimate Guide" the guy shows you the technique for using ndiswrapper.

When I followed the instructions, I concluded that the best driver matchup was the realtek drivers for Win98.

I got that driver from majorgeeks.com.

I installed the driver using the "Ultimate Guide" method shown above.

To get a better handle on stuff I added the "Wireless Assistant" application to Ubuntu.  Just made things more visible.

I used WEP security.

At first, the wireless assistant thing wouldn't connect.  Then, after rebooting the router it did.

I don't know whether this is going to continue to work.  If it does I have about thirty feet of cat5 cable strung across the floor that I won't be needing anymore.

Would wonder whether any of you other folks have any similar luck.

Best regards.

Michael

---

### Post by goofeyfoot on 2007-09-13
Gents:

Another update.  

As you can see from my last post I may have solved my problem with a Realtek 8187 on the Asus M2N32-SLI.  At least I hope that's the case

Wireless still working pretty good to date.

Have had a couple minor disconnects but discovered last night that the desktops' transmit antenna had fallen behind the computer and been ensnared by the many wires back there.  Maybe that accounts for the disconnects.  After I fixed the antenna last night the connection was rock solid.

Am hoping to have continued good luck.

In the meantime, I hope others will post their results here.

Thanks for reading.

Michael

---

### Post by hainesr on 2007-09-13
I assume you're using a 32bit Ubuntu are you? I'm on 64 bit and I'm struggling to find the right drivers...

Is there anyway to run a 32bit NDISwrapper in a 64bit Ubuntu?

Cheers,
Rob

---

### Post by goofeyfoot on 2007-09-13
Dear Hainsr:

Yes, you are right.  It is the 32 bit version which I am using.  Have not tried the other.

Have you tried the 98 version in 32 bit?  

If I see anything that discusses your setup I will post it here.

I wish you the best of luck.  This is something I have been messing around with since early this year.  I know exactly how frustrating it is for you.

Best regards.

Michael

---

### Post by bigmista on 2007-09-21
I am having the same problem on a Gateway mx8739 notebook with the rtl8187b chipset.

I have installed the ndiswrapper. I have installed the driver. I am able to see the card. I configured it with my WEP passcode but it just won't connect to my router.

Please help!

---

### Post by goofeyfoot on 2007-09-21
Hello:

If you are seeing the thing then that is good.

I would recommend that you shut down all of the security stuff and try to see whether that gets you connected.  You can add the security back afterwards.

I would also check the network tools thing under wlan0 to see whether you are getting assigned a good IP number.

I am not very versed in this Linux stuff and am probably still a newbie by any adequate measurement.

I know that this is not much solace but I messed around with this thing for months before I got it working.  There just isn't a lot of comprehensive information available, if you ask me.

Oh yeah, and I use wireless assistant which you can get right off the "add / remove" screen.

I just know that when the ndiswrapper thing went in I was able to see the network and connect. 

I know I haven't helped you much but it's as much as I know.

Keep the faith, I think you're almost there.

Michael

---

### Post by bigmista on 2007-09-23
I found a simple solution. I bought a Trendnet TEW-429UB Wireless USB Adapter and plugged it in. It connected right out of the box. That works for me!

---

### Post by go_beep_yourself on 2008-01-04
Isn't it supposed to be impossible to use a 32 bit driver in ndiswrapper with 64 bit Linux?

---

### Post by ViaD on 2008-01-14
Hi,

The driver do not support master mode..

$sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

The linux driver for the card is here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B")

It is very old though...

"Release Date: 2006-02-09, ver 1.2
RTL8187 Linux driver version 1.2"

And I'm not able to run ./makedrv without errors. I get the same error they describe 
in their faq, but I have both build-essentials and kernel sources installed.. 

But it do not matter... The driver from Realtek do not support master mode anyway..

  - Support Client mode for either infrastructure or adhoc mode
   - Support WEP and WPAPSK connection

---

### Post by bluefightingcat on 2008-02-08
Hi,

I just wanted to let you know that the RTL8187 driver is built into the kernel from version 2.6.23. I run Arch Linux (which is great) and I managed to setup the driver by just loading the rtl8187 module using modprobe. You might want to look at this wiki:

[http://wiki.archlinux.org/index.php/Rtl8187_wireless]("http://wiki.archlinux.org/index.php/Rtl8187_wireless")

The system then recognized my wireless interface. 

BFC

---

