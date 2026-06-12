---
title: "firefox 64-bit on 8.10 -- is it 32 bit or 64?"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by graysky on 2008-11-27
Does the amd64 version of 8.10 use a true 64-bit version of firefox, or is it a 32-bit version with all the warts of running a 32-bit version on amd64 (i.e. flash problems, etc.)?

---

### Post by sonicb00m on 2008-11-27
the 32bit version but it's easy to replace the np wrapped version with the x64 release.

---

### Post by Kilz on 2008-11-27
> **graysky said:**
> Does the amd64 version of 8.10 use a true 64-bit version of firefox, or is it a 32-bit version with all the warts of running a 32-bit version on amd64 (i.e. flash problems, etc.)?

You have that backwards, the 64bit version of Firefox is the one with plugin problems. While a Flash plugin is in Alpha for the 64bit Firefox, there is only an open source java, not a Sun Java plugin. If the browser was 32bit, all the 32bit plugins from Adobe and Sun would work.

---

### Post by jespdj on 2008-11-27
The Firefox that's installed on 64-bit Ubuntu by default is a native 64-bit executable.

You need nspluginwrapper to make the 32-bit Flash plugin work on 64-bit Firefox, but this is installed automatically when you install Adobe Flash from the repository (you don't have to do anything special to make it work).

There's also an alpha version of the 64-bit Adobe Flash 10 plugin, so hopefully in the next release of Ubuntu we will have a native 64-bit Adobe Flash plugin.

Sun has planned to release a 64-bit Java browser plugin in Sun Java 6 Update 12, which will be released sometime in the beginning of 2009. (We're currently at Sun Java 6 Update 10).

So in a few months time there's no need to worry about 32-bit Firefox and 32-bit plugins anymore.

---

### Post by felker2 on 2008-11-27
Easy to check:

```
sander@ubuntu804:~$ uname -a
Linux ubuntu804 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux
sander@ubuntu804:~$ file /usr/lib/firefox-3.0.4/firefox
/usr/lib/firefox-3.0.4/firefox: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
sander@ubuntu804:~$
```

Note: "ELF 64-bit LSB executable, x86-64"

So: firefox on 64-bit Ubuntu is 64-bit.

---

### Post by Kilz on 2008-11-27
> **jespdj said:**
> 
So in a few months time there's no need to worry about 32-bit Firefox and 32-bit plugins anymore.

I will jump for joy.  :D

---

### Post by stmiller on 2008-11-27
There is a 64bit java plugin for Firefox. Install icetea. :)

---

### Post by jespdj on 2008-11-28
> **stmiller said:**
> There is a 64bit java plugin for Firefox. Install icetea. :)
Yes, and for most applets it's fine, but unfortunately it is not 100% compatible with Sun Java, so some websites don't work with this plugin. The IcedTea plugin uses OpenJDK Java instead of Sun Java (as far as I know).

Install the IcedTea plugin by installing the package icedtea6-plugin (if you're using Ubuntu 8.10):
```
sudo apt-get install icedtea6-plugin
```

---

### Post by philinux on 2008-11-28
> **Kilz said:**
> I will jump for joy.  :D

Me too :).

---

### Post by Kryptick on 2008-12-03
After trying everything
I now hate Java so much
I hope it dies a horrid death....

---

### Post by cariboo on 2008-12-03
To fix your flash problems download the 64bit alpha here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

untar it and copy libflashplayer.so to /usr/lib/mozilla/plugins. Restart Firefox and watch all the flash videos you want.

Jim

---

### Post by jespdj on 2008-12-03
> **Kryptick said:**
> After trying everything
I now hate Java so much
I hope it dies a horrid death....
It will not die a horrid death, and things will get better once Sun Java 6 update 12 comes out in a few months time, as already said above.

---

### Post by philinux on 2008-12-03
> **cariboo907 said:**
> To fix your flash problems download the 64bit alpha here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

untar it and copy libflashplayer.so to /usr/lib/mozilla/plugins. Restart Firefox and watch all the flash videos you want.

Jim

You could, alternatively, copy it to
/home/username/.mozilla/plugins

You just have to create the plugins folder first.

---

### Post by jamesstansell on 2008-12-03
> **Kryptick said:**
> After trying everything
I now hate Java so much
I hope it dies a horrid death....

Hi Kryptick,

What did you try?  What did you expect and what happened instead?

---

### Post by jamesstansell on 2008-12-03
> **jespdj said:**
> It will not die a horrid death, and things will get better once Sun Java 6 update 12 comes out in a few months time, as already said above.

I just saw this about Java 6u12:

> Bug# 6770420 has been fixed in 6u12 build02 which will be available early next week on java.net.

[http://forums.java.net/jive/message.jspa?messageID=319884#319884](http://forums.java.net/jive/message.jspa?messageID=319884#319884)

It's not clear if that will be an early access download or a regular release.  I'm guessing the former because of the java.net mention, as well as because 6u11 just came out yesterday.

-james.

---

