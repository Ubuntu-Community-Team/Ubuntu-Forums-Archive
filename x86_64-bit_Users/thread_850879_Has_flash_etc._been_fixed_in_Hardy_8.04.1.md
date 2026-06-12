---
title: "Has flash etc. been fixed in Hardy 8.04.1?"
date: 2008-07-06
forum: x86 64-bit Users
---

### Post by netsurfau on 2008-07-06
I saw that Hardy 8.04.1 was released the other day.

How does it compare to the original release of Hardy?

Have the flash & other issues been fixed in this new release?

Want to know if it's safe to upgrade as I had a s**t of a time (like a lot
of other people) with Hardy when it first came out.

---

### Post by soxs on 2008-07-06
Well.. for me.. there never was a flash problem,...
But for the rest, there are over 200 fixes including a kernel update.

---

### Post by felker2 on 2008-07-06
I have had no problems with flash in Ubuntu 8.04 64-bit.

---

### Post by Marshal0505 on 2008-07-06
Same here, Flash always worked with no problems here.Switched to hardy in march.

---

### Post by soxs on 2008-07-06
This is how I got the latest flash 10 beta aswell as the repo flashplugin-nonfree to work in opera 9.5x and firefox 3.x to work properly:

> **soxs said:**
> ```
sudo apt-get purge nspluginwrapper flashplugin-nonfree
sudo rm -Rvf /usr/bin/nspluginwrapper
sudo rm -Rvf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```
now search in 
```
/usr/lib/firefox/plugins
```
and
```
/var/lib/flashplugin-nonfree
```
for
```
libflashplayer.so
```
and
```
npwrapper.libflashplayer.so
```
and remove it via ```
sudo rm -vf <filepluspath>
```

So now ervything is cleaned up.

copy the libflashplayer from the tar file to ```
/usr/lib/firefox/plugins
```
```
sudo apt-get install nspluginwrapper
sudo nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so
```
As some webpages still require version 9.xxx
```
sudo apt-get install flashplayer-nonfree
``` (this works, as it does not use the same dir as for 10 beta 2 flaslib, at least it does on x86_64 bit with opera)

---

### Post by netsurfau on 2008-07-07
Soxs,

Are you sure this syntax is correct? - sudo rm -Rvf /usr&*libflashplayer.so

Because when I ran it, it completely removed my /usr directory & everything in it.
I couldn't even stop it with a ctrl+c or ctrl+z.

Only took my six-seven hours to get my system back to something resembling what I started with before using your code.

---

### Post by soxs on 2008-07-07
> **netsurfau said:**
> Soxs,

Are you sure this syntax is correct? - sudo rm -Rvf /usr&*libflashplayer.so

Because when I ran it, it completely removed my /usr directory & everything in it.
I couldn't even stop it with a ctrl+c or ctrl+z.

Only took my six-seven hours to get my system back to something resembling what I started with before using your code.
OMG sorry, that was a type.. next time you seee /* stop typing and ask if this is correct. I am so sorry.

---

### Post by philinux on 2008-07-07
This guide has a bit about flash that gets the job done.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mikewhatever on 2008-07-07
> **netsurfau said:**
> I saw that Hardy 8.04.1 was released the other day.

How does it compare to the original release of Hardy?

Have the flash & other issues been fixed in this new release?

Want to know if it's safe to upgrade as I had a s**t of a time (like a lot
of other people) with Hardy when it first came out.

For issues dealt with in 8.04.1 see the [release anouncement]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html"). I very much doubt they worked on flash, since that's Adobe's software and closed source.

---

### Post by steveneddy on 2008-07-08
Any Flash issues are not Ubuntu's issues, but issues with Adobe making Flash issues for Linux users.

I use Flash 10 beta and it works very well for me on my 64 bit Hardy.

Finally the menu's on websites don't render behind the bigger pic in the middle.

---

