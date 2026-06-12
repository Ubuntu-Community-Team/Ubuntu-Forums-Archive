---
title: "I Need JRE Plugin"
date: 2008-12-04
forum: x86 64-bit Users
---

### Post by CarlosinFL on 2008-12-04
I installed the 64 bit version of Ubuntu clearly understanding that the packages for Sun Java JRE and browser plugin don't work or exist for my archetecture. My question is what is the alternative? I was told I might be successful with OpenJDK but I am not sure. Can someone please tell me what they suggest I do besides reinstalling x86. I need to access my Firewall and VPN server which all have Java based consoles including some HP servers. 

The main thing I need is the browser plugin for Firefox. 

Any suggestions?

---

### Post by stchman on 2008-12-04
> **Carlwill said:**
> I installed the 64 bit version of Ubuntu clearly understanding that the packages for Sun Java JRE and browser plugin don't work or exist for my archetecture. My question is what is the alternative? I was told I might be successful with OpenJDK but I am not sure. Can someone please tell me what they suggest I do besides reinstalling x86. I need to access my Firewall and VPN server which all have Java based consoles including some HP servers. 

The main thing I need is the browser plugin for Firefox. 

Any suggestions?

I use open Java.  What version of Ubuntu are you running?

---

### Post by Nepherte on 2008-12-04
Just use OpenJDK + icedtea-webplugin. It works just fine for me.

To install (for Intrepid):
```
sudo apt-get install openjdk-6-jre icedtea6-plugin
```
For hardy, replace icedtea6-plugin with icedtea-gcjwebplugin.

---

### Post by stchman on 2008-12-04
> **Nepherte said:**
> Just use OpenJDK + icedtea-webplugin. It works just fine for me.

To install (for Intrepid):
```
sudo apt-get install openjdk-6-jre icedtea6-plugin
```
For hardy, replace icedtea6-plugin with icedtea-gcjwebplugin.

For Hardy I have found these packages to do what you want.

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

---

### Post by Nepherte on 2008-12-04
Yup, that will work too. They are transitional packages referring to the ones I mentioned.

---

### Post by CarlosinFL on 2008-12-04
I am using 8.10 so I am guessing I can simply use the following:

```
sudo apt-get install openjdk-6-jre icedtea6-plugin
```

Right?

---

### Post by Beernut on 2008-12-04
I installed OpenJDK using the packages that stchman recommends and it has worked great.  :D

---

### Post by Zorael on 2008-12-05
I couldn't get OpenJDK's plugin to play nice with Firefox 2, but now that FF3 is stable enough (barring flash) I guess that's less of an issue.

---

### Post by jespdj on 2008-12-06
> **Carlwill said:**
> I am using 8.10 so I am guessing I can simply use the following: ...

Yes, that's what Nepherte told you...

---

