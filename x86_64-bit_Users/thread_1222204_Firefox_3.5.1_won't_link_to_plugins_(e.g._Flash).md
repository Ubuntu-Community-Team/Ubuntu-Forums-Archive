---
title: "Firefox 3.5.1 won't link to plugins (e.g. Flash)"
date: 2009-07-24
forum: x86 64-bit Users
---

### Post by mathgeek2000 on 2009-07-24
A question for those who may know how,
I've recently installed the new Firefox 3.5.1, co-existing with Ubuntu's version of 3.0.12 following some instructions on this forum. -- ver 3.5.1 is under it's own folder in /usr/lib, and 3.0.12 is under it's folder.

Problem: how can I add plugins to 3.5.1? It has the default plugin, but I can't add for example the adobe flash plugin, because I have a x64 bit version of Ubuntu, and the version on the web is for i386.

For that matter can 3.5.1 and 3.0.12 share the same plugins? if I try by replacing the plugins folder in 3.5.1 with a shortcut, it won't recognize any plugins.

Any help greatly appreciated.

---

### Post by mikewhatever on 2009-07-25
Why not simply install the 64 bit version, which should be able to use the existing plugins from .mozilla/plugins?

---

### Post by RoboNuggie on 2009-07-27
I have the plugins in /usr/lib/mozilla/plugins and also linked to /usr/lib/firefox/plugins....

And I have the various firefox's that I have compiled in /usr/local/lib....

---

### Post by RoboNuggie on 2009-07-27
And, I forgot, the java plugin (the 64-bit one is libnpjp2.so) found in 
/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/amd64/

I copied it over to the /usr/lib/mozilla/plugins directory.

---

### Post by darco on 2009-07-28
> **mikewhatever said:**
> Why not simply install the 64 bit version, which should be able to use the existing plugins from .mozilla/plugins?

because x32 ff is faster than the x64 version.....

darco

---

### Post by daveysan on 2009-08-04
Flash has, for me, been a pain to run but I found a neat page here explaining what is required: [http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)

In essence, you can run the 32 bit version of Adobe Flash in 64 bit Ubintu using nspluginwrapper. So ...

1. Visit [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
2. Download the tar.gz version - this will download the 32 bit version, since their 64 bit version isn't yet ready for prime time
3. Unpack this with a command like tar -zxvf flash.tar.gz
4. cd /usr/lib/nspluginwrapper
5. If there is a file called npwrapper.libflashplayer.so, then back the file up - can't hurt, right?
6. sudo mv /wherever/your/downloads/go/libflashplayer.so npwrapper.libflashplayer.so
7. Restart firefox
8. All should be well with the world - you can check the plugin is there using a url of about:plugins

---

### Post by Yellow Pasque on 2009-08-04
If you want to run a 32-bit browser, then you'll need 32-bit versions of your plugins..

> In essence, you can run the 32 bit version of Adobe Flash in 64 bit Ubintu using nspluginwrapper. So ...
This thread is asking about running plugins in a 32-bit browser, not the other way around. Also, nspluginwrapper isn't known for stability (it's better to use the native 64-bit Flash plugin).

---

### Post by daveysan on 2009-08-04
> This thread is asking about running plugins in a 32-bit browser
My reading of the first post spoke of 32 bit Flash and not the browser, and thus described problems I faced. Hopefully my post may help someone.

I can only speak as I find. I use the 32 bit flash with 64 bit Firefox 3.5 on 64 bit Ubuntu using the method I describe and have so far not had troubles. Before that I used 32 bit flash with 64 bit Firefox 3.0.12 on 64 bit Ubuntu with no troubles.

---

