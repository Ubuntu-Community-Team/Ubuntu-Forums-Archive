---
title: "HOW-TO: Sun Java Plugin (BETA) on 64 Bit Intrepid"
date: 2008-12-19
forum: x86 64-bit Users
---

### Post by kubug on 2008-12-19
UPDATE: Using the latest build (b03) from Dec 22, 2008.

I noticed some other posts already about the 64 Java plugin for intrepid, but found that they are either incomplete or hard to follow. My guide is based on wd5gnr's post here: [http://ubuntuforums.org/showthread.php?t=1011899]("http://ubuntuforums.org/showthread.php?t=1011899")

Note: This is an EARLY ACCESS plugin. Most likely this HOW TO is going to be obsolete soon, but for those of you who need to run logmein.com or gov of canada websites, you will need this now (icedTea didn't work for me there).

Here it goes. Just open a terminal and cut and paste:

```

wget http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin

cd /opt

sudo sh ~/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin

```

Once the installer is done:

```

cd /usr/lib/mozilla/plugins
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so

```

Now you will need to uninstall icedTea for the sun-java-plugin to work:

```

sudo apt-get remove icedtea6-plugin

```

Restart Firefox and you should be good to go.

---

