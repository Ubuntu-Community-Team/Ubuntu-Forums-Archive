---
title: "error checking for updated package information"
date: 2009-04-17
forum: x86 64-bit Users
---

### Post by the.paisley.avenger on 2009-04-17
Hi

When I click on System > Administration > update manager > check it checks for package information and gives me an error. It was working fine until recently. The error output is as follows.

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Does anyone know what i can do to fix this? Any help is appreciated.

---

### Post by dcstar on 2009-04-18
> **the.paisley.avenger said:**
> Hi

When I click on System > Administration > update manager > check it checks for package information and gives me an error. It was working fine until recently. The error output is as follows.

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Does anyone know what i can do to fix this? Any help is appreciated.

Wait a day or so until this particular repository is fully updated with new release files.

---

### Post by sphilli8 on 2009-04-19
Well, I've been having the same problem for about five days now. I changed the server from the Australian one to the main one and it's still happening.
> W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Edit: Ahhh...the problem resolved itself almost as soon as I'd posted that message, after I changed back to the .au server.

---

### Post by the.paisley.avenger on 2009-04-19
I have now changed from using the New Zealand server to the main server and back again and this seems to have fixed the problem, Thank you both for your help.

---

