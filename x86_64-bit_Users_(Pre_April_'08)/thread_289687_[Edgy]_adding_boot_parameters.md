---
title: "[Edgy] adding boot parameters"
date: 2006-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by velozoom on 2006-10-31
Have an AMD64 system running Edgy.  I need to add the -noapic parameter for the system to boot.  In Dapper, I was able to explicitly add the parameters to /boot/grub/menu.lst and that worked fine.  In Edgy, however, adding the parameters to the defoptions line does not help.  I'm a noob, so if I'm asking a stupid question I apologize but I would really like to sort this annoying issue.  

Thanks

---

### Post by fabertawe on 2006-10-31
Why don't you add it to the kernel entry yourself?

Paul

---

### Post by velozoom on 2006-10-31
>>Why don't you add it to the kernel entry yourself?

hehehehehe....simple- because I am a dummy and didn't know I could add to that line without messing things up.  

Thanks, that worked without a problem.  Appreciate it.

---

### Post by fabertawe on 2006-10-31
It's probably good that you're cautious ;) Because things are fixable in Linux I find it too tempting to fiddle with things I know little about... this still depends on me relying on the knowledge of the 'fixers' but hey :rolleyes: 

Paul

---

### Post by velozoom on 2006-10-31
Cautious, yes, very much so.  Despite my Linux ignorance, I am a Systems/Network Admin in a Windoze/Active Directory environment.  If it does nothing else, Winblows teaches you caution.  A downed server or two is all one needs for that lesson.......

---

### Post by Roobert on 2006-11-01
> **fabertawe said:**
> Why don't you add it to the kernel entry yourself?

Paul

Just for the benefit of those who might not know how to do this, could you list the necessary commands here? ;) 

Thanks!

---

### Post by fabertawe on 2006-11-02
> **Roobert said:**
> Just for the benefit of those who might not know how to do this, could you list the necessary commands here? ;) 

Thanks!

Of course :rolleyes: From the terminal...
```
sudo gedit /boot/grub/menu.lst
```
Or use the editor of your choice in place of gedit.

Alter the kernel entry you're using (usually the first after 'End Default Options'). Here is mine as an example (I removed 'quiet')...
```
## ## End Default Options ##

title      Ubuntu, kernel 2.6.17-10-generic
root       (hd0,1)
**kernel  /boot/vmlinuz-2.6.17-10-generic root=UUID=7ab3c71b-9393-4dcb-bab5-af8439973167 ro splash**
initrd     /boot/initrd.img-2.6.17-10-generic
savedefault
boot
```

Paul

---

