---
title: "GPG agent problems?"
date: 2007-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by snakesandstuff on 2007-10-09
I'm running Feisty Fawn on an AMD 64, and all of a sudden my gpg is not working...  The process is running, when I run netstat and compare that to the PID and the GPG_AGENT_INFO everything seems alright, but it fails out when I try to encrypt and gives me the following

```
gpg: problem with the agent - disabling agent use
```

and when I do a sudo apt-get update I get the following:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-amd64/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-amd64/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Any help is greatly appreciated.

---

