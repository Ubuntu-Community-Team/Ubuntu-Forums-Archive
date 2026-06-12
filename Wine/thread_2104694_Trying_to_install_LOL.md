---
title: "Trying to install LOL"
date: 2013-01-14
forum: Wine
---

### Post by 101kitty on 2013-01-14
I'm tired to install leagues of legend but i think i need wine x64, can someone tell me were i can get wine x64 be the one in the USC is not working for me...

---

### Post by sffvba[e0rt on 2013-01-14
The correct version of Wine for the version of Ubuntu you are running will be installed from the Software Centre.

What is the problem error you are having?  (Also, check out PlayOnLinux which is also available in the Software Centre, makes installing games and setting up Wine correctly much easier).


404

---

### Post by 101kitty on 2013-01-14
```
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```

---

### Post by 101kitty on 2013-01-14
It worked thanks to:                                  [TOMBSTONEV2]("http://ubuntuforums.org/member.php?u=1766024")                                               
              

             

                                                           

                                                   
 ```

     sudo apt-get autoremove wine 
    
     sudo apt-get update 
   
     sudo apt-get autoclean 
 
     sudo apt-get clean 
 
     sudo apt-get autoremove 
   
     sudo apt-get install wine
```

---

