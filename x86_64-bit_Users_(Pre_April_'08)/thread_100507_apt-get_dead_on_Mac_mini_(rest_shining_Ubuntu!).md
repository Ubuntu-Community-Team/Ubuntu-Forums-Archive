---
title: "apt-get dead on Mac mini (rest shining Ubuntu!)"
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by etitor on 2005-12-07
Friends, just brought home a Mac mini. Examined MacOSX for a couple of minutes. Decided to substitute Ubuntu Linux.

Installation wiped out the disk (I have the restore CD anyway). It installed really smoothly.

I have sound. I have a decent 2D screen. I have DSL internet OK.

But apt-get and Synaptic are dead!

I click on the "update" red circle on the upper right part of the screen. Nothing happens.

I start a terminal, type

> sudo apt-get update

and nothing happens (just back to the blinking prompt).

So here am I, posting from a Mac mini, but unable to update anything. Can anyone give any advice?

---

### Post by teaker1s on 2005-12-07
sudo synaptic
see what it comes back with -if you have internet access but synaptic can't refresh sources it's dns or repositories
apt-get fix listed under synaptic help 
under limitations

---

### Post by etitor on 2005-12-07
[QUOTE=teaker1s]sudo synaptic
see what it comes back with -if you have internet access but synaptic can't refresh sources it's dns or repositories
apt-get fix listed under synaptic help 
under limitations[/QUOTE]

Ouch! Neither sudo synaptic nor sudo gedit nor sudo anything... Everything preceded by sudo just does nothing.

Maybe it is a "sudoers" thing... I have only one user on this PPC.

So I just run "su". I got a root terminal. Now gedit /etc/sudoers shows me just one user, root. Is this correct?

---

### Post by teaker1s on 2005-12-07
there has been permission problems,can you create another account as a system administrator or is that dead too?

---

### Post by etitor on 2005-12-07
[QUOTE=teaker1s]there has been permission problems,can you create another account as a system administrator or is that dead too?[/QUOTE]
 Thank you teacker. I click on System, then on Administration, then on Users. Nothing happens. I can get root using "su".

---

### Post by teaker1s on 2005-12-07
without using sudo to become root and change password the root terminal and gui login disabled. I would check the install disk md5 checksum as it could be corrupted also did ubuntu partition your drive or did you just install in exsisting partitions as mac is related to freebsd and you may have not completely removed mac os(be aware some rescue discs just unpack os from hd partition so deleting partition could stop recovery disk working)

---

### Post by etitor on 2005-12-07
[QUOTE=teaker1s]without using sudo to become root and change password the root terminal and gui login disabled. I would check the install disk md5 checksum as it could be corrupted also did ubuntu partition your drive or did you just install in exsisting partitions as mac is related to freebsd and you may have not completely removed mac os(be aware some rescue discs just unpack os from hd partition so deleting partition could stop recovery disk working)[/QUOTE]

1. I wiped the disk out. No traces of its past ;)

2. md5 checksum: correct.

3. "without using sudo to become root and change password the root terminal and gui login disabled": I am not getting it. Can you please explain. Thanks thanks thanks.

---

### Post by etitor on 2005-12-07
So I just launched a terminal and typed "su" and then the root password.

I got a # prompt.

I typed "synaptic". I am right now updating everything.

Problem seems to be related to the normal user not being able to gain root privileges using sudo.

---

### Post by teaker1s on 2005-12-07
for safety we use sudo or gksudo to assume root privilage's 
ubuntu disables root account and unless you can use sudo you don't have privilages to enable root login-your option will either be use a live distro to edit sudoers or reinstall unless someone has a suggestion I don't know

---

### Post by teaker1s on 2005-12-07
okay if you can su then just create a new account with admin privilages

---

### Post by etitor on 2005-12-07
But now I *can* edit sudoers!

I just type "su" and then the root password.

Then I launch "gedit /etc/sudoers" and I can edit the file!

---

### Post by teaker1s on 2005-12-07
weird, there has been some strange gnome related problems look here and add to the bug report
[https://launchpad.net/distros/ubuntu/+bug/4738](https://launchpad.net/distros/ubuntu/+bug/4738)

---

### Post by etitor on 2005-12-08
[http://ubuntuforums.org/showthread.php?t=76305](http://ubuntuforums.org/showthread.php?t=76305)

Here it is! I also installed as expert and somehow this kind of installation on PPC acts strangely on users and permissions.

I will try now the automatic install and will let you know.

---

### Post by etitor on 2005-12-08
I reinstalled from Ubuntu 5.10 PPC. This time I chose just "install" instead of "expert". Voilà! Mac mini works with Breezy! Internet, sound, synaptic.

---

### Post by ssam on 2005-12-08
well done for getting it sorted. odd bug. we better get that sorted for dapper. did you file a bug?

also the recommended way to edit the sudoers file is with visudo. it writes to /etc/sudoers.tmp, then check the syntax before saving it. it can stop you getting in a mess. (i have done this, messed up the sudoer file, then sudo refused to work and i had no root password. i had to boot a live cd and fix the file.)

---

### Post by etitor on 2005-12-09
[QUOTE=ssam]well done for getting it sorted. odd bug. we better get that sorted for dapper. did you file a bug?[/QUOTE]
I haven't. Can you point me to some HOWTO file a bug? I will do it.

---

### Post by ssam on 2005-12-09
bugs should be filed at [http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)

do a search first to check the bug does not already exist. if you can't find it click the new button. and fill in the form.

try to be clear and detailed. if the developers need more info they'll ask for it.

---

