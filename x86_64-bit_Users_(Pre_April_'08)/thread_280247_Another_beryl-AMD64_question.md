---
title: "Another beryl-AMD64 question"
date: 2006-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by fenomenoxp on 2006-10-19
Hi everyone. I gess you are tired to answer this question, but I'm trying to install beryl+XGL on ubuntu dapper with AMD64. Well, my problem is that I don't see any package named "beryl" (I see beryl-plugins or something like that). I have tried adding several repositories I found on other forums, but none of them work at all. So, I ask... What is the definitive-working-repositorie to get beryl working on amd64? :P Do I need to do a "dist-upgrade" as I have read in some posts. I'd prefer not to do it, because I have a 56k modem connection (Its frustrating).
Thanks in advance for your help!
By the way, should I use beryl or compiz-gnome?

---

### Post by John.Michael.Kane on 2006-10-19
Have a look over these.

[http://forum.beryl-project.org/index.html](http://forum.beryl-project.org/index.html)

[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

If you need further help there's IRC channels #xgl #beryl #ubuntu-xgl

---

### Post by killkoy on 2006-10-19
AS far as I know there are no 64bit repos for beryl on dapper. I built it from source. although this probably isn't recomended for the average user
[http://www.ubuntuforums.org/showpost.php?p=1609787&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1609787&postcount=5)

---

### Post by pony-tail on 2006-10-19
I also built from source but wound up with XGL not loading - (but I have a Radeon X850XT-PE which can be problematic under Linux ) I just #ed my /etc/gdm/gdm.conf-custom entries at present and am running standard xorg/fglrx until I have seen a definative soloution - or someone puts the Beryl 64bid debs in the repository.
Beryl does load as the menu diamond icon shows up but no eye candy working .
Compiz works on this machine ( under Gentoo - but gentoo has other issues on this machine )- Definately prefer Beryl if it can be got working !

---

### Post by fenomenoxp on 2006-10-20
Thank you very much for your answers. I'll give a try to compile it by myself if I don't get it working with apt. By the way... will it work if I install it under a chroot? (I use a server-i386 ubuntu installation as chroot).

---

### Post by AlReece45 on 2006-10-20
[These repositories]("http://compiz-mirror.lupine.me.uk/") worked for me. Yes it says its a compiz-mirror, but it has beryl packages on it as well.

---

### Post by killkoy on 2006-10-20
> **AlReece45 said:**
> [These repositories]("http://compiz-mirror.lupine.me.uk/") worked for me. Yes it says its a compiz-mirror, but it has beryl packages on it as well.

contains no packages for beryl on 64bit dapper

---

### Post by AlReece45 on 2006-10-21
> **killkoy said:**
> contains no packages for beryl on 64bit dapper

Did you do this?

> If you use amd64, add ' main-amd64' to the end of the line (so it reads 'main main-amd64')

---

### Post by killkoy on 2006-10-21
if you look in the main and main-amd64 sections of this repositories the only beryl amd64 binaries they contain are beryl-plugins-data and emerald-themes

---

### Post by fenomenoxp on 2006-10-21
I tried it and it is so, only beryl-plugins-data. What I would like to know is that if I use xserver-xgl with the default window manager of ubuntu (metacity?)... will I get any better result (I heared that windows do not need to repaint and everything works more smooth), or do I need to use beryl/compiz ?

---

