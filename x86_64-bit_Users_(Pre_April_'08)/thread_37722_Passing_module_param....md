---
title: "Passing module param..."
date: 2005-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ::DoGG:: on 2005-05-28
Hey, sorry fo9r that question, but i have to add some params to  module "nvidia" on boot, i can`t find any modprobe.conf or rc.local, can anybody tell me where i can pass the shell commands that i want to be executed while boot ? i need to load nvidia module with otpion NVreg_Mobile=0 duting boot up so i could load with rhgb mode. Thanks

---

### Post by ola on 2005-05-28
Can you modprobe the module by hand with something like this

Check the last post on this thread: [http://www.ubuntuforums.org/showthread.php?t=34370](http://www.ubuntuforums.org/showthread.php?t=34370)

> 
I created a file in /etc/modprobe.d called 3c59x_o4 which contained the following
options 3c59x options=4 full_duplex=1
 

I guess you can follow that thread to acheive what you want (even if that threas is about a messy network card)..

---

### Post by ::DoGG:: on 2005-05-29
Looks like you used "Search " button before me :D
Thanks a lot, so it looks like u put a scipt witch command in /etc/modprobe.d/ directory and  it will automatically pick that up on a  boot up. Will give it a try, thanks!

---

