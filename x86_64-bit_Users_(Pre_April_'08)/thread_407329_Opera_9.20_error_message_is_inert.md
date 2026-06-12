---
title: "Opera 9.20 error message is inert"
date: 2007-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by sgornick on 2007-04-12
When installing (upgrading) Opera to 9.20 on Ubuntu Dapper (6.06) AMD64 I got the error message:

  Could not parse file '/usr/share/applications/audacity.desktop': desktop entry contain line '?[Desktop Entry]' which is not an entry, group, or comment

However, doing Help -> About in the next launch of Opera showed Opera 9.20.

Here's what I did:
Download Opera 9.20 static-deb

$ sudo dpkg -i --force-architecture opera9.deb

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 135930 files and directories currently installed.)
Preparing to replace opera-static 9.20-20070409.1 (using opera.deb) ...
Unpacking replacement opera-static ...
Setting up opera-static (9.20-20070409.1) ...
Could not parse file '/usr/share/applications/audacity.desktop': desktop entry contain line '?[Desktop Entry]' which is not an entry, group, or comment

Just wanted to share this in case anyone else got the same thing and didn't realize the error message can be disregarded.

---

### Post by kuja on 2007-04-12
The error message you got at the end has nothing to do with Opera anyway, as you may have guessed, it's actually a problem with the audacity package.

---

