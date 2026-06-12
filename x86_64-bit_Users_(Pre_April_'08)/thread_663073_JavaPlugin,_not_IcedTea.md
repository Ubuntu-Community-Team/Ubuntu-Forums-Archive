---
title: "JavaPlugin, not IcedTea"
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by aproan on 2008-01-09
So, I've been using IcedTea for a while, it is the most convenient and stress-free installation.

However, I need to update some pictures to facebook and facebook upload applet does not load, so I  wanted to install Blackdown. 

so i did

```
misantropo@conan:~$ sudo aptitude install j2re1.4 j2re1.4-mozilla-plugin

```

which installed Blackdown, or at least it seemed to, but it doesn't show up when i open up firefox in about:plugins. So I am wondering how to install blackdown or how to make icedtea work with this applet!

am i installing it the right way?

---

### Post by aproan on 2008-01-09
so i realized that perhaps the plugin wasnt where it was supposed to be.

so i did this
```
misantropo@conan:/usr/lib/firefox/plugins$ sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/firefox/plugins/
``` and the output was having firefox crashing everytime i used java and the facebook applet doesn't work stil...

i am not sure what to do.

---

### Post by damvcoool on 2008-01-09
Use this repository and install icedtea

```


deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/


```


for me is working perfectly

---

### Post by aproan on 2008-01-10
ok. i used that repository and re-installed icedtea.

but the applet is just gray, nothing happens. i am not sure what to do.

---

### Post by Kilz on 2008-01-10
If Icedtea doesnt work for you, blackdown ( an even older plugin that causes crashes for a lot of people) will most likely not work. Icedtea is not sun java. Sun java 7 will have a real java plugin from sun. Its still in development.
But there is an option. You can install a 3[2bit firefox, java and fllash]("http://ubuntuforums.org/showthread.php?t=202537") that works. There is even an install script.

---

### Post by damvcoool on 2008-01-10
Did you uninstall the blackdown java before installing IcedTea?

---

