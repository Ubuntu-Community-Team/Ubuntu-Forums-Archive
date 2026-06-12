---
title: "Opera"
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by bofphile on 2006-04-21
Hi all!

I'm using Dapper 64 bits.
I was a little frustrated by Firefox integrated with Dapper. From what I've read on the forum, I know that there is something wrong with it. So I decided to try another browser. I've tested  some browsers like Galeon but I didn't find them as complete as Firefox. Now I'm using Opera 9 Preview and I'm really impressed. It's a lot more faster, more responsive than Firefox. Until the problem with Firefox in Dapper is solved, I will continue to use Opera and enjoy it.

A little question from those who use Opera: How can I have the Personnal Toolbar with the RSS feeds on the top like Firefox ?

Thanks.

---

### Post by rplantz on 2006-04-21
[QUOTE=bofphile]Hi all!

I'm using Dapper 64 bits.
...
Now I'm using Opera 9 Preview and I'm really impressed. It's a lot more faster, more responsive than Firefox. Until the problem with Firefox in Dapper is solved, I will continue to use Opera and enjoy it.
Thanks.[/QUOTE]

I just downloaded opera-static_9.0-20060411.1-qt_en_i386.deb. When I try to install:
```

 sudo dpkg -i --force-architecture opera-static_9.0-20060411.1-qt_en_i386.deb

```
I get the error messages:```

dpkg: dependency problems prevent configuration of opera-static:
 opera-static depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
dpkg: error processing opera-static (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera-static

```
I cannot locate xlib6g or xlibs in Synaptic Package Manager. I have the restricted and universe repositories enabled. How did you get it to install?

---

### Post by bofphile on 2006-04-21
I've downloaded this build: [http://snapshot.opera.com/unix/Weekly-241/intel-linux/opera-9.0-20060419.1-static-qt.i386-en-241.tar.gz]("http://snapshot.opera.com/unix/Weekly-241/intel-linux/opera-9.0-20060419.1-static-qt.i386-en-241.tar.gz")

And it works great.

---

### Post by rplantz on 2006-04-21
[QUOTE=bofphile]I've downloaded this build: [http://snapshot.opera.com/unix/Weekly-241/intel-linux/opera-9.0-20060419.1-static-qt.i386-en-241.tar.gz]("http://snapshot.opera.com/unix/Weekly-241/intel-linux/opera-9.0-20060419.1-static-qt.i386-en-241.tar.gz")

And it works great.[/QUOTE]

Thank you!

It does work. I have to figure out how to get flashplayer to work with it, but I think I can eventually do that.

Edit: I figured out flashplayer. The trick seems to be to install it as root (with sudo).

---

### Post by Adler on 2006-04-21
rplantz,

What commands did you use to install the Flashplayer?

---

### Post by rplantz on 2006-04-21
[QUOTE=Adler]rplantz,

What commands did you use to install the Flashplayer?[/QUOTE]

I went to [www.macromedia.com](www.macromedia.com) and downloaded a file named install_flash_player_7_linux.tar.gz. The ```

tar xvfz install_flash_player_7_linux.tar.gz

```
command gives you a directory named install_flash_player_7_linux. Inside there you will find a Readme file that tells what to do. I used sudo to install it globally:
```

sudo ./flashplayer-installer

```
As I recall, it will ask you for some directories. There is an assumption that you're installing it for mozilla. My opera application is located:
```

/usr/bin/opera

```
and the plugins are in:
```

/usr/lib/opera/plugins/

```
I had already done this for Breezy, then did a fresh install of Dapper. Some things were already in place, and I don't recall exactly what I did in Breezy. I hope this is close enough for you to figure out how to get it to work.

---

### Post by Adler on 2006-04-21
rplanz,

Thanks for that.

---

