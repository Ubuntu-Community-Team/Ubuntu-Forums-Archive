---
title: "Problems Installing Azureus, circular dependencies??"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by shear on 2006-07-10
Hey there.

I'm trying to install Azureus on a laptop running Dapper amd64. When I try installing with apt, I get:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  azureus: Depends: libswt3.1-gtk-java but it is not going to be installed
E: Broken packages

I try to install libswt3.1-gtk-java by itself, but then I get a whole chain of unmet dependencies. EDIT: I also got to a point where two packages had each other as unmet dependencies, and they wouldn't install simultaneously either. I don't really want to go outside the repos to install packages, thats the reason I formatted and reinstalled Dapper fresh instead of upgrading from Breezy.

Can anyone help me figure out what is going on? Thanks.

~shear

---

### Post by Kilz on 2006-07-10
> **shear said:**
> Hey there.

I'm trying to install Azureus on a laptop running Dapper amd64. When I try installing with apt, I get:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  azureus: Depends: libswt3.1-gtk-java but it is not going to be installed
E: Broken packages

I try to install libswt3.1-gtk-java by itself, but then I get a whole chain of unmet dependencies. EDIT: I also got to a point where two packages had each other as unmet dependencies, and they wouldn't install simultaneously either. I don't really want to go outside the repos to install packages, thats the reason I formatted and reinstalled Dapper fresh instead of upgrading from Breezy.

Can anyone help me figure out what is going on? Thanks.

~shear

I just installed the libswt3.1-gtk-java package without problems. Sounds like you got a bad package. have you tried ```
sudo apt-get install -f
```

---

### Post by shear on 2006-07-10
Ok, just tried to force it. Still didn't work for some reason. 

```
sudo apt-get install -f azureus
```

Which gives me libswt3.1-gtk-swt as an unmet dependency. So I try:

```
sudo apt-get install -f libswt3.1-gtk-java
```

Which gives me:

```
The following packages have unmet dependencies:
  libswt3.1-gtk-java: Depends: mozilla-browser (>= 2:1.7.0) but it is not going to be installed

```

Then when I try:

```
sudo apt-get install -f mozilla-browser
```

I recieve:

```
The following packages have unmet dependencies:
  mozilla-browser: Depends: libnspr4 (= 2:1.7.13-0ubuntu5.10) but 2:1.firefox1.5 .dfsg+1.5.0.4-0ubuntu6.06 is to be installed

```

However, libnspr4 says it is the latest version, and doesn't install or give me anything as an error.

I'm quite confused.

~shear

---

### Post by Kilz on 2006-07-10
> **shear said:**
> Ok, just tried to force it. Still didn't work for some reason. 

```
sudo apt-get install -f azureus
```

Which gives me libswt3.1-gtk-swt as an unmet dependency. So I try:

```
sudo apt-get install -f libswt3.1-gtk-java
```

Which gives me:

```
The following packages have unmet dependencies:
  libswt3.1-gtk-java: Depends: mozilla-browser (>= 2:1.7.0) but it is not going to be installed

```

Then when I try:

```
sudo apt-get install -f mozilla-browser
```

I recieve:

```
The following packages have unmet dependencies:
  mozilla-browser: Depends: libnspr4 (= 2:1.7.13-0ubuntu5.10) but 2:1.firefox1.5 .dfsg+1.5.0.4-0ubuntu6.06 is to be installed

```

However, libnspr4 says it is the latest version, and doesn't install or give me anything as an error.

I'm quite confused.

~shear
The command 
```
sudo apt-get install -f 
```
is not to force a package in. The command is to fix the package database. Please try it as is.
Do you have multiverse and universe repositories enabled? libswt3.1-gtk-java is in universe. If you need to know how to do that [look here]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories").

---

### Post by shear on 2006-07-11
Fix, not Force. Gotcha.

Unfortunately though, that didn't change anything. I have all the repos added, double checked and tried again to make sure though.

After "sudo apt-get install -f", I still get the same problems.

~shear

---

### Post by Kilz on 2006-07-11
> **shear said:**
> Fix, not Force. Gotcha.

Unfortunately though, that didn't change anything. I have all the repos added, double checked and tried again to make sure though.

After "sudo apt-get install -f", I still get the same problems.

~shear

What happens if you try and install with synaptic?

---

### Post by shear on 2006-07-11
If I try with Synaptic, I get the same problem. It fails with error:

azureus:
 Depends: libswt3.1-gtk-java but it is not going to be installed

~shear

---

### Post by Kilz on 2006-07-11
> **shear said:**
> If I try with Synaptic, I get the same problem. It fails with error:

azureus:
 Depends: libswt3.1-gtk-java but it is not going to be installed

~shear
In your orignal post the error was broken packages. Maybe the broken one is stuck in the cashe. Maybe clearing it out will help
```
sudo apt-get clean
```

---

### Post by shear on 2006-07-12
Well, that doesn't look like it's the problem. :\


```
contenti@athos:~$ sudo apt-get clean
contenti@athos:~$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  azureus: Depends: libswt3.1-gtk-java but it is not going to be installed
E: Broken packages
contenti@athos:~$

```

---

### Post by The Keeper on 2006-07-12
Empty your cache (sudo apt-get clean) and then edit your sources list (sudo nano /etc/apt/sources.list) to change your repository mirror, it might be a corrupted package in a mirrored repository.

Instead of xx.archive.ubuntu.com, change it temporarily to archive.ubuntu.com or use another country's mirror. If you live in the USA for example, you might want to try ca.archive.ubuntu.com. Then sudo apt-get update and try to install the packages again.

---

### Post by shear on 2006-07-12
Ok, I hadn't noticed before now, since I added the extra repositories through Synaptic, but my sources.list entries were all for breezy, not dapper. I changed to ca.archive.ubuntu rather than archive.ubuntu, which also makes sense since I am Canadian, and I changed the listing from breezy to dapper.

It worked. Thanks guys for all the help.

~shear

---

