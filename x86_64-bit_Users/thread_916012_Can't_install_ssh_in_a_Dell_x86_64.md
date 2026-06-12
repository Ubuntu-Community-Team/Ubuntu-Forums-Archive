---
title: "Can't install ssh in a Dell x86_64"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by xeo_pt on 2008-09-10
Hi,
I can't install the ssh server when using a x86_64 distro,

```
The following packages have unmet depends:
ssh: depends openssh-server but it is not going to be installed.

E:broken package
```

Any ideas ?

---

### Post by jespdj on 2008-09-10
You have broken packages for some reason.

Go to Synaptic (menu: System / Administration / Synaptic Package Manager) and select Edit / Fix Broken Packages.

---

### Post by tangibleorange on 2008-09-10
> **xeo_pt said:**
> Hi,
I can't install the ssh server when using a x86_64 distro,

```
The following packages have unmet depends:
ssh: depends openssh-server but it is not going to be installed.

E:broken package
```

Any ideas ?

also could you please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by xeo_pt on 2008-09-11
I install a 386 version, but I check repository and everything seems ok.
I will install the x86_64 again and will tell the result.

Thank you.

---

### Post by jpkotta on 2008-09-11
The package's name is openssh-server.  The client should be installed by default.  The ssh package is a virtual package that depends on both the client and server.
```
aptitude show ssh
```

---

### Post by xeo_pt on 2008-09-17
The problem was with the repository, I install another x86_64 and it worked fine.
Thank you.

---

### Post by tangibleorange on 2008-09-17
> **xeo_pt said:**
> The problem was with the repository, I install another x86_64 and it worked fine.
Thank you.

glad it's working. please mark this thread solved (Thread Tools -> Solved).

---

