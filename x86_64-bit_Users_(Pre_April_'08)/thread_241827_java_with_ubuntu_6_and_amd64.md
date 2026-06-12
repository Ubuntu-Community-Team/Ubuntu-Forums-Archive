---
title: "java with ubuntu 6 and amd64"
date: 2006-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by bilsa on 2006-08-22
Hi!

Lol, I just installed ubuntu today, I have never used unix systems before :) Literally everything is a pain in the *** for me right now ](*,) 

Though I must say the core installation of ubunto was painless and ubuntu seems really nice to work with.

Anyway, my problem is that I want to install the newest Java jdk.

So I did the following:

Installed fakeroot and make-jpkg and necessary gcc stuff.

Then I downloaded the jdk.bin I wanted.

When I run :
sudo fakeroot make-jpgk my_jdk.bin

I get the following message:

Creating temporary directory: /tmp/make-jpkg.XXXXXc4gwb
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done


I found out that this might help:
DEB_BUILD_GNU_TYPE=x86-64-linux fakeroot make-jpkg jdk-6-rc-bin-b96-linux-amd64-18_aug_2006.bin

But I still get the same error, would really appreciate some help. Since this is needed to install many other applications as I have understood it.

Thx!

---

### Post by RAOF on 2006-08-23
The command you probably want to install Sun Java JDK is:
```

sudo aptiude install sun-java5-jdk

```
That will install the 1.5-06 JDK, which is I believe the most recent **released** one.  That will allow you to develop java apps.

However, if you only want to **run** java applications, you want
```

sudo aptitude install sun-java5-bin

```
which will install the runtime stuff.

You might want to run
```

sudo update-alternatives --config java

```
afterwards, to select the Sun JRE as your default Java-running-program.

---

### Post by bilsa on 2006-08-23
Thanks, though I would like to have the java 6 beta 2 installed, and I don't think it is available from any repository ?

So I have to intall it manually, anyway I would like to know how to convert my .bin to .deb files, seems to me that the command I used should have done the trick?

---

### Post by gmclachl on 2006-08-23
I did this a few nights ago if I remember it's 

 DEB_BUILD_GNU_TYPE=x86_64-linux fakeroot make-jpkg jdk-6-rc-bin-b96-linux-amd64-18_aug_2006.bin

notice the underscore not - between x86 and 64 

George

---

### Post by bilsa on 2006-08-23
Thanks everyone, I have solved it.

I just followed the steps in this thread:
[http://ubuntuforums.org/showthread.php?t=129174&page=2&highlight=Mustang](http://ubuntuforums.org/showthread.php?t=129174&page=2&highlight=Mustang)

Since I didn't have the jdk 6 beta files listed as available packages, it didn't agree on making the deb file.

---

