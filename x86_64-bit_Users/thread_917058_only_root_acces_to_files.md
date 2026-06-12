---
title: "only root acces to files"
date: 2008-09-11
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2008-09-11
Hi guys,

I have some maps & files on my computer that only a root is allowed to change.

I started nautilus as a root and tried to change the right (also on sub folders and files) but without success

So the question is:
how can 'normal' users get change access to files and folders...?


Cheerz

Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2008-09-11
Found it. Google is my friend!!


sudo chown -R username:username /home/username/specificmap

I am so good :-)\

To bad I cant thank myself:lolflag:

---

### Post by bford16 on 2008-09-11
I gotta chime in on this: sometimes Ubuntu just works better when you use the command line!  I have never had success using Nautilus to change permissions.  It just doesn't work.

---

### Post by Nisuspi on 2008-09-12
I have a question along similar lines - almost every application I've installed (Quasar Accounting, VMWare and others) since switching to Ubuntu a couple of weeks ago runs into user restriction errors which I'm sure shouldn't be there.

Basically, in their installed state they're unusable because the folders they need have root access only. Surely it shouldn't be the case that the first thing you have to do after loading a new application is go through the file system painstakingly unlocking every folder it needs? 

Am I doing something wrong? I can't see anyway of installing these apps without using sudo or root, but is that why they're only being associated with that user?

---

### Post by Bloemetjesgordijn on 2008-09-12
@ Nisuspi
I only got this problem with Hellanzb. 

But I presume this is due the fact that I need to start hellanzb in the command line as root "Sudo hellanzb"

I should post this as a bug @hellanzb

Maybe if I have time

@bford 16
True, changing rights with "sudo nautilus" is without success. gksudo nautilus has more success though (not enough but still)BTW nautilus should be started with gksudo !!!!


Cheerz

Bloemetjesgordijn

---

### Post by Thelasko on 2008-09-12
> **bford16 said:**
> I gotta chime in on this: sometimes Ubuntu just works better when you use the command line!  I have never had success using Nautilus to change permissions.  It just doesn't work.

It works fine for me.

---

### Post by bford16 on 2008-09-12
> **Nisuspi said:**
> I have a question along similar lines - almost every application I've installed (Quasar Accounting, VMWare and others) since switching to Ubuntu a couple of weeks ago runs into user restriction errors which I'm sure shouldn't be there.

Basically, in their installed state they're unusable because the folders they need have root access only. Surely it shouldn't be the case that the first thing you have to do after loading a new application is go through the file system painstakingly unlocking every folder it needs? 

Am I doing something wrong? I can't see anyway of installing these apps without using sudo or root, but is that why they're only being associated with that user?

What are the steps you typically use to install an application?

---

### Post by bford16 on 2008-09-12
> **Thelasko said:**
> It works fine for me.
Maybe I wasn't using 'gksudo' properly. All I know is that every time I have tried to use Nautilus to manage permissions and file ownership, I have had trouble. On the other hand, Nautilus-as-root made configuring Avant Window Manager much easier. Go figure.

---

### Post by Nisuspi on 2008-09-13
Doesn't seem to matter. Either using sudo, root or just double clicking on a deb file - all come up with the same problem.

It's not the end of the world, but would put me off recommending Ubuntu to - say - my father...

---

### Post by Thelasko on 2008-09-15
> **bford16 said:**
> Maybe I wasn't using 'gksudo' properly. All I know is that every time I have tried to use Nautilus to manage permissions and file ownership, I have had trouble. On the other hand, Nautilus-as-root made configuring Avant Window Manager much easier. Go figure.

All I do is open the terminal and enter:
```
sudo nautilus
```
and it works fine.

I also have a g-script installed so I don't even have to open the terminal anymore.  I think I remember one time when the permissions didn't change over properly.  I think I determined it was due to hitting cancel instead of ok.

---

### Post by dullard on 2008-09-15
For me...

```
sudo thunar
```

...always does the trick. For some reason Nautilus has failed to change file permissions occasionally but Thunar has worked every time.

---

### Post by Thelasko on 2008-09-15
> **dullard said:**
> For me...

```
sudo thunar
```

...always does the trick. For some reason Nautilus has failed to change file permissions occasionally but Thunar has worked every time.

Do you use Xubuntu?

---

