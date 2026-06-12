---
title: "gedit doesn't work any more..."
date: 2007-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stef@n on 2007-02-04
Hi Guys,

Since this morning the "sudo gedit" command doesn't work any more. I get the following error-message:

sudo: gedit: command not found

I'm using ubuntu 6.10 (AMD64).

Does anybody know what the problem is?

---

### Post by leonelag on 2007-02-04
> sudo: gedit: command not found

First, look whether the gedit package is installed in your system:

```
aptitude search gedit
```

You should see an "i" on the first column of the output. (No need for sudo on this command, because you're not installing/removing anything)

If it is installed, then there should be a file /usr/bin/gedit, which execution permissions. Do this:

```
ls -l /usr/bin/gedit
```

If it is not there, try reinstalling gedit:

```
sudo aptitude reinstall gedit
```

This should do.

---

### Post by Stef@n on 2007-02-04
Thanks Leonelag!

After trying:

sudo aptitude reinstall gedit

I got the message that gedit wasn't installed so it couldn't "reinstall". So I tried:

sudo aptitude install gedit

Now everything works ok again...

Thanks again!

---

