---
title: "ubuntu 64bit for core2duo notebook"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by dhawald3 on 2007-05-02
I am going to buy a core 2 duo (T5xxx series) powerd laptop.
and I am thinking of installing AMD64 version of ubuntu on it.


Or I will be better off with the 32bit version??

please help.

---

### Post by jespdj on 2007-05-02
The Intel Core 2 Duo processor does have 64-bit extensions, so the 64-bit version should work fine.

Just download a 64-bit Ubuntu CD image, burn it onto a CD and try to boot your laptop with it, and you'll see if it works without problems.

---

### Post by skibrianski on 2007-05-02
First, welcome!

Check out the sticky threads, in particular this one:
[URL="http://ubuntuforums.org/showthread.php?t=368607"]http://ubuntuforums.org/showthread.php?t=368607
[/URL]
which outlines the plusses and minusses. I have a core2duo dell d520 and everything works great in 64-bit mode. In general tho, if you don't want to spend a few hours getting everything configured, you should probably stick with 32 bit. But if you want all of your hardware's performance and don't mind dropping a few hours and learning something, I'd say go 64-bit.

As for programs not available in 64-bit mode, there is no flash9 or java plugin, so you have to jump thru a few hoops to make that stuff work by running firefox (or opera/konq/etc.) in 32-bit mode. You might also have some problems with media, but that can be avoided by getting w64codecs in my experience. There's also the possibility that some hardware you have won't have a 64-bit driver when it does have a 32-bit driver.

---

### Post by DJiNN on 2007-05-02
Just grab your flavour of X/K/Ubuntu 64, install in the usual way, then get [Automatix2]("http://www.getautomatix.com") and install that, then run it. It's as easy as that!

Automatix will give you a lot of choice with setting up progs etc, and also install all of the relevant 64 bit Codecs that you may need, and should also take care of the Firefox stuff as well...... 

It couldn't get any easier really. :)

DJiNN

---

### Post by n3twrkm4n on 2007-05-02
I used the AMD64 version of the ISO images on my HP T7200 Core2Duo laptop and things worked great. Model NC8430. Everything was recognized including the video card (Radeon) and resolution 1680x1050. WiFi worked (Intel A/B/G... I forget the model) and I have not tried Bluetooth yet. 

I had SuSE 10.2 installed with KDE but it was dog slow. Ubuntu Feisty is very responsive, and I highly recommend it. One thing I noticed is that if you have the WiFi radio turned on, boot times increase by 20%. Easily solved by turning off the radio (I have a button on the laptop).

Good luck!

---

### Post by colinsanter on 2007-07-14
> **DJiNN said:**
> Just grab your flavour of X/K/Ubuntu 64, install in the usual way, then get [Automatix2]("http://www.getautomatix.com") and install that, then run it. It's as easy as that!

Automatix will give you a lot of choice with setting up progs etc, and also install all of the relevant 64 bit Codecs that you may need, and should also take care of the Firefox stuff as well...... 

It couldn't get any easier really. :)

DJiNN

I am using Ubuntu 7.04 Feisty Fawn on a ACER Aspire 5050 with an AMD Turion 64, and ATI radeon Xpress graphics card. Automatix2 sorted out all my problems. I now have flash and sound in Firefox.

Stunningly easy. 
Thank you :guitar:

---

### Post by elfstone214 on 2007-07-14
IMO if you don't need 64bit you should stick with 32bit Ubuntu. There is nothing wrong with 64bit but you will have to take the time to patch flash, and you may have to chroot to run certain 32bit applications. If you don't actually need 64bit (like me for my work) I wouldn't bother with it.

---

### Post by DJiNN on 2007-07-17
> **colinsanter said:**
> I am using Ubuntu 7.04 Feisty Fawn on a ACER Aspire 5050 with an AMD Turion 64, and ATI radeon Xpress graphics card. Automatix2 sorted out all my problems. I now have flash and sound in Firefox.

Stunningly easy. 
Thank you :guitar:

That's good to hear. I've run the 64bit version of all the Buntu's (K/X/U) & they've all worked really well and in general have not proved any more hassle then the 32 bit version, especially when coupled with Automatix.  The worst of the bunch for me personally was Kubuntu..... it looks great, but i just had so many problems with it.  :) 

I'm still using the 64 bit Xubuntu on my AMD & it's working fine & has been since the day that i installed. 

DJiNN

---

### Post by Kilz on 2007-07-17
> **elfstone214 said:**
> IMO if you don't need 64bit you should stick with 32bit Ubuntu. There is nothing wrong with 64bit but you will have to take the time to patch flash, and you may have to chroot to run certain 32bit applications. If you don't actually need 64bit (like me for my work) I wouldn't bother with it.

This is partly FUD and partly untrue. You dont have to patch Flash. You could run 32bit Firefox and 32bit flash(install script in my signature). You could also use nspluginwrapper on the 64bit Firefox, but its a wrapper and not a patch. It isnt hard to do, 30 seconds and the script in my signature will have nspluginwrapper working.
I have yet found a need to run a chroot to run any 32bit applications. 32bit applications will install to the 64bit install. Its a little work, but so is installing and running a chroot and chroot applications. Granted maybe you are running something I have not tried, would you please list the 32bit applications you say you need a chroot to run?

---

### Post by elfstone214 on 2007-07-17
> **Kilz said:**
> This is partly FUD and partly untrue. You dont have to patch Flash. You could run 32bit Firefox and 32bit flash(install script in my signature). You could also use nspluginwrapper on the 64bit Firefox, but its a wrapper and not a patch. It isnt hard to do, 30 seconds and the script in my signature will have nspluginwrapper working.
I have yet found a need to run a chroot to run any 32bit applications. 32bit applications will install to the 64bit install. Its a little work, but so is installing and running a chroot and chroot applications. Granted maybe you are running something I have not tried, would you please list the 32bit applications you say you need a chroot to run?

blah blah FUD this FUD thath ... the firefox copy that comes with Ubuntu amd64 does NOT work with flash .... that is a FACT. whatever you do ... you have to do SOMETHING to fix it.

> **Kilz said:**
> I have yet found a need to run a chroot to run any 32bit applications. 32bit applications will install to the 64bit install. Its a little work, but so is installing and running a chroot and chroot applications. Granted maybe you are running something I have not tried, would you please list the 32bit applications you say you need a chroot to run?

crossover linux.... just because you have not run into one doesnt mean they don't exist :rolleyes:

lastly, you need to relax you seem to throw the FUD around whenever someone "insults" your precious 64bit.

---

### Post by tgm4883 on 2007-07-17
> **elfstone214 said:**
> blah blah FUD this FUD thath ... the firefox copy that comes with Ubuntu amd64 does NOT work with flash .... that is a FACT. whatever you do ... you have to do SOMETHING to fix it.



crossover linux.... just because you have not run into one doesnt mean they don't exist :rolleyes:

lastly, you need to relax you seem to throw the FUD around whenever someone "insults" your precious 64bit.

News flash, the 32-bit Firefox thats comes with 32-bit Ubuntu does NOT work with flash either, also a FACT.  You have to do SOMETHING to fix it.  (install flash plugin)

In both instances, you have to fix it, but the fix isn't that hard.  Making people scared to run 64-bit OS's over such a non issue is pretty lame.

---

### Post by praxis22 on 2007-07-18
> **elfstone214 said:**
> blah blah FUD this FUD thath ... the firefox copy that comes with Ubuntu amd64 does NOT work with flash .... that is a FACT. whatever you do ... you have to do SOMETHING to fix it.


By default flash doesn't work on a clean install of XP either, what's your point? You did chose of you own free will to install a 64bit variant of Ubuntu I take it?

> 
lastly, you need to relax you seem to throw the FUD around whenever someone "insults" your precious 64bit.

This is the only explicitly 64bit forum here, precious indeed.  But it's not an insult to spread FUD, just small minded and mean spirited. 

Different strokes for different folks I guess, 64bit 7.04 works fine on my core 2 duo. Hell, I replaced my entire CPU and motherboard, switching from AMD to Intel in the process, without so much as hiccup. Flash didn't work originally, but either Automatix or a community script worked fine. YMMV

---

### Post by jcronkhite on 2007-07-18
I think our goal here is to get people to run and enjoy Ubuntu, specifically 64bit in this particular area of the forums.  I'm running the 64bit version and it is great.  I recently found the Flash wrapper thread [here]("http://ubuntuforums.org/showthread.php?t=426921") and got it working beautifully.  I was about to switch back to 32bit, but now I don't need to.  Flash playback was the last thing on 64bit I felt I needed.

In any case, back to the original issue.  I am thoroughly enjoying the 64bit version of Ubuntu Feisty on my hp Core 2 Duo laptop.  If you will be doing things that are process intensive like video/audio editing, etc., you'll likely notice a difference in performance from the 32bit version.  If not and you feel more comfortable with 32bit in general, then just go for that version.  But don't be afraid of 64.  Like I said, I've been enjoying it.  No FUD, no offense.

---

