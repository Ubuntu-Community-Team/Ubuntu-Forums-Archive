---
title: "[SOLVED] How do I reset all WINE settings to their default?"
date: 2008-05-02
forum: Wine
---

### Post by Rytron on 2008-05-02
Hi,
I once had WINE working (albeit slowly). Now nothing will work for me. I may have inadvertently changed settings that I shouldn't have.

How do I reset all WINE settings to their default?

Thank you.

---

### Post by cogadh on 2008-05-02
Delete your ~/.wine directory and create a new one. Of course, you'll also have to reinstall any software you have already installed.

---

### Post by Rytron on 2008-05-03
Problem solved.
I re-installed Wine from synaptic.

Then I got this from a web page:
[I][B]
Running Wine on recent versions of Linux (in particular Ubuntu 8.04, Hardy Heron) may generate errors or warnings such as preloader: Warning: failed to reserve range 00000000-60000000 err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report and may refuse to run Wine applications, especially ones that use Win16 or DOS calls. For instance, Microsoft Word 2000 will crash after a few seconds.

The workaround is to give the command:

```
$ sudo sysctl -w vm.mmap_min_addr=0

```
This fixes the problem until the next time you reboot. (It also reduces security slightly.)

To avoid having to give that same command every time you reboot, also edit the file /etc/sysctl.conf, e.g. with the command

```
$ sudo gedit /etc/sysctl.conf

```
and change the line that reads:

vm.mmap_min_addr = 65536

to:

vm.mmap_min_addr = 0

That will apply the workaround for you when the system starts.
[/B][/I]
Now it may have been a matter of running the above code rather than re-installing Wine, but anyway Wine is now purring like a kitten.

Cheers.

---

### Post by sweldon on 2008-05-03
rm -rf ~/.wine
this command in terminal mode should reset wine to defualt

---

### Post by Rytron on 2008-05-03
Today Wine was running very fast.

Now this evening after my computer was restarted it is incredibly slow again.

I have just tried 

```
rm -rf ~/.wine
```

Wine is still at snail pace. This is so frustrating!

:confused:

---

### Post by buntunub on 2008-05-08
> **Rytron said:**
> Today Wine was running very fast.

Now this evening after my computer was restarted it is incredibly slow again.

I have just tried 

```
rm -rf ~/.wine
```

Wine is still at snail pace. This is so frustrating!

:confused:

Ok, so you deleted the wine dir. No wonder wine is not working for you?   :confused:

Did you run $winecfg from terminal to set up a new local wine directory? Give [PlayOnLinux]("http://www.playonlinux.com/") a shot. That app has been a godsend for me! With it you can very easily work with wine. It works like Crossover Games, but its GPL and free, and IMO, better.

---

### Post by Rytron on 2008-05-08
> **buntunub said:**
> Ok, so you deleted the wine dir. No wonder wine is not working for you?   :confused:

Did you run $winecfg from terminal to set up a new local wine directory? Give [PlayOnLinux]("http://www.playonlinux.com/") a shot. That app has been a godsend for me! With it you can very easily work with wine. It works like Crossover Games, but its GPL and free, and IMO, better.

Hi,
Wine is now working. Funny thing is - if I am online, wine wont work; when I am off line it works.

---

