---
title: "Will opening up of FlashPlayer etc. lead to real 64bit flash for linux?"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by keeler1 on 2008-05-01
I was reading an article on [LinuxInsider.com]("http://www.linuxinsider.com/rsstory/62842.html") about Adobe deciding to open source Flash.  They are initiating something called the Open Screen Project.

Supposedly they are going to 

> open access to Adobe Flash technology by removing restrictions on use of the SWF (Shockwave Flash) and FLV/F4V (Flash Video) specifications. It will publish the device porting layer application programing interfaces for Adobe Flash Player, publish the Adobe Flash Cast protocol and the AMF (Action Message Format) protocol for robust data services, and remove licensing fees, which would make the next major releases of Adobe Flash Player and Adobe AIR for devices free.

Will this lead to reliable 64 bit flash for linux?  Flash works, sortof on my 64bit system right now but definitely not well.  Hopefully, this move by Adobe will give us all what we want.

---

### Post by Yellow Pasque on 2008-05-01
We won't have "real" 64-bit Flash until Adobe opens the actual code or compiles a 64-bit version. However, releasing the specifications does give open source projects like Gnash and swfdec a chance at releasing a fully compatible open-source alternative.

---

### Post by scragar on 2008-05-01
if they do make it open source it should get rid of all the annoying little quirks that flash exibts(such high CPU usage, not intigrating properly, 64 bit version that works, stop crashing if I do something more CPU intensive than it(why does this happen BTW? nothing else crashes just because something is choking it of CPU) etc...).

---

### Post by Yellow Pasque on 2008-05-01
Look into the Flashblock add-on for Firefox/Mozilla. It replaces Flash ads with a play button, so you can view Flash content only when you want to. I had a problem with Flash crashing FF on certain pages (always ads that I didn't want to view anyway) with my Arch Linux install because I was using the latest release (r124). Flashblock stopped that.

---

### Post by Sef on 2008-05-04
> We won't have "real" 64-bit Flash until Adobe opens the actual code or compiles a 64-bit version. However, releasing the specifications does give open source projects like Gnash and swfdec a chance at releasing a fully compatible open-source alternative.

I would like to use GNash, but it is only fully compatible up to Flash 7.  Flash 8.5 and 9 are being worked on.

---

### Post by tastefulasever on 2008-05-06
This makes things  quite a bit easier for the devolopers of gnash and similar projects.  I expect that there will be a full 64-bit flash 9 compatible player in the not too distant future.

---

### Post by rajeev1204 on 2008-05-06
> **Sef said:**
> I would like to use GNash, but it is only fully compatible up to Flash 7.  Flash 8.5 and 9 are being worked on.




swfdec is a revelation. U should try it from hardy.All the time i used to install gnash due to it being mentioned too many times on the forums.It doesnt play nothing.

This time i installed swfdec. You tube works !

---

### Post by Sef on 2008-05-07
> swfdec is a revelation. U should try it from hardy.All the time i used to install gnash due to it being mentioned too many times on the forums.It doesnt play nothing.

This time i installed swfdec. You tube works !

Thanks for that.  I hadn't thought of trying that.

---

