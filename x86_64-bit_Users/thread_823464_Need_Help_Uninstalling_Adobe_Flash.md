---
title: "Need Help Uninstalling Adobe Flash"
date: 2008-06-09
forum: x86 64-bit Users
---

### Post by Jenga-kun on 2008-06-09
I asked this in this in a different category but nobody's helping me and I really need this done. I tried the flash 9 install script that's stickied at the top of this forum but now my flash isn't working. I think it's because I still have adobe flash still installed on my system. The problem is is that I don't know how to uninstall it. Can somebody please help me?

---

### Post by Vadi on 2008-06-09
Hm. Can you point me to this script?

---

### Post by Jenga-kun on 2008-06-09
> **Vadi said:**
> Hm. Can you point me to this script?

It's right at the top of this forum. Here's the link: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by Vadi on 2008-06-09
I wonder why did they sticky it. It looks pretty horrible.

Try this to remove it:

> sudo apt-get remove nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo rm /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
sudo rm /usr/lib/firefox-3.0b5/plugins/npwrapper.libflashplayer.so

Then just go to youtube.com, and install the adobe flash that it gives you.

---

### Post by xebian on 2008-06-09
> **Jenga-kun said:**
> It's right at the top of this forum. Here's the link: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

The official way to install flash plugin is to install it from the repo
```

sudo aptitude install flashplugin-nonfree

```

This is very important especially for 64-bit users as this meta package will install all the supporting 32-bit libs for you in 1 (one) easy simple step.

---

### Post by Kilz on 2008-06-09
> **xebian said:**
> The official way to install flash plugin is to install it from the repo
```

sudo aptitude install flashplugin-nonfree

```

This is very important especially for 64-bit users as this meta package will install all the supporting 32-bit libs for you in 1 (one) easy simple step.

I took a look at the post history of the original poster. It looks like they are running Gutsy still. If this is the case that commands will not help. Flash packages are broken in 64bit Gutsy.

---

### Post by xebian on 2008-06-09
> **Kilz said:**
> I took a look at the post history of the original poster. It looks like they are running Gutsy still. If this is the case that commands will not help. Flash packages are broken in 64bit Gutsy.

I have been using this since Gutsy, and I still have a Gutsy box.

I think the Kilz scripts sticky needs a refresh/update.  :guitar:

---

### Post by Kilz on 2008-06-09
> **xebian said:**
> I have been using this since Gutsy, and I still have a Gutsy box.

I think the Kilz scripts sticky needs a refresh/update.  :guitar:

What do you think needs to be included?

---

