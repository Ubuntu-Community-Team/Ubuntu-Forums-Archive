---
title: "Help needed for installing Wine"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by golebara on 2007-12-04
Hi,

I'm having troubles installing Wine one my Ubuntu 64-bit. I'm following instructions at [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) and I got to the part before compiling. I couldn't get the following line to work:

CC="gcc -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure

When entered, it gives me this:

root@Kharak:/home/golebara# CC="gcc -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L'pwd'/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
bash: ./configure: No such file or directory

Could someone please give me a hand with this? Thanks.

Jay

---

### Post by gazj on 2007-12-04
it sound like you are not in the directory (folder) where you downloaded the source code from the wine website.

Just before we go any further with this one, is there why your are compiling the source code straight from the wine site.

can you not just install it with the following command from the ubuntu repositories

```
sudo apt-get install wine
```

---

### Post by golebara on 2007-12-04
Hi gazj,

Thanks for helping out.

No, sudo apt-get install wine will return:

root@Kharak:/home/golebara# sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

I take it it's something to do with the 64 bit.

I also figured that I'm not in the right directory. The instruction didn't say anything about downloading the source and I guess I haven't done so yet. Could you please tell me where I can get the source? Is it this one:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

Jay

---

### Post by Kilz on 2007-12-04
> **golebara said:**
> Hi gazj,

Thanks for helping out.

No, sudo apt-get install wine will return:

root@Kharak:/home/golebara# sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

I take it it's something to do with the 64 bit.

I also figured that I'm not in the right directory. The instruction didn't say anything about downloading the source and I guess I haven't done so yet. Could you please tell me where I can get the source? Is it this one:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

Jay

What version of Ubuntu are you running?

---

### Post by golebara on 2007-12-04
I'm running Ubuntu 7.04.

I downloaded the source from the URL in my last post and extracted it then I ran the same command:

root@Kharak:/home/golebara/Desktop/wine-0.9.50# CC="gcc -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Now it says "C compiler cannot create executables". What am I doing wrong?

Jay

---

### Post by gazj on 2007-12-04
not being a 64 bit user, prob best leaving you in the hands kilz if your running 64 bit ubuntu, i know wine is not so friendly with 64 bit or so i hear.

I wrote a how to on wine some time back, it's dated but i think it still stands up with some tips even today.

[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

---

### Post by gazj on 2007-12-04
just a note, if you are going to build from source you will definitely need the build-essential package before it will work.

```
sudo apt-get install build-essential
``` plz check my bad spelling on essential it could be wrong

---

### Post by Rhubarb on 2007-12-04
From the notes [here]("http://www.winehq.org/site/download-deb"):
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```
This should give you the latest version of wine for your 64bit system (I think this worked for my 64bit Ubuntu last month when I had 7.04).

---

### Post by golebara on 2007-12-04
Rhubarb,

root@Kharak:/home/golebara# wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
root@Kharak:/home/golebara# sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
--11:51:47--  [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

11:51:47 (13.28 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

What do I do after this?

---

### Post by golebara on 2007-12-04
Nevermind.

---

### Post by Rhubarb on 2007-12-06
Oops, sorry.  I should've also mentioned:
```
sudo aptitude install wine
```

---

