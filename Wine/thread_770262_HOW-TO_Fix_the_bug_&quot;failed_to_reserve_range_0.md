---
title: "HOW-TO: Fix the bug &quot;failed to reserve range 00000000-00010000&quot; in Hardy (8.04)"
date: 2008-04-27
forum: Wine
---

### Post by andrebrait on 2008-04-27
Hmm... so, you were running winecfg and looke at this:

> preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000


Or this

> preloader: Warning: failed to reserve range 00000000-60000000


And you never saw this bug before? :confused:

Well... here's the solution... :)

Open your console and type:

```
sudo sysctl -w vm.mmap_min_addr=0
```

But it will only fix the problem until the next reboot, so, to fix it permanently, edit sysctl using any text editor.

For Ubuntu
```
sudo gedit /etc/sysctl.conf
```

For Kubuntu
```
sudo kedit /etc/sysctl.conf
```
There have been a few years since I used KDE for the last time... don't know if Kedit is still the default text editor.

For Xubuntu
```
sudo nano /etc/sysctl.conf
```

Look for this line:
> vm.mmap_min_addr = 65536

Now change it to:
```
vm.mmap_min_addr = 0
```

That's it :lolflag:

Sources:
[http://wiki.winehq.org/PreloaderPageZeroProblem]("http://wiki.winehq.org/PreloaderPageZeroProblem")
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/114025]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/114025")

---

### Post by Fate Reconciled on 2008-05-01
Thanks alot! This bug has been puzzling me for the last few days.

---

### Post by elvinatom on 2008-05-01
Really, thanks!
(And a bump for others with the same trouble)

---

### Post by oedipuss on 2008-05-02
Wasn't this a feature of hardy, related to security? Besides, I've seen this exact warning in several wine apps, but none of them refused to run because of it.

---

### Post by cherva on 2008-05-04
What is this error anyway ?

---

### Post by evozniak on 2008-05-04
this is not a error is a warning, application runs fine over this errors.

---

### Post by oedipuss on 2008-05-04
From 'New features in 8.04'
> Memory Protection
[..]
The lower 64K of system memory is no longer addressable by default. This will help defend against malicious code that attempts to leverage kernel bugs into security vulnerabilities. 
[..]

I think that's what this is about.  Perhaps this restriction shouldn't be removed without a second thought, unless you're absolutely sure the application you're trying to run is failing because of this.
I don't know how useful something like that might be in a real world scenario (I've never have had any problems with gutsy or any previous release), anyone have any info on that?

---

### Post by Charlie708 on 2008-05-04
I saw that too, and was puzzled by it.  So far, Guitar Pro 5 and ePSXe both worked fine with the warning, but I want to see how they work without it, and how the rest of the system is doing without it.

---

### Post by joris1977 on 2011-06-11
> **evozniak said:**
> this is not a error is a warning, application runs fine over this errors.

Not sure why, but "an ancient" application I use wouldn't run because of this error. This was not with wine but with codeweavers 6.2.0 (2007 version) in lucid lynx.

Oh yeah in Lucid the file you need to change to make this change permanent is: 

/etc/sysctl.d/10-zeropage.conf

---

