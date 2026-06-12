---
title: "64-bit vs. 32-bit"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by kernco on 2007-11-17
I'm trying to decide if I should install the 64-bit version or not.  What problems and difficulties can I expect if I use the 64-bit version?  I'm already aware of the problems with flash and java browser plugins.  What else is there?

Also, does anyone have some actual data on the performance differences between the two?

---

### Post by kleeman on 2007-11-17
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by x64Jimbo on 2007-11-17
The java and flash issues have been resolved for 64 bit in Gutsy. I have personally seen great increases in performance on processor-intensive apps such as video encoding and rendering when running 64 bit, but most other apps do not exhibit any noticeable performance gain.

---

### Post by Kilz on 2007-11-17
> **x64Jimbo said:**
> The java and flash issues have been resolved for 64 bit in Gutsy. I have personally seen great increases in performance on processor-intensive apps such as video encoding and rendering when running 64 bit, but most other apps do not exhibit any noticeable performance gain.

The java issue is not solved for Gutsy. Icedtea and Blackdown only work for some sites. The only way to get every site is installing a 32bit browser. That has been available since Dapper.


Is this going to be yet another useless thread rehashing the same old tired question that is referenced in the stickies? One that will go on and on with little facts and opinions (mostly by new users who cant resist these types of threads) and say the exact same thing countless other topics that have the same subject have already done?

The search is your friend.

---

### Post by stmiller on 2007-11-18
> **Kilz said:**
> The java issue is not solved for Gutsy. Icedtea and Blackdown only work for some sites. The only way to get every site is installing a 32bit browser. That has been available since Dapper.



I think that is exactly what that person means, as they said, 'java and flash.'

As far as performance:

I get about 10FPS *faster* encoding with 64bit Handbrake vs. 32bit Handbrake to encode DVDs, as x264 can make use of 64bit goodness. LAME 3.97 encodes mp3s slightly *slower* in 64bit vs. 32bit, as it is not coded to take advantage of 64bit.  Etc, etc, etc, etc.
 
So basically, it depends if the program is written to take advantage of 64bit. There are wikipedia articles on this, as well as plenty of threads on this already in this [forum]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+64bit+vs.+32bit&btnG=Google+Search").

---

### Post by x64Jimbo on 2007-11-18
> **Kilz said:**
> The java issue is not solved for Gutsy. Icedtea and Blackdown only work for some sites. 
Hm. I haven't had any problems. Sorry to mislead.

---

### Post by Kilz on 2007-11-18
> **x64Jimbo said:**
> Hm. I haven't had any problems. Sorry to mislead.

I dont think you were trying to mislead anyone. Since some sites work and others dont, its possible you may not visit the ones that dont work.  Just letting you and the op know that there are some people that still have issues with Blackdown and icedtea. The good news is that a 64bit sun plugin should be released with java 7 that is now under development. So there is a light at the end of the tunnel.

---

### Post by binary_bob on 2007-11-18
Kilz,
Maybe we won't have to wait for Java 7
check this out.
[http://infoworld.com/article/07/10/18/sun-rework_1.html](http://infoworld.com/article/07/10/18/sun-rework_1.html)

---

