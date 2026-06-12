---
title: "Command line install of linux-amd64-k8-smp"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nachtengel on 2006-04-15
Attempting to install breezy on my new Athlon X2 machine, I've had to run the installation process from the terminal booting off the x86 live cd because I needed to run dmraid for my software RAID which I'm installing to.  

I've installed the base system to /target, but when I chroot /target and input the following command:

[B][B]ubuntu@ubuntu: apt-get install ubuntu-base linux-amd64-k8-smp ubuntu-desktop dmraid grub

Reading Package Lists...Done
Building Dependency Tree...Done
E: Couldn't find package linux-amd64-k8-smp[/B]

I am given the above error about linux-amd64-k8-smp not existing.  I know it exists somewhere, can someone point me in the right direction?  [/B]

I have the Universe repositories available in my /etc/apt/sources.list as well as Main and Security.

---

### Post by localzuk on 2006-04-15
Try the 'kernel-image-2.6.11-9-amd64-k8-smp' package

---

### Post by Nachtengel on 2006-04-15
[QUOTE=localzuk]Try the 'kernel-image-2.6.11-9-amd64-k8-smp' package[/QUOTE]


Same issue:

E: Couldn't find package kernel-image-2.6.11-9-amd64-k8-smp

Which repository should these packages be in?

---

### Post by localzuk on 2006-04-15
That one should have been in Universe - assuming you are using Breezy.

Have you ran apt-get update since you added the other repo's?

---

### Post by Nachtengel on 2006-04-15
I am using Breezy and I do have the Universe repository in my sources.list.  I have run apt-get update a few times and have gotten a success message back from the universe repositories.  Every time I try, I get the same error message that it can't find the package.  This seems straightforward but it is really baffling that it is not working.  Any further suggestions?

Anyone else want to put in their 2 cents?

---

### Post by Stormbringer on 2006-04-15
Try it that way...

# sudo apt-get install linux-image-amd64-k8-smp

This package will always depend on the latest kernel image available (currently 2.6.12.16.1)

Cheers,
Storm

---

### Post by Nachtengel on 2006-04-15
The exact same error again.  Are there any theories on why this isn't working other than  a typo? I've done the apt-get update... seems to be pulling the universe packages.  

ubuntu@ubuntu: apt-get update

These two show up during the update process:

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources

---

### Post by Stormbringer on 2006-04-15
Hmm ... this is kind of strange.

"linux-image" is located in the standard main repository - no need for Universe or Multiverse to be enabled.

Could you please post your /etc/apt/sources.list?

[EDIT - Here's a copy of mine]

```

## Breezy CD-/DVD-ROM
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

## Breezy Officially Supported Main Restricted (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://at.archive.ubuntu.com/ubuntu breezy main restricted

## Breezy Officially Supported Main Restricted Updates (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://at.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Breezy Community Maintained Universe (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy universe
deb-src http://at.archive.ubuntu.com/ubuntu breezy universe

## Breezy Non-Free Multiverse (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://at.archive.ubuntu.com/ubuntu breezy multiverse

## Breezy Backports (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://at.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## Breezy Officially Supported Security Updates (Binary / Source)
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

## Breezy Community Maintained Universe Sercurity Updates (Binary / Source)
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Ubuntu Backports Project - OpenOffice.org2 AMD64
deb http://people.ubuntu.com/~doko/OOo2-amd64 ./


```

Try to go with this one ... replace "at." with your country code or take it out.
And DON'T forget to do a sudo apt-get update when you do changes to your sources.list

Thanks.

---

### Post by localzuk on 2006-04-16
Also, you can do a search in the database by using 
```

sudo apt-cache search linux-image | less

```

This should list all kernels available to you.

---

### Post by Nachtengel on 2006-04-16
[QUOTE=Stormbringer]Hmm ... this is kind of strange.

"linux-image" is located in the standard main repository - no need for Universe or Multiverse to be enabled.

Could you please post your /etc/apt/sources.list?

[EDIT - Here's a copy of mine]

```

## Breezy CD-/DVD-ROM
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

## Breezy Officially Supported Main Restricted (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://at.archive.ubuntu.com/ubuntu breezy main restricted

## Breezy Officially Supported Main Restricted Updates (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://at.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Breezy Community Maintained Universe (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy universe
deb-src http://at.archive.ubuntu.com/ubuntu breezy universe

## Breezy Non-Free Multiverse (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://at.archive.ubuntu.com/ubuntu breezy multiverse

## Breezy Backports (Binary / Source)
deb http://at.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://at.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## Breezy Officially Supported Security Updates (Binary / Source)
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

## Breezy Community Maintained Universe Sercurity Updates (Binary / Source)
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Ubuntu Backports Project - OpenOffice.org2 AMD64
deb http://people.ubuntu.com/~doko/OOo2-amd64 ./


```

Try to go with this one ... replace "at." with your country code or take it out.
And DON'T forget to do a sudo apt-get update when you do changes to your sources.list

Thanks.[/QUOTE]

Well since I'm not using the computer that is having the issue to post on the forums, it's hard to copy/paste back and forth... so I copied your sources.list file with the following changes:

Did not include the OpenOffice.org Sources

[http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) becomes [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

Other than that, I now have an exact copy of those sources.list in the chrooted environment

[QUOTE=localzuk]Also, you can do a search in the database by using 
```

sudo apt-cache search linux-image | less

```

This should list all kernels available to you.[/QUOTE]

This command lists x86, PPC and amd-k7 (with and without smp) as valid options.  What gives?  amd64-k8 should be an option, right?

Can anyone tell me which repository exactly holds **linux-kernel-amd64-k8-smp**?

---

### Post by localzuk on 2006-04-16
Hmm... Now that I look at it, the amd64 kernels are not in the repos for me either. Have you tried using the 64bit installer?

---

### Post by Stormbringer on 2006-04-16
[QUOTE=Nachtengel]Can anyone tell me which repository exactly holds **linux-kernel-amd64-k8-smp**?[/QUOTE]
The pre-compiled kernel images reside in MAIN ...
```

deb http://archive.ubuntu.com/ubuntu breezy main restricted

```
I just made a screenshot of Synaptic (did a update before) - the file you are looking for is there, see for yourself [here]("http://img398.imageshack.us/img398/8363/synapticamd64k8smp8vq.png").
BTW: It's not Dapper - it's just Breezy AMD64 with Dapper's theme.

In case you are looking for the kernel source, you better take a look at the following threads ...

[HOWTO: Kernel Compilation for Newbies]("http://ubuntuforums.org/showthread.php?t=56835")
[HOWTO: Compile the new 2.6.16 kernel from kernel.org]("http://ubuntuforums.org/showthread.php?t=157560")

There you will find all the required information on how to compile your own custom kernel.

Also, make sure you actually have the AMD64 version of Ubuntu 5.10 installed on your box - if you are running the i386 Release you won't be able to see amd64 packages in apt-get or Synaptic.

EDIT - Here the output of "sudo apt-cache search linux-image"; the command that got suggested by localzuk on the first page.
```

stormbringer@nebuchadnezzar:~$ sudo apt-cache search linux-image
linux-image-2.6.12-9-amd64-generic - Linux kernel image for version 2.6.12 on x86_64.
linux-image-2.6.12-9-amd64-k8 - Linux kernel image for version 2.6.12 on AMD K8.
linux-image-2.6.12-9-amd64-k8-smp - Linux kernel image for version 2.6.12 on AMD K8 SMP.
linux-image-2.6.12-9-amd64-xeon - Linux kernel image for version 2.6.12 on Intel x86_64.
linux-image-2.6.12-10-amd64-generic - Linux kernel image for version 2.6.12 on x86_64.
linux-image-2.6.12-10-amd64-k8 - Linux kernel image for version 2.6.12 on AMD K8.
linux-image-2.6.12-10-amd64-k8-smp - Linux kernel image for version 2.6.12 on AMD K8 SMP.
linux-image-2.6.12-10-amd64-xeon - Linux kernel image for version 2.6.12 on Intel x86_64.
linux-image-amd64-generic - Linux kernel image on x86_64.
linux-image-amd64-k8 - Linux kernel image on AMD K8.
linux-image-amd64-k8-smp - Linux kernel image on AMD K8 SMP.
linux-image-amd64-xeon - Linux kernel image on Intel x86_64.
linux-tree-2.6.12 - Linux kernel tree for building prepackaged Ubuntu kernel images

```
Storm.

---

### Post by Nachtengel on 2006-04-16
Stormbringer, you hit the nail on the head.  I was attempting to do the update from an x86 LiveCD boot.  That must be why I'm not seeing the amd64 packages.

Guess it's back to square one... I was using the live CD to follow these instructions [FakeRAIDHowTo]("https://wiki.ubuntu.com/FakeRaidHowto")
and hit a snag about where I was installing the linux kernel.

Thank you for all your help everyone... it has been most illuminating.

Here's hoping I can get as far with the AMD64 live CD...

---

### Post by Stormbringer on 2006-04-16
[QUOTE=Nachtengel]Stormbringer, you hit the nail on the head.  I was attempting to do the update from an x86 LiveCD boot.  That must be why I'm not seeing the amd64 packages.
[/QUOTE]

Glad we got your issue sorted.

Keep in mind: mixing architectures is not possible! A 64-Bit kernel won't run on an 32-Bit x86 install and vice versa.

If you need the k8-smp kernel for some reason, then you need to have Ubuntu AMD64 installed ("k8" implies that this is a 64-Bit compile).

[QUOTE=Nachtengel]Here's hoping I can get as far with the AMD64 live CD...[/QUOTE]

If the x86 Live CD worked for you, then you shouldn't have any troubles with the amd64 one either.

Regards,
Storm

---

