---
title: "gkrellm"
date: 2005-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthaddon on 2005-03-31
Does anyone know whether there are plans to include gkrellm in amd64 or any other way of installing it? I tried compiling from source without luck and figured I'd check in before delving further...

Thanks, Tom

Okay, update here - I have gkrellm installed:

Simply added the following to /etc/apt/sources.list 

# Debian Pure64
deb [http://debian-amd64.alioth.debian.org/debian-pure64](http://debian-amd64.alioth.debian.org/debian-pure64) sid main contrib non-free
deb-src [http://debian-amd64.alioth.debian.org/debian-pure64](http://debian-amd64.alioth.debian.org/debian-pure64) sid main contrib non-free

sudo apt-get update
sudo apt-get install gkrellm

Very happy...

---

### Post by soul_rebel on 2005-04-01
if you like some skins:
[ftp://soul-rebel.homelinux.org/pub](ftp://soul-rebel.homelinux.org/pub)

---

### Post by mthaddon on 2005-04-01
There's only one skin worth having on gkrellm as far as I'm concerned - "invisible" :smile:

---

### Post by soul_rebel on 2005-04-01
that's what I am using  ;)

---

