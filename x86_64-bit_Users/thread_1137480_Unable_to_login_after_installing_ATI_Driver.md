---
title: "Unable to login after installing ATI Driver"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by browntown on 2009-04-25
Hello,

Today is the day that I installed Ubuntu on my second hard drive. I have had the disk since 8.1 was released but today I downloaded 9.04. I have no, wait, very little experience with Linux. I played around with the Live CD for a little bit but I am a complete noob.

So I did not like the display on Firefox once I got into it. I decided to install the ATI Catalyst Display Driver 9.4. Man, was that a fun experience! After reading, reading and more reading, I finally got it to install. It takes a little while to get used to using the terminal and all that jazz...

Now, when I go to log into Ubuntu, I get the Ubuntu screen with the status bar moving, but then the screen goes "funny". There are random "digitals", if you can call them that but I cannot log in and I cannot hear the bongo's when/if I type anything.

I am running:
AMD Athalon 64 Processor 3800+ 2.4Ghz
4Gb RAM
Onboard video - ATI Raedon Express 1250.

I have tried to login to the recovery but it seems a little over my head.

Any help would be greatly appreciated.

---

### Post by MidGe48 on 2009-04-25
I had the same problem. Fixed it this way, NOT using catalyst!

Run the following from the command line:
aticonfig --initial -f

Then rebooting and everything was dandy for me at least.  :smile:

Hope this help you!

---

### Post by GerMulvey on 2009-04-26
Catalyst 9.4 does not support your 1250 - this is now legacy hardware and the last driver to support was 9.3
Also due to the implementation of xserver 1.6 and the fact 9.3 has no support for this is another issue.
aticonfig --initial -f didn't work for me so for me i had to boot using the failsafe and open the root option, then I apt-get removed the fglrx components. This allowed me to recover the desktop. If you don't have data you need to save it may be quicker to just re-install. aAsyou say your new to linux you might find that an easier option.

The current opensource radeon driver works pretty good (not perfect) but it's your best option.

---

### Post by gyaneshwar on 2009-04-26
I also had a problem after upgrading to 9.04.

My ati x1650 started to play funny and finally I had to do:
apt-get remove --purge xorg-driver-fglrx

---

### Post by browntown on 2009-04-26
Thanx for all of the reply's! I have tried running aticonfig --initial -f, this did nothing.
I tried apt-get remove --purge xorg-driver-fglrx, and it told me the components were not installed. 

I think the apt-get remove will work, I am just not sure where to find what needs to be removed??? Should this not be Catalyst or ATI Catalyst or something to that affect? I will re-install if I have to, but I would rather get my hands dirty now and try to troubleshoot this head on. 

This is the driver(9.4 - Release date: 4/16/09) that I downloaded:
[ATI Catalyst&#8482; Proprietary Display Driver - Linux x86 & Linux x86_64]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.5.3.2.3.2&lang=English&rev=9.4&ostype=")

I have also tried to unistall/reinstall the ATI drivers through the ENVYNG text option, logging in using recovery mode and using the root command. I get the message: failed to fetch [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com). The uninstall went through ok, but I still have the same issue when trying to log in normally. 

Once again, thanx for the help and any advice will be greatly appreciated!

browntown

---

### Post by browntown on 2009-04-30
Well I broke down and re-installed Jaunty. All is mostly working well now. Thank you for all the help!

---

