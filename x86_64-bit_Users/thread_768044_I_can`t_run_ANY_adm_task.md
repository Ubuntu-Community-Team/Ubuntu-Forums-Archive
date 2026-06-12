---
title: "I can`t run ANY adm task"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by FAO56 on 2008-04-26
I can`t run any adm task. I can not add ou remove any program, run Synaptic Manager, ...
They look like that they are going to run (a place holder shows in the botton panel), but after a time they go away. I upgraded my system to 8.04 using the alternate CD (amd64).

---

### Post by GeekGirl1 on 2008-04-26
Those ADM (root privilege) tasks open a dialog box to ask for the root password. Are you seeing that dialog box?

Can you open a terminal and run "su"? That's the root account. Do you know the root password? If not, that's a good place to start.

---

### Post by FAO56 on 2008-04-26
> **GeekGirl1 said:**
> Those ADM (root privilege) tasks open a dialog box to ask for the root password. Are you seeing that dialog box?

Can you open a terminal and run "su"? That's the root account. Do you know the root password? If not, that's a good place to start.

No, those ADM tasks does not open a dialog box asking for the root password. But some tasks, like configure network, asked for the password and worked well.

If I try to run "su", it ask for the root password, if I enter my user passaword (like I did when configuring de network), it says that is a invalid password. I suppose I don't know the root password, I don't know how to discover it. By the way, I do not remenber the ever be asked for a root password. I am not familiar with the command line. I only use it in occassions where someone tell all the necessary step.

---

### Post by FAO56 on 2008-04-27
Somebody with any idea how to solve these?

---

### Post by Patsoe on 2008-04-27
On a standard Ubuntu setup, the root password is disabled, so you shouldn't be able to su anything.

You should be able to sudo though, with your user account password. Try "sudo echo helloworld" for a harmless test.

---

### Post by FAO56 on 2008-04-27
> **Patsoe said:**
> On a standard Ubuntu setup, the root password is disabled, so you shouldn't be able to su anything.

You should be able to sudo though, with your user account password. Try "sudo echo helloworld" for a harmless test.

The result was this:

sudo: unable to resolve host aablinux01

I have no idea what this means.

---

### Post by Patsoe on 2008-04-27
Hmmm, I don't know... I assume aablinux01 is the name of your machine?

A couple of tips: send a message to a forum moderator to ask if this can be moved to the security forum - or at least out of the amd64 forum, because I think it's not really related. There you'll get more readers who know. (Alternatively, just start a new thread there).

I think it may help to post the output of "cat /etc/hosts", "cat /etc/hostname", "ifconfig", "cat /etc/group".

Edit: fix probably in this thread: [http://ubuntuforums.org/showthread.php?t=770801](http://ubuntuforums.org/showthread.php?t=770801)

---

### Post by FAO56 on 2008-04-28
The problem was solved. Thanks.
By the way, there is a way to mark that this question was solved?

---

### Post by Patsoe on 2008-04-28
It used to be possible to mark a thread solved, but I think the forum admins are reworking the part that does that.

So did you solve in the way the other thread said? ([http://ubuntuforums.org/showthread.php?t=770801](http://ubuntuforums.org/showthread.php?t=770801))
I think this is a bug in the upgrade-manager, so please consider opening a bug report on launchpad.

---

