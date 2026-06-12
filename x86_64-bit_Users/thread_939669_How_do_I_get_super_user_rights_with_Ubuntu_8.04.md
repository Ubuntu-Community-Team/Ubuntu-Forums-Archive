---
title: "How do I get super user rights with Ubuntu 8.04??"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by khelben1979 on 2008-10-06
I have a serious problem.

I need root rights in order to install packages and run different scripts, but I just get permission denied all the time.

This Ubuntu system have only one user which was defined at the base install of Ubuntu. This user should be able to do everything which a super user adminstrator should be able to do, but... I have problems with this.

Any suggestions?

(I will probably format this harddrive at a later time and start all over with another Linux distribution, eventually, but at the present I'm giving Ubuntu a chance of showing what it can do.)

---

### Post by vanadium on 2008-10-06
In Ubuntu, no root account is enabled by default. It is recommended to use the sudo command to run selected commands with root privileges. Some info on this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

That said, you still can enable the root account if you prefer that approach: this is linux after all. How is easily found on the net.

---

### Post by khelben1979 on 2008-10-06
Okay. Can you recommend a graphical interface where I can setup accounts in Ubuntu 8.0.4? I'm hoping that I don't need to reinstall the whole Ubuntu distribution just to get an root account.

The way I see it, having a root account will solve all my problems which I currently am experiencing.

---

### Post by snowpine on 2008-10-06
> **khelben1979 said:**
> Okay. Can you recommend a graphical interface where I can setup accounts in Ubuntu 8.0.4? I'm hoping that I don't need to reinstall the whole Ubuntu distribution just to get an root account.

The way I see it, having a root account will solve all my problems which I currently am experiencing.

There is a very simple terminal command that will set the password for root so that you can log in as root. We are not allowed to tell you this command because it is not officially recommended by the Ubuntu project (forum rules). You can find it easily on other websites with a search.

My recommendation is to use the sudo command in front of anything you need to do as root. If instructions say "Log in as root and..." it just means they were written for a different Linux distro, and you can substitute sudo (or gksu for graphical apps) to accomplish the same thing. Enabling root login may "solve all your problems" but that doesn't mean it won't create new problems. ;)

---

### Post by Yellow Pasque on 2008-10-06
Enabling a root account is not recommended as it's a security risk, especially if you choose a weak password. If a program needs root access, run it with 'sudo' (for command-line) or 'gksudo' (for GUI programs).

EDIT: (Beaten to it by snowpine)

---

### Post by SeanHodges on 2008-10-06
> **khelben1979 said:**
> Okay. Can you recommend a graphical interface where I can setup accounts in Ubuntu 8.0.4?

Top panel: System -> Administration -> Users and Groups

> **khelben1979 said:**
> The way I see it, having a root account will solve all my problems which I currently am experiencing.

Tell us more about these problems you are having...

---

### Post by Kilz on 2008-10-06
I have a suggestion. [Dont double post issues. ]("http://ubuntuforums.org/showthread.php?t=939619")

---

### Post by vanadium on 2008-10-06
If you know well what you are doing, "sudo -i" will give you a terminal with root privileges. Not the same as a root account ("su" won't work by default) but I cannot see how the Ubuntu approach would be more limiting than the traditional approach.

---

### Post by Kilz on 2008-10-06
> **khelben1979 said:**
> Okay. Can you recommend a graphical interface where I can setup accounts in Ubuntu 8.0.4? I'm hoping that I don't need to reinstall the whole Ubuntu distribution just to get an root account.

The way I see it, having a root account will solve all my problems which I currently am experiencing.

```
gksudo nautilus
```

---

