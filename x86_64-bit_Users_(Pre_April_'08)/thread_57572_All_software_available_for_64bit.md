---
title: "All software available for 64bit?"
date: 2005-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by funkahdafi on 2005-08-17
Hi,

I am going to install Ubuntu to my new AMD64 system. Now I am wondering whether I should go for the 64bit version. My concern is that I may not get all the packages that are available for the 32bit version.

How about that? Are all packages always available for both versions? Or will I be able to run 32bit apps on the 64 bit version? How are repositories set up? Will they search 64bit repos and then "failover" to 32bit repos in case the 64bit repository doesn't carry what I want?

Or put it this way: How much sense does it make to the normal user to run 64bit?

Thanks for your input.

Sascha

(BTW: What font is being used here? I like it...)

---

### Post by DancingSun on 2005-08-17
In short, not all packages are available for Ubuntu 64.

If you do a little poking around in this forum, you will see that most people complain about the lack of 64-bit Flash Player and the Sun Java Plug-in.  However, the availability of these software is dependent on their respective owners.  All we can do is write/petition to Macromedia and Sun to make these available in 64-bit binaries.

Windows32 codecs is another piece that is missing in the 64-bit scene, although we do have a how-to on getting it to work under Ubuntu 64.  But your mileage may vary.

It really depends on whether you can make due without these packages.  I'm a first time Linux user, and I find myself pretty comfortable in Ubuntu 64.

It should also be noted that we have an AMD64 community here that is running our own AMD64 repositories, you can find this in the "amd64 packages" thread.  Take a visit to the project's wiki page to see a list of requests in addition to the list of packages already ported.

The Official Backports Project have also just started to port packages to the AMD64 architecture, so things are looking much better than it did 2-3 months ago.

---

