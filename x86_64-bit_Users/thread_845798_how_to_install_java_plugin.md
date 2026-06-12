---
title: "how to install java plugin???"
date: 2008-06-30
forum: x86 64-bit Users
---

### Post by shonwein on 2008-06-30
I just download the file from the sun-java page. It's a .bin file.
I'm new at this.. third day.
¿what do i do now with this file?

---

### Post by stchman on 2008-07-01
> **shonwein said:**
> I just download the file from the sun-java page. It's a .bin file.
I'm new at this.. third day.
¿what do i do now with this file?

There is no SUN Java plugin for 64 bit.

Use Icedtea.

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

The plugin is comppatible with some but not all websites.

---

### Post by philinux on 2008-07-01
Or just install

ubuntu-restricted-extras from synaptic.

---

### Post by shonwein on 2008-07-01
What are those restricted extras?

---

### Post by Sef on 2008-07-01
[From Java on 64-bit Systems]("http://ubuntuforums.org/showthread.php?t=774956"):

> The easiest way to download OpenJDK is Applications > Add/Remove > Change the search box to either "All OpenSource Applications" or "All Available Applications." (The former is also known as Universe and does not contain any proprietary applications, while the latter is also known as Multiverse and contains proprietary appliations.)


Also if you want some more information, you can click on the link above.

---

### Post by Yellow Pasque on 2008-07-01
> **stchman said:**
> Use Icedtea.
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

icedtea is now called OpenJDK, and the package names have changed. The icedtea packages now refer to the new package names.

From the Syanptic description of icedtea packages:
> This is a transitional package. It can safely be removed after an upgrade to Ubuntu 8.04 (hardy).

Instead,
```
sudo apt-get -y install openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-jdk
```

---

### Post by stchman on 2008-07-01
Yes, the new line would be:

```
sudo apt-get -y install icedtea-gcjwebplugin openjdk-6-jre openjdk-6-jdk
```

---

### Post by Sef on 2008-07-02
> icedtea is now called OpenJDK, and the package names have changed. The icedtea packages now refer to the new package names.

Due to licensing issues, IceTea is RedHat's name for Sun's OpenJDK.

---

