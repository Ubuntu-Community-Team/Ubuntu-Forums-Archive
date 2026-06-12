---
title: "how to install java sun on gutsy amd64 ?"
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by piju on 2008-02-12
hello all,
i need ur help,
i have installed sun-java6-jdk
but on my firefox, still cannot show java runtime when i open any java's website
hope can hear from u as soon as possible
my ubuntu is gutsy gibbon amd64

---

### Post by Kilz on 2008-02-12
> **piju said:**
> hello all,
i need ur help,
i have installed sun-java6-jdk
but on my firefox, still cannot show java runtime when i open any java's website
hope can hear from u as soon as possible
my ubuntu is gutsy gibbon amd64

The jdk is the java development kit. I don't think it has the plugin. That would be the jre or java runtime. But even so, there is no 64bit Sun Java plugin. There will be when Sun releases java 7. There is only a 32bit Sun java plugin in java 6, that the 64bit browser that is in the Ubuntu amd64 version  cant use. You have a few options.
1. Install icedtea and the icedtea plugin packages. These will work for a lot of sites, but there are some they will not. 
2. Install a[ 32bit browser and 32bit Sun Java plugin.]("http://ubuntuforums.org/showthread.php?t=202537")

---

### Post by 8200 on 2008-02-17
Hi piju!

I have got the same problem. On my new ubuntu 7.10 amd64 Java doesn't work in firefox.

I have already installed "icedtea-java7-plugin" but when I go to a website with java, through firefox started in console, I got this error in the console:
```
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so [libjvm.so: cannot open shared object file: No such file or directory]
```


I have tried many solutions but nothing worked.


Thank you!

---

### Post by 8200 on 2008-02-17
Hey I found a solution:

You have to add this sources to /etc/apt/source.list and apt-get update + upgrade.
#iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/


Works very fine :)

---

### Post by Dencrypt on 2008-02-26
It might be possible now to get java without 32bit browser or java32.

[https://help.ubuntu.com/community/Firefox3AMD64Java](https://help.ubuntu.com/community/Firefox3AMD64Java) 

I tried it myself but the compiling took over 4 hours to complete so do this on your own risk.

---

### Post by cybergalvez on 2008-02-26
Ok I've real lots and lots of these java firefox x64 threads and this is what I've come to understand.  Please someone correct me if I'm wrong
1) Icetea does work sometimes (there is an update out there thats reported to work better) but is insecure so I'm not sure I want to use that
2) java 5 and 6 do not have plugins that work with firefox
3) there is the option of installing firefox32 which will work with flash and java

so my question is:  do the firefox64 and firefox32 live together nicely?  If I install the 32 bit version with the recommended scripts (see posts above) will I still be able to user firefox64 as the default browser and run firefox32 when I want to use a site that uses java?  Do they get different menu entries? are they listed under /bin differently?

thanks in advance for the help
Jose

---

### Post by Kilz on 2008-02-26
> **cybergalvez said:**
> Ok I've real lots and lots of these java firefox x64 threads and this is what I've come to understand.  Please someone correct me if I'm wrong
1) Icetea does work sometimes (there is an update out there thats reported to work better) but is insecure so I'm not sure I want to use that
2) java 5 and 6 do not have plugins that work with firefox
3) there is the option of installing firefox32 which will work with flash and java

so my question is:  do the firefox64 and firefox32 live together nicely?  If I install the 32 bit version with the recommended scripts (see posts above) will I still be able to user firefox64 as the default browser and run firefox32 when I want to use a site that uses java?  Do they get different menu entries? are they listed under /bin differently?

thanks in advance for the help
Jose

Yes they are completely separate, they share no files, and have different menu entries. The only thing is, you will have to close one to use the other. A bug with firefox is that if one version is open, and you click on another firefox launcher it will open a window with the version already open.

---

### Post by steveneddy on 2008-03-06
> **8200 said:**
> Hey I found a solution:

You have to add this sources to /etc/apt/source.list and apt-get update + upgrade.
#iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/


Works very fine :)

You have to add this sources to /etc/apt/source[COLOR="Red"]**s**[/COLOR].list and apt-get update + upgrade.

Some may not see that and get lost.

---

### Post by steveneddy on 2008-03-06
> **8200 said:**
> Hey I found a solution:

You have to add this sources to /etc/apt/source.list and apt-get update + upgrade.
#iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/


Works very fine :)

I was having issues today ( 3-6-2008 ) and this fixed it for me.

---

### Post by d_singo69 on 2008-03-07
You have to add this sources to /etc/apt/source.list and apt-get update + upgrade.
#iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

Worked a treat thanks so much:)

---

### Post by robb0100 on 2008-03-15
> **8200 said:**
> Hey I found a solution:

You have to add this sources to /etc/apt/source.list and apt-get update + upgrade.
#iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/


Works very fine :)

This only works on some sites - unfortunately not the one I am interested in. Looks like the Firefox 3 Beta for me.

---

### Post by glauber_ananda on 2008-03-18
Quick workaround:

- Install wine
- Download firefox for windows
- Use wine to install firefox for windows
- Use wine to run firefox for windows
- Install java plugin on firefox for windows installed on wine

It worked for me.

---

