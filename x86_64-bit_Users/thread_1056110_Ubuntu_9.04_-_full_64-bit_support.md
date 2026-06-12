---
title: "Ubuntu 9.04 - full 64-bit support?"
date: 2009-01-31
forum: x86 64-bit Users
---

### Post by MarcowyKocur on 2009-01-31
Hi.

I'm just wondering if someone know... We've java/flash x64. So, will we have in new Ubuntu native Firefox x64 with posibility of installing those programs from repository? Without problems such: "How to install sth. 32-bit...".

Anyone?

---

### Post by jespdj on 2009-01-31
The current 64-bit Flash 10 from Adobe is still a beta version (as far as I know), even though it works great. I don't know exactly what the policy is, but it might be that it's not going to be included because it's beta software. The same for Sun Java 6 update 12, which contains Sun's 64-bit Firefox plugin.

Let's hope that Flash and Java 6 update 12 will be out of beta in time for Jaunty, so that all the hassle with these two things on 64-bit Ubuntu can finally be over.

---

### Post by zika on 2009-01-31
what about(dmesg) : warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
is that happening also in Jaunty?

---

### Post by Yellow Pasque on 2009-01-31
Java 6u12 (which includes the Java64 plugin) is scheduled to be released shortly and Ubuntu devs expect to have it in Jaunty:
[https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)

I don't see any official bugs or developer discussion of using the Flash64 Alpha. Hopefully, a release version of Flash64 will be out in time to have it included in Ubuntu 9.10

> what about(dmesg) : warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
is that happening also in Jaunty?
This is a harmless warning (until legacy capabililty support is phased out of the kernel). Yes, it still occurs in Jaunty Alpha 3. I posted a comment in the bug report inquiring if it will be fixed for Jaunty.
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/248577](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/248577)

---

### Post by sanderj on 2009-02-01
> **MarcowyKocur said:**
> Hi.

I'm just wondering if someone know... We've java/flash x64. So, will we have in new Ubuntu native Firefox x64 with posibility of installing those programs from repository? Without problems such: "How to install sth. 32-bit...".

Anyone?

My Athlon 64 has been running 64-bit Ubuntu since 2007, and I've never experiences any problems: I just install everything via the repositories and everything works.

So for me Ubuntu has "full 64-bit support" since 7.10.

---

### Post by dBuster on 2009-02-01
I bought a new laptop which would not take an Ubuntu load of anything but the alpha 3 of Jaunty/9.04!

I have been running stable now for a few weeks with full 64bit support in firefox with flash and java.  I followed the script installs in the following post.

[64 bit Flash and Java install scripts - Thanks to Kilz!]("http://ubuntuforums.org/showthread.php?t=772490")


I am excited for when 9.04 comes out in April!!!

---

### Post by jespdj on 2009-02-01
> **Temüjin said:**
> Java 6u12 (which includes the Java64 plugin) is scheduled to be released shortly and Ubuntu devs expect to have it in Jaunty:
[https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)
Great! :)

> **sanderj said:**
> My Athlon 64 has been running 64-bit Ubuntu since 2007, and I've never experiences any problems: I just install everything via the repositories and everything works.

So for me Ubuntu has "full 64-bit support" since 7.10.
The problem is not that it's impossible to run Java or Flash; the problem is that those have been, until recently, 32-bit programs. They work on 64-bit Ubuntu, but it would be better to have 64-bit native versions of Java and Flash.

---

### Post by Thelasko on 2009-02-02
> **jespdj said:**
> The current 64-bit Flash 10 from Adobe is still a beta version (as far as I know), even though it works great. I don't know exactly what the policy is, but it might be that it's not going to be included because it's beta software.

Being in beta didn't stop the developers from releasing Firefox 3 in Hardy.

---

### Post by tuxxy on 2009-02-02
I agree, the beta should be included by default even if tis down to performance.

---

### Post by jespdj on 2009-02-03
Sun just released Java 6 update 12 with the new 64-bit Java browser plug-in (final release, no longer beta), see [this topic](http://ubuntuforums.org/showthread.php?t=1058539). Great! :)

---

### Post by JAwuku on 2009-02-07
The final release of 64-bit Linux Mint 6, "Felicia" was released today:


It has native Sun java 6u12 support for 64-bit firefox,
as well as Flash 10 64-bit.

[http://www.linuxmint.com/blog/?p=595](http://www.linuxmint.com/blog/?p=595)

[http://distrowatch.com/?newsid=05316](http://distrowatch.com/?newsid=05316)

---

