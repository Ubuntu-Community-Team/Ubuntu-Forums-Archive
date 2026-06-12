---
title: "Prob with FireFox after updrade to Gutsy"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by crazykiller on 2007-10-21
Hi, i upgraded to Gutsy, and since then th Firefox stucks on some pages for about 30secs to 3min!!!!!!

Any ideas why does this happends? I notice that this doesnot happend at very simple html pages.
I tried konqueror,  but when I pressed any "login" button it tries  to open Firefox and the system stucks again!

I reistalled Firefox but same again :(

Though,I do not have this problem through Epiphany Web Browser. But I dont like this program, i want Firefox. 

Any ideas??? I have an AMD x2 and 64-bit Kubuntu. 

Thanx!

---

### Post by darkness5723 on 2007-10-21
Yea I'm also having this problem. I read in another post that disabling IPv6 should fix it, but I did that and it didn't work for me.

The fix involves:
Go to about:config
find the "disable IPv6" option
set the boolean to true..

No luck for me, but it might work for you. 
Mine seems to specifically freeze on going to pages with embedded video, like youtube.

---

### Post by crazykiller on 2007-10-21
If you mean this: "network.dns.disableIPv6", its already set at TRUE.
I think that it has something to do with Java. Or the ia32libs. 


Thanx for your post!

---

### Post by praxis22 on 2007-10-21
try installing swiftweasel or swiftfox, you can get a 64bit process specific version, that way you won't have issues with 32bit libraries. Flash works just fine.

---

### Post by esunday on 2007-10-21
install firefox3 thru synaptics

---

### Post by steveneddy on 2007-10-22
I had to install the **flashplugin-nonfree** to get mine working again.

I also had to disable ipv6 to get it to load pages faster.

I think using the flash plugin from the repos may be the answer here.

:popcorn:

---

