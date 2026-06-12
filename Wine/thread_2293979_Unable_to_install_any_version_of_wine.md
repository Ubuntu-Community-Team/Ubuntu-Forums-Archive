---
title: "Unable to install any version of wine"
date: 2015-09-08
forum: Wine
---

### Post by chfakht on 2015-09-08
Hi ,[COLOR=#111111][FONT=Ubuntu]i'm using UBUNTU 14.04 , and i want to install wine1.6 since it the latest stable version , i tried from the command line[/FONT][/COLOR]
i tried 

sudo apt-get install wine1.6
sudo apt-get install wine1.7 [COLOR=#111111][FONT=Ubuntu]i get :[/FONT][/COLOR]

The following packages have unmet dependencies :
wine : Depends : wine1.6 but will not be installed or wine1.7 but will                                     
not be installed E: Unable to correct problems , defective packets are    
mode " keep state
[COLOR=#111111][FONT=Ubuntu]when trying to install it from the software center i get this :           
[/FONT][/COLOR]apt://wine1.7

    The following packages have unmet dependencies:
wine1.7: Depends: wine1.7-amd64 (= 1:1.7.50-0ubuntu1) but 1:1.7.50-0ubuntu1 is to be installed
         Depends: wine1.7-i386 (= 1:1.7.50-0ubuntu1) but it is a virtual package
[HR][/HR]apt://wine1.6
    The following packages have unmet dependencies:
    wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4) but 1:1.6.2-0ubuntu4 is to be installed
             Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4) but it is a virtual package7

[COLOR=#111111][FONT=Ubuntu] i have tried to install wine 1.6.2 from the source too : 

[/FONT][/COLOR]
./configure
make 
sudo make install
[COLOR=#111111][FONT=Ubuntu]after that it seems that wine haven't been installed because when typing wine i get :[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
wine: command not found

Any hints please ):P i have been looking for a solution more than a week but without any luck :p
i'm under ubuntu 14.04 x64bits

---

### Post by albaniaguard on 2015-09-09
try this: 
sudo apt-get autoremove 
and leater dowland the wine from here [https://www.winehq.org/download/](https://www.winehq.org/download/) and try to install from softwere center
 hope work :)

---

### Post by chfakht on 2015-10-09
thanks i tried that but didn't work : got the same errors, any other suggestions 
[[IMG]http://s13.postimg.org/ipul910f7/Wine_Problem.jpg[/IMG]]("http://postimg.org/image/ipul910f7/")

[http://s13.postimg.org/oe0vzx4rr/Wine_Problem.png](http://s13.postimg.org/oe0vzx4rr/Wine_Problem.png)

---

