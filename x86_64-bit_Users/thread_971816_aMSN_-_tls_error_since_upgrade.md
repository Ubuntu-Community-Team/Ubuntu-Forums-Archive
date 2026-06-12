---
title: "aMSN - tls error since upgrade"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by Steeperton on 2008-11-05
I upgraded to 8.10 yesterday, and now aMSN doesn't work - it asks me to download TLS, and tried to do it for me... Which doesn't work - it says it was successful, but still gives the same error message.

I've reinstalled tls through synaptic, and reinstalled amsn by compiling from source (the autopackage says that 64bit is not supported). Still the same error!

Any ideas?

---

### Post by Thelasko on 2008-11-05
> **Steeperton said:**
> I've reinstalled tls through synaptic, and reinstalled amsn by compiling from source (the autopackage says that 64bit is not supported). Still the same error!

Any ideas?

That's not true, I found the 64-bit package in the repositories [right here.]("http://packages.ubuntu.com/intrepid/amsn")

The tls package it depends on is called [tcl-tls.]("http://packages.ubuntu.com/intrepid/tcl-tls")

---

### Post by Yellow Pasque on 2008-11-05
If compiling from source, you should also install libgnutls-dev and tcl-dev.

---

### Post by Steeperton on 2008-11-11
It's a 64 bit version of autopackage that doesn't exist apparently. I'm not particularly hopeful of the autopackage working anyway, since the one from the repositories doesn't work...

I've got those packages installed already, and still nothing - I get the message about installing TLS. 

I've made sure that aMSN is pointing to /usr/lib/tls1.50, which seems to be my installation of TLS, but still it doesn't recognise it!

---

### Post by Thelasko on 2008-11-11
> **Steeperton said:**
> It's a 64 bit version of autopackage that doesn't exist apparently. I'm not particularly hopeful of the autopackage working anyway, since the one from the repositories doesn't work...

I've got those packages installed already, and still nothing - I get the message about installing TLS. 

I've made sure that aMSN is pointing to /usr/lib/tls1.50, which seems to be my installation of TLS, but still it doesn't recognise it!

Ok, I'm going to ask you to [read this]("http://www.psychocats.net/ubuntu/installingsoftware") and then get back to me.

---

### Post by Thelasko on 2008-11-11
> **Steeperton said:**
> I upgraded to 8.10 yesterday, and now aMSN doesn't work 

Upon rereading this post I think you need to completely remove amsn and reinstall it.

```
sudo apt-get remove --purge amsn
```

should do that.  Hopefully you didn't do any damage by attempting to install from source.

P.S. "Mark for complete removal" in Synaptic does the same thing as the code above.

---

### Post by Steeperton on 2008-11-12
> **Thelasko said:**
> Upon rereading this post I think you need to completely remove amsn and reinstall it.

```
sudo apt-get remove --purge amsn
```

should do that.  Hopefully you didn't do any damage by attempting to install from source.

P.S. "Mark for complete removal" in Synaptic does the same thing as the code above.

Unfortunately that didn't work either - I purged tcl-tls too, to see if that helped, and it didn't.

I tried compiling tls from source - not amsn, as this seems to be where the problem is. I've now purged all installs of tls and amsn, tried again, and still no joy.

Edit: A bit more information...
I ran tclsh, and entered "package require tls". I get the following message, if that helps?
```

couldn't load file "/usr/lib/tls1.50/libtls-1.50.so": libssl.so.0.9.7: cannot open shared object file: No such file or directory

```

I don't have an option to install libssl.so.0.9.7 - I have 0.9.8 installed already. libtls-1.50.so exists in the directory mentioned.

---

