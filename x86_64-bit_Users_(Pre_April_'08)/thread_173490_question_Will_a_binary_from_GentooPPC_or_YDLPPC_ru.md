---
title: "question: Will a binary from GentooPPC or YDLPPC run in UbuntuPPC?"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by davygravy on 2006-05-10
Question: Will a binary* (executable) from GentooPPC or YDLPPC run in UbuntuPPC?

Always, sometimes or never?

Will a DebianPPC binary run in UbuntuPPC?

A, S or N?

thanks,

davygravy



*I'm not talking about installing packages - just a simple binary.

---

### Post by nkbj on 2006-05-10
[QUOTE=davygravy]Question: Will a binary* (executable) from GentooPPC or YDLPPC run in UbuntuPPC?
[...]
*I'm not talking about installing packages - just a simple binary.[/QUOTE]

The binaries should run if the libraries the binaries are linked with has the same major version numbers on the various distributions. That means (almost) always for the newest distribution releases.

To be 100% sure you can build your binaries as statically linked binaries, i.e. linking the libraries into the binaries. The downside is that the binary files are huge.

Regards,
Niels Kristian

---

### Post by farruinn on 2006-05-11
Mixing binaries can have unexpected results if, as NKBJ points out. Personally, I would rather build packages from source on my own system so I *know* the libraries used to build the source are the same as what the binary will use.

---

### Post by ssam on 2006-05-11
might work. it its something simple its more likely. i think c++ programs are more sensitive to changes in gcc versions than c ones.

---

### Post by farruinn on 2006-05-11
That's a good point. The breezy kernel is an excellent example where the kernel has to be compiled with gcc3.4 but breezy uses gcc4.0 by default. I wonder if the same situation will occur with Dapper?

---

### Post by ssam on 2006-05-14
in dapper everything is compiled with gcc4.0, so no more of the workarounds for compiling drivers.

---

