---
title: "Install SyncKolab for Thunderbird for AMD64"
date: 2008-07-30
forum: x86 64-bit Users
---

### Post by davemc on 2008-07-30
I couldn't find a [SyncKolab]("http://www.gargan.org/extensions/synckolab.html") xpi install for AMD64.

Here's how to build it from source, it's quick and easy.

Turns out it's only a couple of zip's to build a chrome xpi.

Download the source, as shown at [http://synckolab.mozdev.org/source.html](http://synckolab.mozdev.org/source.html)

Password is guest

```

cvs -d :pserver:guest@mozdev.org:/cvs login
cvs -z3 -d :pserver:guest@mozdev.org:/cvs co synckolab

```

It doesn't seem to come with a make or build. 

Adapting from this one [http://www.captain.at/howto-firefox-toolbar-tutorial.php](http://www.captain.at/howto-firefox-toolbar-tutorial.php)

src/make.sh
```

#!/bin/sh
cd chrome
zip -r sync_kolab-cvs-amd64.jar content/ skin/ locale/
cd ..
zip sync_kolab-cvs-amd64.xpi install.rdf chrome/sync_kolab-cvs-amd64.jar

```

Then install from Thunderbird / Add Ons / Install.

Easy!

David

---

