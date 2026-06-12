---
title: "Compiling and installing .tar.gz from source on amd64"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by midorigin on 2007-05-31
Is there anything different I have to do or take into consideration when compiling and installing programs from source on amd64?

There are several, unrelated programs I've tried to compile that never get past the ./configure stage, always giving me the error:

```
checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
configure: error: libtool configure failed

```

Searches over the last hour indicate that this is a fairly uncommon error message.

Is this
- a problem with my computer's configuration that I should fix?
- a problem with the .tar.gz I've downloaded, that its creators should fix?
- a problem inherent in all amd64 systems?
- or something else?

---

### Post by Kilz on 2007-06-01
> **midorigin said:**
> Is there anything different I have to do or take into consideration when compiling and installing programs from source on amd64?

There are several, unrelated programs I've tried to compile that never get past the ./configure stage, always giving me the error:

```
checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
configure: error: libtool configure failed

```

Searches over the last hour indicate that this is a fairly uncommon error message.

Is this
- a problem with my computer's configuration that I should fix?
- a problem with the .tar.gz I've downloaded, that its creators should fix?
- a problem inherent in all amd64 systems?
- or something else?

To my knowledge , and I am far from an expert on compiling it is .
**- a problem with the .tar.gz I've downloaded, that its creators should fix**
What the error is saying is that when it was configuring , it found your system wasnt one of the listed ones its been written to build for. I hope someone else can explain exactly how we as end users could fix this. But I have a feeling it involves writing code.

---

### Post by boogachamp on 2007-06-01
Could recomplile the kernel to be specific to your AMD architecture??

Thats seems a little much to get this to work though.


or maybe just try ./configure --host=whatever the amd64 specific host name is.

---

### Post by midorigin on 2007-06-02
> **boogachamp said:**
> or maybe just try ./configure --host=whatever the amd64 specific host name is.

How can I find out what that should be?

---

### Post by Kuraudo on 2007-06-02
Try a ./configure --help and see if you get anything out of that.

---

