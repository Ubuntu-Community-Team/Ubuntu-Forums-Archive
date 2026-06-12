---
title: "HOWTO: install 64-bit java plugin"
date: 2009-01-06
forum: x86 64-bit Users
---

### Post by Kilbasar on 2009-01-06
I had a lot of trouble figuring this out, so thought I would make a post about it. Many applets do not work with IcedTea, so here's how to get the official Sun java plugin working with your 64-bit firefox. It should work on all versions of Ubuntu, although I'm running intrepid. You'll need jre1.6.0_12, which is not the default provided when you download java from Sun's site.

Download the files:
```
cd /usr/lib/jvm
*(the above path can be changed, but make sure to also change the path when making the link)*
sudo wget http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin
```

Extract:
```
sudo sh jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin
```

Make Link:
```
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/
```

Done! Check about:plugins, and it should show the java plugin as being installed.

---

### Post by CarlosinFL on 2009-01-06
From a fresh Ubuntu install I don't have /usr/lib/jvm directory. Do I need to create this manually or will this generate after I use apt to install sun-java6-jre?

---

### Post by Arup on 2009-01-08
ln -s wont' work, instead you need to copy the libnpjp2 to /usr/lib/mozilla/plugins folder.

---

### Post by jamesstansell on 2009-01-10
> **Arup said:**
> ln -s wont' work, instead you need to copy the libnpjp2 to /usr/lib/mozilla/plugins folder.

The symbolic link ("ln -s") is important.  Without it the plugin won't be able to locate the JRE (java virtual machine runtime engine) that it needs to use.

Well, not that locating it would be impossible; but in most cases it would be unlikely.

---

### Post by cr-ab-by on 2009-01-18
Hi Kilbasar

   Your instructions work for me (x64 Ubuntu) exactly as they are. That save me from a lot of troubles, just wanna to say thanks.

---

### Post by katalyst23 on 2009-01-20
Just wanted to say the same as cr-ab-by - this worked exactly the way you said.  Thanks so much!

---

### Post by Cris(c) on 2009-01-22
Same here...everything worked just as Kilbasar said. Thanks a lot for the post!

---

### Post by xoros on 2009-01-22
So does [this guide]("http://ubuntuforums.org/showthread.php?t=1019314") also work?

Seems like that one does some extra things.  I do notice one file is b02 versus b03, not sure what the difference is.

Edit: I see it is an older beta version,  but the method should still work the same I assume.

---

