---
title: "32bit chroot - syntax clarification"
date: 2004-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dylanby on 2004-12-27
Ok...I'm setting up a 32bit chroot.
I just want some clarification on the syntax so I don't screw it up.

After editing my fstab & adding:
```
/home /var/chroot/home none bind 0 0
/tmp /var/chroot/tmp none bind 0 0
/proc /var/chroot/proc proc defaults 0 0
/media/cdrom /var/chroot/media/cdrom none bind 0 0
``` 

Now I would do this?
```
sudo mkdir /var/chroot/home
``` 

& then this?
```
sudo mount /var/chroot/home
``` 

& do the same for the other two lines?

Is that correct?

---

### Post by Dylanby on 2004-12-27
When using apt under the chroot I'm getting locale errors:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_CA:en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en_CA"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
``` 

How can I fix them?

Also hostname errors:
```
sudo apt-get update
sudo: unable to lookup <my hostname> via gethostbyname()
postdrop: warning: unable to look up public/pickup: No such file or directory
``` 

Not "showstoppers", but I would like to know how to fix them.

---

### Post by ahyden on 2004-12-27
[QUOTE=Dylanby]
Now I would do this?
```
sudo mkdir /var/chroot/home
``` 

& then this?
```
sudo mount /var/chroot/home
``` 

& do the same for the other two lines?

Is that correct?[/QUOTE]

That should work. You could just make the directories and type mount -a and it will mount everything in /etc/fstab. It will automatically get mounted next time you boot too.

---

### Post by ahyden on 2004-12-27
[QUOTE=Dylanby]When using apt under the chroot I'm getting locale errors:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_CA:en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en_CA"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
``` 

How can I fix them?
[/QUOTE]

Try sudo dpkg-reconfigure locales

[QUOTE=Dylanby]
Also hostname errors:
```
sudo apt-get update
sudo: unable to lookup <my hostname> via gethostbyname()
postdrop: warning: unable to look up public/pickup: No such file or directory
``` 

Not "showstoppers", but I would like to know how to fix them.[/QUOTE]

Copy /etc/hosts to /var/chroot/etc/

Or you could just write your own hosts file.

---

### Post by Dylanby on 2004-12-27
Thanks for pointing me in the right direction.

This is what I did:

```
$ sudo cp /etc/hosts /var/chroot/etc/
``` 

...

```
$ dchroot -d
Executing shell in 'warty' chroot.
``` 

...

```
$ sudo apt-get install localeconf
``` 

...

```
$ sudo dpkg-reconfigure locales
```

---

