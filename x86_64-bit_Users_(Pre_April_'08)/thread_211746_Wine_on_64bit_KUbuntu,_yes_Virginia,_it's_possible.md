---
title: "Wine on 64bit K/Ubuntu, yes Virginia, it's possible!"
date: 2006-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jonnycat26 on 2006-07-08
I've seen some confusion and some angst in this forum where wine is concerned, and I hadn't had much luck getting it going until today.  So since I've gotten it going, I figured I'd share what worked.  

First of all, go to this page and follow the compile instructions:

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

The configure command they give is not right tho.  It should be as follows (all on one line):

./configure LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"  

Once it's configured, follow the rest of the instructions, and then do the make install.

But you're not done yet  :)

Following the make install, the libwine libraries aren't quite in the right place.  These commands will rectify this.

cd /usr/lib32
sudo ln -s /usr/local/lib/libwine* ./

And once that's done, you've got your very own self compiled wine.

Enjoy!

---

### Post by x64Jimbo on 2006-07-08
A thread for this already exists
[http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557)
Glad you figured it out on your own though. The more we depend on ourselves, the better. :)

---

### Post by darcu on 2006-07-09
That thread seems to be about how to get the i386 .deb to work while this is how to compile the sources on an 64bit machine . Still I'm getting an error related to "freetype" even tho I have it installed . Any ideas ?
```
gcc -m32 -g -O2 -o sfnt2fnt sfnt2fnt.o -L../libs/unicode -lwine_unicode -L../libs/port -lwine_port -L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32 -lfreetype -lz
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libz.a when searching for -lz
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libz.a when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/libz.a when searching for -lz
/usr/bin/ld: cannot find -lz


```

---

### Post by Kilz on 2006-07-09
While the first post is how to compile wine, and the second post is how to install wine from a deb with my howto. With both methods you end up with 32bit wine. You cant compile a 64bit version.
But thanks Jonnycat26, I have been looking for a way to compile wine on 64bits so I can make a deb file for amd64.

---

### Post by Jonnycat26 on 2006-07-09
> **darcu said:**
> That thread seems to be about how to get the i386 .deb to work while this is how to compile the sources on an 64bit machine . Still I'm getting an error related to "freetype" even tho I have it installed . Any ideas ?


Did you follow the instructions on the wine wiki page which dealt with creating the symbolic links for the freetype libraries?

---

### Post by gnowak on 2007-03-16
> **darcu said:**
> That thread seems to be about how to get the i386 .deb to work while this is how to compile the sources on an 64bit machine . Still I'm getting an error related to "freetype" even tho I have it installed . Any ideas ?
```

/usr/bin/ld: cannot find -lz

```

I got the same error: /usr/bin/ld: cannot find -lz when I tried to compile Soplex-1.3.1. The solution for this was to install zlib1g-dev: apt-get install zlib1g-dev

:)

---

### Post by saneone on 2007-03-19
I installed Wine using Apt-get... It just works perfectly for me...

---

