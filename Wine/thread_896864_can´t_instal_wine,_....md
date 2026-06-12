---
title: "can´t instal wine, ..."
date: 2008-08-21
forum: Wine
---

### Post by eragon100 on 2008-08-21
... because samba can´t be installed, which means that winbind can´t be installed, which means... exactly :(

terminal output for wine:

eragon@Asgard:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: winbind but it is not going to be installed
E: Broken packages

terminal output from samba:

eragon@Asgard:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4.4) but 3.0.28a-1ubuntu4.5 is to be installed
E: Broken packages

terminal output for winbind:

eragon@Asgard:~$ sudo apt-get install winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  winbind: Depends: samba-common (= 3.0.28a-1ubuntu4.4) but 3.0.28a-1ubuntu4.5 is to be installed
E: Broken packages


Are the repo´s being updates, seems like a bit of a mess right now :confused:

---

### Post by eragon100 on 2008-08-21
Don´t worry, problem solved:

- went to synaptic

- forced a downgrade of samba-common to *-ubuntu-4.4

- had it remove smbclient, and ubuntu-, kubuntu-, and xubuntu desktop because that was necessary (and no, that doesn´t remove any packages :))

- reinstalled the four packages above

- installed wine, which of course worked now :)

---

