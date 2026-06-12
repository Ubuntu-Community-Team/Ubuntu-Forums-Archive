---
title: "E:couldnt find package ....."
date: 2008-06-30
forum: x86 64-bit Users
---

### Post by vajjala1986 on 2008-06-30
Hi, 

I have installed Kubuntu 8.04 hardy heron recently. 
After the install, I wanted to install some softs like amarok etc.

But no matter what I try , its saying:

# sudo apt-get install build-essential
packages...
building tree....
...blah blah.......
E: couldnt find package build-essential

Not only build-essential, no matter what i want to install the error is same
I believe, it is something to do with sources.list which may not have all the sources.
Any suggestions , what I need to do. Anywhere I can download this file for kubuntu 8.04 hardy

---

### Post by Zorael on 2008-06-30
Deleting/renaming your /etc/apt/sources.list file and have Adept Manager regenerate a new one might work.

```
$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
$ kdesu software-properties-kde &
```

---

### Post by vajjala1986 on 2008-07-02
Thanks for the response.

But it turned out that the problem is with the pppoe connection I am having. I do not know how to configure pppoe on ubuntu.
There is a pppoe tab in network manager.But its not helping much. 

Is there any other pppoe connection manager available for ubuntu? 
PPPOE is the only thing, thats not allowing me to switch to ubuntu.
As I cannot access internet, I cannot update graphics drivers, sound drivers, could not install anything. 

Google did not help much in this case.

---

