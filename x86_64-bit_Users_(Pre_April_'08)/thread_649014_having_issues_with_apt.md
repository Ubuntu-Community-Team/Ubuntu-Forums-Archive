---
title: "having issues with apt"
date: 2007-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by NumPy on 2007-12-24
This is something new to me, as I can usually fix anything that comes my way... but this takes it.. ill save the rest.. 
Gusty 64 
error: apt gives this on use with any "install" request:
   1.
      The program 'nmap' is currently not installed.  You can install it by typing:
   2.
      sudo apt-get install nmap
   3.
      bash: nmap: command not found
   4.
      brbaldwin@blue:~$ sudo apt-get install ksniffer
   5.
      Reading package lists... Done
   6.
      Building dependency tree
   7.
      Reading state information... Done
   8.
      The following packages were automatically installed and are no longer required:
   9.
        intltool-debian
  10.
      Use 'apt-get autoremove' to remove them.
  11.
      The following extra packages will be installed:
  12.
        traceroute whois
  13.
      The following NEW packages will be installed:
  14.
        ksniffer traceroute whois
  15.
      0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
  16.
      Need to get 0B/532kB of archives.
  17.
      After unpacking 1982kB of additional disk space will be used.
  18.
      Do you want to continue [Y/n]?
  19.
      (Reading database ... 107017 files and directories currently installed.)
  20.
      Unpacking whois (from .../whois_4.7.21_amd64.deb) ...
  21.
      dpkg: error processing /var/cache/apt/archives/whois_4.7.21_amd64.deb (--unpack):
  22.
       trying to overwrite `/usr/share/man', which is also in package oclock
  23.
      Unpacking traceroute (from .../traceroute_2.0.9~rc1-1_amd64.deb) ...
  24.
      dpkg: error processing /var/cache/apt/archives/traceroute_2.0.9~rc1-1_amd64.deb (--unpack):
  25.
      trying to overwrite `/usr/share/man', which is also in package oclock
  26.
      Selecting previously deselected package ksniffer.
  27.
      Unpacking ksniffer (from .../ksniffer_0.3-1_amd64.deb) ...
  28.
      Errors were encountered while processing:
  29.
       /var/cache/apt/archives/whois_4.7.21_amd64.deb
  30.
       /var/cache/apt/archives/traceroute_2.0.9~rc1-1_amd64.deb
  31.
      E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by NumPy on 2007-12-24
for future refference i fixed this issue... 
the error, pointing to "/usr/share/man" was that "man" was a symbolic link that pointed to "../man" which did NOT exist. I renamed that link to .old and made a new directory called "man" and tried apt again. Worked perfectly.

---

