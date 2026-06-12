---
title: "So I am unable to install wine."
date: 2008-09-11
forum: Wine
---

### Post by SecurityCop on 2008-09-11
I typed in sudo apt-get install wine and here is what came up.
```
krystle@krystleslaptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.5 is to be installed
        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1.2 is to be installed
        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1.2 is to be installedE: Broken packages

```

However, when I tried to install and update these files, heres what came up.

```
krystle@krystleslaptop:~$ sudo apt-get install libasound2
Reading package lists... Done
Building dependency tree... Done
libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

What do I do?
Oh and if you can explain this, I need VERY simple steps, as I am very new and unsure of this OS.

---

### Post by ad_267 on 2008-09-11
Can you provide a bit more information, like what version of Ubuntu are you using? Have you modified your sources.list file to add another repository for wine?

---

### Post by SecurityCop on 2008-09-11
> **ad_267 said:**
> Can you provide a bit more information, like what version of Ubuntu are you using? Have you modified your sources.list file to add another repository for wine?

Using Ubuntu 6, and that second thing I have no idea because my brother used to own this laptop so I have no idea what he did on it.

---

### Post by ad_267 on 2008-09-11
Ok that's pretty old. Have you considered upgrading to the latest version, 8.04?

Can you post the output of these commands from a terminal:
```
cat /etc/apt/sources.list
apt-cache show wine
```

---

### Post by SecurityCop on 2008-09-11
> **ad_267 said:**
> Ok that's pretty old. Have you considered upgrading to the latest version, 8.04?

Can you post the output of these commands from a terminal:
```
cat /etc/apt/sources.list
apt-cache show wine
```

I really doubt this crappy crappy laptop could run that.
```
krystle@krystleslaptop:~$ cat /etc/apt/sources.list

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt dapper main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
#AUTOMATIX REPOS END
deb http://apt.emesene.org/ ./
deb-src http://apt.emesene.org/ ./
```

---

### Post by ad_267 on 2008-09-11
Ok it looks like automatix has added a repository for wine. That could be what's causing the problem but I don't really know anything about automatix. You could try running automatix to install wine and see if it works. Otherwise I would delete this line:
```

deb http://wine.lowvoice.nl/apt dapper main

```
You can run "gksu gedit /etc/apt/sources.list" to delete that line.
And then try installing again.
```
sudo apt-get update
sudo apt-get install wine
```

Oh and you might be surprised, Ubuntu seems to keep getting better on older hardware. What are the specs? Another option is something a bit lighter like Xubuntu.

---

### Post by SecurityCop on 2008-09-12
I just tried that and absolutely nothing changed. 
And here are the specs.
[http://reviews.cnet.com/laptops/hp-compaq-presario-2100/4507-3121_7-21271063.html](http://reviews.cnet.com/laptops/hp-compaq-presario-2100/4507-3121_7-21271063.html)

---

### Post by ad_267 on 2008-09-12
Ok try this command which is supposed to fix broken packages:
```
sudo apt-get install -f
```

That laptop should be able to run Ubuntu 8.04 fine.

---

### Post by SecurityCop on 2008-09-12
> **ad_267 said:**
> Ok try this command which is supposed to fix broken packages:
```
sudo apt-get install -f
```

That laptop should be able to run Ubuntu 8.04 fine.

```
krystle@krystleslaptop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

See the problem is that I can't install it without having a working CD/DVD drive. Plus if I could do it without the drive, I have no idea how. I'm not very good when it comes to software. Hardware I'm pretty good at, but otherwise, not really.

---

### Post by YokoZar on 2008-09-12
Try removing this line: deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


Basically, automatix screws things up and it's good that we've gotten rid of it since 8.04.

---

### Post by SecurityCop on 2008-09-12
> **YokoZar said:**
> Try removing this line: deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


Basically, automatix screws things up and it's good that we've gotten rid of it since 8.04.

I got rid of it, and heres what comes up.

```
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://apt.emesene.org/./Sources.gz 404 Not Found
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Is it just not meant to be on this laptop?

---

### Post by ad_267 on 2008-09-13
When does that come up?

Did you run "sudo apt-get update"?

---

### Post by SecurityCop on 2008-09-14
> **ad_267 said:**
> When does that come up?

Did you run "sudo apt-get update"?

It comes up when I type 'sudo apt-get install wine'. And I did run that , and nothing changed, it still doesn't update the 5 files I am missing.

---

### Post by Meow27 on 2008-09-14
"I really doubt this crappy crappy laptop could run that"



your laptop will be able to run hardy more than it would with edgy

besides hardy was developed for much older systems as long as you have 256+ ram you are good to go i guess,,,,,,

---

### Post by SecurityCop on 2008-09-14
> **Meow27 said:**
> "I really doubt this crappy crappy laptop could run that"



your laptop will be able to run hardy more than it would with edgy

besides hardy was developed for much older systems as long as you have 256+ ram you are good to go i guess,,,,,,

I would install it, but I don't have enough space on my harddrive to parition it and save all of my files, music and ect.

But I still wouldn't mind figuring out the wine problem on this laptop.

---

### Post by aoanla on 2008-09-15
> **SecurityCop said:**
> I got rid of it, and heres what comes up.

```
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://apt.emesene.org/./Sources.gz 404 Not Found
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Is it just not meant to be on this laptop?


Well, why don't you apply your experience of how you solved the previous problems?
You removed some lines from your sources.list so that apt didn't check those repositories.
Now, you can see that apt is complaining about the [http://dl.google.com](http://dl.google.com) repository, so try removing the line concerning it from your sources.list.

At the very least, it should stop apt complaining about it.

---

### Post by desertboy on 2008-09-15
Won't the deb's work

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by SecurityCop on 2008-09-17
Nope everytime I download one, and go to install it, it opens the dev opener, and then it closes. For no apparant reason.

Apparantly this mystery is much more baffling then I expcted.

EDIT: New problem when I try to update. I fixed one by removing a few lines.

Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Reading package lists... Done

---

### Post by linux.convert on 2008-09-18
As far as which Ubuntu to use, I recommend 7.04.
7.10 was a tad glitchy on my laptop:

1.6 GHz
380 RAM
40 GB Hard Drive

---

### Post by jofre on 2008-09-19
Hi, I am having a similar problem:

Just installed xubuntu 8.04.1, and I get the same problem when trying to install wine. (after following the instruction in: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) )


Les paquets suivants contiennent des dépendances non satisfaites*:
  wine: Dépend: ia32-libs (>= 1.6) mais ne sera pas installé
        Dépend: lib32asound2 (> 1.0.14) mais ne sera pas installé
        Dépend: lib32nss-mdns (>= 0.10-3) mais ne sera pas installé
        Dépend: libc6-i386 (>= 2.6-1) mais ne sera pas installé
E: Paquets défectueux

(I know it is in French, but the message is clear, isn't it?)

Any ideas?

---

