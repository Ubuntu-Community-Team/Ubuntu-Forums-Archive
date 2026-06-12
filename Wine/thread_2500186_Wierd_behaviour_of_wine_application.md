---
title: "Wierd behaviour of wine application"
date: 2024-08-25
forum: Wine
---

### Post by nariub on 2024-08-25
so first the setup
ubuntu 22.04.4 running wine 9 from winehq
and a really old version of qwicken2000 
works fine 

so i got a new laptop (old 6540 dell to new 7490 dell) 
went through a new docking station and setup etc.. 
got the new laptop up and working installed all my software
then moved the Home directory from the old laptop to the new laptop

```
tar -czvf MYTARBALL.tar.gz /home/<myusername> 

```
on the new laptop

```
tar -xzvf MYTARBALL.tar.gz -C /
```

and everything was fine
even remembered my open tabs in google chrome
put it throught the common function test and life was cool

so i technically have three monitors .. the laptop built in monitor, and two 32in big monitors running 1080p
since i work with the laptop lid closed 
i disabled the builtin laptop monitor   all fine still

now for the weird part
if i make my primary screen the left monitor (technically monitor 3)
my wine app (qwicken) doesnt display an app.. it goes through the motions but no app window appears   

if i make my primary screen the right monitor. then the app window shows up on monitor 3 (the left monitor)

feels weird.. 
anyone know what is going on under the hood on that..   i can live with the primary on the right but still feels arbitrary ya know

---

