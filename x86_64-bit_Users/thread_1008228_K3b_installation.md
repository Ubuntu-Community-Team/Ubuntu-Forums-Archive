---
title: "K3b installation"
date: 2008-12-11
forum: x86 64-bit Users
---

### Post by Gins on 2008-12-11
I installed Ubuntu 8.04 LTS Desktop Edition.

It works fine. I can go the Internet. So I am pleased with Ubuntu.

By default it has not installed CD/DVD burning program K3b.

So I tried to install using the following command.

sudo apt-get install k3b.

I got the following error message.

Could not find pacakage k3b.

[B]Why is this?

Please help me.[/B]

-----------------------------------------------------------------
I am new to Ubuntu. I have been using Mandriva and Open SuSE for a few years. I have never used Ubuntu.

[I]I try in vain the basic installation method by downloading it from the K3b website. It was a tar.gz file.

The installation was a hell. I expected problems. It complains about a missing C compiler in the middle of the process.[/I]

---

### Post by howefield on 2008-12-11
Did you type k3b or K3b, it is case sensitive.

You use both in your posting.

---

### Post by albinootje on 2008-12-11
Can you show us your /etc/apt/sources.list ?

You can also find the package here,
and put it manually in /var/cache/apt/archives/

[http://packages.ubuntu.com/search?keywords=k3b](http://packages.ubuntu.com/search?keywords=k3b)
But you will need more packages.

---

### Post by Gins on 2008-12-11
Thanks howefield for the reply.

I just tried again both 'k3b' and 'K3b'.

I got the same old eror message.

----------------------------
Reading package lists...  Done
Building dependency tree
Reading state information... Done
**E: Couldn't find package k3b**
..............................

Reading package lists...  Done
Building dependency tree
Reading state information... Done
**E: Couldn't find package K3b**


[COLOR="Red"]What is the problem? [/COLOR]
The program works fine. I mean Ubuntu works fine.

 *I badly need to burn a program. I know the way k3b works. I have used it other distros for a severl years.*

-----------------------------------------------------
albinootje 
There are many programs on that list.

I don't what to download or rather what to do.

I am familiar with k3b because I have been using it for many years.

----------------------------------------------------------------------------

**I know how to logon as a root user in Linux as I did it for about 10 years.**

I am used to write the following:

su root

Then it asks the password.

Ubuntu behaves strangely.

It says 'Authentication failure.

Why is this?

I wrote the command 'sudo apt-get install k3b' and pressed enter.

It asked the password.


I wrote the password and pressd enter.

**It accepted the password and elicited the above error message.**

[COLOR="Red"]Ubuntu behaves strangely.[/COLOR]

---

### Post by stchman on 2008-12-11
Enable all universe, multiverse, and restricted repositories.  Type the following in a terminal:

```
sudo apt-get -y install k3b libk3b2-extracodecs
```

The extracodecs package allows you to burn .mp3 files as an audio CD.

---

### Post by Gins on 2008-12-11
I thank everybody for the replies.


I struggled with the following command and óther similar ones for about 6 hours.

**sudo apt-get install k3b**


It worked fine, nearly 10 minutes ago, and the program k3b was installed.

[SIZE="4"][COLOR="Red"]Who knows the reason for these strange things we experience in the domain of IT from time to time.
[/COLOR][/SIZE]

---

### Post by steveneddy on 2008-12-12
Great hints, guys.

Just posting to find it tonight to add it to the archives.

Maybe we could mark this as solved?

---

### Post by philinux on 2008-12-12
There are no capitalised apps in synaptic, all are lower case.

---

### Post by DeMus on 2008-12-13
> **Gins said:**
> I installed Ubuntu 8.04 LTS Desktop Edition.

It works fine. I can go the Internet. So I am pleased with Ubuntu.

By default it has not installed CD/DVD burning program K3b.

So I tried to install using the following command.

sudo apt-get install k3b.

I got the following error message.

Could not find pacakage k3b.

[B]Why is this?

Please help me.[/B]

-----------------------------------------------------------------
I am new to Ubuntu. I have been using Mandriva and Open SuSE for a few years. I have never used Ubuntu.

[I]I try in vain the basic installation method by downloading it from the K3b website. It was a tar.gz file.

The installation was a hell. I expected problems. It complains about a missing C compiler in the middle of the process.[/I]

Next time you want to install something use Synaptic first: System - Administration - Synaptic package manager.
There are a lot of programs available there which you can install with a few mouse clicks. Use search and type the name (or part of the name) in the search field.

I know I will get the whole Linux-Unix society on top of me because I do not use the command line, but hey it's the 21st century. We are long past that.

---

