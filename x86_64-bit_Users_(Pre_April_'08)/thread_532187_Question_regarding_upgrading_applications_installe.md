---
title: "Question regarding upgrading applications installed using --force"
date: 2007-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by willyram on 2007-08-22
Hi fellow 64er's!

I installed Feisty on my new AMD64 machine and it just flies. For me it's a solid and very polished distro. I am amazed at how fast things like firefox or openoffice start and work. And beryl/fusion makes it a nice and pleasing experience.

I have one question though. I had to install some applications by using the dpkg with --force parameter, for example skype (as I have friends with only skype on their machines). And then I used getlibs tool to get additional libraries. Then I followed the guidelines on this forum for java and flash (honestly don't recall if they used force).

I was wondering how do you manage the upgrades on this forced applications, for instance the security updates (mainly java or flash). 

I am no linux guru, but I tend to think that if the package does not come from a repository, then we have no way the update manager would get updates. And if the package came from a repository, would the updates be notified? Is it actually possible to have packages on a repo that have to be installed with force??

Thank you so much and please excuse me if this as already been answered, honestly I did a search and did not find this documented the way I asked.

Thanks in advance, Willie.

---

### Post by Kilz on 2007-08-22
> **willyram said:**
> Hi fellow 64er's!

I installed Feisty on my new AMD64 machine and it just flies. For me it's a solid and very polished distro. I am amazed at how fast things like firefox or openoffice start and work. And beryl/fusion makes it a nice and pleasing experience.

I have one question though. I had to install some applications by using the dpkg with --force parameter, for example skype (as I have friends with only skype on their machines). And then I used getlibs tool to get additional libraries. Then I followed the guidelines on this forum for java and flash (honestly don't recall if they used force).

I was wondering how do you manage the upgrades on this forced applications, for instance the security updates (mainly java or flash). 

I am no linux guru, but I tend to think that if the package does not come from a repository, then we have no way the update manager would get updates. And if the package came from a repository, would the updates be notified? Is it actually possible to have packages on a repo that have to be installed with force??

Thank you so much and please excuse me if this as already been answered, honestly I did a search and did not find this documented the way I asked.

Thanks in advance, Willie.

Forced applications will not get updates, you will have to keep an eye on it. But if like a lot of people you wipe and reinstall when the new Ubuntu is released, yur software is never more than 6 months old.
Java isnt forced, there is a 32bit package in the 64bit repo's. Flash isnt in the repositories, but downloaded from macromedia. When a new version of it is released  in the past there has been a post on the forums about it.

---

