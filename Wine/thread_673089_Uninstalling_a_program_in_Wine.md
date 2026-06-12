---
title: "Uninstalling a program in Wine"
date: 2008-01-20
forum: Wine
---

### Post by teejay17 on 2008-01-20
How do I uninstall IEs 4 Linux from Wine? I'd like to get rid of it completely. 
Once that is done, how do I get rid of Wine completely?

---

### Post by ajgreeny on 2008-01-20
I think if you just uninstall wine with synaptic or ```
sudo apt-get remove wine
``` and then delete the ~/.wine folder that will do it for you.  If anyone knows differently no doubt they will get on here quickly.  I believe ie4linux is installed with a script, so I am not sure if that makes a difference, but as far as I'm aware, wine only installs programs into the ~/.wine folder so  if that is the case, all should be well.

---

### Post by teejay17 on 2008-01-20
> **ajgreeny said:**
> I think if you just uninstall wine with synaptic or ```
sudo apt-get remove wine
``` and then delete the ~/.wine folder that will do it for you.  If anyone knows differently no doubt they will get on here quickly.  I believe ie4linux is installed with a script, so I am not sure if that makes a difference, but as far as I'm aware, wine only installs programs into the ~/.wine folder so  if that is the case, all should be well.
Where do I find this ~/.wine folder? In what folder?

---

### Post by Fred_E _krugar on 2008-01-21
It should be in your home folder. Make sure you check view hidden files. It will be .wine just delete it.

---

### Post by teejay17 on 2008-01-21
> **Fred_E _krugar said:**
> It should be in your home folder. Make sure you check view hidden files. It will be .wine just delete it.
Okay, thanks. 
I guess there aren't any dependent files that I have to worry about?

---

### Post by gruhland on 2008-01-21
The /.wine folder contains all your personal settings and the installed programs. Deleting it means you get rid of all wine stuff. And the synaptic does all things to get rid of wine.

---

### Post by clasificado on 2008-01-22
if you wants to delete even configuration files, use the command "PURGE" in synaptic (or adept).

Clasificado

---

### Post by hikaricore on 2008-01-22
> **clasificado said:**
> if you wants to delete even configuration files, use the command "PURGE" in synaptic (or adept).

Clasificado

That's a dangerously vague way to say it.

```
sudo apt-get remove --purge wine
```

Would be the best way to go about this.

---

### Post by teejay17 on 2008-01-22
> **hikaricore said:**
> That's a dangerously vague way to say it.

```
sudo apt-get remove --purge wine
```Would be the best way to go about this.
Okay, thanks. That seemed to take out the rest of the stuff that was left behind.

---

