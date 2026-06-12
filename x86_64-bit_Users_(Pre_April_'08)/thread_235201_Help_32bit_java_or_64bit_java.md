---
title: "Help: 32bit java or 64bit java"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by soongwoo on 2006-08-12
I've installed ADM64 server on Intel server.
I'm goinf to install java5 and tomcat5.

When I install java via 'apt-get', there is no 'sun-java5-xxx".
I searched the forum for installation java.
But, most of threads are talking about 32bit java and firefox.

q1) Which one do I have to install on my 64bit Intel server?
32 bit jdk or 64 bit jdk?

q2) I downloaded Java5 update 8(32bit) from sun site and tries to install
the .bin file. Fail! The error messages look like this:
```
Unpacking...
Checksumming...
0
0
Extracting...
./jdk-1_5_0_08-linux-i586.bin: line 412: ./install.sfx.11222: No such file or directory
./jdk-1_5_0_08-linux-i586.bin: line 679: cd: jdk1.5.0_08: No such file or directory
```

Please advise me which version I have to install and how to install
.bin file from sun site.

Thanks
soongwoo

---

### Post by Kilz on 2006-08-12
There is a [java5 jdk for amd64]("http://packages.ubuntu.com/dapper/devel/sun-java5-jdk"), its in the multiverse repository. You probably have to enable the multiverse.

---

### Post by hecato on 2006-08-12
My /etc/apt/sources.list only display the following (with comments)

> 
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 
Where I can fin the list of servers for the other sections like the multiverse???

But I cant see in synaptic the java TM???

---

### Post by Kilz on 2006-08-12
> **hecato said:**
> My /etc/apt/sources.list only display the following (with comments)



Where I can fin the list of servers for the other sections like the multiverse???

It looks like you have it to me. There is only the universe and multiverse.

---

### Post by hecato on 2006-08-12
Yea, is the default install (I guess, I only let the lines of the multiverse)... but searching in *synaptic* for "sun", "sun-java5" dosent give results...

---

### Post by Kilz on 2006-08-12
> **hecato said:**
> Yea, is the default install (I guess, I only let the lines of the multiverse)... but searching in *synaptic* for "sun", "sun-java5" dosent give results...

Thats strange because a search for java5 brings up what you need. sun-java5 packages.

---

### Post by Kilz on 2006-08-12
> **hecato said:**
> Yea, is the default install (I guess, I only let the lines of the multiverse)... but searching in *synaptic* for "sun", "sun-java5" dosent give results...

Thats strange because a search for of sun-java5 or java5 brings up what you need. sun-java5 packages.

---

### Post by Kilz on 2006-08-12
> **hecato said:**
> Yea, is the default install (I guess, I only let the lines of the multiverse)... but searching in *synaptic* for "sun", "sun-java5" dosent give results...

Thats strange because a search for of sun-java5 or java5 brings up what you need. sun-java5 packages for me. Have you tried to add the [repositories in synaptic]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") and not just the file or refreshing the repositories by clicking reload?

---

### Post by hecato on 2006-08-12
mmmm:?, is the same archive??? the mx. perhaps the resource dosent have suchs java5 files... :???:


I have unchecked all the chekboxes in the sources from synaptic, make a reload (clean the xxx.gz downloaded before... I guess), then checked all the boxes and reload (get the xxx.gz from the resources) searched *java5* 
and I still without watching them at the result of the search...

also apt-cache search java5 dosent return something.



Edit: I will check add them, I come back soon](*,)](*,)](*,)

---

### Post by hecato on 2006-08-12
Yes, selecting more sections of the sources worked... tought I click on all of them inary and src (this one I havent added more)....

I get 2 errors

> 
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.bz2:) The subproces bzip2 returned code error (2)
 

And
> 
W: Duplicate sources.list entry [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-amd64_Packages)



I guess I have clicked to much checkboxes???:rolleyes::confused:

---

### Post by soongwoo on 2006-08-12
> **Kilz said:**
> There is a [java5 jdk for amd64]("http://packages.ubuntu.com/dapper/devel/sun-java5-jdk"), its in the multiverse repository. You probably have to enable the multiverse.

Thank you very much. I've installed jdk by enabling multiverse.
By the way, I have no idea which version, 32bit java or 64bit java,
I have to use. Some people are saying 64bit causes problems,
so they changed to 32bit jdk.

Could you give me some help regarding it?

Thanks
soongwoo

---

### Post by Kilz on 2006-08-12
> **soongwoo said:**
> Thank you very much. I've installed jdk by enabling multiverse.
By the way, I have no idea which version, 32bit java or 64bit java,
I have to use. Some people are saying 64bit causes problems,
so they changed to 32bit jdk.

Could you give me some help regarding it?

Thanks
soongwoo

You will have to force install and manualy install any needed lib's if you want a 32bit jdk.
[Download this file the jdk from a local mirror]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsun-java5%2Fsun-java5-jdk_1.5.0-06-1_i386.deb&md5sum=df90908c77345a172242ba5090343817&arch=i386&type=main") Open a terminal and navigate to the location you saved the file. You might also have to uninstall the 64bit jdk first. then type in
```
sudo dpkg --force-architecture -i sun-java5-jdk_1.5.0-06-1_i386.deb
```
Im not sure how to test it to see what other files it needs since I have never used the java jdk.

---

### Post by soongwoo on 2006-08-13
Thanks. I'll try it when 64bit java causes problems.

soongwoo

---

### Post by hecato on 2006-08-13
Only an extra thing... after install java5, I ran

```

$ java --version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

```

Tought it was good, wawsnt able to use an app I like... searching I found this command

```

$ update-alternatives --config java
Tun it as root if you whant take effect

```


in /etc/alternatives I found

[HTML]
update-java-alternatives
[/HTML]


tought this one I dont know how to use it.


With java5 I was able to run the app that was crashing because a class not found or something like that.



(By the way, what about the errors about duplicate packages I get??, I must unselect wich ones for dont get "duplicates"?... or there is no problem in have duplicates?)

---

