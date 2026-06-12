---
title: "Karmic 9.10 - 64 bit and Adobe Flash"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by kubug on 2009-11-08
If you, like me, have upgraded your ubuntu you may have found that all the flash applications don't respond to user input (you can click on things but nothing happens, ie: on nvidia's website you can't get past the splash screen. 

Here is the fix that worked for me. Adobe now has a 64 bit client out that seems to work better than whats in the repository.

```
sudo apt-get remove flashplugin-installer flashplugin-nonfree mozilla-plugin-gnash
cd /tmp
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```

Taken from this site: [http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/]("http://www.khattam.info")

Hopefully this will help someone else.

---

### Post by ghostborg on 2009-11-08
Thanks, what an annoying thing when flash doesn't work properly. Enough to drive you crazy. I've seen comments in threads that people have dumped Ubuntu over this even though its really not a Ubuntu issue.

Another issue is the Home network sharing. Not straight forward with a mix of OS's on it.

---

