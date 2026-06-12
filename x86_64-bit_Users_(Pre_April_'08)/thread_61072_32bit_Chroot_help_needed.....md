---
title: "32bit Chroot help needed...."
date: 2005-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by dickohead on 2005-08-30
Hey guys,

THis problem is pretty massive, but i will try and keep it as simple as i can.

**1** - I am trying to run ConsoleOne in Ubuntu (64bit)
**2** - Alien will not convert the packages for ConsoleOne from rpm to deb because i am on a 64bit system and the packages are 32bit
**3** - how do i create a chroot from which i can run alien on these rpm files (there are 62 rpm files for consoleone - joy joy joy) so that then i can have my debs to install ConsoleOne as a 32bit app

I'm assuming i'd also then need 32bit Java inside that chroot? And then set up links so ConsoleOne can find it......

Now so far my understanding is that a chroot environment for 32 bit applications is like another Linux system, but with only the programs you wish to run in it... ie:

/ - everything
/chroot - all 32bit apps
/chroot/ConsoleOne - eventually where consoleone will run from

Is the above correct?

This is for a school project - the aim is to attempt and replace the need to administer Netware 6.5 from a windows machine Using FREELY available Linux, Ubuntu is my choice since RedHat and SuSE already have the rpm's it was only a matter of installing them.... I wanted to actually have a really hard time getting everything to work.......... Contemplating using SuSE 9.3.

---

### Post by FLeiXiuS on 2005-08-30
So first off, I'll let you know that YOU DIDN'T READ THE RULES.  

The howto forum is not a place to ask questions!  It's a place to give instructions on HOW TO do something.  

Secondly, I've moved your post to AMD-64bit.

Third, if you do a quick forum search on "32bit chroot" you'll find a lot of wonderful things such as... [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by dickohead on 2005-08-31
[QUOTE=FLeiXiuS]So first off, I'll let you know that YOU DIDN'T READ THE RULES.  

The howto forum is not a place to ask questions!  It's a place to give instructions on HOW TO do something.  

Secondly, I've moved your post to AMD-64bit.

Third, if you do a quick forum search on "32bit chroot" you'll find a lot of wonderful things such as... [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)[/QUOTE]
 i have read the rules, i simply put it in the wrong forum, appologies.

I have read that page multiple times and am still unable to figure it out, if anyone has ConsoleOne running could they possibly let me know? Thanks.

---

