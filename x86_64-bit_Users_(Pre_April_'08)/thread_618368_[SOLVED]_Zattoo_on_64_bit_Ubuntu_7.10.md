---
title: "[SOLVED] Zattoo on 64 bit Ubuntu 7.10"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by guillelo11 on 2007-11-20
How can I install [Zattoo]("http://zattoo.com") on Ubuntu 7.10 64 bit?

---

### Post by Cappy on 2007-11-20
Install getlibs here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
And then try running
```

sudo apt-get install ia32-libs lib32asound2 libgtkglext1 libxul0d
sudo dpkg -i --force-all zattoo.deb
sudo getlibs /usr/bin/zattoo_player

```

You'll need to change zattoo.deb to whatever the file is actually named. Also, if you saved the file on your desktop don't forget to ```
cd ~/Desktop
``` first.

---

### Post by dabl on 2007-11-20
"Log-In or Sign-up", apparently.

:)

It says it's available for Linux, but it's impossible to tell what exactly that means, wrt rpm vs deb, and whether a 64-bit package is out there.  Guess some brave soul will have to ... Log-In, or Sign Up!

:)

Well, there you go -- Cappy knows!  ;-)

---

### Post by borobudur on 2007-11-22
Has any one successfully installed it under amd64 ubuntu 7.10? I'm worried about my fglrx driver...

---

### Post by borobudur on 2007-11-23
Works perfectly under Compiz, amd64, ATI! Thanks Cappy!

---

### Post by Philipp717 on 2008-02-19
I'm running Debian Testing 64bit and tried to install Zattoo following the steps Cappy listed. However, when trying to run Zattoo it tells me, that there is no match for two libs:

No match for libssh2.so.1
No match for libldap_r-2.4.so.2

Any help would be much appreciated!

---

### Post by Cappy on 2008-02-19
Apparently those packages aren't in gutsy and that is why.

Since you are using debian you can use
```
sudo getlibs -p libssh2-1 libldap-2.4-2
```

---

Ubuntu users would have to use
```

sudo getlibs -w http://mirrors.kernel.org/debian/pool/main/libs/libssh2/libssh2-1_0.18-1_i386.deb
sudo getlibs -w http://mirrors.kernel.org/debian/pool/main/o/openldap2.3/libldap-2.4-2_2.4.7-4_i386.deb

```

---

### Post by Philipp717 on 2008-02-19
that was easy, thanks a bunch

---

### Post by Malzan on 2008-06-15
Hi,

Thanks for the hints on how to install Zattoo under AMD64 Ubuntu! 

I'm trying to install Zattoo under my 8.04 Hardy Heron AMD64 and did follow your instructions. Unfortunately, however, when calling 

```
sudo getlibs /usr/bin/zattoo_player
```

I get the folllowing error:

```
Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Fatal Error: /emul/ia32-linux does not exist
Your distro may not have been detected properly
Detected as: x86_64 debian unstable
No LSB modules are available.
Distributor ID: Ubuntu Description: Ubuntu 8.04 Release: 8.04 Codename: hardy
```

I tried creating the directory /emul with a symlink to folder /usr/lib32, but that resulted in the following error when calling getlibs ... :

```
Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
```

Does anybody know the solution to that problem? Thanks a bunch!

---

### Post by Malzan on 2008-06-15
Hi again,

Well, I have now created the folder /emul/ia32-linux/usr with a symlink called "lib" pointing to /usr/lib32.

I found out that the getlibs script has an error at line 106, where it says:
```
heron) distroname="heron"; set_site_ubuntu;;
```
That should read 
```
hardy) distroname="hardy"; set_site_ubuntu;;
```
instead. 

Still, when I run 
```
sudo getlibs /usr/bin/zattoo_player
```
I get the following error:
```
No match found for package libbonoboui-2.so.0
No match found for package libcurl.so.3
No match found for package libdbus-glib-1.so.2
No match found for package libgnome-2.so.0
No match found for package libgnome-keyring.so.0
No match found for package libgnomeui-2.so.0
No match found for package libgnomevfs-2.so.0
No match found for package libgtkembedmoz.so.0d
No match found for package libmozjs.so.0d
No match found for package libnspr4.so.0d
No match found for package libplc4.so.0d
No match found for package libplds4.so.0d
No match found for package libxpcom.so.0d
No match found for package libxul.so.0d
No libraries to download.

```

When I try to start zattoo_player, I get the following error:
```
zattoo_player: error while loading shared libraries: libgnomeui-2.so.0: cannot open shared object file: No such file or directory
```

Does anyone have an idea what my problem is? Any help would be greatly appreciated! 

Cheers,
Malzan

---

### Post by scorp123 on 2008-06-15
> **Malzan said:**
>  When I try to start zattoo_player, I get the following error:
```
zattoo_player: error while loading shared libraries: libgnomeui-2.so.0: cannot open shared object file: No such file or directory
``` According to [http://packages.ubuntu.com](http://packages.ubuntu.com) you are probably missing this package: libgnomeui-0

Details can be found here:
[http://packages.ubuntu.com/hardy/libgnomeui-0](http://packages.ubuntu.com/hardy/libgnomeui-0)

Maybe you could use that web site's search engine and find out what packages you'd need to install to get all the files you're missing?

---

### Post by Malzan on 2008-06-15
Thanks for your reply, Scorp! I just figured out what the problem was... I had to download the newest version of getlibs (2.06) (cf. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)).

That solved the last issue.

Thanks for that great tool Cappy!

---

