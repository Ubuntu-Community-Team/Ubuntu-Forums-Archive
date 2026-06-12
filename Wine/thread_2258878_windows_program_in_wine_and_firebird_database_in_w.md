---
title: "windows program in wine and firebird database in wine"
date: 2014-12-31
forum: Wine
---

### Post by tomas25 on 2014-12-31
I am in need of support. I have a windows program - Fitness manager that is dependent on a firebird database. I would like to run the program on ubuntu through wine.
It installs ok, however it cannot access the firebird database it creates during the installation. It seems the firebird server is running in Wine, however Fitness manager cannot find the database.
I tried also running the native firebird on ubuntu, and pointing the Fitness manager to that database through the .ini file, but also didn't work. (the ubuntu firebird works fine, as I can connect to the database in Terminal)
Has anyone tried doing a similar set up? Any ideas how to make it work? Any comments as to what I am doing wrong?

The original .ini file:

[local]
NetworkMode=server
RemoteServerPath=D:\gdrive\NET\MyProjects\FitnessManager\FitnessManager\FitnessManager\bin\Debug
ImagesPath=C:\FMMemberImages
SN=5649525048

Edited .ini:

[local]
NetworkMode=client
RemoteServerPath=localhost: /home/centrum/FM/Fitnes.fdb
ImagesPath=C:\FMMemberImages
SN=5649525048

---

### Post by dragonfly41 on 2014-12-31
Your ini file has a rogue space ...

RemoteServerPath=D:\gdrive\NET\MyProjects\FitnessM anager\FitnessManager\FitnessManager\bin\Debug

is that just a typo error?

---

### Post by oldos2er on 2014-12-31
Moved to Wine.

---

