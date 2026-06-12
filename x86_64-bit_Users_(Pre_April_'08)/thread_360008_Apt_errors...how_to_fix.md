---
title: "Apt errors...how to fix?"
date: 2007-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-02-12
I'm getting the following errors when i do an apt-get update.  How can I fix them?  Much thanks.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://raof.dyndns.org/falcon/dists/edgy/Release](http://raof.dyndns.org/falcon/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release)  Unable to find expected entry restricteddeb/binary-amd64/Packages in Meta-index file (malformed Release file?)

I'm sure the first error has to do with the site being down temporarily, but i've never seen the "malformed release file" errors before.

---

### Post by John.Michael.Kane on 2007-02-14
If your still having these issues have you tried commenting out the unneeded sources?

---

