---
title: "Unable to update via Synaptic"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Incendium on 2006-08-15
I try to update, and I get these errors:

[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz:) 403 Forbidden
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:) 403 Forbidden [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz:) 403 Forbidden
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz:) 403 Forbidden [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 403 Forbidden
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 403 Forbidden [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 403 Forbidden [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 403 Forbidden
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz:) 403 Forbidden [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz:) 403 Forbidden [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 403 Forbidden [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 403 Forbidden [IP: 146.137.96.15 80]

I pulled up the files in a web browser and they are showing up just fine. All ports are open on my router, so i'm guessing something is wrong on the software side. Any suggestions?

---

### Post by jordilin on 2006-08-15
Try doing it in the command line
```
sudo apt-get update
```

---

### Post by Incendium on 2006-08-15
Same errors. Here is a dump:

matt@serenity:~$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
matt@serenity:~$

---

### Post by Incendium on 2006-08-15
Solved my problem using the method in [this](http://www.ubuntuforums.org/showthread.php?t=186455) thread.

---

