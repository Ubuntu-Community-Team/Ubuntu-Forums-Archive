---
title: "Problems Firefox 2 and Icedtea gcjwebplugin.so"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by schapp on 2008-10-16
Hi,

I've been using Firefox 3 and gcjwebplugin.so and so far java works fine in Ubuntu 64-bits.  However, there's an application at work that requires Firefox 2.x and I haven't been able to make the plugin work.  I've created a link under /usr/lib/firefox/plugins:

```

root@laptop:/usr/lib/firefox/plugins#ls -l
total 12
lrwxrwxrwx 1 root root    37 2008-09-27 02:16 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    57 2008-10-16 18:44 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
-rw-r--r-- 1 root root 11456 2008-09-24 07:39 libunixprintplugin.so

```

,but when I start FF2, I get the following error:

```
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so [libxul.so: cannot open shared object file: No such file or directory]

```

, and of course, the plugin doesn't show up in about:plugins.  The file does exist:

```
root@laptop:/usr/lib/firefox/plugins# ls -l /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
-rw-r--r-- 1 root root 28088 2008-03-28 11:55 /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

```

What could be wrong?

Thanks!

---

### Post by Yellow Pasque on 2008-10-16
If it's FF2, it's probably looking for the older directory structure of xulrunner. Hopefully, the solution to this will be to simply create a symbolic link. Please post output of:
```
ls -la /usr/lib | grep xul
```

---

### Post by schapp on 2008-10-16
Thanks for your quick answer!

This is the command output:

```
$ ls -la /usr/lib | grep xul
drwxr-xr-x   3 root root     4096 2008-09-27 02:16 xulrunner
drwxr-xr-x  11 root root     4096 2008-09-27 03:36 xulrunner-1.9.0.3
drwxr-xr-x   4 root root     4096 2008-04-22 14:07 xulrunner-addons

```

The last two directories have a link to the xulrunner plugin:
```
lrwxrwxrwx 1 root root    45 2008-10-16 18:28 libjavaplugin.so -> /etc/alternatives/xulrunner-1.9-javaplugin.so
```

, and that link is apparently OK:
```
lrwxrwxrwx 1 root root  57 2008-10-16 18:28 xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

```

I created a similar libjavaplugin.so under /usr/lib/xulrunner/plugin but didn't work either.

Thanks!

---

### Post by Yellow Pasque on 2008-10-16
FF2 is probably looking for the older xulrunner 1.8 libs. THe following command should give it what it wants:
```
sudo apt-get install libxul0d
```
You may have to create a symbolic link if libxul.so doesn't show up in /usr/lib:
```
sudo ln -s /usr/lib/libxul.so.0d /usr/lib/libxul.so
```

---

### Post by schapp on 2008-10-16
The plug-in finally loaded Installing the libxul0d package!  However, the plug-in is not working.

This is the link I created for the plugin:

```

# pwd
/usr/lib/firefox/plugins
# ls -l libjavaplugin.so 
lrwxrwxrwx 1 root root 45 2008-10-16 23:45 libjavaplugin.so -> /etc/alternatives/xulrunner-1.9-javaplugin.so

```

When I try to see if java is running (f.e. at [http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)), the following message appears in the terminal:

```
gcjwebplugin.cc:1450: thread 0x619ab0: Error: Invalid browser function table.

```

Am I missing something?

---

### Post by Yellow Pasque on 2008-10-17
I'm confused as to why you created that link. I think that link is what's causing the problem (by linking to the xul sdk for FF3). This is your plugin:
```
lrwxrwxrwx 1 root root    57 2008-10-16 18:44 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

```
It was complaining because it couldn't find libxul.so  You've fixed that, so no additional links should be necessary.

---

### Post by schapp on 2008-10-17
Forgot to mention that... I tried linking to xul because the original link that I had, returned the same error:

```
# ls -l
lrwxrwxrwx 1 root root 57 2008-10-17 00:14 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

```

I have the same error with both links.  :(

---

