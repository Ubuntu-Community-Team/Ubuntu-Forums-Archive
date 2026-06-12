---
title: "Dual Boot"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Origin on 2006-08-15
I'm not sure if this is possible, but my current "dual boot" is definitely one sided. It has the typical window to load Ubuntu, with a choice down there that gives me the option to load other Operating Systems.

The problem is, I have Win XP Home and Win XP Pro x64 both installed (dual boot) before I installed Ubuntu. Is it possible to display all three Operating systems at the same page, and default to Win XP x64 when nothing is chosen for, say 10 seconds?

Thanks.

---

### Post by kuja on 2006-08-15
It should be possible. You would need to edit the file /boot/grub/menu.lst - The file itself has a wealth of information about what you can do to the file.

Near the top of the file there is a line that says
> timeout 3, you can change that to 10 to do the delay. you wanted

Further down, on a commented out line, you'll see something that says > howmany=all by default, meaning that it's showing everything that is listed. Is one (or more of the OS's not in the list right now?

---

### Post by Origin on 2006-08-15
None of the OS's are in the list right now. I need to choose the last option, which redirects me to another dual-boot page of my Windows OS's.

What I mean is, I don't want to have to navigate too many pages before I can start Win XP Pro or Ubuntu. I just want all the options to be on one page.

I can do that by editing boot/grub/menu.lst? If so, thanks!

---

### Post by Origin on 2006-08-15
I just turned off my computer and logged onto Ubuntu. I tried editing the file, but I was alerted that I have no permission. That the "owner" was "root", and I don't have the privileges.

What the heck? I installed the system. How can I not have permission over my own files?

How can I edit the files then?

It doesn't make sense for me not to have permission over files in an OS I installed :(

What's the syntax for me to add an entry to Win XP Pro x64?

---

### Post by kuja on 2006-08-15
You can edit the file by running the editing program with root privileges. To edit the file, run this command in a terminal ```
sudo sudo gedit /boot/grub/menu.lst OR
kdesu kate /boot/grub/menu.lst
```, use gedit if you're a GNOME user, use kate if you're a KDE user.

As per the format for adding the windows XP things, if they aren't already in the list, there should be a sample in the list that looks similar to this:  >  title         Windows 95/98/NT/2000
 root          (hd0,0)
 makeactive
 chainloader   +1

It will likely require some changes! 

Some useful things to know would be, in which order did you install the operating systems, what is your partition setup, and what does your /boot/grub/menu.lst file look like currently.

---

### Post by Origin on 2006-08-15
How do I get root privileges though? Shouldn't I be root, considering I installed the system?

---

### Post by maubp on 2006-08-16
Your account will normally run as a "normal user" but at the command prompt using "sudo" will let you run commands as root (using your normal password).

Its to make you think before doing anything as root - because you could shoot yourself in the foot.

---

### Post by Origin on 2006-08-16
Is it possible to login as root? Maybe username: sudo; password: whatever I have now?

---

### Post by kuja on 2006-08-16
Possible yes, advisable no.

---

### Post by Origin on 2006-08-16
How, may I ask?

If not, how do I give myself root powers when I need it?

---

### Post by kuja on 2006-08-16
> **Origin said:**
> How, may I ask?

If not, how do I give myself root powers when I need it?

Well, you'll usually do this from a terminal.

You gain root privileges by using the command sudo to run the command you want to run as root.

For example, lets say you want to edit a file. Instead of saying something like "gedit *file*", you would use "**sudo** gedit *file*" instead. 

ex:
**sudo** apt-get install frozen-bubble
**sudo** reboot
**sudo** shutdown -h now

---

### Post by Origin on 2006-08-20
Thanks :D Now that I have root permission...

I added Win XP to the menu.lst, but the question is how can I add Windows XP Home and Win XP Pro (x64) both to menu.lst? So I don't need to use Windows' dual-boot page?

I'd like a one-stop page though. Thanks!

---

### Post by kuja on 2006-08-20
Well, I assume they have to be on seperate partitions, right? How do you have your drive partitioned? Also, which entries do you already have in your menu.lst file? (altogether)

---

### Post by Origin on 2006-08-20
Yeah, separate partitions. I have Win XP Home on the first partition (Drive C on Windows), XP Pro x64 on 2nd partition (Drive E -- D is for CD drive).

When I change the windows part to something like:

```
title Windows XP Home
root (hd0,1)
makeactive
chainloader +1

title Windows XP pro
root (hd0,2)
makeactive
chainloader +1
```

Some incompatibility error occurs. I think I read that GRUB can't directly handle windows bootups?

How can I do it then? Thanks

---

### Post by Origin on 2006-08-26
Anyone? :(

---

### Post by Lonthong on 2006-08-27
Your XP64 boot files probably resides in home XP.
If you hide yr home XP partition before installing XP64 than you will have 2 totally independent OS from each other. In this case surely grub will be able to boot any of them with no problem.
Have a look at this short [how-to]("http://www.vectorlinux.com/forum2/index.php?topic=15.0") for more detail

---

