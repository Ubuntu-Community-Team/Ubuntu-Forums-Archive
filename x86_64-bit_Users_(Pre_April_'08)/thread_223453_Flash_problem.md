---
title: "Flash problem"
date: 2006-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fedcer on 2006-07-26
Hi, I'm having some problems with repoducing falsh movies. The thing is that when I try to reproduce a video it runs slowly, stuttering; for example it plays for 1-2 seconds then both sound and video stop completly for 4-5 seconds and so on (no it is not becasue it is still downloading the video). I kown the description is very bad but I find it hard to explain it well.

I'm using the flsh plugin in Opera 9.0. To install the flash player I extracted the conetens of the .tar.gz file and the run:
```

sudo linux32 ./flashplayer_installer

```
and I install it to "/usr/lib/opera"
I think that what I'm doing to install is ok because I've done the same in another pc and it is working fine.

I even tried to uninstall opera and flash comlpetly and then reinstall them but it is the same.

Thank you,

Fedcer

---

### Post by jordilin on 2006-07-26
> **Fedcer said:**
> 
```

sudo linux32 ./flashplayer_installer

```


I don't understand this command. What's the meaning of linux32 in front of the installer script?
You should write:
```
sudo ./flashplayer_installer
```

---

### Post by Fedcer on 2006-07-26
> **jordilin said:**
> I don't understand this command. What's the meaning of linux32 in front of the installer script?
You should write:
```
sudo ./flashplayer_installer
```

But the script checks for the architecture. If I don't use linux32 the script will fail saying that my architecture is not supported.

---

### Post by jordilin on 2006-07-26
> **Fedcer said:**
> But the script checks for the architecture. If I don't use linux32 the script will fail saying that my architecture is not supported.

And what architecture are you using? Seeing this linux32 I suppose it's an intel pentium, and running an intel pentium you should run directly the script without writing down this linux32 command. I have taken a look at the readme.txt of this package (I also installed the flashplayer from this package) and it does not say anything about linux32. :(

---

### Post by Fedcer on 2006-07-26
I'm using Ubuntu 64bit , this is the 64bit subforum. :)

---

### Post by juicemansam on 2006-07-26
I'm just jumping in here with no real information about the subject.

[quote="Linux32 package description"]**Wrapper to set the execution domain**
the linux32 tools allows 64bit systems with support for 32 bit
applications to set the personality to the 32 bit native type.

For instance, on an amd64 or ia64 machine, commands run with this
wrapper will think the machine type is i686, as returned by uname -m.

On systems without support for the PER_LINUX_32 execution domain, this
program has no effect.[/quote]

I'm currently trying [Gnash](http://www.gnu.org/software/gnash/), but it's missing sound and never loads flash files with the browser plugin, but does at the command line (which is were I get no sound). It also only supports Flash 7 and older.

---

### Post by jordilin on 2006-07-27
> **Fedcer said:**
> I'm using Ubuntu 64bit , this is the 64bit subforum. :)
Oops! You are right, I didn't notice that :oops: . So, I can't be of much help as my cpu is an intel pentium 32 bit. Let's see if anyone else has installed the flashplayer in a 64bit platform. If macromedia does not provide it I'm not sure if it will be available, but let's await :)

---

### Post by Kilz on 2006-07-27
If you want flash movies playing in your browser. You can use gnash or you can setup [32bit firefox with the 32bit plugins]("http://www.ubuntuforums.org/showthread.php?p=1174435") with my howto/scripts for the amd64 version.

---

### Post by Fedcer on 2006-07-28
> **Kilz said:**
> If you want flash movies playing in your browser. You can use gnash or you can setup [32bit firefox with the 32bit plugins]("http://www.ubuntuforums.org/showthread.php?p=1174435") with my howto/scripts for the amd64 version.

I know, and Opera is 32bit, so flash should work there too, in fact in another pc with Ubuntu 64bit I have it working. The strange thing is that the flash plugin is recognized, but it plays movies with a lot of stutter.

Anyways, I'll install Firefox 32bit and see if with it flash works properly.

EDIT: Well, I installed Firefox, and with it flash works fine. Apparently, it's a problem with Opera (which I still don't understand since, as I said, in another pc it works).
Since it is an Opera-specific problem I'll post the issue at the Opera forums,

Thanks,

Fedcer

---

