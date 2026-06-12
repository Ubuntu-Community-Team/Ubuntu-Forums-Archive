---
title: "p11-kit error Workaround WINE in AMD64 Ubuntu 12.04"
date: 2012-09-24
forum: Wine
---

### Post by frogotronic on 2012-09-24
If you get the following error on 12.04 when running WINE:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```

Install the gnome-keyring and p11-kit

```
$ sudo apt-get install gnome-keyring p11-kit
```

Open up nautilus as root

```
$ gksu nautilus
```

Navigate to **/usr/lib/i386-linux-gnu/** and create a directory called **pkcs11**

Then, go to **/usr/lib32/i386-linux-gnu/pkcs11/[COLOR="Red"]gnome-keyring-pkcs11.so[/COLOR]** (while still in root nautilus) and make that *.so file executable (right-click -> properties).

Close root nautilus.

Issue the following command (in a terminal) to establish a symlink.

```
sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
```

Restart WINE.

Regards,
CH

---

### Post by cwwilson721 on 2012-09-24
> **cement_head said:**
> If you get the following error on 12.04 when running WINE:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
```

Install the gnome-keyring and p11-kit

```
$ sudo apt-get install gnome-keyring p11-kit
```

Open up nautilus as root

```
$ gksu nautilus
```

Navigate to **/usr/lib/i386-linux-gnu/** and create a directory called **pkcs11**

Then, go to [B[COLOR="Magenta"]]/usr/lib32/i386-linux-gnu/pkcs11/[/COLOR][COLOR="Red"]gnome-keyring-pkcs11.so[/COLOR][/B] (while still in root nautilus) and make that *.so file executable (right-click -> properties).

Close root nautilus.

Issue the following command (in a terminal) to establish a symlink.

```
sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
```

Restart WINE.

Regards,
CH
This is NO directory of i386-linux-gnu on a "clean" 12.04 install, so from the highlighted part o, your "solved" is NOT SOLVED

---

### Post by frogotronic on 2012-09-24
> **cwwilson721 said:**
> This is NO directory of i386-linux-gnu on a "clean" 12.04 install, so from the highlighted part o, your "solved" is NOT SOLVED

```
sudo apt-get install ia32-libs
```

Which you would need to run just about any 32 bit application(s), and should install on an AMD64 bit install for compatibility.

- CH

---

### Post by cwwilson721 on 2012-09-24
> **cement_head said:**
> ```
sudo apt-get install ia32-libs
```

Which you would need to run just about any 32 bit application(s), and should install on an AMD64 bit install for compatibility.

- CH

Already installed, and no such directory.

Not a noob to Linux, already have all the stuff needed, I'm just saying:

THERE IS NO DIRECTORY ```
/usr/lib32/i386-linux-gnu
``` on a clean 12.04 install
```
USER@desktop:~$ ls /usr/lib32/i386*
ls: cannot access /usr/lib32/i386*: No such file or directory
USER@desktop:~$ 
```

I'm not making this up.

```

USER@desktop:~$sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="red"]ia32-libs is already the newest version[/COLOR].
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR="Red"][B]USER@desktop:~$ ls /usr/lib32/i386*
ls: cannot access /usr/lib32/i386*: No such file or directory[/B][/COLOR] 
USER@desktop:~$ sudo apt-get install gnome-keyring p11-kit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-keyring p11-kit
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,419 kB/1,426 kB of archives.
After this operation, 4,346 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main gnome-keyring amd64 3.2.2-2ubuntu4 [1,419 kB]
Fetched 1,419 kB in 1s (850 kB/s)        
Selecting previously unselected package gnome-keyring.
(Reading database ... 225253 files and directories currently installed.)
Unpacking gnome-keyring (from .../gnome-keyring_3.2.2-2ubuntu4_amd64.deb) ...
Selecting previously unselected package p11-kit.
Unpacking p11-kit (from .../p11-kit_0.12-2ubuntu1_amd64.deb) ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme ...
Setting up gnome-keyring (3.2.2-2ubuntu4) ...
Setting up p11-kit (0.12-2ubuntu1) ...
[COLOR="Red"][B]USER@desktop:~$ ls /usr/lib32/i386*
ls: cannot access /usr/lib32/i386*: No such file or directory[/B][/COLOR]

```

I'm not making this up.

You have done something else to your system and just plain forgot to mention it. It happens.

But your solution does not work the way you have it written here.

(P.S.: Just installing the keyring "solves" the issue without the "extra" steps you have. Just saying...)

---

### Post by frogotronic on 2012-09-24
Ok, I believe you - changing back to "unsolved".

Can't remember what I did...

Oh well...


- CH

---

### Post by cwwilson721 on 2012-09-24
Actually, if you just do the "install" part, it IS solved

It's the mucking around after that with symlinks, non-existent folders, etc, that doesn't work.

Just use
```
sudo apt-get install gnome-keyring p11-kit
```

and it's fixed

---

### Post by MrsUser on 2012-10-03
> **cwwilson721 said:**
> Actually, if you just do the "install" part, it IS solved

It's the mucking around after that with symlinks, non-existent folders, etc, that doesn't work.

Just use
```
sudo apt-get install gnome-keyring p11-kit
```and it's fixed

I have the same error on a fresh Ubuntu install. I installed this as suggested. Still get the same error.

---

### Post by NoCyberDom on 2012-12-09
I have the same issue and installing ia32 did not help here either.

Installing the keyring resulted in the .so being installed to /usr/lib/x86_64-linux-gnu/pkcs11/

Here's a link to my thread on the forums... still unsolved.

[http://ubuntuforums.org/showthread.php?t=2092956](http://ubuntuforums.org/showthread.php?t=2092956)

---

### Post by XDan on 2012-12-10
Would this be a supported way to fix the problem?

[http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so](http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so)

---

### Post by xv1700 on 2012-12-16
I'm using 12.10 and have had the same problem - Installing wine 1.5 fixed it for me: [http://noobslab.com/2012/10/install-wine-1515-in-ubuntu.html]("http://noobslab.com/2012/10/install-wine-1515-in-ubuntu.html")

---

### Post by Gandalf6596 on 2013-01-11
Feedback...

**sudo apt-get install ia32-libs**
[sudo] password for gandalf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.

Installed Ubuntu 12.10 amd64 just yesterday.

---

### Post by Colin Keenan on 2013-01-13
> **cwwilson721 said:**
> Actually, if you just do the "install" part, it IS solved

It's the mucking around after that with symlinks, non-existent folders, etc, that doesn't work.

Just use
```
sudo apt-get install gnome-keyring p11-kit
```

and it's fixed

That wasn't enough to fix the problem for me, so I decided to find out where the gnome-keyring-pkcs11.so file was located by running the following:

```
sudo find -name gnome-keyring-pkcs11.so
```

Which told me it was located at ```
/usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
```

So, I ran

```
sudo ln -s /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

```

After the fact, I realized you had recommended making gnome-keyring-pkcs11.so executable, so I did that too.

My problem is that it now gives me a new error:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: wrong ELF class: ELFCLASS64
```

Which lead me to comment on the following bug: [https://bugs.launchpad.net/ubuntu/+source/p11-kit/+bug/1027299]("https://bugs.launchpad.net/ubuntu/+source/p11-kit/+bug/1027299")

---

### Post by Colin Keenan on 2013-01-13
> **xv1700 said:**
> I'm using 12.10 and have had the same problem - Installing wine 1.5 fixed it for me: [http://noobslab.com/2012/10/install-wine-1515-in-ubuntu.html]("http://noobslab.com/2012/10/install-wine-1515-in-ubuntu.html")

This worked for me and I installed wine 1.5 with the following steps:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo aptitude full-upgrade
```

When I ran aptitude, it asked if it should uninstall the previous version of wine because it wouldn't be able to install wine 1.5 unless it did. I said yes to go ahead and uninstall the previous version.

In order to get rid of the error, I also had to uninstall the troublesome application from wine and re-install it. However, the application still won't run and has another error I'm working on.

---

### Post by Colin Keenan on 2013-01-13
Upgrading to wine1.5 helps because wine1.5 ignores the error, but to actually get rid of the error, follow the answer given on askubuntu:

[http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so]("http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so")

Which is to first delete the link you may have created by following advice on this page, and then do the following:


```
wget https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb
sudo dpkg -i getlibs_2.06-0ubuntu1~ppa2_all.deb
sudo getlibs -p gnome-keyring:i386
sudo mkdir -p /usr/lib/i386-linux-gnu/pkcs11/ 
sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
```

That's 5 commands executed one at a time.

---

### Post by frogotronic on 2013-01-15
Correct, newer versions of WINE shouldn't have this error.

- CH

---

### Post by MrsUser on 2013-01-15
Not working on 12.10 64-bit.  Just did a fresh install of 12.10, then installed WINE 1.5x. Same error. And there is no directory lib32.

Had to create the lib32 directory manually:

```
sudo mkdir /usr/lib32
```then this worked:

```
wget https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb
sudo dpkg -i getlibs_2.06-0ubuntu1~ppa2_all.deb
sudo getlibs -p gnome-keyring:i386
sudo mkdir -p /usr/lib/i386-linux-gnu/pkcs11/ 
sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
```

However, I still get errors:

```
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0xffe8d0, overlapped 0xffe8dc): stub
```

---

### Post by yohoho46 on 2013-04-12
What appeared to fix this for me was to add the wine ppa to get the latest wine.  With that and the normal update, upgrade, the problem resolved.  What is maddening is that this very same wine setup worked last week and this week was broken.  That has to mean that a normal "approved" update broken my system.  

This is just another in a long string of updates that has broken my ubuntu installes.  If I could find something that worked better than Ubuntu I would probably move.

---

### Post by sdgiffin on 2013-05-12
I'm using Ringtail x64 (13.04) with WINE 1.4. The path for me was actually [COLOR=#ff0000]**[FONT=courier new]/usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so[/FONT]**[/COLOR] and not [COLOR=#ff0000]**[FONT=courier new]/usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so[/FONT]**[/COLOR] as it says above. I changed  that, and the error has gone away, but I still can't run Photoshop CS4 from my old XP install. That's more an issue with Photoshop I think, rather than WINE.

---

### Post by axept on 2013-07-17
I get this error, and my .so file is all ready in BOTH of those directories, what should I do when I get the error of opening shared object error? Running Wine 1.6... Ubuntu 13.04 64..

---

### Post by calder76 on 2013-09-11
I had the same problem with Wine and I solved it by downloading gnome-keyring_3.2.2-2ubuntu4_i386.deb from [http://packages.ubuntu.com/precise/i386/gnome-keyring/download](http://packages.ubuntu.com/precise/i386/gnome-keyring/download) and extracting the file CONTENTS/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so and putting it to /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
Hope it helps somebody.

---

### Post by Xara on 2013-10-25
Saucy trust/keyring files. Should be similar package names for 12.04.

p11-kit-trust.so --> [http://packages.ubuntu.com/saucy/i386/p11-kit/download](http://packages.ubuntu.com/saucy/i386/p11-kit/download)

gnome-keyring-pkcs11.so --> [http://packages.ubuntu.com/saucy/i386/libp11-kit-gnome-keyring/download](http://packages.ubuntu.com/saucy/i386/libp11-kit-gnome-keyring/download)

Fixed wine's complaining about those files for me. Just put them where calder76 pointed to. Both files go in the same dir.

---

