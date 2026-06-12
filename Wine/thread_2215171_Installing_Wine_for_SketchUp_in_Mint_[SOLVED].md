---
title: "Installing Wine for SketchUp in Mint [SOLVED]"
date: 2014-04-05
forum: Wine
---

### Post by Ian_M._Stewart on 2014-04-05
Hi, I'm new(ish) to Wine, which I see just as a tool I don't understand.

I've been trying to install the latest version of SketchUp to run in WINE.  If it matters, I'm running Mint 16 Petra Cinnamon AMD64 with lots of memory and drive space.  I know, this is a Ubuntu forum, but Mint16 is based on Ubuntu 13.10 and there's probably more Wine expertise here. :)  I've followed the instructions here:  [http://ubuntuhandbook.org/index.php/2013/07/install-sketchup-2013-ubuntu-13-04/](http://ubuntuhandbook.org/index.php/2013/07/install-sketchup-2013-ubuntu-13-04/),  I can't find any for 13.10

When I start the SketchUpMake-en.exe in c: drive, it starts the install and then reports:

```
Prerequisite check for system component Microsoft Windows failed with the following error message:
"Installation of SketchUp requires Windows XP Professional x64 Service Pack 2 or later."

See the setup log file located at 'C:\users\ian\Temp\VSD8981.tmp\install.log' for more information.
```

The log file follows:

```
The following properties have been set:
Property: [AdminUser] = true {boolean}
Property: [InstallMode] = HomeSite {string}
Property: [ProcessorArchitecture] = AMD64 {string}
Property: [VersionNT] = 5.1.3 {version}
Running checks for package 'Microsoft Windows', phase BuildList
The following properties have been set for package 'Microsoft Windows':
Running checks for command 'SketchUpPrerequisites\32-bit'
Result of running operator 'ValueNotEqualTo' on property 'ProcessorArchitecture' and value 'Intel': true
Result of checks for command 'SketchUpPrerequisites\32-bit' is 'Bypass'
Running checks for command 'SketchUpPrerequisites\64-bit'
Result of running operator 'ValueNotEqualTo' on property 'ProcessorArchitecture' and value 'AMD64': false
Result of running operator 'VersionGreaterThanOrEqualTo' on property 'VersionNT' and value '5.2.2': false
Result of running operator 'VersionLessThan' on property 'VersionNT' and value '5.2.2': true
Result of checks for command 'SketchUpPrerequisites\64-bit' is 'Fail'
'Microsoft Windows' RunCheck result: Fail
A prerequisite failed for Package "Microsoft Windows"
Package failed with message "Installation of SketchUp requires Windows XP Professional x64 Service Pack 2 or later."
```

Can anyone tell me what I'm missing please?  I had this working for an earlier version of SktchUp on an earlier version of Mint15, but I can't remember now how I got there.

Thanks.

---

### Post by Ian_M._Stewart on 2014-04-05
OK, I've now re-read the instructions I linked to, and the answer is in there in my earlier post (January this year).  I think old age is catching up with me.  However, here is the solution for anyone who stumbles on this thread:

SOLUTION:   In winecfg, change away from WindowsXP and then BACK TO  WindowsXP.  Suddenly, the SU installation works as it should.

Sorry to take up your time.

---

