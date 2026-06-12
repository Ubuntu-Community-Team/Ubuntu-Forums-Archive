---
title: "Ubuntu server on an Intel 64-bit processor?  Which install CD?"
date: 2006-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jfighter on 2006-09-14
My server computer:
Gateway 838 GM
64-bit Intel Pentium 4 & hyperthreading technology, 3.0 GHz
200 GB HD

I wish to run this computer as a domain controller for 14 Windows XP workstations, among other things.  There will be no Windows partitions.  I tried to install Ubuntu on it but am having problems with which install CD I should use.

I tried installing with the AMD64 server CD (I realize that I have an Intel64) but when installation finished, I couldn't run any basic commands (i.e. ping, ifconfig, etc.)---very strange.  Then I installed using the AMD64 desktop CD and things worked better.  But I want a console-only server.  How could this happen?

I've heard that a 32-bit install should work on a 64-bit computer, but is this true?  How so?

Btw, things didn't work perfectly.  When I try to do a remote ssh session to the server from my laptop from another location, sometimes I get a connection and sometimes I don't.  When I do, it doesn't last for more than a minute before it hangs (not disconnects, but freezes so that I can't type anymore).

Sorry about all the questions, but I'm so confused and frustrated!  I'm even pondering whether I should get Windows Server to avoid the pain.  Thanks all for any help!

---

### Post by John.Michael.Kane on 2006-09-14
What video card is in this machine?

Also have you tried using the noacpi caommand before installing?


Just the info you have given is not enough. have you added any other networking cards to it?

From the looks of what you have said i would say you have a bad burned cd.

---

### Post by jfighter on 2006-09-15
Hmm, looks like the server is starting to work now and my SSH sessions are stable too.  Turns out I didn't put in the correct IP values for my host config file...  I did do an md5 check on the ISO before I burned it but maybe it was a badly burned CD.

Btw, I actually had to buy a new ethernet card for my system to get it to work with Ubuntu.  'noacpi' also didn't work.  In any case, things are going well at least for now.

---

