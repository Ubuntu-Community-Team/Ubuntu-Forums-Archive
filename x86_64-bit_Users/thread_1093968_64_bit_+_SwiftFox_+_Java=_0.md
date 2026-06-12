---
title: "64 bit + SwiftFox + Java= 0"
date: 2009-03-12
forum: x86 64-bit Users
---

### Post by d_fiant_1 on 2009-03-12
I installed Ubuntu 8.10 64 bit the other day, it certainly is a step up from other 64 bit versions.

I got flash work without a drama, but when it comes to Java I have a problem....Java works fine in Firefox after a link has been put in it 'plugins' folder, but I am using Swiftfox web browser and I couldn't get Java working in Swiftfox. I have even linked Java in Swiftfox's 'plugins' folder but no go. Flash works fine in Swiftfox, just not Java.

Yes, Java is enabled in both browsers.

Any Ideas?

---

### Post by nikgare on 2009-03-12
Does Java show up in about:plugins in Swiftfox?

---

### Post by d_fiant_1 on 2009-03-12
yeah it does :-(

libnpjp2.so

    File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_12 	Java 		Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by stchman on 2009-03-12
I thought Swiftfox was defunct?

---

### Post by d_fiant_1 on 2009-03-13
> **stchman said:**
> I thought Swiftfox was defunct?

no, I have been using since I started using ubuntu, 2 years ago, tried swiftweasel as well, but swiftfox was prettier :-)

---

### Post by stchman on 2009-03-13
> **d_fiant_1 said:**
> no, I have been using since I started using ubuntu, 2 years ago, tried swiftweasel as well, but swiftfox was prettier :-)

I see.  I thought Swiftfox was Firefox compiled for a certain processor architecture.

Does using Swiftfox really make a difference?

---

### Post by d_fiant_1 on 2009-03-14
> **stchman said:**
> I see.  I thought Swiftfox was Firefox compiled for a certain processor architecture.

Does using Swiftfox really make a difference?

Basically it is, as is swiftweasel. I think it makes a difference, for me it seems to use less ram and is quicker.

I have since discovered that SwiftFox isn't actually a 64 bit browser and probably hasn't been updated in a while, so I have decided to go back to Swiftweasel.

You can use most of the Firefox plugins and themes in swiftfox and swiftweasel.

But if you want to know, give swiftweasel a go for yourself

---

### Post by d_fiant_1 on 2009-03-14
I'm playing around with quite a few browsers at the moment. Opera, Epiphany, SwiftWeasel, Konqueror and Flock.

So far, Flock, Konqueror and Epiphany suck big time as far as the 64bit Flash plugin goes. I'm sure you can get it to work, but iclick and install as it wants to install the 32 bit version Flash.

Opera and Swiftweasel install the 64 bit Flash in their 64bit version web browser without a drama, but I have found that some website will not support Opera, namely some apps in Facebook and a couple of match maker websites have removed support for Opera and will not load.

So to me, that leaves SwiftWeasel as the pick of the crop because it just works and you barely have to do a thing. It is easy to import bookmarks and settings from Firefox and it will use a huge chunk of Firefox's addons and themes.

---

### Post by northwestuntu on 2009-03-30
only bad thing is it's never updated.

---

