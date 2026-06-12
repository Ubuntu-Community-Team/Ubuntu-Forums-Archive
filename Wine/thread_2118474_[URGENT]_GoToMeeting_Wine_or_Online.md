---
title: "[URGENT] GoToMeeting Wine or Online"
date: 2013-02-21
forum: Wine
---

### Post by CedArctic on 2013-02-21
Dear forum users,

 I made a huge overatlantic trip to attend a meeting in the USA. Also I will be needing to make a very serious web meeting in 2 days (23/2/13) with the GoToMeeting. My netbook has Ubuntu and Windows 8 dual booted. This morning my Windows 8 partition failed and had a blue screen. The PC restarts multiple times but nothing happened. So I need to run GoToMeeting on ubuntu (v: 12.10). Can I run GoToMeeting with wine? Also I know the GoToMeeting Online Viewer exists. But how do you access that? I assume the web viewer is cross platform. Please help me to run through wine or show me how to access the web viewer! It is urgent for my business! Thank you very much!

---

### Post by oldos2er on 2013-02-21
According to [this]("http://community.gotomeeting.com/gotomeeting/topics/go2meeting_for_wine_hq") GoToMeeting doesn't work in Wine.

---

### Post by kurt18947 on 2013-02-21
Certainly not a perfect solution but if you can't get Windows 8 to start, buy a copy of Windows 7 or 8 locally?  You could also do this - I think it's legal but I'm not an attorney.

You can download legitimate Windows 7 images online and burn to DVD using Ubuntu then install.  It would probably be wise to create a live Ubuntu disk and maybe a boot recovery disk.  I'd expect a Windows install to mess up GRUB.    Here is the download site:

[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)

The Windows 7 install would become illegal in 30 days but presumably you'd be home and able to restore your machine before the 30 days expires.  On the other hand,  if you have a legitimate Windows 8 license,  the Windows 7 install may be fine.  In some cases, you can install a previous version of Windows under a current license and be legal.  PCs coming with Vista and 'downgrading' to XP is one example.  Windows licensing is so complex I have no real idea.  

The other concern would be drivers.  If you install Windows 7, you'd want to make sure at least basic video and networking were available.  You could do 'lsusb' and 'lspci' and make note of things like ethernet & wireless adapters, video chipset,  webcam and see if there are Windows 7 drivers available for them.  There is an app in the repositories called "hardinfo" that may give a more detailed inventory of your hardware.   It would be a task but it should be doable.  Good luck, I hope you're able to work it out.

---

### Post by Mark Phelps on 2013-02-21
Obtaining Win8 does NOT automatically come with downgrade rights to Win7.  You need to know this before you go down this path ...

In SOME cases, new Win8 Pro machines come with Win7 downgrade rights -- but it varies by machine.  Simply having one is no guarantee. You would really need to check with the supplier of the Win8 machine because you will need a totally different KEY to activate Win7 -- and you can only get that (as a downgrade) through the machine supplier.

Preinstalled Win8 Home machines (generally) do NOT come with downgrade rights. So, if you bought one of these, you're out of luck regarding downgrading.  It doesn't hurt to check with the machine supplier, but they'll most likely say NO -- you can't downgrade.

---

### Post by CedArctic on 2013-02-21
Guys, I have lost all faith in windows on this laptop, and since I am in an area I don't really know, aqcuiring Windows Discs and committing an installation is nearly impossible, I may just need to buy a new laptop, cause this business is seriously important to me. Just please focus on these : Windows does not even boot, meeting tomorrow!, I have ubuntu, So I can't run GoToMeeting, is there any access to the webviewer? Thank you.


I Appreciate all the answers I got! Helped a lot up to here~!:popcorn:

---

### Post by Lightning Dragon on 2013-02-22
You can try to install a Virtual version of Windows and run it from there. You can try these evaluated versions;

[http://www.microsoft.com/en-us/download/details.aspx?id=11575](http://www.microsoft.com/en-us/download/details.aspx?id=11575)

Other than that, this page here; [http://support.citrixonline.com/en_US/gotomeeting/all_files/GTM130018](http://support.citrixonline.com/en_US/gotomeeting/all_files/GTM130018)

Says that you don't need to download anything, you just need a browser to use the Web Viewer. Please see this link for how to use Web Viewer.

[http://support.citrixonline.com/en_US/gotomeeting/all_files/GTM130019#enabled](http://support.citrixonline.com/en_US/gotomeeting/all_files/GTM130019#enabled)

It says;

> 
**What are the system requirements for the Web Viewer?**         
         
[LIST]
[*]Firefox 4.0+, Internet Explorer 7.0+, Chrome 5.0+ or Safari 3.0+
[*]Flash Player 10.0+ (attendees will be prompted to install or upgrade)
[*]JavaScript enabled
[/LIST]
          
         **Does the Web Viewer work on Mac or Linux systems?**         
         Yes, the GoToMeeting Web Viewer works on Mac and Linux  systems that meet the above requirements (even though GoToMeeting does  not officially support Linux). If you have difficulties using the Web  Viewer on Linux, our Global Customer Support team cannot help you.

Install Firefox 4.0 or newer if you haven't already (or try IE if you want), install the latest Flash Player, install the latest JavaScript and make sure it is enabled. Next go to your account and do the rest. :)

Good luck!

---

### Post by kurt18947 on 2013-02-22
If you can make Lightning Dragon's idea work, that seems the way to go.  If you can't, buying another laptop might not be the worst idea.  Buy it, use it,  then take it home  and sell it or pay the restocking fee to return it. I don't know where you are in the U.S. but "big box" stores are everywhere.  I'm on the East Coast of of the U.S. and common names are Staples, Office Max, Best Buy and Walmart.  I was recently in a Best Buy and saw this:

[http://www.bestbuy.com/site/Toshiba+-+Satellite+15.6%22+Laptop+-+4GB+Memory+-+320GB+Hard+Drive+-+Satin+Black/7704082.p?id=1218858584798&skuId=7704082]("http://www.bestbuy.com/site/Toshiba+-+Satellite+15.6%22+Laptop+-+4GB+Memory+-+320GB+Hard+Drive+-+Satin+Black/7704082.p?id=1218858584798&skuId=7704082")

**Toshiba - Satellite 15.6" Laptop - 4GB Memory - 320GB Hard Drive - Satin Black**

**[SIZE=4]$279.99[/SIZE]**


Processor AMD E-Series
Processor Speed 1.3GHz


System Memory (RAM) 4GB



Graphics AMD Radeon HD 6310


Built-in Webcam Yes
Networking Built-in 10/100 Ethernet LAN (RJ-45 connector)


Wireless Networking Wireless-B+G+N



Operating System Windows 8  


In Best Buy's case, there is this complication to returning and paying a restocking fee:


**What type of ID is required for returning or exchanging an item in store?**

              We accept the following forms of identification: US, Canadian or  Mexican driver's license; US state-issued ID; Canadian province-issued  ID; Matricula Consular; US military-issued ID; passport; US Laser Visa;  or US permanent resident ID.


Good luck.  I hope you're able to work it out.

---

### Post by CedArctic on 2013-02-22
Wow! Thanks for the replies... today I had this ingenious idea: Make the meeting from my Android Smartphone, apparently the smartphone failed too! BAD LUCK :mad: ! Although I intend to buy another laptop as kurt said, if I cannot locate a tech shop near by, I will try to reinstall windows as Dragon said. Thanks for all the support guys, makes me feel like I have a huge family in this community!

---

### Post by Mark Phelps on 2013-02-22
Not trying to push you away ... but if the goal is to get Windows BACK on the PC and working, you might do better going to a Windows forum -- where they have forum sections and tutorials.

For Windows 8, go to eightforums.com.

For Windows 7, go to sevenforums.com

---

### Post by superchar42 on 2013-02-22
If you don't *have* to do video, then you can call in using your phone. 

When my job requires me to use gotomeeting, I get on my mom's computer. 

PLEASE email citrix and tell them you want Linux capabilities. They said to me their engineers have plans but no implementation date.

---

### Post by kurt18947 on 2013-02-22
This thread has made me think.  I don't travel much right now but if I did, I think I'd create a complete image of any Windows partitions on DVDs and carry them with me.  If Windows gets corrupted, I could restore the image and be back in business, including apps.

---

### Post by CedArctic on 2013-02-23
Hey guys, well thanks again for the replies. I contacted the meeting host and we arranged for me to join via phone (thanks superchar42), also I will be keeping an acronis image of my dual-boot (thnx kurt) and finally yes my goal is to reinstall windows but after I go back home (appreciate the sites Mark Phelps). Thank you all for the help and resolving of my issue! Makes me feel welcome to the ubuntu community! :popcorn:

---

### Post by CedArctic on 2013-02-23
YES! Someone should email them! MAN have they have not been working for the linux support?! I just emailed them!

---

