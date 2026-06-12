---
title: "Apt Update Errors."
date: 2009-08-14
forum: x86 64-bit Users
---

### Post by cchester on 2009-08-14
Hello,

I am having issues with Apt and not sure what has caused it.

When I try and update Apt sources list I get this error for example:

apt-get: -q update
Get: [http://ftp.debian.org](http://ftp.debian.org) sid/main Sources
Get: [http://ftp.debian.org](http://ftp.debian.org) sid/contrib Sources
Get: [http://ftp.debian.org](http://ftp.debian.org) sid/non-free Sources
Convert: acl 2.2.47-3
Convert: alsa-lib 1.0.20-3
Convert: arts 1.5.9-3
Convert: atk1.0 1.26.0-1
Convert: at-spi 1.26.0-1
Convert: attr 1:2.4.43-3
Error: Binary / source version mismatch, skipping.

I have tried to revert to the old source list and have even deleted the source list that was being used when this started but no matter what I get the above. So Apt never updates because of the errors. I can install programs just can't update my source list and do system updates.

Any ideas? Please help because I don't want to have to reinstall.

Thanks.

---

### Post by cchester on 2009-08-15
BUMP Bump

---

### Post by warp99 on 2009-08-15
Why is your source list getting packages from Debian instead of the Ubuntu repositories? Did you change them at some point?

---

### Post by cchester on 2009-08-15
I am not sure. I added something to my source list and then one day the above started happening. Don't remember what I added because at the time when I updated I wasn't getting the above error so I can figure out what is causing it to do it.

Like I said though I wiped out my source list and tried to start over from scratch and it hasn't done any good. So I am thinking apt's settings have changed somehow.

Any ideas?

What could I do to fix this?

---

### Post by warp99 on 2009-08-15
You don't need to re-install unless there is a major screw up. First we need to generate a new repository sources.list. You can do that here:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Replace this list with your /etc/apt/sources.list file.

Then remove the archive files as follows:

```
sudo rm /var/lib/apt/lists/*
```

and any old packages:

```
sudo rm /var/cache/apt/archives/* /var/cache/apt/archives/partial/*
```

This will remove all of the older package files, but leave the directories intact. After that issue a "sudo apt-get update" to see if this helps.

---

### Post by cchester on 2009-08-16
Hello,

Thanks for the reply.

I get the following error when I run the first command listed.

rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

I also get the following error when I run the second command listed.

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory

Do I need to be in the directory?

Still need help on this.

I did generate a new source list successfully though.

Thanks for the help.
> **warp99 said:**
> You don't need to re-install unless there is a major screw up. First we need to generate a new repository sources.list. You can do that here:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Replace this list with your /etc/apt/sources.list file.

Then remove the archive files as follows:

```
sudo rm /var/lib/apt/lists/*
```

and any old packages:

```
sudo rm /var/cache/apt/archives/* /var/cache/apt/archives/partial/*
```

This will remove all of the older package files, but leave the directories intact. After that issue a "sudo apt-get update" to see if this helps.

---

### Post by warp99 on 2009-08-16
> I get the following error when I run the first command listed.

rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

I also get the following error when I run the second command listed.

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory

Do I need to be in the directory?

Just ignore those messages since you don't want to remove any directories plus the partial directory was already empty.

---

### Post by cchester on 2009-08-16
Hello,

Ok but I am still getting the same thing as before.

Where else can I look because it is still trying to do the same thing after running the sudo apt-get update with the new source list?

Thanks for any more help.

> **warp99 said:**
> Just ignore those messages since you don't want to remove any directories plus the partial directory was already empty.

---

### Post by warp99 on 2009-08-16
Run the following command and post the output:

```
dpkg -s apt
```

Also post the output of apt-get update without the -q parameter. You can run this command:

```
sudo apt-get update | tee output.txt
```

And just attach the file to your post. You can also use tee with the previous command since it just redirects stdout to a file.

---

### Post by cchester on 2009-08-17
Hello,

Thanks for the reply.

Here is what I get when I run dpkg -s apt:

Package: apt
Status: install ok installed
Priority: important
Section: admin
Installed-Size: 5280
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.7.20.2ubuntu6
Replaces: libapt-pkg-dev (<< 0.3.7), libapt-pkg-doc (<< 0.3.7)
Provides: libapt-pkg-libc6.9-6-4.7
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.2.1)
Recommends: ubuntu-keyring
Suggests: aptitude | synaptic | gnome-apt | wajig, dpkg-dev, apt-doc, bzip2, lzma, python-apt
Conffiles:
 /etc/apt/apt.conf.d/01autoremove 2b6786021f1ac070e6aa9615ca8f91c5
 /etc/apt/apt.conf.d/01ubuntu 078b96538a377743bee0f554eb5b2fc6
 /etc/logrotate.d/apt 172476f0940b1793f6190ed60031871a
 /etc/cron.daily/apt 57e82a97f436190a5fad105079a7351c
Description: Advanced front-end for dpkg
 This is Debian's next generation front-end for the dpkg package manager.
 It provides the apt-get utility and APT dselect method that provides a
 simpler, safer way to install and upgrade packages.
 .
 APT features complete installation ordering, multiple source capability
 and several other unique features, see the Users Guide in apt-doc.
Original-Maintainer: APT Development Team <deity@lists.debian.org>

Here is what I get when I run sudo apt-get update | tee output.txt:

I will post this when it finishes because it takes forever when I run it.

Where will the output file end up? In my home directory maybe?

Also the apt-get update -q command is happening automatically I am not telling it to do that myself.

Thanks for anymore help on this.

> **warp99 said:**
> Run the following command and post the output:

```
dpkg -s apt
```

Also post the output of apt-get update without the -q parameter. You can run this command:

```
sudo apt-get update | tee output.txt
```

And just attach the file to your post. You can also use tee with the previous command since it just redirects stdout to a file.

---

### Post by warp99 on 2009-08-17
> Where will the output file end up?

In the directory where you ran the command.

---

### Post by cchester on 2009-08-17
Hello,

Wasn't sure because sometimes even if you run the a command from one place it can default to a different directory.

Here is the out put from the command you said to run.

Thanks for anymore help.

---

### Post by warp99 on 2009-08-17
You're still getting packages from a Debian source. Since you already updated you sources.lst file there must be a source file in your "/etc/apt/sources.list.d" directory. Go into that directory and delete any files that may be in there and try again.

---

### Post by cchester on 2009-08-17
Hello,

The only thing in the directory was something for medibuntu and I deleted it and still have the same problem when I run the update.

Is there a way to get apt to stop doing the -q or whatever it is doing when it updates?

I am lost with this.

Thanks for any more help on this.

> **warp99 said:**
> You're still getting packages from a Debian source. Since you already updated you sources.lst file there must be a source file in your "/etc/apt/sources.list.d" directory. Go into that directory and delete any files that may be in there and try again.

---

### Post by warp99 on 2009-08-17
Can you post the output of 'apt-config dump' and your sources.list file. This is very perplexing since apt-get according to the man pages will only use the sources.list file and directory unless configured to use a different location.

---

### Post by cchester on 2009-08-18
Hello,

Thanks again for the reply.

Here is the apt-config dump file you requested.

Sorry I had to rename the fiels to upload them.

Thanks for any more help.

> **warp99 said:**
> Can you post the output of 'apt-config dump' and your sources.list file. This is very perplexing since apt-get according to the man pages will only use the sources.list file and directory unless configured to use a different location.

---

### Post by cchester on 2009-08-18
Bump Bump

---

### Post by warp99 on 2009-08-18
Everything looks in order with apt-config and your sources.list file. Try these options in this order:

1) Make an empty sources.list file, then try to update

2) Run the command 'sudo dpkg-reconfigure apt'

3) Download the apt package from here:

   [http://packages.ubuntu.com/hardy/apt](http://packages.ubuntu.com/hardy/apt)

   Then install using 'sudo dpkg -i apt_0.7.9ubuntu17.2_i386'

Try to run the update between each attempt to see if this takes care of the problem.

Edit: If you're using a 64-bit OS then use that package instead.

---

### Post by cchester on 2009-08-18
Hello,

Ok I tried what you said and still no go.

1) Make an empty sources.list file, then try to update

Did this then tried to update got same problem as before.

2) Run the command 'sudo dpkg-reconfigure apt'

Did this with no errors and then tried to update got sam problem as before.

3) Download the apt package from here:

   [http://packages.ubuntu.com/hardy/apt](http://packages.ubuntu.com/hardy/apt)

   Then install using 'sudo dpkg -i apt_0.7.9ubuntu17.2_i386'

Did this but got the 64bit version and it said it was already installed. Was going to remove it and reinstall it but said it would remove Ubuntu and so forth so didn't want to take the chance.

So any more thoughts? I tried looking at the man pages and couldn't figure anything out to try to fix this.

Thanks for any more help.

> **warp99 said:**
> Everything looks in order with apt-config and your sources.list file. Try these options in this order:

1) Make an empty sources.list file, then try to update

2) Run the command 'sudo dpkg-reconfigure apt'

3) Download the apt package from here:

   [http://packages.ubuntu.com/hardy/apt](http://packages.ubuntu.com/hardy/apt)

   Then install using 'sudo dpkg -i apt_0.7.9ubuntu17.2_i386'

Try to run the update between each attempt to see if this takes care of the problem.

Edit: If you're using a 64-bit OS then use that package instead.

---

### Post by warp99 on 2009-08-18
Well I'm truly stumped. I've never seen this type of behavior before. At this point it would be best to put in a bug report at launchpad. Here's the link:

[https://bugs.launchpad.net/apt](https://bugs.launchpad.net/apt)

I would explain that apt is trying to obtain a package list from outside your sources.list. Make sure you link back to this thread so the devs have some additional information. I'm sorry I couldn't be more helpful.

---

### Post by cchester on 2009-08-19
Hello,

Thanks for all the help. Not long after my last post I had just decided to reinstall Ubuntu because I got tired of messing with it.

I do thank you for the help and who knows I might be able to figure out which repository caused it to happen if I add whatever messed everything up and it comes up again with the same stuff.

My only other thought was maybe it was something with wget since it was saying get whatever.

Thanks again.

> **warp99 said:**
> Well I'm truly stumped. I've never seen this type of behavior before. At this point it would be best to put in a bug report at launchpad. Here's the link:

[https://bugs.launchpad.net/apt](https://bugs.launchpad.net/apt)

I would explain that apt is trying to obtain a package list from outside your sources.list. Make sure you link back to this thread so the devs have some additional information. I'm sorry I couldn't be more helpful.

---

### Post by martinzul on 2009-10-30
HI,

I see this post is from a good while ago...

I run into the same puzzling problem... at the end i found out that the "guilty" was the ia32-apt-get package, it generated a script "apt-update" placed in /usr/lib/ia32-archive/bin which contained the debian sid repositories information... (attaches as  apt-update.txt -- if i did the attachment procedure properly :) -- )

surely, doing somehitng i can't remember, i got his package "ia32-apt-get" from the wrong place :)

just removing the ia32-apt-getp ackage solved the problem :)

---

