---
title: "Ubuntu 64 but using default Firefox 32bit"
date: 2009-03-19
forum: x86 64-bit Users
---

### Post by bhoth on 2009-03-19
Hi All,

so if I am using Ubuntu 64bit but using Firefox that is included, do I install Java 64bit or 32bit since Firefox is a 32bit app?

And same goes for Adobe flash. Do I install 32bit or 64bit?

Thanks,

---

### Post by stchman on 2009-03-19
> **bhoth said:**
> Hi All,

so if I am using Ubuntu 64bit but using Firefox that is included, do I install Java 64bit or 32bit since Firefox is a 32bit app?

And same goes for Adobe flash. Do I install 32bit or 64bit?

Thanks,

The Firefox that comes with Ubuntu 64 bit is a 64 bit version.

[http://packages.ubuntu.com/intrepid/firefox-3.0](http://packages.ubuntu.com/intrepid/firefox-3.0)

To get a Java plugin for Firefox in 64 bit use openjdk.

```
sudo apt-get install icedtea-gcjwebplugin
```

This will give you what you need.

---

### Post by sanderj on 2009-03-20
> **bhoth said:**
> Hi All,

so if I am using Ubuntu 64bit but using Firefox that is included, do I install Java 64bit or 32bit since Firefox is a 32bit app?

And same goes for Adobe flash. Do I install 32bit or 64bit?

Thanks,

Just go to Add/Remove, and install Java and Flash. Ubuntu will take care of it all.
And if you want to check the bit-ness afterwards, you can use the "file" command. You can then report back that information.

HTH

---

### Post by Sef on 2009-03-20
> To get a Java plugin for Firefox in 64 bit use openjdk.

 	Code:
 	sudo apt-get install icedtea-gcjwebplugin 
This will give you what you need.

To get it an easier way, see my [sticky]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by Kareeser on 2009-03-20
How would following a guide possibly be easier than using the synaptic package manager...?!

---

