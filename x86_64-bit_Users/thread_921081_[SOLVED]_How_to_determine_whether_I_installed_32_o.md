---
title: "[SOLVED] How to determine whether I installed 32 or 64 bit ubuntu?"
date: 2008-09-15
forum: x86 64-bit Users
---

### Post by jeffbmartinez on 2008-09-15
I installed Ubuntu 7.xx on my machine a while back and I recently upgraded to 8.04. I have a core 2 duo so I know it can handle the x64 version. But frankly I just don't remember what I installed. Furthermore I lost the disc which I installed it from.

I just wanna know if I have the 32 or 64 bit version of ubuntu installed on my machine.

While I'm at it, *if* I have a 32 bit install, can I use software compiled for a 64 bit install? And if so would there be any point to it?

Some quick info about my machine:

martinez@sour-lenovo:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy
martinez@sour-lenovo:~$ uname -a
Linux sour-lenovo 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Does any of this give a hint as to 32 bit vs 64 bit? Or where can I find this info? Thanks all...

 - jeff

---

### Post by tuxxy on 2008-09-15
You are running 32-bit

---

### Post by tuxxy on 2008-09-15
> While I'm at it, *if* I have a 32 bit install, can I use software compiled for a 64 bit install? And if so would there be any point to it?

No, however if you chose to upgrade to a 64-bit install then you could run any 32-bit application aswell as the native 64-bit apps.

I would recommend upgrading to 64-bit, you should see a performance increase in video/photo manipulation, virtualisation etc,  really any 64-bit application will outperform the equivelant 32-bit app

Heres a link tot he [64-bit user group]("http://ubuntuforums.org/group.php?groupid=258") for when you decide to take the plunge :)

---

### Post by jeffbmartinez on 2008-09-15
Thanks for the *very* quick response. Which bit of information did you use to figure that out? My guess is the 'generic' in my uname?

And I guess tonight my plan is to get 64 bit action happening on my machine. It's already downloaded and burned.

Thanks again!

---

### Post by Neo0351 on 2008-09-15
the key piece of information is
> i686

---

### Post by jeffbmartinez on 2008-09-15
Excellent, I have installed x64 now and I see the difference. i686 vs x86_64.

Thanks again guys!

---

### Post by JackVancouver on 2008-09-16
> **jeffbmartinez said:**
> I installed Ubuntu 7.xx on my machine a while back and I recently upgraded to 8.04. I have a core 2 duo so I know it can handle the x64 version. But frankly I just don't remember what I installed. Furthermore I lost the disc which I installed it from.

I just wanna know if I have the 32 or 64 bit version of ubuntu installed on my machine.

martinez@sour-lenovo:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy
martinez@sour-lenovo:~$ uname -a
Linux sour-lenovo 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Does any of this give a hint as to 32 bit vs 64 bit? Or where can I find this info? Thanks all...

 - jeff

A response by Neo0351 indicated that "i686" revealed that Jeff was running 32 bit Ubuntu.

How do I find out if I have "i686" or "x86_64"?
--- Jack

---

### Post by techstop on 2008-09-16
> **JackVancouver said:**
> A response by Neo0351 indicated that "i686" revealed that Jeff was running 32 bit Ubuntu.

How do I find out if I have "i686" or "x86_64"?
--- Jack

See in the first post;

```
martinez@sour-lenovo:~$ uname -a
Linux sour-lenovo 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 **i686** GNU/Linux
```

So, run;

```
uname -a
```

...and you should be able to see your answer.

---

### Post by JackVancouver on 2008-09-16
> **techstop said:**
> See in the first post;

```
martinez@sour-lenovo:~$ uname -a
Linux sour-lenovo 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 **i686** GNU/Linux
```

So, run;

```
uname -a
```

...and you should be able to see your answer.

Thank you for gently pointing out what should have been obvious. 
- Jack

---

