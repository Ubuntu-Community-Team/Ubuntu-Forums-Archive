---
title: "beryl wont start right : deadly signal 11"
date: 2006-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by akshaymodi on 2006-12-10
I can't get beryl to work. I have Ubuntu edgy with AMD64 and am very new to linux. I had beryl a little while ago, and it worked fine on my computer, but then I reinstalled linux, and beryl(and got 0.1.2 instead of 0.1.1), and it just would not work. so i know its something silly.

I get the error "beryl caught deadly signal 11" when I run in the terminal... Can someone please help me get around this, or get 0.1.3 where they have hopefully corrected this "error" if it is indeed one!

---

### Post by Chenzo on 2006-12-10
I had the exact same problem and posted here
[http://ubuntuforums.org/showthread.php?t=315869](http://ubuntuforums.org/showthread.php?t=315869)

I am running edgy 64 bit with a radeon X800.  beryl worked with 0.1.1, but gave me deadly signal 11 when I upgraded to 0.1.2.  Until I can fix it or upgrade to a working version, I went back to 0.1.1.  To do this, 'sudo apt-get --purge remove beryl', '...beryl manager', and '...xserver-xgl' then sudo apt-get remove autoremove to get rid of associated packages (thanks to isntitknoying). edit your sources.list to only include
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy main-edgy-amd64
because that repository does not yet have 0.1.2. when you apt-get update and reinstall xserver, beryl manager and beryl you will have 0.1.1. not a fix, but you'll have your desk cube back until there is one. 

good luck

---

### Post by John.Michael.Kane on 2006-12-12
Should you need to start over heres a guide for 64bit users [http://ubuntuforums.org/showthread.php?t=316520&highlight=beryl+64](http://ubuntuforums.org/showthread.php?t=316520&highlight=beryl+64)

---

