---
title: "Synaptic update manager will no longer update properly"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by espressobeanies on 2008-07-21
The problem is that every time I go to update my drivers, a box will appear that says "Starting Admin..." after I ask the Update Manager. It will not freeze the screen and ask me to put in my password anymore. It was a problem that I was able to correct on the next boot, but now it seems more permanent. What do I do?

BTW: This will only happen with the update manager. I can unlock functions, access sudo through the terminal, and perform other password required functions without a problem.

AMD Athlon +3200 Socket 754,
1 GB DDR RAM
Plenty HDD space
GPU set to Nvidia Propreitary Drivers

---

### Post by drs305 on 2008-07-21
You may have a corrupted /etc/hosts file.

If you are an experienced user, make sure your hostname hasn't become corrupted in the hosts file. Sometimes an app will append something extra to the hostname (e.g. mycomputer.somethingelse)
Check your hosts file and correct it if the hostname is not correct:
```
cat /etc/hosts
```

If you are less experienced:
Look up your hostname (computer name):
```
hostname
```

Backup and inspect your current hosts file.
```

sudo cp /etc/hosts /etc/hosts.bak1
gksu gedit /etc/hosts

```

There should be a line that looks like the one below. The computer name should match the results of the *hostname* command, with no additions such as .network, .web, .local, etc. :
```
127.0.1.1  **your-computer-name**
```

If the line doesn't exist, add it. If the computer name has additional information after a period, remove the period and everything thereafter.

---

### Post by acrousey on 2008-08-06
It seems as if I am experiencing much of the same problem. I can still download and get updates through the terminal, but every time I try to install new updates, the Update Manager freezes. It opens just fine and lets me see the new updates; I just can't download them. And, I tried following your steps to fix this problem. I do not think that my hostname has been changed, but I haven't really been able to fix it either. Every time I enter this line of code
```
sudo cp /etc/hosts /etc/hosts.bak1
```
I get a response that says
```
sudo: unable to resolve host ubuntu
```

I am pretty new in the world of Ubuntu and Linux, so I am not too experienced at figuring out what is wrong with this on my own. Any help would be great help to me. Thanks guys!

---

### Post by drs305 on 2008-08-06
> **acrousey said:**
> It seems as if I am experiencing much of the same problem. I can still download and get updates through the terminal, but every time I try to install new updates, the Update Manager freezes. It opens just fine and lets me see the new updates; I just can't download them. And, I tried following your steps to fix this problem. I do not think that my hostname has been changed, but I haven't really been able to fix it either. 

I get a response that says
```
sudo: unable to resolve host ubuntu
```


Okay, we can troubleshoot this problem a bit. Can you run normal commands with sudo? For instance, can you run "sudo blkid" without generating any error messages? It should ask for your password and then produce a list of your devices.

You said you don't think your hosts file changed. Sometimes programs change or append your computer's name in the /etc/hosts file. Is your computer's name *ubuntu*? To check the hosts file, run this command:
```
cat /etc/hosts | grep 127
```
You should see something like this as a result:
```

~: cat /etc/hosts | grep '127'
**127.0.0.1** localhost
**127.0.1.1** ***yourcomputersname***

```
It should not have anything attached, like *yourcomputersname.**net***

You should also check /etc/hostname, which should return the name of your computer - again without attachments:
```
cat /etc/hostname
```

If you aren't sure if the results are correct please post the results and we can fix this for you.

---

