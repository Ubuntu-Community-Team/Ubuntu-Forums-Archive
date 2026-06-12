---
title: "adobe flash player in firefox/opera"
date: 2009-07-18
forum: x86 64-bit Users
---

### Post by che guevara93 on 2009-07-18
firefox:
I've installed flash player 10 alpha in firefox like this: i've unpacked flashplayer which i downloaded from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)   then typed in terminal 
cd
mkdir -p .mozilla/plugins
mv libflashplayer.so .mozilla/plugins

and it works but very slooow... thats because it's alpha, right? But older versions even don't work they just show white screen...
what should i do?

opera:
how  to instal in opera? is it complicated as in firefox? how does  it work?

---

### Post by Arup on 2009-07-18
It works the best, better than Windows flash player, in your case the problem most likely is video driver, maybe you haven't installed them yet or you are probably using a Intel built in. Also delete the mozilla folder you have created, instead untar it and then do a sudo mv libflashplayer.so /usr/lib/mozilla/plugins Opera automatically picks up flash from this folder.

---

### Post by che guevara93 on 2009-07-19
no, i have a working nvidia driver... how i'm gonna find that firefox folder???

---

### Post by Moop on 2009-07-19
You can use ctrl-h to see hidden files (folders) or click on view and check the box for viewing hidden files.

---

### Post by Arup on 2009-07-19
> **che guevara93 said:**
> no, i have a working nvidia driver... how i'm gonna find that firefox folder???

You have to execute the command I posted, the /usr/lib/mozilla/plugins exists in your filesystem.

---

### Post by For The People on 2009-07-19
Do you have an older flash installed already? It is recommended that you uninstall any previous flash player before installing the latest one.

Follow the advice of Arup...

I installed that exact plugin somewhere somewhow... it also came with the icedtea-java-plugin if I recall.  I'll go try and find it and get back....

---

