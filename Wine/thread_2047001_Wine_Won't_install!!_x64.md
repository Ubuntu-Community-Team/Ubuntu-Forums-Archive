---
title: "Wine Won't install!! x64"
date: 2012-08-24
forum: Wine
---

### Post by darksidedude on 2012-08-24
Fresh install of 12.04 x64 all updates applied. I tried to install wine from the PPA and it is throwing errors at me. any thoughts on the matter?

```
 sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages  
```

```
sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.11-0ubuntu1)
E: Unable to correct problems, you have held broken packages.
 
```

---

### Post by thatguruguy on 2012-08-24
Run the following in a terminal and post the results here:

```
sudo apt-get update
```

---

