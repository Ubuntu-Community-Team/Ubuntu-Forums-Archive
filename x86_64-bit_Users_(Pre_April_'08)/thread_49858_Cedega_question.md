---
title: "Cedega question"
date: 2005-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flac on 2005-07-18
Ok, finaly took the time to get a chroot going for my 32 bit apps... I got cedega installed, But i failed every test down the line, except for posix...

So my question is. DO i need drivers for video/sound card installed under the 32-bit chroot, or under my full 64-bit for runing cedega?

---

### Post by negatory on 2005-07-18
You need only the drivers in your 64bit enviroment as the kernel will handle the calls for your X server.But I can't understand what you want to say with: "But i failed every test down the line, except for posix...",can you explain it better?
And by the way...you don't need a chroot for Cedega, you can just follow [this instructions](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)   and have Cedega work in 64bit.
Hope that helps.
Pedro Carrico

---

### Post by Jet2k5 on 2005-07-18
yepp.  You don't need a 32-bit chroot mode environment to get Cedega working.  All you need to do is install the proper drivers for you ATI/NVIDIA card.  And follow the instructions on that website that negatory has linked you to.  Make sure you are following the " Install Cedega on 64-bit blah blah "  

Good Luck. Post back if you are having trouble with the guide.

---

### Post by Flac on 2005-07-18
as for "i failed every test" apparantly my drivers arent working right, As i failed the openGL test, the sound test, some other random test, ectect.

and thanks for the link, i'll try that out. Heh, look sharp i'll probably be asking for help with my drivers next :p

---

### Post by Turmoyl on 2005-07-18
Once you follow the directions given int hat Wiki article the only test you should fail is ALSA (which stinks but OSS does fine for now).  TransGaming is aware of this issue and 64-bit support has been voted on strongly so it is safe to assume we will have a pure 64-bit version soon.

---

