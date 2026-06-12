---
title: "new here, cant get flash working"
date: 2008-10-19
forum: x86 64-bit Users
---

### Post by LakaiorDie on 2008-10-19
no matter what i've tried, i cant get flash working. i'd like to use linux full time. other than the occasional booting into xp pro to sync my iphone with itunes and get updates. but not having flash sucks. ive searched everywhere but nothing has worked. 

thanks.

---

### Post by LakaiorDie on 2008-10-19
this is what i get

~$ sudo apt-get install nspluginwrapper flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nspluginwrapper: Depends: ia32-libs (>= 1.6) but it is not going to be installed
                   Depends: lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19) but it is not going to be installed
E: Broken packages

---

### Post by LakaiorDie on 2008-10-20
the only player that works is swfdec and its kinda choppy in full screen. and when i click high quality in youtube it doesnt work. i also cant skip through the video.

this sucks

---

### Post by Thelasko on 2008-10-20
Make sure you have the [multiverse repository enabled.]("http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html")

---

### Post by kaivalagi on 2008-11-03
Has the issue been resolved? I have the same dependancy problems when trying to install flashplugin-nonfree and nspluginwrapper on a new 8.10 install...e.g.

```
sudo apt-get install nspluginwrapper flashplugin-nonfree
```

gives me:

```
The following packages have unmet dependencies.
  nspluginwrapper: Depends: ia32-libs (>= 1.6) but it is not going to be installed
                   Depends: lib32gcc1 (>= 1:4.1.1) but it is not going to be installed
E: Broken packages

```

Is it just a waiting game here? The dependencies look out of whack...if I drill down through the dependancies trying to install those I find this:

```
lib32gcc1:
  Depends: gcc-4.3-base (=4.3.2-1ubuntu10) but 4.3.2-1ubuntu11 is to be installed
```

???

---

### Post by CJ56 on 2008-11-03
Has anyone tried this - 

[http://queleimporta.com/the-easiest-...tu-64-bits/en/](http://queleimporta.com/the-easiest-...tu-64-bits/en/)

I used it on 8.04 so I can't speak for 8.10, but it worked well - just go to the webpage, copy the command & paste

Took about 30 seconds...

So easy, I feel sure there must be something wrong with it

---

### Post by kaivalagi on 2008-11-03
This:

[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

talks about installing using a script, which I do not want to do.

The latest post about flash on the site:

[http://queleimporta.com/installing-flash-10-on-intrepid-ubuntu-810-64-bits/en/](http://queleimporta.com/installing-flash-10-on-intrepid-ubuntu-810-64-bits/en/)

advices to use this:

sudo apt-get install flashplugin-nonfree

Which is what I was doing...

---

### Post by kaivalagi on 2008-11-03
Fixed the issue with my dependancies

I used aptitude rather than apt-get and it sorted the mess out for me. I shall be using this from now on...It turns out my install of build-essentials and devscripts may have played a part in introducing the dependency issue.

I first removed the main packages I thought were causing issues as follows:

```
sudo aptitude remove build-essentials
sudo aptitude remove devscripts
```

then did this for gcc-4.3-base for good measure:

```
sudo aptitude remove gcc-4.3-base
```

then proceeded to install build-essentials, devscripts and flash support using:

```
sudo aptitude install build-essentials
sudo aptitude install devscripts
sudo aptitude install flashplugin-nonfree
```

All sorted now :)

---

### Post by Yellow Pasque on 2008-11-03
```
lib32gcc1:
  Depends: gcc-4.3-base (=4.3.2-1ubuntu10) but 4.3.2-1ubuntu11 is to be installed
```

This problem appears to be fixed by updating the repo database (i.e. lib32gcc1 has been upgraded to 4.3.2-1ubuntu11 and now depends on gcc-4.3-base..ubuntu11)

---

### Post by kaivalagi on 2008-11-03
> **Temüjin said:**
> ```
lib32gcc1:
  Depends: gcc-4.3-base (=4.3.2-1ubuntu10) but 4.3.2-1ubuntu11 is to be installed
```

This problem appears to be fixed by updating the repo database (i.e. lib32gcc1 has been upgraded to 4.3.2-1ubuntu11 and now depends on gcc-4.3-base..ubuntu11)

Good news, thanks

---

