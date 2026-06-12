---
title: "Problem istalling Wine. Dependancies not met."
date: 2016-02-09
forum: Wine
---

### Post by Jordan_Karadakov on 2016-02-09
Ok, guys I have a big problem installing wine.


I either get this,
    user@user:~$ sudo apt-get install wine
      [sudo] password for user:
  
      Reading package lists... Done 
      Building dependency tree        
      Reading state information... Done 
      Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:
     
        The following packages have unmet dependencies:  wine : Depends:
        wine1.6 but it is not going to be installed E: Unable to correct
        problems, you have held broken packages.

Or when i try: sudo apt-get install wine1.6 i get:
user@user:~$ sudo apt-get install wine1.6
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4)
E: Unable to correct problems, you have held broken packages.

I have followed the instructions from the wine website as well as I have tried Software Center. Same error.
Any ideas,

---

### Post by howefield on 2016-02-09
Thread moved to the "*WINE*" forum.

---

### Post by Jordan_Karadakov on 2016-02-09
I found a solution, thank you very much. 

[http://ubuntuforums.org/showthread.php?t=2188107](http://ubuntuforums.org/showthread.php?t=2188107)

---

