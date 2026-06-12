---
title: "Xubuntu - 'Unable to locate package winehq-stable'"
date: 2017-04-01
forum: Wine
---

### Post by peter1897 on 2017-04-01
I am trying to install wine on Xubuntu 16.10, but when i type:
```
sudo apt-get install --install-recommends winehq-stable
```
i get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq-stable
```

Why it doesn't find the wine package?

---

### Post by deadflowr on 2017-04-02
Is this from the winehq repository?

---

### Post by peter1897 on 2017-04-03
I added the repository following the instructions from the official wine page: [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu). This is what i get when i run 'apt-get update':
```
osboxes@osboxes:~$ sudo apt-get update
Get:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]
Hit:2 http://gb.archive.ubuntu.com/ubuntu yakkety InRelease
Get:3 http://gb.archive.ubuntu.com/ubuntu yakkety-updates InRelease [102 kB]       
Get:4 http://gb.archive.ubuntu.com/ubuntu yakkety-backports InRelease [102 kB]                
Get:5 http://security.ubuntu.com/ubuntu yakkety-security/main amd64 DEP-11 Metadata [10.9 kB]
Get:6 http://security.ubuntu.com/ubuntu yakkety-security/main DEP-11 64x64 Icons [15.7 kB]
Get:7 http://security.ubuntu.com/ubuntu yakkety-security/universe amd64 DEP-11 Metadata [18.7 kB]
Get:8 http://security.ubuntu.com/ubuntu yakkety-security/universe DEP-11 64x64 Icons [18.4 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main i386 Packages [228 kB]                                
Get:10 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 Packages [232 kB]
Get:11 https://dl.winehq.org/wine-builds/ubuntu yakkety InRelease [4,672 B]
Get:12 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 DEP-11 Metadata [146 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main DEP-11 64x64 Icons [82.2 kB]  
Get:14 https://dl.winehq.org/wine-builds/ubuntu yakkety/main i386 Packages [3,228 B]
Err:14 https://dl.winehq.org/wine-builds/ubuntu yakkety/main i386 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Checksum-FileSize:3228 [weak]
   - SHA256:4d6ff0956b21c1f7b4d02d3bf3067cc5753e99467ef05260e7b53bde9fbe25ad
   - SHA1:22d80ec32c8945f8c77b89715da530770c79b6b0 [weak]
   - MD5Sum:936a2931f0d4981fa8bfb9f92439ded0 [weak]
  Hashes of received file:
   - SHA256:0164eda0d063d33baf2892527b84c7a8bf15a0da001702d64e45673bdc84b820
   - SHA1:8d67ce71ad303248be3450fb92b93db70c83cbad [weak]
   - MD5Sum:9514718ff1baedbfbffe7681584aa6ba [weak]
   - Checksum-FileSize:1896 [weak]
  Last modification reported: Tue, 28 Mar 2017 19:54:53 +0000
  Release file created at: Tue, 28 Mar 2017 22:00:26 +0000
Get:15 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe i386 Packages [143 kB]
Get:16 https://dl.winehq.org/wine-builds/ubuntu yakkety/main amd64 Packages [3,252 B]
Get:17 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe amd64 Packages [145 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe amd64 DEP-11 Metadata [111 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe DEP-11 64x64 Icons [144 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu yakkety-backports/main amd64 DEP-11 Metadata [3,328 B]
Fetched 1,615 kB in 3s (469 kB/s)       
Reading package lists... Done
E: Failed to fetch https://dl.winehq.org/wine-builds/ubuntu/dists/yakkety/main/binary-i386/Packages.xz  Hash Sum mismatch
   Hashes of expected file:
    - Checksum-FileSize:3228 [weak]
    - SHA256:4d6ff0956b21c1f7b4d02d3bf3067cc5753e99467ef05260e7b53bde9fbe25ad
    - SHA1:22d80ec32c8945f8c77b89715da530770c79b6b0 [weak]
    - MD5Sum:936a2931f0d4981fa8bfb9f92439ded0 [weak]
   Hashes of received file:
    - SHA256:0164eda0d063d33baf2892527b84c7a8bf15a0da001702d64e45673bdc84b820
    - SHA1:8d67ce71ad303248be3450fb92b93db70c83cbad [weak]
    - MD5Sum:9514718ff1baedbfbffe7681584aa6ba [weak]
    - Checksum-FileSize:1896 [weak]
   Last modification reported: Tue, 28 Mar 2017 19:54:53 +0000
   Release file created at: Tue, 28 Mar 2017 22:00:26 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.
osboxes@osboxes:~$ sudo apt-get install --install-recommends winehq-staging
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq-staging
```

---

### Post by deadflowr on 2017-04-03
See if the usual hash sum mismatch fix clears it up
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by peter1897 on 2017-04-03
I run the 'rm' command but it didn't fix the issue:
```
osboxes@osboxes:~$ sudo apt-get update
Hit:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu yakkety InRelease                    
Hit:3 http://gb.archive.ubuntu.com/ubuntu yakkety-updates InRelease            
Hit:4 http://gb.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Get:5 https://dl.winehq.org/wine-builds/ubuntu yakkety InRelease [4,672 B]
Get:6 https://dl.winehq.org/wine-builds/ubuntu yakkety/main amd64 Packages [3,252 B]
Get:7 https://dl.winehq.org/wine-builds/ubuntu yakkety/main i386 Packages [3,228 B]
Err:7 https://dl.winehq.org/wine-builds/ubuntu yakkety/main i386 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Checksum-FileSize:3228 [weak]
   - SHA256:4d6ff0956b21c1f7b4d02d3bf3067cc5753e99467ef05260e7b53bde9fbe25ad
   - SHA1:22d80ec32c8945f8c77b89715da530770c79b6b0 [weak]
   - MD5Sum:936a2931f0d4981fa8bfb9f92439ded0 [weak]
  Hashes of received file:
   - SHA256:0164eda0d063d33baf2892527b84c7a8bf15a0da001702d64e45673bdc84b820
   - SHA1:8d67ce71ad303248be3450fb92b93db70c83cbad [weak]
   - MD5Sum:9514718ff1baedbfbffe7681584aa6ba [weak]
   - Checksum-FileSize:1896 [weak]
  Last modification reported: Tue, 28 Mar 2017 19:54:53 +0000
  Release file created at: Tue, 28 Mar 2017 22:00:26 +0000
Fetched 9,820 B in 1s (8,080 B/s)
Reading package lists... Done
E: Failed to fetch https://dl.winehq.org/wine-builds/ubuntu/dists/yakkety/main/binary-i386/Packages.xz  Hash Sum mismatch
   Hashes of expected file:
    - Checksum-FileSize:3228 [weak]
    - SHA256:4d6ff0956b21c1f7b4d02d3bf3067cc5753e99467ef05260e7b53bde9fbe25ad
    - SHA1:22d80ec32c8945f8c77b89715da530770c79b6b0 [weak]
    - MD5Sum:936a2931f0d4981fa8bfb9f92439ded0 [weak]
   Hashes of received file:
    - SHA256:0164eda0d063d33baf2892527b84c7a8bf15a0da001702d64e45673bdc84b820
    - SHA1:8d67ce71ad303248be3450fb92b93db70c83cbad [weak]
    - MD5Sum:9514718ff1baedbfbffe7681584aa6ba [weak]
    - Checksum-FileSize:1896 [weak]
   Last modification reported: Tue, 28 Mar 2017 19:54:53 +0000
   Release file created at: Tue, 28 Mar 2017 22:00:26 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2017-04-04
Yeah, I see it's a known issue:
[https://bugs.winehq.org/show_bug.cgi?id=42759]("https://bugs.winehq.org/show_bug.cgi?id=42759")
[https://bugs.winehq.org/show_bug.cgi?id=40346]("https://bugs.winehq.org/show_bug.cgi?id=40346")
Hopefully they'll get it sorted out.

Oddly, I did not see this on zesty 17.04, but do see it on trusty 14.04.
But who knows what tomorrow will bring.

---

