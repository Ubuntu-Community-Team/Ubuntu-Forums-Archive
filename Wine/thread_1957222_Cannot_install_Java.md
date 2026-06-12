---
title: "Cannot install Java?"
date: 2012-04-12
forum: Wine
---

### Post by Drowz0r on 2012-04-12
Hello all

I'm in Ubuntu 11.10 64 bit running PlayOnLinux and wine 1.5.1

Some games have their own little launchers, usually mmorpgs such as Star Trek Online for example.

I found that these launchers can use flash and steam itself uses flash - which is why a lot of my navigation was troublesome at the beginning - I didn't realise it did!

I've managed to install flash through PoL but I seem unable to install Java.

When attempting to install it from an online .exe, I get the error:

Download failed:
from=http://javadl.sun.com/webapps/download/GetFile/1.6.0_31-b79/windows-i586/jre1.6.0_31-c-l.msi,to=Sun/Java/fre1.6.0_31/jre1.6.0_31-c-l.msi


So I try the offline installer but get this error:

Installer : Wrapper.CreateFile  failed with error 3: Path not found.

Any idea how I can get Java installed?

I have tried running it in WinXP and Win7 mode.

---

### Post by aura7 on 2012-04-12
You can install java by following the instruction given in this link

[http://deadmango.com/index.php/archives/973](http://deadmango.com/index.php/archives/973)

---

### Post by Drowz0r on 2012-04-12
> **aura7 said:**
> You can install java by following the instruction given in this link

[http://deadmango.com/index.php/archives/973](http://deadmango.com/index.php/archives/973)

Sorry but doesn't that install it on Ubuntu 11.10? I need it installed in Wine/PlayOnLinux for my games to work in Steam.

---

### Post by aura7 on 2012-04-12
OK, got it you need to install the windows version of jre, download the windows version of Sun JRE from [this]("http://java.com/en/download/index.jsp") website.

Right click and run the exe via wine.

---

### Post by Drowz0r on 2012-04-12
Thanks for your quick reply.

I tried that but:

> **Drowz0r said:**
> Hello all

When attempting to install it from an online .exe, I get the error:

Download failed:
from=http://javadl.sun.com/webapps/download/GetFile/1.6.0_31-b79/windows-i586/jre1.6.0_31-c-l.msi,to=Sun/Java/fre1.6.0_31/jre1.6.0_31-c-l.msi


So I try the offline installer but get this error:

Installer : Wrapper.CreateFile  failed with error 3: Path not found.

Any idea how I can get Java installed?

I have tried running it in WinXP and Win7 mode.

---

### Post by Drowz0r on 2012-04-21
It's ok, I managed to install IE8 and that seems to have Java in it already or something. It works within IE8 in wine now.

---

