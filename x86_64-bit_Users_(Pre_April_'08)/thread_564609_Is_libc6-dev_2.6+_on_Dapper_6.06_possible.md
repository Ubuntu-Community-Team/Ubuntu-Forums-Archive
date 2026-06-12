---
title: "Is libc6-dev 2.6+ on Dapper 6.06 possible??"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by isync on 2007-10-01
I am trying to install libavutil1d_0.cvs20070307-5ubuntu4+medibuntu1_amd64.deb from the medibuntu repository.

But it requires: "libavutil1d depends on libc6 (>= 2.6-1); but: version of libc6 installed is 2.3.6-0ubuntu20.5." as I am running Dapper.

So far, I found out Dapper uses version 2.3 of libc6
Edgy 2.4, Feisty 2.5 etc. Is it possible to have 2.6+ on Dapper (to be able to install the latest libavutil) Or can I force to install although I run an older libc6??

I am using gdebi to install the .deb.

Is this related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/138602](https://bugs.launchpad.net/ubuntu/+bug/138602) ??

---

### Post by John.Michael.Kane on 2007-10-01
> **isync said:**
> I am trying to install libavutil1d_0.cvs20070307-5ubuntu4+medibuntu1_amd64.deb from the medibuntu repository.

But it requires: "libavutil1d depends on libc6 (>= 2.6-1); but: version of libc6 installed is 2.3.6-0ubuntu20.5." as I am running Dapper.

So far, I found out Dapper uses version 2.3 of libc6
Edgy 2.4, Feisty 2.5 etc. Is it possible to have 2.6+ on Dapper (to be able to install the latest libavutil) Or can I force to install although I run an older libc6??

I am using gdebi to install the .deb.

Is this related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/138602](https://bugs.launchpad.net/ubuntu/+bug/138602) ??

You would have to download more then just that file. Most likely you will have to download that lib, and all it's dependencies.

I would try getlibs talked about here [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790), As It's not advised to pass the force command on lib's. 

Or

Backing up your data, and moving over to a newer release with the libs/files/programs you need

---

### Post by isync on 2007-10-01
Your answer did not exactly work for me...

using getlibs would mean I have a compiled binary that needs additional libs - but I am not able to compile to that stage.

And: I would download 100 packages if that would solve my problem.

But: Is it possible to have version 2.6.1 of libc6-dev on Dapper or not? And if so, how??:confused:

---

### Post by John.Michael.Kane on 2007-10-01
> **isync said:**
> Your answer did not exactly work for me...

using getlibs would mean I have a compiled binary that needs additional libs - but I am not able to compile to that stage.

And: I would download 100 packages if that would solve my problem.

But: Is it possible to have version 2.6.1 of libc6-dev on Dapper or not? And if so, how??:confused:

IMHO I doubt you can have 2.6.1 of libc6-dev on Dapper without system breakage, As your talking about a lib that is three versions ahead of what your running, eg: it's included in gutsy.

You would need to upgrade a lot more then the lib in question as already said you would need to upgrade the gcc file among other files.

Your best off upgrading to next release.

---

