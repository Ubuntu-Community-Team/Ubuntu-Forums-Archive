---
title: "comfirmed java +firefox"
date: 2005-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-05-17
how many of you out ther have gotten java to work with firefox without chrooting??

---

### Post by harryc on 2005-05-17
I did it using this method.

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

Is there a problem with that method?

---

### Post by w4e on 2005-05-17
No worries whatsoever. Just install the JRE (or if you're a developer, the JDK) and link the libjavaplugin.so from your plugin directory.

---

### Post by blinksilver on 2005-05-17
so let me get this right, WITHOUT chroot, you just got a copy of the 32bit version of java and it worked???? how is that possilbe???

btw, (except for blackdown, which refuses to work) there is no 64bit java plugin

---

### Post by Jarz Corp on 2005-05-18
My two cents.

I have tried both the blackdown, which is one or two versions behind the one from sun (aka the Microsoft Unix Company).

I didn't have any problems with any of them, of course I had to manually create links for webplugin etc, but after having done that a couple of times to test the difference betweeen blackdown and suns own U will be able to do that in your sleep.

Can't remeber where I found the Sun 64 bit 1,4 jre, but I will look into that in case U want to install that version. As microsoft/Intel/Sun/Etc doesn't want to support the personal 64bit market, U have do a lot of looking around on the sun website to find it, U cant even search your way to it.

Sorry about the rant, but I am getting so p. off with all the hassle of running on a system based on a 2 year old cpu arch.

And no way in .... am I going to chroot, if I want to run 32 bit on my 64 bit cpu I simply boot into XP.

---

### Post by AndreAPL on 2005-05-21
[QUOTE=Jarz Corp]My two cents.

I have tried both the blackdown, which is one or two versions behind the one from sun (aka the Microsoft Unix Company).

I didn't have any problems with any of them, of course I had to manually create links for webplugin etc, but after having done that a couple of times to test the difference betweeen blackdown and suns own U will be able to do that in your sleep.

Can't remeber where I found the Sun 64 bit 1,4 jre, but I will look into that in case U want to install that version. As microsoft/Intel/Sun/Etc doesn't want to support the personal 64bit market, U have do a lot of looking around on the sun website to find it, U cant even search your way to it.

Sorry about the rant, but I am getting so p. off with all the hassle of running on a system based on a 2 year old cpu arch.

And no way in .... am I going to chroot, if I want to run 32 bit on my 64 bit cpu I simply boot into XP.[/QUOTE]
 there is avaiable sun jre1.5.0.03 for 64bits linux ....

---

### Post by blinksilver on 2005-05-21
but it is the hotspot server version and hence does not have a web plugin

---

### Post by Jarz Corp on 2005-05-21
blinksilver is absolutely right, it is not worth anything except for running java apps locally and only a few at that, everything else doesn't work/isn't included yet.

I will pull my finger out of . . . and try and find the 1.5 64 bit with webstuff I have downloaded once, but as I said previously it is well hidden on the sun site, they do not wish to piss off microsoft by starting to support 64bit on personal pc's.

---

