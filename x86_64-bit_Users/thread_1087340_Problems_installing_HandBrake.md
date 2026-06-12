---
title: "Problems installing HandBrake"
date: 2009-03-04
forum: x86 64-bit Users
---

### Post by qwertypianist on 2009-03-04
Hi, 

First, I'm new to Ubuntu and Linux. I like the idea of open software, I read 'The Cathedral & the Bazarr' as part of my migration from Windows & Mac to Ubuntu and it makes so much sense after reading that. It should be required. 

I was surprised about not being able to watch DVD's by default but I read up on it and I get it. I did my due diligence and I can watch DVD's now.

Now I'm trying to now rip my DVD collection so I have a copy on my computer so I can just watch it from my HDD's. I've followed some processes that I've found on google, one from lifehacker seems to be the most help so far. They suggested k9copy, which I've got running but it's not exactly ripping dvd's correctly. I've got some rips but they're weird or missing sound or have counters on the copies.  They said it might not work on my copy of Ubuntu since it's not for Gnome. I used to use DVDShrink on windows to do my backups. It worked pretty well. I'd like to get to that point again if possible.

On to my question: I'm now trying Handbrake, still at the install phase and getting nowhere fast! lol.  What am I as a new user doing wrong!?

I downloaded it from here: 
[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)
The 64bit GUI version.

1) I click on the package from the Firefox Downloads box
2) The Package Installer comes up, I click 'Install Package' and enter my password. 
3) A new window comes up over that, looks like it's installing and then says "Installation Finished" but then under the blue bar it says "Failed to install package 'HandBrake-0.9.3-Ubuntu_GUI_amd64.deb'.

There is a drop down for "Terminal", in there is says 

(Reading database ... 159037 files and directories currently installed.) Unpacking handbrake (from .../HandBrake-0.0.0-Ubuntu_GUI_amd64.deb) ...  

and then there is this little square thing,



I look forward to any help offered! Thanks in advance.

-poor newb.

---

### Post by sanderj on 2009-03-05
Are you sure you're running 64-bit Ubuntu? Post the output out

```
uname -a
```

here and check for "x86_64 GNU/Linux"

And try another way of installation: download the deb file unto your computer, open a terminal and then install the deb file by hand

```
sudo dpkg -i HandBrake-0.9.3-Ubuntu_GUI_i386.deb
```

(use your correct deb file name; this is the 32-bit version) and post the output here.

---

### Post by sanderj on 2009-03-05
FWIW: here's my install

```

sander@ubuntu810-on-athlon64:~/Desktop$ ls -al HandBrake-0.9.3-Ubuntu_GUI_amd64.deb
-rw-r--r-- 1 sander sander 10086558 2009-03-05 08:26 HandBrake-0.9.3-Ubuntu_GUI_amd64.deb


sander@ubuntu810-on-athlon64:~/Desktop$ sudo dpkg -i HandBrake-0.9.3-Ubuntu_GUI_amd64.deb
[sudo] password for sander:
Selecting previously deselected package handbrake.
(Reading database ... 318592 files and directories currently installed.)
Unpacking handbrake (from HandBrake-0.9.3-Ubuntu_GUI_amd64.deb) ...
Setting up handbrake (0.9.3-1) ...


sander@ubuntu810-on-athlon64:~/Desktop$ uname -a
Linux ubuntu810-on-athlon64 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux


sander@ubuntu810-on-athlon64:~/Desktop$ ghb


```

---

### Post by qwertypianist on 2009-03-05
> **sanderj said:**
> Are you sure you're running 64-bit Ubuntu? Post the output... ...And try another way of installation...
```
sudo dpkg -i HandBrake-0.9.3-Ubuntu_GUI_i386.deb
```
(use your correct deb file name; this is the 32-bit version) and post the output here.

This my ver:
```
2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```

Unfortunately right off I'm having a problem. I got the link to "sudo dpkg -i HandBrake-0.9.3-Ubuntu_GUI_amd64.deb" from their site and appended it to the 'sudo dpkg' option you asked me to try, I get the following error:
```
converse@converse-desktop:~$ sudo dpkg -i HandBrake-0.9.3-Ubuntu_GUI_amd64.deb
dpkg: error processing HandBrake-0.9.3-Ubuntu_GUI_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 HandBrake-0.9.3-Ubuntu_GUI_amd64.deb
converse@converse-desktop:~$ 
```

I know it's just something wrong with the way I have something configured that it doesn't know where to look? I don't know how to correct this issue. :( 

I'll keep looking around google and see if I can get past this hurdle. :)

Thanks again!

---

### Post by marcelkoopman on 2009-03-05
Are you sure you have downloaded the amd64 one?

---

### Post by qwertypianist on 2009-03-05
> **marcelkoopman said:**
> Are you sure you have downloaded the amd64 one?

No. :-/

I used the download site [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Choose:

> Ubuntu 8.10 Desktop (the latest version): Includes the latest enhancements and is maintained until 2010

and then used the option of 

> 64bit version: May provide additional capabilities to computers that are able to use 64bit software


Is there a specific one for AMD_64? The one I have installed and running is called x86_64, 

```
converse@converse-desktop:~$ uname -a
Linux converse-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
converse@converse-desktop:~$ 
```

---

### Post by marcelkoopman on 2009-03-05
Did you download the amd64 version of handbrake?

---

### Post by qwertypianist on 2009-03-05
> **marcelkoopman said:**
> Did you download the amd64 version of handbrake?

Oh, right. The amd64 version of handbrake... LOL, I thought you meant Ubuntu.  

Yes, I'm sure. I'm using their site which provides the following link: 
> [http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_amd64.deb](http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_amd64.deb)

I've also tried what sanderj suggested: 
> sudo dpkg -i HandBrake-0.9.3-Ubuntu_GUI_amd64.deb



Both are for AMD_64, neither work. The step sanderj suggested gives me the error in my post above. 

TY!

---

### Post by vandorjw on 2009-03-05
I didn't know handbrake was available for linux. I though it was a mac only app. I went to your site and downloaded the source for handbrake. I tried to compile with make, but that produced an error. Then I tried JAM, but that also gives an error.

---

### Post by Arup on 2009-03-06
I got the x64 for my Intrepid from [www.getdeb.net](www.getdeb.net) and it works fine.

---

