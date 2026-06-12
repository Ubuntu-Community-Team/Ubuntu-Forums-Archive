---
title: "Wine installation"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by M$LOL on 2007-03-16
Following the instructions on using the script in Kilz' howto I get:
./wine
./wine: line 3: cd: /home/ciaran/Desktop/wine: Not a directory
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg-dev is already the newest version.
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0 cdda2wav libgettext-ruby1.8 dhcdbd network-manager
  pouetchess-data liblo0 phalanx
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.
--18:08:24--  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb)
           => `wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:08:44 ERROR 404: Not Found.

dpkg: error processing wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb
--18:08:45--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb)
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        42.64K/s             

18:09:05 (42.55 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/10062]

dpkg-deb: failed to chdir to directory: Not a directory
cp: cannot stat `/home/ciaran/Desktop/wine/usr/lib/*': Not a directory
./wine: line 13: cd: ./sidenet: No such file or directory
./wine: line 14: ./setup: No such file or directory

And it has been there for a good 20 mins without bringing me back to a command prompt.

Help?

---

### Post by Kilz on 2007-03-16
That script is quite old, and I stoped updating it because some others have created 64bit packages for wine. If you still want to go the 32bit way you might want to just follow toe howto.

---

### Post by Kilz on 2007-03-16
I just updated the scripts, if you want to use one, go to the howto page and get the new one for the newest version of wine.

---

### Post by M$LOL on 2007-03-16
I tried the 9.32 one and got this:

./wine
./wine: line 3: cd: /home/ciaran/Desktop/wine: Not a directory
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg-dev is already the newest version.
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal0a libnl1-pre6 libglpng libnm-util0 cdda2wav libgettext-ruby1.8
  libalut0 dhcdbd network-manager pouetchess-data liblo0 phalanx libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.
--20:22:34--  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb)
           => `wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,708,094 (9.3M) [application/x-debian-package]

100%[====================================>] 9,708,094     39.19K/s    ETA 00:00

20:26:14 (47.76 KB/s) - `wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb' saved [9708094/9708094]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package wine.
(Reading database ... 113003 files and directories currently installed.)
Unpacking wine (from wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb) ...
Setting up wine (0.9.32~winehq0~ubuntu~6.10-1) ...

--20:26:29--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb)
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        18.85K/s             

20:26:51 (18.83 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/10062]

dpkg-deb: failed to chdir to directory: Not a directory
cp: cannot stat `/home/ciaran/Desktop/wine/usr/lib/*': Not a directory
./wine: line 13: cd: ./sidenet: No such file or directory
./wine: line 14: ./setup: No such file or directory

Is there somethig wrong?

---

### Post by M$LOL on 2007-03-16
Well, I used the howto and it seems to have worked... I'll try a couple of apps and see how I get on. Thanks so much for all the effort you've put into helping me. Much appreciated. :)

---

### Post by John.Michael.Kane on 2007-03-16
Heres the method I used may be of some help --> [**WineTestInstall**]("http://www.ubuntuforums.org/showpost.php?p=2300188&postcount=15") only some adjust made other then that all info came from kilz guide.

---

### Post by Kilz on 2007-03-16
> **M$LOL said:**
> I tried the 9.32 one and got this:

./wine
./wine: line 3: cd: /home/ciaran/Desktop/wine: Not a directory
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg-dev is already the newest version.
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal0a libnl1-pre6 libglpng libnm-util0 cdda2wav libgettext-ruby1.8
  libalut0 dhcdbd network-manager pouetchess-data liblo0 phalanx libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.
--20:22:34--  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb)
           => `wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,708,094 (9.3M) [application/x-debian-package]

100%[====================================>] 9,708,094     39.19K/s    ETA 00:00

20:26:14 (47.76 KB/s) - `wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb' saved [9708094/9708094]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package wine.
(Reading database ... 113003 files and directories currently installed.)
Unpacking wine (from wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb) ...
Setting up wine (0.9.32~winehq0~ubuntu~6.10-1) ...

--20:26:29--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb)
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        18.85K/s             

20:26:51 (18.83 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/10062]

dpkg-deb: failed to chdir to directory: Not a directory
cp: cannot stat `/home/ciaran/Desktop/wine/usr/lib/*': Not a directory
./wine: line 13: cd: ./sidenet: No such file or directory
./wine: line 14: ./setup: No such file or directory

Is there somethig wrong?

Did you happen to take the script out of the Wine folder it came in?

---

### Post by M$LOL on 2007-03-17
Yes, I did. DOH! So, I'm supposed to extract the whole dir then?

---

### Post by MrJavalava on 2007-03-17
Is it possible to get a link to that script of yours? It's pretty hard to mess about in the forum to locate it.

---

### Post by M$LOL on 2007-03-17
[Kilz' edgy script]("http://home.comcast.net/~next/wine-.9.32-install-edgy.tar.gz")
[Killz' guide]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by Kilz on 2007-03-17
> **M$LOL said:**
> Yes, I did. DOH! So, I'm supposed to extract the whole dir then?

Yes the directory contains the instruction in a readme file and the sidenet setup script. The script itself uses the location of the folder.

---

### Post by M$LOL on 2007-03-17
OK, thanks, I'll know for again. I got Wine working anyway. Thanks.

---

### Post by M$LOL on 2007-03-18
Hey Kilz, how do I upgrade to Wine 0.9.33? I hear it has better DX support and lots of bugfixes.

---

### Post by Kilz on 2007-03-18
> **M$LOL said:**
> Hey Kilz, how do I upgrade to Wine 0.9.33? I hear it has better DX support and lots of bugfixes.

Just force in the new deb file

---

### Post by UberKnight on 2007-03-19
I was struggling to find the new .deb for Wine 0.9.33 as it is not yet on the [archive page]("http://wine.budgetdedicated.com/archive/index.html").  However, I have managed to track it down.  You can download it [here.]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.33~winehq0~ubuntu~6.10-1_i386.deb")

Remember to install it by typing the following in the terminal:
> cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb

Note: You might have downloaded it to a directory other than "Desktop".  Change to whichever directory where you downloaded the file.

---

### Post by M$LOL on 2007-03-19
Thanks guys.

---

### Post by pixeldotz on 2007-03-19
has anyone gotten wine 0.9.33 to install? i keep getting dependency errors.

```
dpkg: dependency problems prevent configuration of wine:
 wine depends on libgphoto2-2 (>= 2.3.0); however:
  Version of libgphoto2-2 on system is 2.2.1-2ubuntu4.
 wine depends on libgphoto2-port0 (>= 2.3.0); however:
  Version of libgphoto2-port0 on system is 2.2.1-2ubuntu4.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine
```

updated the repos, the list, and everything else. tried using apt-get, and synaptic and always this dependency error. anyone have any suggestions?

---

### Post by Kilz on 2007-03-19
> **pixeldotz said:**
> has anyone gotten wine 0.9.33 to install? i keep getting dependency errors.

```
dpkg: dependency problems prevent configuration of wine:
 wine depends on libgphoto2-2 (>= 2.3.0); however:
  Version of libgphoto2-2 on system is 2.2.1-2ubuntu4.
 wine depends on libgphoto2-port0 (>= 2.3.0); however:
  Version of libgphoto2-port0 on system is 2.2.1-2ubuntu4.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine
```

updated the repos, the list, and everything else. tried using apt-get, and synaptic and always this dependency error. anyone have any suggestions?

Exactly how are you using synaptic/apt-get to install wine? Wine isnt in the 64bit repositories.

---

### Post by pixeldotz on 2007-03-19
64bit repos?

i added the wine repos to my list according to winehq's howto. installed 0.9.32 fine this way.

btw i'm not using 64bit ubuntu.

---

### Post by Kilz on 2007-03-19
> **pixeldotz said:**
> 64bit repos?

i added the wine repos to my list according to winehq's howto. installed 0.9.32 fine this way.

**btw i'm not using 64bit ubuntu**.

Thats why I asked. You are aware that your replying to a post in the 64bit section, and that wine is not in the 64bit Ubuntu repo's, right?

---

### Post by M$LOL on 2007-03-19
Regardless, that error happenes anyway. I posted in another thread about that same problem, after the i386 libgphoto2-2 packages failed to install.

---

### Post by Kilz on 2007-03-19
> **M$LOL said:**
> Regardless, that error happenes anyway. I posted in another thread about that same problem, after the i386 libgphoto2-2 packages failed to install.

The problem is that libgphoto2-2 is only at version 2.2.1 in Ubuntu (even i386) and the 9.33 wine requires version 2.3.0 so even if you got the libgphoto2-2 to install , wine would still not install.

---

### Post by M$LOL on 2007-03-20
So no on Wine 33 then?

---

### Post by Kilz on 2007-03-20
> **M$LOL said:**
> So no on Wine 33 then?

At present I would say no, stay with 9.32.

---

