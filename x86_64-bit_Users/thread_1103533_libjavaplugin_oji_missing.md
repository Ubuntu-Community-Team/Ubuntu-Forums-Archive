---
title: "libjavaplugin_oji missing?"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by vandorjw on 2009-03-22
When I need to run java applications in my webbrowser I use JRE from SUN.

However, with their last update jre6u12, there is no "libjavaplugin_oji.so" that I should have been able to find here; jre1.6.12/plugin/i386/ns7/libjavaplugin_oji.so .

Now, instead the closest thing I can find is the following.
/opt/jre/jre1.6.0_12/plugin/desktop/sun_java.desktop

Does anyone know what I can do with this.

I always used to follow these instructions.
[http://www.java.com/en/download/help/5000010500.xml#enable](http://www.java.com/en/download/help/5000010500.xml#enable)

But now I don't know what to do.

-CC7

---

### Post by hodge24 on 2009-03-22
Update 12 now has a 64 Bit plugin, but it's named libnpjp2.so and it's located in a different folder:

```
jre1.6.0_12/lib/amd64/libnpjp2.so
```

Just copy this file (or create a link to it) to your ~/.mozilla/plugins/ directory, and it should work.

[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

Hope that helps

---

### Post by vandorjw on 2009-03-24
yes that helps.
Thanks :)

---

