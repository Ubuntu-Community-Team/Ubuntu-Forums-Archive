---
title: "some 64-bit java applets not working?"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by kasper.sorensen on 2008-04-26
I'm a bit in doubt what the heck the source of this problem is. Whether it's 64-bit java, the firefox plugin or the applets them selves. Either way, here's my problem:

I just did an installation of Hardy and everything seems to work fine. But my netbanking solution seems to fail and I cant figure out why - it worked on Gutsy but that wasn't the 64-bit version either, so that may be part of the problem?

The sun test-applets works fine:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

Here's my netbanking applet, it just shows up as a gray box with no content:
[https://www.sparnord.dk/bank/logon/](https://www.sparnord.dk/bank/logon/)

I have two other banks that I have the same problems with (but I don't want to post the links here since the problem only occur after login). It seems very weird to me that some applets are working while others are not? Can this be a security related issue, since netbanking applets are probably pretty restrictive? Is there a way to debug the problem?

Other than that: Really enjoying Hardy :)

/Kasper

---

### Post by Migoo on 2008-04-26
Hi Kasper!

The problem is that there are no new releases of Java for the 64bit platform. My quess is that your netbank is using alot more "latest and greatest" codings than the small test applet at [www.java.com](www.java.com).

The only solution for this, as far as I know, is to install FireFox 32 bit version and runing the 32 bit versions of the plugins.

This page might help you:
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)


//Kamijo

---

